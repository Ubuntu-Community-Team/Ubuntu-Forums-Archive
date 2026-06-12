---
title: "pthread_cond_signal() and pthread_cond_wait() call hangs on ubuntu 18.04, 20.04"
date: 2021-03-25
forum: Ubuntu Application Development
---

### Post by teammeilinux on 2021-03-25
[SIZE=2][FONT=Calibri][FONT=arial]Following application program executes successfully on Ubuntu 16.04. 
[/FONT][/FONT][/SIZE][FONT=Calibri][SIZE=3][FONT=arial][SIZE=2]But a HANG condition is observed on Ubuntu 18.04, and [FONT=Calibri][FONT=arial]Ubuntu [/FONT][/FONT]20.04.[/SIZE]
[/FONT][/SIZE][/FONT]
[SIZE=2][FONT=Calibri][FONT=arial]The application program contains two parts Sender and Receiver.[/FONT][/FONT]

[FONT=Calibri][FONT=arial]Below are the steps to reproduce the problem.[/FONT][/FONT]
[/SIZE]
[LIST=1]
[*][SIZE=2][FONT=Calibri][FONT=arial]Execute the "Sender" application program with command [FONT=Calibri][FONT=arial]"./Sender_Receiver Sender Init" on new terminal[/FONT][/FONT][/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial]Observe prints on the terminal after every 5 seconds to confirm that [FONT=Calibri][FONT=arial][FONT=Calibri][FONT=arial]Sender[/FONT][/FONT][/FONT][/FONT] [FONT=Calibri][FONT=arial]application [/FONT][/FONT]is sending the  signal[/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial]Execute the "[FONT=Calibri][FONT=arial]Receiver[/FONT][/FONT]" application program with command [FONT=Calibri][FONT=arial]"[FONT=Calibri][FONT=arial]./Sender_Receiver Receiver[/FONT][/FONT]" on new terminal[/FONT][/FONT][/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial]Observe prints on the terminal after every 5 seconds to confirm that [FONT=Calibri][FONT=arial]Receiver[/FONT][/FONT] [FONT=Calibri][FONT=arial]application [/FONT][/FONT]is receiving the  signal[/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial]Terminate the "Receiver" application using (ctrl + c). This will terminate the [FONT=Calibri][FONT=arial]Receiver application.[/FONT][/FONT][/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial]Observe prints on the Sender terminal after every 5 seconds to confirm that [FONT=Calibri][FONT=arial][FONT=Calibri][FONT=arial]Sender[/FONT][/FONT][/FONT][/FONT] [FONT=Calibri][FONT=arial]application [/FONT][/FONT]still sending the  signal and running[/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial]Again Execute the "[FONT=Calibri][FONT=arial]Receiver[/FONT][/FONT]" application program with command [FONT=Calibri][FONT=arial]"[FONT=Calibri][FONT=arial]./Sender_Receiver Receiver[/FONT][/FONT]" on terminal[/FONT][/FONT][/FONT][/FONT]
[/SIZE] 
[*][SIZE=2][FONT=Calibri][FONT=arial][FONT=Calibri][FONT=arial]Observe prints on the Sender and [FONT=Calibri][FONT=arial]Receiver [/FONT][/FONT]terminals, [/FONT][/FONT]The "Sender" and "Receiver" application will be observed in the HANG condition [FONT=Calibri][FONT=arial]on Ubuntu 18.04, and [FONT=Calibri][FONT=arial]Ubuntu [/FONT][/FONT]20.04.[/FONT][/FONT][/FONT][/FONT][/SIZE] 
[/LIST]
[SIZE=2][FONT=Calibri][FONT=arial][FONT=Calibri][FONT=arial]Note:- For the same steps, the application program works normally when executed [SIZE=2][FONT=Calibri][FONT=arial] on Ubuntu 16.04.[/FONT][/FONT][/SIZE][/FONT][/FONT][/FONT][/FONT][/SIZE]

