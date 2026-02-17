#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t child_pid;

    child_pid = fork();

    if (child_pid < 0) {
        perror("Fork failed");
        return 1;
    }
    else if (child_pid == 0) {
        // Child
        printf("Child process: PID=%d\n", getpid());

        execl("/bin/ls", "ls", "-l", NULL);

        perror("execl failed");
        return 1;
    }
    else {
        // Parent
        printf("Parent process: PID=%d\n", getpid());
        wait(NULL);
        printf("Child process finished.\n");
    }

    return 0;
}

output
Parent process: PID=4123
Child process: PID=4124
total 12
-rw-r--r-- 1 user user  120 Feb 17 file1.txt
-rwxr-xr-x 1 user user 8560 Feb 17 a.out
Child process finished.
