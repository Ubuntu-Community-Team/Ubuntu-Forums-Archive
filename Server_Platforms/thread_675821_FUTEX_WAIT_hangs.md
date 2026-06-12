---
title: "FUTEX_WAIT hangs"
date: 2008-01-23
forum: Server Platforms
---

### Post by hlynur on 2008-01-23
Hello,
On a dapper (6.06) we have a problem with a concurrent network server (parent forks off a child to do the real work).

The problem looks like this in the process table:
root     20000     1  0 Nov27 ?        00:00:35 /usr/bin/replychan -h peer -s 
servicename -l logdir -d

root     11250 20000  0 Dec01 ?        00:00:00 [replychan] <defunct>

As you can see the child process ends up in a defunct state.

Here is an strace of the parent process:
strace -p 20000
Process 20000 attached - interrupt to quit
futex(0xb7f3a9cc, FUTEX_WAIT, 2, NULL <unfinished ...>
Process 20000 detached

At this point you can restart the service and everything works again. However, 
this should not be necessary. 

The concurrent server uses the normal system calls (like bind, accept, fork 
etc.) but not the futex call. The futex calls seem to be for synchronisation 
purposes (semaphores around the fork etc.) which makes good sense.

In a test setup (5 runs) we were able to reproduce the problem after the 
following number of forks:
155.374
 24.635
668.920
502.345
303.190

On the Internet we can find all sorts of descriptions of what seems to be the 
precise same problem:
for instance [http://lwn.net/Articles/124747/](http://lwn.net/Articles/124747/)

From descriptions it seems the problem has been resolved as of kernel 2.6.17 
but when we tried to update the kernel to 2.6.20 the problem did NOT go away. 
We suspect that futexes may necessitate an update to glibc etc.

Does anybody have an idea of what to do ? Thank you in advance.

Best regards,

Hlynur

---

### Post by hlynur on 2008-01-28
The problem seems to be associated with NPTL instead of LinuxThreads when 2.6 kernel is used. If I set the environment variable LD_ASSUME_KERNEL=2.4.1 the problem disappears (because LinuxThreads is used). Note that
NPTL uses futex for mutex protection, instead LinuxThreads uses
signal. The  LD_ASSUME_KERNEL=2.4.1 hack works on dapper, but not on feisty and gutsy. 

Here is a small test program that will deadlock under 2.6 but works if you force it to use LinuxThreads try to run it cuple of times ..  see ctime-hang.c

see also  

[http://lists.infodrom.org/infodrom-sysklogd/2007/0015.html](http://lists.infodrom.org/infodrom-sysklogd/2007/0015.html)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=301511](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=301511)

___________________________ ctime-hang.c ___________

#include <sys/time.h>
#include <time.h>
#include <signal.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>

volatile char *r;

void handler(int sig)
{
    time_t          t;

    time(&t);
    r = ctime(&t);
}

int main()
{
    struct itimerval    it;
    struct sigaction    sa;
    time_t          t;
    int counter = 0;

    memset(&sa, 0, sizeof(sa));
    sa.sa_handler = handler;
    sigaction(SIGALRM, &sa, NULL);

    it.it_value.tv_sec = 0;
    it.it_value.tv_usec = 1000;
    it.it_interval.tv_sec = 0;
    it.it_interval.tv_usec = 1000;
    setitimer(ITIMER_REAL, &it, NULL);

    while(1) {
        counter++;
        time(&t);
        r = ctime(&t);
        printf("Loop %d\n",counter);
    }


    return 0;
}

---

