---
title: "Please help"
date: 2012-08-08
forum: Server Platforms
---

### Post by cana2000 on 2012-08-08
Good morning all,
 
We just had a power failure on our Ubuntu server, we just turn it back on and we got the error "**No init found. Try passing init=bootarg". **We searched on the internet and saw a lot of helps to fix this problem. One of the helps said that we can boot the Ubuntu server from a LiveCD, but we do not know what the LiveCD is, we assume LiveCD is the original CD which we used to install Ubuntu at the first time, we do not have that CD. We tried to download Ubuntu server from the internet, but the oldest version of Ubuntu server is 4.10, but our Ubuntu version is 1.1.13-3-1. Our question is: can we dowload Ubuntu server version 4.10 or later versions of Ubuntu, burn it to a CD and use it like a LiveCD to boot our Ubuntu server? or is there any other ways we can do to fix our problem? We lamost tried everything but it did not help. Thank you very much for all of your helps.

---

### Post by rubylaser on 2012-08-08
Hello, and welcome to the Forums :)  You should be able to boot off of any LiveCD.  Most people would suggest running an [fsck on your disk to correct this issue]("http://ubuntuforums.org/showthread.php?t=1386549"), but before you do anything, you'll want a backup (I hope you have one already). The fsck will likely create a large number of orphaned inodes in lost+found.

What was this machine doing?  If it was just a fileserver, I'd suggest putting the disk in a new machine, salvaging the data, and doing a fresh install.  Ubuntu's first released version was [4.10]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history"), are you certain your version of Ubuntu isn't 11.10, or something similar?

---