[SIZE=2][FONT=Calibri][FONT=arial]Command used to build the code: gcc -g -Wall Sender_Receiver.cpp -o Sender_Receiver  -L /lib -lrt -lpthread
[SIZE=2][FONT=Calibri][FONT=arial]Command used to execute Sender application: [/FONT][/FONT][/SIZE]./Sender_Receiver Sender Init
[SIZE=2][FONT=Calibri][FONT=arial][SIZE=2][FONT=Calibri][FONT=arial]Command used to execute [SIZE=2][FONT=Calibri][FONT=arial][FONT=Calibri][FONT=arial]Receiver[/FONT][/FONT][/FONT][/FONT][/SIZE] application: [/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE]./Sender_Receiver Receiver
[/FONT][/FONT][/SIZE]
Can any one suggest the reason for the [SIZE=2][FONT=Calibri][FONT=arial]HANG condition [FONT=Calibri][FONT=arial]on Ubuntu 18.04, and [FONT=Calibri][FONT=arial]Ubuntu [/FONT][/FONT]20.04 with the probable solution. 
[/FONT][/FONT][/FONT][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][FONT=arial]Code in the Sender_Receiver.cpp as below,
[/FONT][/FONT][/SIZE]
```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <unistd.h>
#include <string.h>
#include <time.h>
#include <sys/mman.h>
#include <sys/stat.h>        
#include <fcntl.h>           
#include <pthread.h>
#include <cerrno>
#include <sys/time.h>
#include <limits.h>


#define     SHM_DIR_PATH    "/dev/shm/"
#define     ERROR            -1


/* share memory access using MMAP */
void mmap_wrapper(void** vppPtr, unsigned int uiMemorySize, char* cpMemoryName)
{
    int iFdShm = ERROR;
    char cShmPath[NAME_MAX] = { 0 };
    int iRet = ERROR;
    void* vpMmapPtr = NULL;

    /* Sanity Check for pointer*/
    if(vppPtr == NULL)
    {
        printf("\nvppPtr Error");
    }
    /* Sanity Check memory size*/
    if(uiMemorySize < 1)
    {
        printf("\nuiMemorySize Error");
    }
    /* Sanity Check memory name pointer*/
    if(cpMemoryName == NULL)
    {
        printf("\ncpMemoryName Error");
    }
    /* Sanity Check memory name string size */
    if( (strlen(cpMemoryName) + strlen(SHM_DIR_PATH)) >= NAME_MAX)
    {
        printf("\ncpMemoryName Error");
    }

    /* Open share memory object */
    iFdShm = shm_open(cpMemoryName, O_CREAT | O_RDWR, ACCESSPERMS);
    if(iFdShm == ERROR)
    {
        printf("\nError during shm_open()");
        printf("\nError:%d: %s",errno, strerror(errno));
    }

    /* Create file name with particular path SHM_DIR_PATH*/
    strcpy(cShmPath, SHM_DIR_PATH);
    strcat(cShmPath, cpMemoryName);

    /* Change permission of the file*/
    iRet = chmod(cShmPath, ACCESSPERMS);
    if(iRet == ERROR)
    {
        printf("\nError during chmod()");
        printf("\nError:%d: %s",errno, strerror(errno));
    }

    /* truncate the file as per the required memory size */
    iRet = ftruncate(iFdShm, uiMemorySize);
    if(iRet == ERROR)
    {
        printf("\nError during ftruncate()");
        printf("\nError:%d: %s",errno, strerror(errno));
    }

    /* map the shared memory in the processes address space*/
    vpMmapPtr = mmap(0, uiMemorySize, PROT_WRITE, MAP_SHARED, iFdShm, 0);
    if(vpMmapPtr == MAP_FAILED)
    {
        printf("\nError during mmap()");
        printf("\nError:%d: %s",errno, strerror(errno));
    }

    /* close the file */
    iRet = close(iFdShm);
    if(iRet == ERROR)
    {
        printf("\nError during close()");
        printf("\nError:%d: %s",errno, strerror(errno));
    }

    /* return the shared memory pointer */
    (*vppPtr) = vpMmapPtr;
}


int main(int argc, char *argv[])
{
    printf("\nExecuting_main");

    if( argc == 3 )
    {
       printf("\nThe argument supplied is %s\t%s\n", argv[1],argv[2]);
    }
    else if( argc == 2 )
    {
       printf("\nThe argument supplied is %s\n", argv[1]);
    }
    else if( argc > 3 )
    {
       printf("\nToo many arguments supplied.\n");
    }
    else
    {
       printf("\nOne argument expected.\n");
    }

    /* condition variable shared between Sender process and Receiver process */
    pthread_cond_t *shmVar;
    mmap_wrapper((void**)&shmVar, sizeof(pthread_cond_t),(char*)"shmVar");

    /* mutex shared between Sender process and Receiver process */
    pthread_mutex_t *shmVarMutex;
    mmap_wrapper((void**)&shmVarMutex, sizeof(pthread_mutex_t),(char*)"shmVarMutex");

    if(( argc == 3 ) && (strcmp(argv[2],"Init") == 0))
    {
        printf("\n%s::Init",argv[2]);

        pthread_condattr_t attr;
        pthread_condattr_init(&attr);
        pthread_condattr_setpshared(&attr, PTHREAD_PROCESS_SHARED);
        pthread_cond_init(shmVar, &attr);

        pthread_mutexattr_t attr1;
        pthread_mutexattr_init(&attr1);
        pthread_mutexattr_setpshared(&attr1, PTHREAD_PROCESS_SHARED);
        pthread_mutex_init(shmVarMutex, &attr1);
    }

    if(strcmp(argv[1],"Sender") == 0)
    {
        printf("\nSender::LoopStarting");

        while(1)
        {
            sleep(5);
            printf("\nSender::Locking");
            pthread_mutex_lock(shmVarMutex);
            printf("\nSender::Locked");

            printf("\nSender::Sending");
            pthread_cond_signal(shmVar);
            printf("\nSender::Sent");

            printf("\nSender::Unlocking");
            pthread_mutex_unlock(shmVarMutex);
            printf("\nSender::Unlocked");
        }

    }

    else if(strcmp(argv[1],"Receiver") == 0)
    {
        int iRet = ERROR;
        
        printf("\nReceiver::LoopStarting");
        while(1)
        {

            printf("\nReceiver::Locking");
            pthread_mutex_lock(shmVarMutex);
            printf("\nReceiver::Locked");

            printf("\nReceiver::Waiting");
            if((iRet = pthread_cond_wait(shmVar, shmVarMutex)) == 0)
            {
                printf("\nReceiver::Received");
            }

            printf("\nReceiver::Unlocking");
            pthread_mutex_unlock(shmVarMutex);
            printf("\nReceiver::Unlocked");
        }
    }
    printf("\nExiting_main");
}

```

---

