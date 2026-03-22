# HOTEL-MANAGMENT-.C
#include <stdio.h>
#include <string.h>

struct Hotel {
    int roomNumber;
    char name[50];
    int days;
};

struct Hotel rooms[100];
int count = 0;

void addBooking() {
    printf("Enter Room Number: \n");
    scanf("%d", &rooms[count].roomNumber);

    printf("Enter Customer Name: ");
    scanf("%s", rooms[count].name);

    printf("Enter Number of Days: ");
    scanf("%d", &rooms[count].days);

    count++;

    printf("Booking Added Successfully!\n");
}

void showBookings() {
    if(count == 0) {
        printf("\nNo bookings available.\n");
        return;
    }

    printf("\nRoomNo\tName\tDays\n");

    for(int i = 0; i < count; i++) {
        printf("%d\t%s\t%d\n", rooms[i].roomNumber, rooms[i].name, rooms[i].days);
    }
}

void searchCustomer() {
    char name[50];
    int found = 0;

    printf("\nEnter customer name to search: ");
    scanf("%s", name);

    for(int i = 0; i < count; i++) {
        if(strcmp(rooms[i].name, name) == 0) {
            printf("\nCustomer Found!\n");
            printf("Room Number: %d\n", rooms[i].roomNumber);
            printf("Days: %d\n", rooms[i].days);
            found = 1;
        }
    }

    if(found == 0) {
        printf("Customer not found.\n");
    }
}

int main() {
    int choice;

    while(1) {
        printf("\n--- Hotel Management System ---\n");
        printf("1. Add Booking\n");
        printf("2. Show Bookings\n");
        printf("3. Search Customer\n");
        printf("4. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                addBooking();
                break;
            case 2:
                showBookings();
                break;
            case 3:
                searchCustomer();
                break;
            case 4:
                printf("Thank you!\n");
                return 0;
            default:
                printf("Invalid choice.\n");
        }
    }

    return 0;
}
