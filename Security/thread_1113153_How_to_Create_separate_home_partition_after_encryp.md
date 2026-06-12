---
title: "How to Create separate /home partition after encrypted disk installation"
date: 2009-04-01
forum: Security
---

### Post by yeehi on 2009-04-01
I used AMD64 alternate Intrepid Ibex 8.10 CD to do an encrypt whole disk installation.

The problem is, that automatic setting does not create a separate partition for /home or /opt.

I really wish this option was available during installation! (I don´t know how to do it manually.)

I can see some guides on how to create a separate /home partition, but not when the disk has already been encrypted.

How can I do this? Is there a tutorial for this case?

I have an entire unused hard drive too, if that helps.

Thank you!

---

### Post by bodhi.zazen on 2009-04-01
You can do it, but it is much much easier to back up your data and re-install.

IMO the easiest way to do this with manual partitioning on the alternate CD ...

However, also know that when you upgrade, preserving an encrypted home is NOT automatic and will take some work.

Again it is far easier to back up your data and restore.

To give you an idea of what you are looking at see these threads :

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

There is a how-to on these forums with step by step instructions on how to preserve an encrypted home directory, and it is also very manual and prone to errors.

I do not have the link at the moment.

---

### Post by hyper_ch on 2009-04-01
doing it with an unused partitions is rather simple IMHO.

---

### Post by bodhi.zazen on 2009-04-01
Ah, here is the thread I was talking about :

[http://ubuntuforums.org/showthread.php?t=1034910](http://ubuntuforums.org/showthread.php?t=1034910)

---

