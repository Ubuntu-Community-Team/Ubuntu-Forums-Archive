---
title: "On-board RAID on Jetway NF99FL-525 (ICH9R)"
date: 2014-04-04
forum: Server Platforms
---

### Post by m-dw on 2014-04-04
Hi.  I've bought one of [these]("http://www.jetwaycomputer.com/NF99.html") mainly because it has 6 SATA ports built in to the motherboard.  I also bought 1 x 2.5" SATA drive for the OS, and 4 x 3.5" SATA drives to deploy in a RAID array as this is going to become my home server (file, mail, DNLA and LMS).

On re-reading the literature, I was surprised to notice that it boasted support for RAID 0,1,5,10.  Its an Intel ICH9R chipset, so is not a true RAID controller but it is hardware accelerated.  It's limited to RAID 10, but I was going to use that anyway anyway. I do backups of my data every night and have a tendency to replace failed drives immediately so concurrent disk failures do not scare me.

I was expecting to configure all the SATA ports as AHCI and set up RAID in software but this now has me thinking...  Should I configure SATA 2,3,4,5 (which will hold my data disks) as RAID in the BIOS, or stick with my original plan using 100% software raid.  Server will be Ubuntu server 14.04LTS  How will Linux (and GNU) see an ICH9R based biosRAID array, and is it sustainable in the event of a mobo failure?

It's odd, but I can't find any current postings onthe topic, and most seem to be dated around 2008-2009, so looking to see if any kernel updates since then have changed the landscape.

---

### Post by lukeiamyourfather on 2014-04-04
I would use mdadm (Linux software RAID) or ZFS. I wouldn't use fake RAID on a motherboard. Ever. If you do intend to use a proprietary RAID controller get a good one with a dedicated processor and widely supported drivers (LSI, Adaptec, Areca, etc.).

---

### Post by m-dw on 2014-04-04
> **lukeiamyourfather said:**
> I wouldn't use fake RAID on a motherboard. Ever. 

Cool, thanks.  Sticking with Plan A then :)

---

