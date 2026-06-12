---
title: "[XP] Making a recovery disk?"
date: 2008-11-14
forum: Windows
---

### Post by fiddler616 on 2008-11-14
Hello,
After several jumbo-economy-size headaches, I've managed to reinstall Windows XP on my computer.
I now want to make a recovery disk, so that future problems are easier to deal with (I reinstalled it with BartPE, which worked, but was a pain in the neck)
I know that results show up on Google, but I'm kind of wary of l33t h3x0r forums--they just seem kinda shady or whatever (especially since I've gotten spoiled with these forums)
How do I go about this?
Thank you very much.

---

### Post by srt4play on 2008-11-14
What I do is boot with [system rescue cd]("http://sysresccd.org") and use partimage to image the partition and save it to an external drive.

---

### Post by fiddler616 on 2008-11-14
> **srt4play said:**
> What I do is boot with [system rescue cd]("http://sysresccd.org") and use partimage to image the partition and save it to an external drive.
Thanks, but it seems a bit overkill...I guess I'll give it a shot if nothing else comes up.

---

### Post by srt4play on 2008-11-14
I'm curious why you think that is overkill.

---

### Post by fiddler616 on 2008-11-14
> **srt4play said:**
> I'm curious why you think that is overkill.
I guess overkill wasn't the best word choice--it just seems more complicated than having a straight-up recovery disk. For one thing the less I put on my external hard drive the better--it's only 120GB and is housing *all* my media. And backups of partitions that don't exist anymore. 
Call me old-fashioned or crotchety or whatever else you want, but...I dunno.

---

### Post by srt4play on 2008-11-14
Well, I just think you're being old-fashioned and crotchety. :p

I'll just add one more thing - what I have been doing lately is [installing system rescue cd to a partition]("http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk") and keeping the rescue image on that same partition, eliminating the need for a disc or an optical drive. Kind of creating a makeshift recovery partition, similar to what the manufacturers do on new machines.

---

### Post by fiddler616 on 2008-11-15
> **srt4play said:**
> Well, I just think you're being old-fashioned and crotchety. :p

I'll just add one more thing - what I have been doing lately is [installing system rescue cd to a partition]("http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk") and keeping the rescue image on that same partition, eliminating the need for a disc or an optical drive. Kind of creating a makeshift recovery partition, similar to what the manufacturers do on new machines.
I'm using all four primary partitions-- /, /home, swap and C:\. I guess I could make it a logical partition, but to be honest I don't know how.

---

### Post by fiddler616 on 2008-11-15
OK, I'm a convert--it seems like to burn a CD you need one to base it off of. (If that isn't a *stupid* idea....)
So I'm gonna give it a shot, I'll let y'all know how it goes.

---

