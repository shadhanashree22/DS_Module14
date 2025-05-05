# Ex10 Applications of Queue – FCFS
## DATE:26.2.25
## AIM:
To write a C function to calculate the turnaround time of each process given their burst time and waiting time in First Come first Serve scheduling algorithm.
## Algorithm
1.Start the program.

2.Read the number of processes.

3.Input the burst time for each process.

4.Calculate the waiting time for each process: Waiting time for the first process is 0. For other processes: 

5.waiting_time[i] = burst_time[i-1] + waiting_time[i-1]

6.Calculate the turnaround time for each process: turnaround_time[i] = burst_time[i] + waiting_time[i]

7.Display the waiting time and turnaround time for each process.

8.End the program.   

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: S V SHADHANASHREE
RegisterNumber:  212223230202
*/

#include <stdio.h>

void findTurnAroundTime(int processes[], int n, int bt[], int wt[], int tat[]) {
    for (int i = 0; i < n; i++)
        tat[i] = bt[i] + wt[i];
}

void findWaitingTime(int processes[], int n, int bt[], int wt[]) {
    wt[0] = 0; // waiting time for first process is 0

    // calculating waiting time
    for (int i = 1; i < n; i++)
        wt[i] = bt[i - 1] + wt[i - 1];
}

void findavgTime(int processes[], int n, int bt[]) {
    int wt[n], tat[n], total_wt = 0, total_tat = 0;

    findWaitingTime(processes, n, bt, wt);
    findTurnAroundTime(processes, n, bt, wt, tat);

    printf("\nProcesses  Burst time  Waiting time  Turnaround time\n");

    for (int i = 0; i < n; i++) {
        total_wt += wt[i];
        total_tat += tat[i];
        printf("   %d\t\t%d\t    %d\t\t%d\n", processes[i], bt[i], wt[i], tat[i]);
    }

    printf("\nAverage waiting time = %.2f", (float)total_wt / n);
    printf("\nAverage turnaround time = %.2f\n", (float)total_tat / n);
}

int main() {
    int n;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    int processes[n], burst_time[n];

    for (int i = 0; i < n; i++) {
        processes[i] = i + 1;
        printf("Enter burst time for process %d: ", i + 1);
        scanf("%d", &burst_time[i]);
    }

    findavgTime(processes, n, burst_time);
    
    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/9a38262a-5586-4a3a-bd62-e2635ddb2b6d)



## Result:
Thus, the C function to calculate the turnaround time of each process given their burst time and waiting time in First Come first Serve scheduling algorithm is implemented successfully.
