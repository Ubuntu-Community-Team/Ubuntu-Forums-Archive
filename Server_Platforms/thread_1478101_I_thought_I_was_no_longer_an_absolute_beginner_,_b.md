---
title: "I thought I was no longer an absolute beginner , but ..."
date: 2010-05-09
forum: Server Platforms
---

### Post by ZizzerZuz on 2010-05-09
I have one of these:
 
[http://www-947.ibm.com/support/entry/portal/docdisplay?lndocid=MIGR-38914](http://www-947.ibm.com/support/entry/portal/docdisplay?lndocid=MIGR-38914)
 
2x1.2 GHz procs
2 Gigs ram
64 + 34 + 34 gig SCSI drives
AHA2390 PCI SCSI card
external DRW + memory card reader in external enclosure
 
A few months ago I managed to get Ubuntu desktop to load and run. After struggling with Busybox and the initramfs and the IAPIC etc etc etc ... I finaly manged to get the to run. Every time it rebooted I had to type exit at the busybox/initramfs shell and it would boot right up and worked pretty well. Welll enough that I managed to get synergy to run and was using one KB and mouse on my desk instead of two. I had even managed to get Citrix to work on it and I had been using it to log into work and get my remote desktop.
 
Then the new LTS came out and I wanted to move to that. I did the update not the clean install and now the thing won't boot. It just boots in to the initramfs and I can't get past it.
 
Hoping to fix this and try something new I've been trying to get the LTS server to load instead but I can't seem to get past the initramfs and busybox.
 
I would realy like to simply wipe all three drives and use them all as part of a Linux server for my home. I think I'd like to try to set up SAMBA and run the server as a PDC. I'd like to serve music up from this box and use it as a print server, among other things.
 
I've been looking for some good reading material about how better to set up the SCSI drives and devices, but I'm having a hard time finding relevant material. 
 
When I try the server install CD I can get in to one of the option menus and find the AHA2400 scsi cards mentioned but I can't find the 2390. I think this has prevented the external drive enclosure from working in the past.
 
I'm frustrated and having a hard time finding a way to get around this.
 
I loved this box when it was runnning just last week. LOVED it. Now I'm very sad and I can't seem to work this out on my own.
 
Please help ...
 
ZizzerZuz

---

### Post by cariboo on 2010-05-09
Moved to server platforms.

---

### Post by tgalati4 on 2010-05-09
Back up any critical data and reload the older distro.  Then burn a disk of Lucid and boot the Live CD and run that for a few days.  You need to look at dmesg for any strange errors when running Lucid:

dmesg | more

Upgrading in place is convenient but can quickly take you from a working system to a non-working, head-scratching system.

---

### Post by ZizzerZuz on 2010-05-10
Thanks for moving this ...

Aside from a few config files, there is no critical data, so nothing to back up per se.

I'm starting over from scratch.  I'm running the system level drive format local to the SCSI controller on the mother board.  I hope it doesn't break anything else.

I'm a little iffie on which version I should be downloading, the AMD or the i386 version.  I'm leaning toward the i386 version ... more reading.

Thanks for the help,

ZizzerZuz

---

### Post by ZizzerZuz on 2010-05-10
Processor	
Intel Pentium III microprocessor with MMX technology and SIMD extensions
256 KB ECC, level-2 cache (min.)
133 MHz front-side bus (FSB)
Support for up to two microprocessors

i386 version, not the AMD ?

---

### Post by Queue29 on 2010-05-11
> **ZizzerZuz said:**
> Processor	
Intel Pentium III microprocessor with MMX technology and SIMD extensions
256 KB ECC, level-2 cache (min.)
133 MHz front-side bus (FSB)
Support for up to two microprocessors

**i386 version, not the AMD ?**

Correct. (be careful, on the server distros, amd64 is the default download)

Which distribution did you 'upgrade' from?

---

### Post by ZizzerZuz on 2010-05-11
Yeah ... I think I opened this in the right place after all.  It was originally opened in Absolute beginners ... I think I made some real beginner mistakes.

The upgrade was from 9.something desktop to 10.4 desktop LTS.  When that botched I decided to try to do the install from scratch with the 10.4 server.  That gets me to here.

This server has some interesting built in utilities that I'm running.  I've never seen anything like the ROM Bios on this box.  Ever.  I was able to format all three drives last night from the BIOS.  I'm going to finish running through the diagnostics and see what I can learn.  I was never able to get the Adaptec AHA-2930 SCSI PCI card to work under Ubuntu before.  Maybe if I start over I can get it right this time.

I've downloaded the correct install disk, checksummed it and burned it slow to a nice clean CD.  I'm going to go fiddle with the SCSI cards and devices and see if I can this working again.

When it worked last, it screamed.  

Thanks for the help.

---

### Post by ZizzerZuz on 2010-05-11
Here's another user getting the same error as I am ...

[http://ubuntuforums.org/showthread.php?t=1468499](http://ubuntuforums.org/showthread.php?t=1468499)

I can boot to Desktop 8.10 just fine.  Booted in non-change mode for the test.  

Ziz

---

