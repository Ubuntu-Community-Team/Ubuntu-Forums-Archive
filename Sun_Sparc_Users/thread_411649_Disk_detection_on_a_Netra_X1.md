---
title: "Disk detection on a Netra X1"
date: 2007-04-17
forum: Sun Sparc Users
---

### Post by yrrab on 2007-04-17
Hi,

I've been trying to get Feisty Fawn installed on a Sun Netra X1 and have so far managed to get to the hardware detection phase. The problem I'm having is that it can't see the disc, I know that its not a hardware issue as Solaris boots perfectly.

Has anyone else came across this?

Cheers,

Barry

---

### Post by netztier on 2007-04-17
> **yrrab said:**
> Hi,

I've been trying to get Feisty Fawn installed on a Sun Netra X1 and have so far managed to get to the hardware detection phase. The problem I'm having is that it can't see the disc, I know that its not a hardware issue as Solaris boots perfectly.

Has anyone else came across this?

Cheers,

Barry

Might be a missing  IDE driver.

When the installer searches for the disks, can you switch to another console (Alt +F2) and issue the **lspci**, **lsmod** and **dmesg** commands? Maybe we just need to modprobe an additional kernel module for the IDE adapter - lspci should be able to help finding out which one.

Ultra2s and Ultra1s needed a similar procedure back with Dapper and Hoary, because the *esp* SCSI module wasn't loaded by default - search the forum, there's more than one explanation on how to circumvent this that could be adapted to this situation.

best regards

Marc

---

### Post by yrrab on 2007-04-17
Hi,

Thanks for your reply. I'll attempt that later on, although I can see a problem with switching to another console as the box has no monitor output and i'm running it through minicom. I did try switching consoles last night but couldn't figure it out :(

---

### Post by yrrab on 2007-04-19
Thought I'd post what I managed to figure out for anyone in who's having the problem in the future.

The cause wasn't the disk controller it was the model of HD that was in the box. I can't remember the model but it's a 20Gb Seagate and I believe one of the default disks supplied with Netra X1's. As soon as i tryed another disk it went perfectly.

---

