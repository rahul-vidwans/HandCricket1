#include <stdio.h>
#include <stdlib.h>
#include <time.h>
int main() {

    int playerScore = 0;
    int computerScore = 0;
    int playerRuns = 0;
    int computerRuns = 0;
    
    srand(time(NULL));

    printf("Welcome to Hand Cricket Game (One Player)\n");

    while (1) {
        int playerChoice, computerChoice;

        printf("\nYour turn to bat! Enter your choice (1-6): ");
        scanf("%d", &playerChoice);

        if (playerChoice < 1 || playerChoice > 6) {
            printf("Invalid input. Please enter a number between 1 and 6.\n");
            continue;
        }

        computerChoice = 1 + rand() % 6;
        printf("Computer bowls %d\n", computerChoice);

        if (playerChoice == computerChoice) {
            printf("Out! Your innings is over.\n");
            break;
        } else {
            playerRuns += playerChoice;
            printf("Your score: %d/%d\n", playerRuns, playerScore);
        }
    }

    printf("Your final score: %d\n", playerRuns);
    printf("\nComputer is batting...\n");
    while (computerScore <= playerRuns) {
        int computerChoice = 1 + rand() % 6;
        int playerChoice;

        printf("You bowl %d: ", computerChoice);
        scanf("%d", &playerChoice);

        if (playerChoice < 1 || playerChoice > 6) {
            printf("Invalid input. Please enter a number between 1 and 6.\n");
            continue;
        }

        if (playerChoice == computerChoice) {
            printf("Out! Computer's innings is over.\n");
            break;
        } else {
            computerRuns += computerChoice;
            printf("Computer score: %d/%d\n", computerRuns, computerScore);
        }
    }

    printf("Computer's final score: %d\n", computerRuns);

    if (playerRuns > computerRuns) {
        printf("Congratulations! You win!\n");
    } else if (playerRuns < computerRuns) {
        printf("Computer wins! Better luck next time.\n");
    } else {
        printf("It's a tie!\n");
    }

    return 0;
}
