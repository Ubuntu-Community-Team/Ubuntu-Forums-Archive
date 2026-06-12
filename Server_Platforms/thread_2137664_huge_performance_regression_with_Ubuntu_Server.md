---
title: "huge performance regression with Ubuntu Server"
date: 2013-04-21
forum: Server Platforms
---

### Post by dhalperi on 2013-04-21
Hi everyone,

Our computer science department has ordered a cluster for database experiments---big, beefy machines with four fast hard disks, 64GB of RAM, etc. They came with RHEL, and we want to convert them to Ubuntu server for all the reasons you know and love.

Right now we have a few machines running Ubuntu and a few running RHEL still.  I deployed our database application to the Ubuntu machines and to the RedHat machines and found an insane performance difference in RedHat's favor. I am trying to track it down and fix it so that we can go ahead with Ubuntu.

I have reduced the error down to a trivial test case. See this public git repository with the code: [https://github.com/dhalperi/sqlite-test/tree/master/command-line](https://github.com/dhalperi/sqlite-test/tree/master/command-line)
All it does is open a sqlite3 database, CREATE a few tables, and close it.

On RHEL, this takes ~60ms. On my Mac laptop, this takes ~80ms. On Ubuntu server, it takes almost 1 second(!!!). It's replicable across a few different machines and drives. And since the RHEL and the Ubuntu machines are the same hardware, their results should be comparable!

How do I debug this? Could it be hdparm settings? Could it be some security daemon running on Ubuntu (e.g., AppArmor?)? Could it be some kernel option different between the two distros by default?

Any ideas would be greatly appreciated!
Dan

---

### Post by dhalperi on 2013-04-21
Found the problem. It's the kernel version indeed; it appears that fsync wasn't actually doing anything in the older kernels that RHEL uses. So of course those calls were really fast!

[http://stackoverflow.com/questions/8875708/why-fsync-takes-much-more-time-on-linux-kernel-3-1-than-kernel-3-0](http://stackoverflow.com/questions/8875708/why-fsync-takes-much-more-time-on-linux-kernel-3-1-than-kernel-3-0)

---

### Post by matt_symes on 2013-04-21
Hi

Blimey. 

Thanks for posting this and the conclusions you discovered. 

Interesting reading !

Kind regards

---

