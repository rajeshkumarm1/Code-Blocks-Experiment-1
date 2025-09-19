# Code-Blocks-Experiment-1
Implementation of Go-Back-N Protocol – Sliding Window

🎯 Aim

To write and execute a program for the Go-Back-N protocol using the sliding window technique.

🛠️ Equipments Required

• 	Personal Computer

• 	Turbo C Compiler

📋 Procedure
1. 	Connect two computers in a Wired/Wireless LAN.
2. 	Ensure both machines are on the same network and can ping each other.
3. 	Open a new C file in Code::Blocks or any C IDE and type the program.
4. 	Navigate to:
Project -> Properties -> Project Build Options -> Linker Settings
Add: netproto and pthread
5. 	Execute the program on both server and client machines.
6. 	Enter:
• 	IP address of the remote machine
• 	Port address of both local and remote machines
• 	Error rate
7. 	Choose the file and verify the Go-Back-N protocol operation.

💻 Program
#include <stdio.h>
#define WINDOW_SIZE 4

int main() {
    int i, window_start = 1, ack;
    int n;

    printf("SLIDING WINDOW PROTOCOL\n");
    printf("GO BACK N ARQ\n");

    printf("Enter the number of frames to send: ");
    scanf("%d", &n);

    char frame[n + 1][10];  // frame[1] to frame[n]

    for (i = 1; i <= n; i++) {
        printf("Enter content for frame %d: ", i);
        scanf("%s", frame[i]);
    }

    while (window_start <= n) {
        printf("\nSending frames in window:\n");

        for (i = window_start; i < window_start + WINDOW_SIZE && i <= n; i++) {
            printf("Sending Frame %d: %s\n", i, frame[i]);
        }

        printf("\nEnter the frame number that did NOT receive ACK (0 if all received): ");
        scanf("%d", &ack);

        if (ack == 0) {
            printf("All frames ACKed. Sliding window forward by %d.\n", WINDOW_SIZE);
            window_start += WINDOW_SIZE;
        } else if (ack >= window_start && ack < window_start + WINDOW_SIZE) {
            printf("No ACK for Frame %d. Go-Back-N triggered.\n", ack);
            printf("Resending frames from Frame %d...\n", ack);
            window_start = ack;
        } else {
            printf("Invalid ACK frame number.\n");
        }
    }

    printf("\nAll frames sent successfully.\n");
    return 0;
}

🖥️ Sample Output
<img width="1280" height="719" alt="image" src="https://github.com/user-attachments/assets/d219d0a3-b75a-4d32-824f-6a86add62a04" />

✅ Result

Thus, the Go-Back-N protocol using the sliding window technique was successfully implemented and verified.
