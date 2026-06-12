---
title: "Gutsy (7.10) unstable on Sun Blade 150"
date: 2007-10-30
forum: Sun Sparc Users
---

### Post by drosky on 2007-10-30
Hello,

I have several Sun Blade 150's that have been running combinations of Debian Stable and Ubuntu Dapper for several years with no problem.  Recently I installed Gutsy on one of them and was experiening random hangs, usually during disk activity.  Note, I have been using "ide=nodma" as I always have for years.  I tried installing on another  150 and the root partition became corrupted after a few days.  On a third machine, the hard drive was not properly recognized during install.

Once again, all this time, I was passing "ide=nodma" to the kernal as usual.

I took the corrupt hard disk from the second system and reformatted it in another (Pentium4) computer and the drive worked fine, so it appears not to be a problem with the drive hardware.

Is anyone else experiencing this?  It seems like there is either a new bug in the IDE driver, or for some reason the new kernel is not recognizing the ide=nodma parameter.

Dave

---

### Post by drosky on 2007-10-31
The problem appears to be the Gutsy kernel (2.6.22) not recognizing the ide=nodma parameter.

If I boot dapper with ide=nodma (2.6.15 kernel), and run hdparm on /dev/hda, it shows using_dma=0.  On the other hand, when Gutsy is booted with ide=nodma, hdparm shows that using_dma=1.

Looking at the syslog shows that "ide=nodma" was indeed passed to the kernel, even though dma is turned on.  In the case of the dapper kernel, there is an acknowledgment of dma being forced off in the syslog.  In the case of the Gutsy kernel, there is no such acknowledgment in the syslog.

One could use hdparm to turn dma off after booting, however, the system would still be subject to possible corruption during boot and during installation.

---

### Post by mossholderm on 2007-11-11
I am seeing the same things under x86... passing in ide=nodma doesn't seem to do anything.

     --Matt

---

### Post by drosky on 2007-11-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159152](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159152) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **mossholderm said:**
> I am seeing the same things under x86... passing in ide=nodma doesn't seem to do anything.

     --Matt

I started a bug on this, which hasn't received any reply after several weeks.  Don't know if it will help, but you may want to add a confirmation to the bug.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159152](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159152)

Since I am using these machines for non-mission-critical servers, for now I have switched to Debian Testing ("Lenny"), which is also at kernel 2.6.22, but doesn't have this problem.  Like Gutsy, it also has up-to-date versions of Apache, Mysql, and PHP.  Unfortunately, it has a few minor bugs in GNOME, so it might not be as great as a desktop system (or try KDE or XFCE instead).

Dave

---

