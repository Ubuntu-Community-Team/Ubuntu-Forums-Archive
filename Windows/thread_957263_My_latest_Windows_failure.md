---
title: "My latest Windows failure"
date: 2008-10-24
forum: Windows
---

### Post by Nameless Neko on 2008-10-24
It's time for Windows to be reinstalled on my desktop PC (many thanks to Securom from Spore speeding up this decision), and since my Hardy install is pretty old and probably had a bunch of old, useless junk in it (also couldn't get my USB modem running in it on my desktop, so I figure it's worth giving a reinstall a shot, since I'm lazy), I decided to do a full reinstallation of both OS's.  I backed everything up, nlited a customized XP installation disc, carefully planned out the partitions, and installed XP first, to get it out of the way.
The installation goes without incident (besides me forgetting to input unattended settings.  My fault entirely), until I boot up windows and notice that it's installed on the D drive for some reason.
As it turns out, XP decided to spit out its boot files on the first partition of the drive I installed to, which I set aside for Ubuntu, even though I told it not to format it.
Man, why does Windows have to do this crap to me every time?  :(

---

### Post by karellen on 2008-10-24
> **Nameless Neko said:**
> It's time for Windows to be reinstalled on my desktop PC (many thanks to Securom from Spore speeding up this decision), and since my Hardy install is pretty old and probably had a bunch of old, useless junk in it (also couldn't get my USB modem running in it on my desktop, so I figure it's worth giving a reinstall a shot, since I'm lazy), I decided to do a full reinstallation of both OS's.  I backed everything up, nlited a customized XP installation disc, carefully planned out the partitions, and installed XP first, to get it out of the way.
The installation goes without incident (besides me forgetting to input unattended settings.  My fault entirely), until I boot up windows and notice that it's installed on the D drive for some reason.
As it turns out, XP decided to spit out its boot files on the first partition of the drive I installed to, which I set aside for Ubuntu, even though I told it not to format it.
**Man, why does Windows have to do this crap to me every time?  **:(

maybe because you forgot to select drive C instead of D? :D

---

### Post by sdowney717 on 2008-10-24
take the drive out

---

### Post by Battie on 2008-10-24
The last time I started from scratch (which was over a year ago, so I don't know what's changed), I found that Windows didn't like partitions made with gparted.  It couldn't read them correctly and led to all sorts of issues.

The easiest thing I've found to do is use the Windows partitioner during the setup process to layout what you want.  Install Windows on the very first partition because that makes it happy.  You can use gparted during Ubuntu's setup to fix up the partitions you want for that OS.  It sounds like a sloppy way to do things but I found that it gave me the least headaches.

I don't know what makes XP occasionally install to the wrong drive letter when you don't ask it to.  I've even had that happen on a PC with four card reader bays.  For some reason it labeled on of those c:!

---

### Post by Nameless Neko on 2008-10-24
> **sdowney717 said:**
> take the drive outMade sure to do that with the two SATA drives I didn't want touched.  I've learned that the hard way.  Here's how I told it to set it up:
60 GB <- Unformatted, was going to install Ubuntu on it afterwards
60 GB <- NTFS, for XP
2 GB <- Unformatted, for swap
Remaining 100some <- Unformatted, for /home

What it did was format the first two partitions instead of just the second one, and tossed it's boot stuff on the first partition.  I guess it makes sense now that I think about it, but it's still annoying.  :(

karellen:  hm, now that I think about it, it did mention it being the D drive in the partitioner, but I figured nothing would come of it since I told it not to format the first partition. :/

Ah well.  It's set up now, after a long night, and I'm working on the Ubuntu install now.

---

