---
title: "Quick question about ps"
date: 2011-05-23
forum: The Cafe
---

### Post by alem189 on 2011-05-23
Just something I've always been curious about: Why do some processes have numbers after their names, like ksoftirqd/0
or aio/0? I've only seen 1 and 0, and only on processes in single or double digits. Is it only on kernel processes or something?

---

### Post by itguy1985 on 2011-05-23
> **alem189 said:**
> Just something I've always been curious about: Why do some processes have numbers after their names, like ksoftirqd/0
or aio/0? I've only seen 1 and 0, and only on processes in single or double digits. Is it only on kernel processes or something?

It's a process tree. If I remember correctly. Programs started by root have 0s, the ones started by your session will be ones, and if those programs start a program they would be 2s and so on. I've only had one quarter of Linux, so this may be wrong, but I'm pretty sure that's the way it works. I think Windows has it too, not sure though.

---

### Post by itguy1985 on 2011-05-23
> **hija.hejab said:**
> Yes, if they co-sign. The interest will be high but with their good  credit it can be done easily. The question should be can you afford the  payment, insurance, :o

:-k

---

### Post by FuturePilot on 2011-05-23
> **hija.hejab said:**
> Yes, if they co-sign. The interest will be high but with their good  credit it can be done easily. The question should be can you afford the  payment, insurance, :o

WAT? :confused:

---

### Post by alem189 on 2011-05-25
> **itguy1985 said:**
> It's a process tree. If I remember correctly. Programs started by root have 0s, the ones started by your session will be ones, and if those programs start a program they would be 2s and so on. I've only had one quarter of Linux, so this may be wrong, but I'm pretty sure that's the way it works. I think Windows has it too, not sure though.

But if that were true, wouldn't all programs have numbers? The ones I've been talking about are ones at the very beginning of the list such as:

```

    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 migration/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns

```


Ones after that don't have them. Also, I've never seen a >1.

EDIT: Did hija-hejab post here and then get deleted or something? That's quite random.

---

### Post by itguy1985 on 2011-05-25
> **alem189 said:**
> But if that were true, wouldn't all programs have numbers? The ones I've been talking about are ones at the very beginning of the list such as:

```

    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 migration/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns

```
Ones after that don't have them. Also, I've never seen a >1.

EDIT: Did hija-hejab post here and then get deleted or something? That's quite random.
I think hija was a spam-bot. I cant remember; maybe root doesn't have a number, 0s are session and so on. I know it has something to do with a processes tree, unless I'm just completely way off.

---

### Post by lykwydchykyn on 2011-05-25
I'm pretty certain the numbers refer to processor cores -- those processes are presumably specific to core 0 or core 1.

Just checked one of my quad-core servers and the numbers go up to 3.  Also checked a single core and it only has /0 processes.

I have no other real proof, but that's my best guess.

---

### Post by itguy1985 on 2011-05-25
> **lykwydchykyn said:**
> I'm pretty certain the numbers refer to processor cores -- those processes are presumably specific to core 0 or core 1.

Just checked one of my quad-core servers and the numbers go up to 3.  Also checked a single core and it only has /0 processes.

I have no other real proof, but that's my best guess.

I must be thinking of something else.

---

### Post by NMFTM on 2011-05-25
> **lykwydchykyn said:**
> I'm pretty certain the numbers refer to processor cores -- those processes are presumably specific to core 0 or core 1. Just checked one of my quad-core servers and the numbers go up to 3.  Also checked a single core and it only has /0 processes.
Is there a way to switch which core a given app is running on like you can do in task manager on Windows 7?

---

### Post by matt_symes on 2011-05-25
Hi

> **lykwydchykyn said:**
> I'm pretty certain the numbers refer to processor cores -- those processes are presumably specific to core 0 or core 1.

Just checked one of my quad-core servers and the numbers go up to 3.  Also checked a single core and it only has /0 processes.

I have no other real proof, but that's my best guess.

I'm pretty sure this is correct as well. The /X (where X is a number) is the core the process is on.
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23848   356 ?        Ss   00:00   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    00:00   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    00:00   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    00:00   0:05 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    00:00   0:00 [watchdog/0]
```

Incidently, if my memory servers me correctly, processes wrapped in [XXX] as in the ones above are running in kernel space. The ones not enclosed in [] are user space processes.

Kind regards

---

### Post by alem189 on 2011-05-25
> **matt_symes said:**
> Hi



I'm pretty sure this is correct as well. The /X (where X is a number) is the core the process is on.
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23848   356 ?        Ss   00:00   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    00:00   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    00:00   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    00:00   0:05 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    00:00   0:00 [watchdog/0]
```

Incidently, if my memory servers me correctly, processes wrapped in [XXX] as in the ones above are running in kernel space. The ones not enclosed in [] are user space processes.

Kind regards

Thanks, that makes a lot of sense, as the relevant processes are always duplicated.

---

### Post by PhillyPhil on 2011-05-25
Now that that's been answered, I want to hijack the knowledge of people in this thread to ask something I'm a little embarrassed about not knowing:

The CPU scheduler schedules (kernel) threads, but what I want to know is can it schedule them completely independant of the process they are in, or can it only schedule threads *within* the time slice for the process (ie schedules processes first then threads within processes).

Or another way of asking:
Processes 1 and 2 both have two threads each: A and B.  Is it possible for the scheduler to schedule the four threads like this: 1A 2A 1B 2B? (single core)

---

