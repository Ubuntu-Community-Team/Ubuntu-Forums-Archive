---
title: "mhddfs + SnapRAID = Opensource Drobo alternative?"
date: 2012-10-15
forum: Server Platforms
---

### Post by FieldDoc on 2012-10-15
As a newbie to Linux - can somebody just clarify that my understanding is correct?
 
I have a hot swappable enclosure for 2.5" SATA drives that contains four 1TB drives.
 
1. Say I use [mhddfs ]("http://romanrm.ru/en/mhddfs")to merge these four drives into one 4TB virtual volume. Am I right in thinking that I can use [SnapRAID ]("http://snapraid.sourceforge.net/")to monitor and protect this virtual volume against one (or two) of the disks failing?
2. If question (1) above is true then am I able to pull out one of the 1TB drives, replace it with a 2TB drive and have SnapRAID fix/restore any data that was on the pulled out drive?
 
Essentially, I'm trying to build a reliable open source version of Drobo for my home,
Is this possible?

---

### Post by rubylaser on 2012-11-18
> **FieldDoc said:**
> As a newbie to Linux - can somebody just clarify that my understanding is correct?
 
I have a hot swappable enclosure for 2.5" SATA drives that contains four 1TB drives.
 
1. Say I use [mhddfs ]("http://romanrm.ru/en/mhddfs")to merge these four drives into one 4TB virtual volume. Am I right in thinking that I can use [SnapRAID ]("http://snapraid.sourceforge.net/")to monitor and protect this virtual volume against one (or two) of the disks failing?
2. If question (1) above is true then am I able to pull out one of the 1TB drives, replace it with a 2TB drive and have SnapRAID fix/restore any data that was on the pulled out drive?
 
Essentially, I'm trying to build a reliable open source version of Drobo for my home,
Is this possible?

Sorry for the delayed response.
1. Yes, you can use mhddfs to pool the drives together.  Personally, I use AUFS, because it runs in kernel space, so it's much faster than mhddfs and has less overhead.  SnapRAID will provide protection from 1 (or 2) disks failing. I have a [quick writeup]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") on my website covering my setup.

2. Yes, you can remove a drive and have SnapRAID fix it, or you can partition the new drive and rsync the data from the old to the new as well.  You will need to update /etc/fstab and /etc/snapraid.conf to reflect these changes.

---

