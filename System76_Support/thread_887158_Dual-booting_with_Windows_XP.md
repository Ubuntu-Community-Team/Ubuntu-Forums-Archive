---
title: "Dual-booting with Windows XP"
date: 2008-08-11
forum: System76 Support
---

### Post by Caeliferum on 2008-08-11
Hi there! I just got my new Pangolin Performance and its running great! Anyways, I tried running a few games under Wine to test things out like the 8600GT. Had issues with both (Fable and Devil May Cry 4) and so I've decided just to use XP for any gaming purposes. So, using the LiveCD I created a 40 gig Fat32 partition from my 160 and then rebooted with the XP install disc. It'll begin to load files but eventually it'll get to a point where it says that it can't detect any installed HDDs. Anyway to fix this? (Note this is before the actual GUI)

---

### Post by sillyxone on 2008-08-11
if you have a SATA drive, Windows XP setup won't recognize it. If that's the case, check your BIOS if you can set HDD mode to non-AHCI (ATA mode). 

You can also provide the SATA driver during Windows XP setup by pressing F6, but it requires a floppy drive (built-in or USB). 

Slipstreaming is another option but requires more work, might be the last solution.

---

### Post by cdtech on 2008-08-11
Try reformatting using vfat through Ubuntu.
```
$ sudo mkfs.vfat /dev/**sdb1**
```
Change the bold to your partition with the fat32.

---

### Post by thomasaaron on 2008-08-12
The SATA driver is definitely the problem, especially if you have an older XP disk. There are a number of tutorials out there for dealing with this issue.

This one is a good one...
[http://rockmanx.wordpress.com/2008/06/03/install-windows-xp-on-sata-without-a-floppy-f6/](http://rockmanx.wordpress.com/2008/06/03/install-windows-xp-on-sata-without-a-floppy-f6/)

---

### Post by Caeliferum on 2008-08-12
Thanks a lot! The non-AHCI mode bit did the trick. Its installing now with 8 minutes left to go. :)

Can I re-enable AHCI after setup or does XP prefer non-AHCI?

---

### Post by jdb on 2008-08-12
> **Caeliferum said:**
> Thanks a lot! The non-AHCI mode bit did the trick. Its installing now with 8 minutes left to go. :)

Can I re-enable AHCI after setup or does XP prefer non-AHCI?

I like VirtualBox better than dual booting.

Windows opens just like any other application & it does it really fast, no long boot.
Things that won't run in wine will run just fine.


John

---

### Post by logos34 on 2008-08-12
> **Caeliferum said:**
> 
Can I re-enable AHCI after setup

no.  But there are no drawbacks performance-wise, unless you have an SataII drive, in which case you lose hot-plugging support and maybe NCQ (native-command queing)

---

### Post by glacialfury on 2008-08-14
> **jdb said:**
> I like VirtualBox better than dual booting.

Windows opens just like any other application & it does it really fast, no long boot.
Things that won't run in wine will run just fine.


John

VirtualBox emulates the underlying graphics hardware, so you will get no true 3D performance out of it; as such, using VirtualBox for gaming is not a viable solution.

Also, as I found out tonight, not all DVDs are compatible.  I received Microsoft Office 2007 through work on a DVD; when inserted into a Windows machine, it autoloads the disc's installer.  When I insert that same disc into the Serval, Ubuntu can't mount it.  Because Ubuntu can't mount it, WinXP inside of VirtualBox can't mount it, so I can't install it in the guest OS (unless you have some tricks up your sleeve to force linux to mount the DVD, which I would welcome).

In these situations, a dual-boot is a better option, if less convenient than VirtualBox, which I adore.

---

### Post by thomasaaron on 2008-08-15
Yeah, that's true.

I use Virtual box for cross-platform software testing. It's easy to set up a share between Ubuntu and VirtualBox, so I can keep Ubuntu running while testing a program in Windows.

VirtualBox definitely has its place. But if you need to do certain things, a dual boot is superior. 

I await the day that it is no longer necessary, though. :popcorn:

---

### Post by jdb on 2008-08-16
> **glacialfury said:**
> VirtualBox emulates the underlying graphics hardware, so you will get no true 3D performance out of it; as such, using VirtualBox for gaming is not a viable solution.

Also, as I found out tonight, not all DVDs are compatible.  I received Microsoft Office 2007 through work on a DVD; when inserted into a Windows machine, it autoloads the disc's installer.  When I insert that same disc into the Serval, Ubuntu can't mount it.  Because Ubuntu can't mount it, WinXP inside of VirtualBox can't mount it, so I can't install it in the guest OS (unless you have some tricks up your sleeve to force linux to mount the DVD, which I would welcome).

In these situations, a dual-boot is a better option, if less convenient than VirtualBox, which I adore.

I guess I'm not much of a gamer, I should have asked one of my boys, they would have set me straight :)

jdb

---

### Post by glacialfury on 2008-08-16
Oh yes, one other thing re: VirtualBox to be aware of.  I don't know the cause, so any details beyond this are a mystery to me.

According to speedtest.net, I get ~10 MBPS download and 1.8 MBPS upload in Ubuntu on the Serval, which roughly corresponds to what I'm supposed to get.  On that same speedtest in Windows XP (inside of VirtualBox), I get about the same download speed, but the upload speed drops to about 0.095 MBPS.  These tests were consistent with several speedtest sites at several times in the day.

So I don't know the hardware/software reason behind it, but VirtualBox kills the upload speed on my connection.

---

