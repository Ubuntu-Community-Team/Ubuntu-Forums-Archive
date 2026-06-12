---
title: "Processes with many threads, top -H gkrellm"
date: 2008-04-14
forum: Security Discussions
---

### Post by ShawnS on 2008-04-14
Hi to the Forum!
I noticed that gkrellm an top showed different quantities of processes. Then i realized that running top with the -H option would eliminate the discrepancy between top and gkrellm. So now i know that the individual processes are themselves split into many threads.

I got curious about this phenomenon because i'm sure that it wasn't there all the time. On my debian machine gkrellm, top and top -H show always the same amount of processes. :confused:

Is it possible that my parallel installation of kubuntu, mythbuntu and xubuntu to ubuntu or my installation of compiz was the cause for the processes being split in so many threads ?

Is there a security problem ?

---

### Post by ShawnS on 2008-04-15
I'll try to make myself more clear:

I installed Ubuntu

Top and gkrellm reported the same amount of running processes (about 120) like it is the case on my debian system

More then a year past in which I installed kubuntu, mythbuntu, (obviously xubuntu, can't remember that one) and compiz

I noticed that gkrellm shows nearly twice the amount of running processes (ca. 230) compared to the time when my system was a fresh Ubuntu installation. 

Running top with the '-H' option now reports ca. 230 running processes as well.

Does someone have an idea where all these additional threads come from ?

---

### Post by roaldz on 2008-04-15
Processes are devided into threads, for example one thread for the gui of a program, one thread for the functions, processing and so on. Threads are devided over your processors or cores. This means the more threads you have, the better your dual-core cpu is used.
This is by no means a security thread.

---

### Post by ShawnS on 2008-04-15
Ok, if you say that's all right i'm more calm now.
I just don't understand why the number of threads exploded so abruptly (from 120 to 230) but maybe i missed something that i configured by myself.
Thanks a lot for your reply!

Greets S.

---

### Post by roaldz on 2008-04-15
You probably didn´t configure that yourself, and you probably don´t want to do that either. Most processes spawn more than one thread, so if all your 130 processes spawn 2 threads, its 260 threads in total. 230 is less than that. Believe me, your system behaves just like it should.
I´m wishing for more threads myself! The more threads, the better your dual/quad-core will do the job:)

---

