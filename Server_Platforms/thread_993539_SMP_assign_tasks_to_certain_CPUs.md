---
title: "SMP: assign tasks to certain CPUs"
date: 2008-11-25
forum: Server Platforms
---

### Post by wkitty42 on 2008-11-25
i've a dual PIII box that i'm trying to press into service and i want to do what i can to ensure that the servers running on it are assigned to to the CPUs to gain the best processing thruput...

mainly, i'm wanting to try to put mysql on one CPU so that it doesn't bog down the rest of the system... currently, there's 4 virtual domains running on the apache server and then mysqld with a slave attached for replication...

is there some way that i can assign mysqld to run on the second CPU so that it gets the full benefit of that CPU and leave the other tasks on the first CPU??

---

### Post by wkitty42 on 2008-11-27
bump!

is this a "st00pid" request or has it simply been missed with all of the other traffic?

[i'm a support specialist, too :?]

---

### Post by wkitty42 on 2008-11-27
i *just* found a thread, somewhere, that said that i could do something like this...

taskset -c 0,1 /etc/init.d/oracle start

which would assign oracle to the 2nd CPU...

so, i stopped mysql and then restarted it with the above and substituting mysql in place of "oracle"... as far as i can tell with top, it seems to have been the answer... but now how to ensure that this is how it starts this way all the time???

and, i guess, first and foremost, how can i ensure that mysql is actually running only on the 2nd cpu?? top doesn't indicate which cpu a task is running on unless i've really missed something basic :?

---

### Post by wkitty42 on 2008-12-02
bump...

---

### Post by gombadi on 2008-12-02
You are assuming that CPU is the only resource that needs to be assigned.

How often is mysql cpu bound? If you lock mysql to one cpu then what happens if it is running two tasks at once? They will both have to wait on each other while the other cpu and apache are sitting waiting on mysql to return a result. The whole response time of the system will suffer.

How I/O bound is the system. How fast are the disks. Can you move the mysql databases to a different disk than the web sites so apache and mysql are not fighting for the disks.


> 
are assigned to to the CPUs to gain the best processing thruput


After years of tinkering I think that the kernel people and the big corporations funding some of the kernel development have developed a kernel that will deliver the best throughput if left alone to do the job it was programmed to do.

You may have a different opinion but after years of looking after *nix machines I would avoid taking such drastic measures.

But then again feel free to experiment and let us know the results you found.

---

### Post by Vegan on 2008-12-02
The 2.6 kernal is fine at assigning CPU threads to optimize general operations. No need to much with it as you are likely to have problems that are hard to fix.

I write multithreaded programs and I let the OS deal with the muck.

:guitar:

---

### Post by HermanAB on 2008-12-02
Hmm, for experimental purposes go ahead and assign processors and memory manually.  It can be fun to look at what happens.

However, you will eventually find that the Linux scheduler and memory manager is pretty good and this kind of thing is best left to the kernel, since that is what it is designed to do.

---

### Post by wkitty42 on 2008-12-02
thank you for the replies... i was able to determine that my use of taskset did not do what i had thought and that what i was seeing was due to the mysqld task being placed on the 2nd CPU at that time... yeah, a coincidence...

in digging deeper into the scripts, i was still unable to force mysqld onto the 2nd CPU and so i have decided to just let the system's scheduler handle it...

oh well :?

---

