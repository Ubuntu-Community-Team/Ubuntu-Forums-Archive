---
title: "remote hard drive repair, possible?"
date: 2010-04-12
forum: Server Platforms
---

### Post by xkaliburx on 2010-04-12
one of our webservers crapped out, and we have both remove keyboard as well as remote power.  After a power cycle, I am getting dumped at the following prompt;
(initramfs)

So, what commands (if any) can be done at this level to try to see/repair the drive?  As I said, I can power cycle, tried failsafe mode with the same results.

I might have to make a drive and re-stage the box, but this would really make it easier....

Tnx

---

### Post by KB1JWQ on 2010-04-12
If you can't get into single user mode / recovery mode, your options are somewhat limited.  Maybe boot from a LiveCD and see what's going on?

---

### Post by xkaliburx on 2010-04-12
Yea, thats what I was figuring, the co-lo is 45 or so from the office, and I just did try a reboot, single and get the same results;

A bunch of mount failures, then finally a "Target filesystem doesn't have /sbin/init.  Not init found. Try passing init= bootarg" so alas, it will be a drive and live cd boot.

Thanks.

---

### Post by Vegan on 2010-04-13
I use Webmin and if that crapps out, I am forced to get to the local console. Thankfully my machine has lasted for over 5 years with no error, but I have upgraded the disk 3 times.

---

