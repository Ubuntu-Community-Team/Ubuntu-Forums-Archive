---
title: "Unable to install windows 10 PC"
date: 2016-04-04
forum: Windows
---

### Post by wijnaldumwilliam on 2016-04-04
I want to install the latest ISO on the 10240 oartition, but when I try I get, "Windows cannot be installed to this disk. The selected disk has an MBR partition table. On EFI systems, Windows can only be installed to GPT disks."



- Delete all partitions on the disk, so you can use GPT (GUID Partition Table).
- But if you want to use MBR (Master Boot Record) partition table[,]("http://goo.gl/HBR5JL") then boot from the Windows installation media inLegacy BIOS Boot Mode.

Quote from this post: UEFI Boot Mode (installing using the GPT partition style) and Legacy BIOS Boot Mode (installing using the MBR partition style).

---

### Post by howefield on 2016-04-04
Thread moved to the "*Windows*" forum and font reset to default.

---

### Post by yancek on 2016-04-04
What exactly are you trying to do.  If you want to install windows to an empty hard drive, just follow the steps in the message.  If it is not an empty hard drive (you posted nothing to indicate otherwise?) then following the steps suggested will likely delete everything you have.

What is the "10240" partition?

You can't install windows UEFI unless you have a GPT partition table.  If you have another system on the computer using UEFI, you need to install windows UEFI which requires a GPT partition table.  You need to post more info on what you have to get any proactical suggestions.

---

