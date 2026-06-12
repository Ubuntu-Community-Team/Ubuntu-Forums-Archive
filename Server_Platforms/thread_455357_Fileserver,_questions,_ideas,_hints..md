---
title: "Fileserver, questions, ideas, hints."
date: 2007-05-26
forum: Server Platforms
---

### Post by WezH on 2007-05-26
Advertisement company where I work needs new fileserver to replace old-and-ready-to-explode fileserver.

So this is machine what's gonna be new fileserver (at least what I'm thinking):

- Intel P4D (non 64-bit) processor
- Intel mobo with integrated LAN/video
- 512Mb memory
- three 200Gb Serial-ATA disks

I'm planning to make RAID5 with mdadm from SATA disks, so there will be approx 400Gb of storage and using Samba to serve files to Windows machines.

We have 8 users to fileserver, mainly CorelDraw and plotter files.

So now I'm asking your opinions, why not's and everything what pop ups to your mind.

And of course answers to what ifs:
- what if machine (mobo etc) breaks down and I have to replace it with different one, how I'm able to recover data to "new" machine?
- what if one disk brokes down, is it easy to replace it in raid?
- is samba good for this, is there any other options?

So please, please reply if you have anything to say.

---

### Post by craigp84 on 2007-05-26
> - Intel P4D (non 64-bit) processor
- Intel mobo with integrated LAN/video
- 512Mb memory
- three 200Gb Serial-ATA disks

Where's the tape drive or other backup medium?

> so there will be approx 400Gb of storage

It's probably be nearer 285Gb (formatted).

---

### Post by WezH on 2007-05-27
> **craigp84 said:**
> Where's the tape drive or other backup medium?


In PDC which will backup all current (this years) data. Archive data is (previous years) is stored to external HD which is not in use (stored in safe ;)

> **craigp84 said:**
> 
It's probably be nearer 285Gb (formatted).

How so? 200Gb's real capacity is approx 185 so in RAID5 it should be approx 370Gb. Where goes 100Gb in your calculations?

---

### Post by hartz on 2007-05-28
Suggestions:
Disable all the fake-hw-raid RAID functions in your server BIOS, even JBOD.  Use the S-ATA disks natively, because if your motherboard then fails you don't need to worry what type of motherboard you get to recover the server asn any S-ATA controller can then read the disks.  This means you will use software raid (eg DMraid / LVM)

This is fine for a file-server, it has got plenty spare CPU.

Also I suggest that you get one extra disk drive, just to install the operating system - it is just easier to manage/recover/troubleshoot/upgrade as these things goes (eg don't put OS on part of the raid-5).

For sharing with Windows clients, SAMBA is quirky but fine.

dmraid will serve you well enough, eg for replacing a failed drive, etc, but do not skimp on making backups.

---

### Post by WezH on 2007-05-28
> **hartz said:**
> Suggestions:
Disable all the fake-hw-raid RAID functions in your server BIOS, even JBOD.  Use the S-ATA disks natively, because if your motherboard then fails you don't need to worry what type of motherboard you get to recover the server asn any S-ATA controller can then read the disks.  This means you will use software raid (eg DMraid / LVM)

Yes, that was my plan. Several RAID documents suggested that don't use so-called raids.

> **hartz said:**
> 
Also I suggest that you get one extra disk drive, just to install the operating system - it is just easier to manage/recover/troubleshoot/upgrade as these things goes (eg don't put OS on part of the raid-5).


You got point on troubleshooting with RAID but then again, redundancy is lost if OS is in single disk. If things go south, then I just install OS again and recover data from backups.

> **hartz said:**
> 
For sharing with Windows clients, SAMBA is quirky but fine.


What do you mean quirky? My English is decent but not so good that I could understand what you mean ;)

> **hartz said:**
> 
dmraid will serve you well enough, eg for replacing a failed drive, etc, but do not skimp on making backups.

dmraid or mdadm, which one I should use?

---

