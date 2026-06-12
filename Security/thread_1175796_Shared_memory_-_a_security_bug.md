---
title: "Shared memory - a security bug?"
date: 2009-06-01
forum: Security
---

### Post by blingo on 2009-06-01
Hello,
Created a program that creates Shared Memory Segment using the function 'shmget' then exit, and doesn't release it on before exiting.
Created a script to run the program 10000 times.

effects:
1) I see more and more Shared Memory Segments being created using the command 'icps -a'

2) After some time Ubuntu tried to close/restart(!?) and some applications disappeared/damaged  (compiz, etc')

Is this a security bug?

Working on:
Ubuntu 8.04.2

kernel:
2.6.24-24-generic

Thanks.

---

### Post by sisco311 on 2009-06-01
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/182960]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/182960")

---

### Post by blingo on 2009-06-01
Thanks for the link.
This is not what I'm talking about.
In my case the program already exited yet the memory is not released, in the case you've linked, the program consumes only when running.

---

### Post by whoop on 2009-06-02
> **blingo said:**
> Hello,
Created a program that creates Shared Memory Segment using the function 'shmget' then exit, and doesn't release it on before exiting.
Created a script to run the program 10000 times.

effects:
1) I see more and more Shared Memory Segments being created using the command 'icps -a'

2) After some time Ubuntu tried to close/restart(!?) and some applications disappeared/damaged  (compiz, etc')

Is this a security bug?

Working on:
Ubuntu 8.04.2

kernel:
2.6.24-24-generic

Thanks.

I'm far more worried that ubuntu tried to close/restart? Did it crash? Was it using swap at the time?

---

### Post by blingo on 2009-06-02
Much thanks for the reply.

I'll start by saying that I just re-run the experiment, same results:

* When using ipcs -a I see my lot's of memory segments.

* At some time, the program I run which requests shared memory segments returns with a failure to allocate (which is fine)

* Then when writing this on Firefox (started by saying that all was o.k... , the screen blanked, I've got back to log-in screen, then when re-entering,
the tool-bars (all of them, the lower, the upper, etc') were gone. have a keyboard-key opening terminal that worked so I've shutdown from there, and all is o.k again, the lot's of memory shared segments are gone from ipcs -a. 

I assume that this can be recreated with a simple shmget requesting, not releasing before exit, program, that is runed in a loop by shell. (hope to upload something like this when I'll have more time, can't upload the original program)

No there was no swapping, the system was  quiet, and nothing happened until the blank and log-in. I've heard the hard-drive only during the blank and log-in screen. (I believe if I remember correctly that the cpu/memory on 'top' didn't show anything remotely to stress the system).

My theory - I estimate that some of the programs I use wanted some shared memory, and couldn't get it. but I don't know which, nor how to find out. 
 
Have compiz b.t.w (just adding some info about my system)

Much thanks.

---

