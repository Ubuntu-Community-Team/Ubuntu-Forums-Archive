---
title: "Modifying the Linux Process Scheduler to be nonpreemptive"
date: 2009-11-04
forum: Ubuntu Dev Link Forum
---

### Post by AcerAspirant on 2009-11-04
Hello, I've been tasked to modify the Ubuntu kernel's process scheduler in order to have to work non-preemptively.  Does anyone know where I should start in terms of a guide to the scheduler and how to modify it so I will know where to begin?

---

### Post by jabl on 2009-11-04
Open a terminal, type

```

$ grep PREEMPT /boot/config-2.6.31-14-generic

```(or some other filename if you're using an older Ubuntu version). Then you check the output of the command and see that CONFIG_PREEMPT is not set. Finally, report success. :D

You'll see that by default an option called CONFIG_PREEMPT_VOLUNTARY is set, however, that is incredibly badly named as it's not actually about preemption.

EDIT: Now that I think about it, actually you probably meant preemptability of user space processes, not kernel space, so forget what I wrote above. For user space, I'm not sure it makes sense at all. E.g. what happens when you get an interrupt? Are you just going to ignore it? Well, the PREEMPT_RT kernel allows user space processes with realtime priority to run at higher priority than most of the kernel (except for things like, well, hard irq handlers and the scheduler itself), but that's not really what you're asking for either.

---

### Post by AcerAspirant on 2009-11-08
Is there anything in sched.c that would be useful for it?

---

### Post by jabl on 2009-11-20
> **AcerAspirant said:**
> Is there anything in sched.c that would be useful for it?

Maybe. Now, why do I get this feeling that you're rushing headlong into this without realizing the consequences? What are the actual high-level requirements that led to the decision to try to make user space processes non-preemptive?  To strictly answer your question, what you need to do in order to make user space processes non-preemptive, is to disable or mask all interrupts before returning to user space. Also, you presumably need to poll the interrupts at some suitable point (assuming you ever arrive at such a point, which is doubtful), since they are then normally masked. But, don't you realize this will make the system more or less completely unusable? Unix, and by extension Linux, was always designed as a preemptive multitasking OS; user space applications are not written with the assumption that they must voluntary yield in order to allow other applications or the kernel to run.

---

### Post by Maz_ on 2010-01-30
If your purpose is to grant more scheduling time to some userspace process, while still allowing it to be preempted by kernel threads, interrupts and so on - which makes sense sometimes - you can consider using SCHED_FIFO with high priority. But it can still be interrupted by some kernel threads, interrupts and so on. However no SCHED_OTHER scheduled userspace process (or even SCHED_FIFO process with lower priority) can do this. However great care must be taken. Such a process can easily cause starvation, and forgetting to yield the task occasionally will make even shell to be non responsive => you cannot kill your app.

If you really want to make your userspace app to preempt kernel, you may want to look RTAI linux. 
Oh, RT linux would allow you to do this quite effectively, only a few interrupts will preempt RT threads.


Sorry for resurrecting this old thread, I just entered this forum first time, and did not realize this place is not so frequently used :/

---

### Post by Emanuele_Z on 2010-01-31
Hi guys, I think the idea to have a RT preemptive kernel would be great for games et similia.
Is there a way to enable this without recompiling the kernel?
If yes, how?
Otherwise, what are the steps to recompile it this way?

Cheers.

---

### Post by Maz_ on 2010-01-31
RTLinux (if we are talking about same thing), is not just linux. It is a specific microkernel running under linux kernel, and executing linux as one of it's own low priority threads. So with it you can write regular linux SW using POSIX API, which will be executed in linux's user space. But you can also write realtime threads that will be executed on top of the RT microkernel, parallel to the thread executing linux kernel + applications.

These microkernel threads (realtime threads) need to be inserted as kernel modules, and they share the kernel resources && HW is visible to them. The full posix api is not available when writing the RT thread either. Thus they're far from being optional to being used in gaming. A bug in your pacman could crash the whole kernel...

---

### Post by Emanuele_Z on 2010-01-31
> **Maz_ said:**
> RTLinux (if we are talking about same thing), is not just linux. It is a specific microkernel running under linux kernel, and executing linux as one of it's own low priority threads. So with it you can write regular linux SW using POSIX API, which will be executed in linux's user space. But you can also write realtime threads that will be executed on top of the RT microkernel, parallel to the thread executing linux kernel + applications.

These microkernel threads (realtime threads) need to be inserted as kernel modules, and they share the kernel resources && HW is visible to them. The full posix api is not available when writing the RT thread either. Thus they're far from being optional to being used in gaming. A bug in your pacman could crash the whole kernel...

Thanks mate.
No, I would like to actually maybe give a quicker response to processes (instead of calling the scheduler 1/100 sec, like 1/1000 sec).
I don't know how is the Linux scheduler implemented, which algorithm it does use, but I'd like to keep my *top* priority processes in the *execute* queue basically always.

Cheers,

---

### Post by Maz_ on 2010-02-02
I would love to see this happening too - when I am at work. At home I prefer current responsiveness.

Originally linux was developed in time, when multitasking did not play such a big role. Also it was (and still is not) really planned to be a realtime system. Hence there are only certain points where process can be interrupted. With new 2.6 kernels the responsiveness has improved a lot though.

But when we look the issue a bit deeper, we'll notice that:
Every time the OS decides if it is a good idea to change task that is running, it will have to do some work, like check if the change is needed. More we do such things, more we waste precious time. Also, more often we actually do context switches, more overhead we will get from task changing, more we will end up wasting cached data, and so on. So basically, improving responsiveness means losing some of the performance. That is the deal.

However:
> I don't know how is the Linux scheduler implemented, which algorithm it does use, but I'd like to keep my *top* priority processes in the *execute* queue basically always.
That you can achieve, assuming you write your top priority processes yourself, and assuming you're willing to live with constraint that these processes need to be started as root. You can set the scheduling per thread.

The default scheduling policy on linux is the SCHED_OTHER. And almost all userspace apps do use this timeslice scheduler. But you have also SCHED_RR and SCHED_FIFO in use, which are purely priority based schedulers. And processes set to run under SCHED_FIFO or SCHED_RR will always preempt SCHED_OTHER processes. But there is a danger too. Especially with SCHED_FIFO.

SCHED_FIFO does not let SCHED_OTHER processes run, or smaller or same priority SCHED_RR or SCHED_FIFO processes either, untill it yields itself (Eg, blocks to wait something/sleeps). Thus you can end up halting your whole system if you're not carefull.

---

### Post by Emanuele_Z on 2010-02-02
Thanks mate, that is clear.
My question was about games. Basically what would you recommend to set a game process in order to be *really* top priority?
Honestly I don't want to fiddle around with the kernel+recompiling...

Btw nice blog, I'll take a look (I'm a C/C++ dev/fan)!
Cheers,

---

### Post by Maz_ on 2010-02-03
For already compiled binary of a game, the best thing I can instruct is to use renice to change the nice value.

For a game you're writing, you can use SCHED_FIFO/SCHED_RR scheduling - for most time critical threads. But chaging scheduler to FIFO / RR requires root privileges, so it may not be a good idea for a game. Not everyone want to install a game with root user. But it still is an option. If you want to go that road, look for pthread_setschedparam().

---

### Post by DreamKaka on 2012-04-06
Hello Iam new to linux kernel development and I am implementing scheduler for multi-core system and I have understood the sched.c file dut I require to calculate process dependency so how can I calculate process dependencies.Can anybody help me:p

---

