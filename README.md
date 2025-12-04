# To-Do-List-File-Operation
#include <stdio.h>

int main() {
    FILE *fptr;
    int choice;
    char text[50];

   while (1) {
        printf("\n--- TO-DO LIST MENU ---\n");
        printf("1. Write New List\n");
        printf("2. Add to List\n");
        printf("3. Read List\n");
        printf("4. Exit Program\n");
        printf("Enter your choice: ");
        
  if (scanf("%d", &choice) != 1) {
            while (getchar() != '\n'); 
            printf("Invalid input. Please enter a number.\n");
            continue;
        }

  if (choice == 4) {
            printf("Exiting To-Do List program.\n");
            break; 
        }

   else if (choice == 1) {
            fptr = fopen("todo.txt", "w");
            if (fptr == NULL) {
                printf("Error opening file!\n");
                continue;
            }
            printf("Enter your task: ");
            scanf("%s", text);
            fprintf(fptr, "%s\n", text);
            fclose(fptr);
            printf("New list created.\n");
        }
        
  else if (choice == 2) {
            fptr = fopen("todo.txt", "a");
            if (fptr == NULL) {
                printf("Error opening file!\n");
                continue;
            }
            printf("Enter task to add: ");
            scanf("%s", text);
            fprintf(fptr, "%s\n", text);
            fclose(fptr);
            printf("Task added.\n");
        }

   else if (choice == 3) {
            fptr = fopen("todo.txt", "r");
            if (fptr == NULL) {
                printf("File not found! (Add tasks first)\n");
                continue;
            }
            printf("\n--- List Content ---\n");
            while(fscanf(fptr, "%s", text) != EOF) {
                printf("%s\n", text);
            }
            fclose(fptr);
        }

  else {
            printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
