---
title: "Will not install"
date: 2016-01-12
forum: Ubuntu Development Version
---

### Post by jallain on 2016-01-12
I am running a HP AMD-64, 16GB ram machine. My hard drive is partitioned as msdos and not GPT. My BIOS is set for legacy booting. I created both a usb stick and a DVD for 16.04. Both boot up fine but only in UEFI mode. As a result, it will not install to my hard drive. I get the first screen of ubiquity to select language and when I click continue the window closes with an error. I have tried to install running ubiquity manually and I get a message abut my disk being partitioned with msdos and if I continue it will destroy my other partitions. Any advice?

---

### Post by QDR06VV9 on 2016-01-12
I am curious about the format also [COLOR=#000000] msdos??
Is there a reason you choose msdos as a partition and not ext3 or ext4 or even btfs..
Maybe I am misreading your post.
Kind Regards[/COLOR]

---

### Post by grahammechanical on 2016-01-12
The Ubuntu installer of whatever version when loaded in EFI mode will expect a GPT partition table on the hard drive. This is my guess. The UEFI boot system may be set for legacy loading of Windows but we can still load a live/install Ubuntu DVD/USB stick in EFI mode.

I think the problem is being caused by the live session being loaded in EFI mode and a hard disk with MBR partition table.

Regards

---

### Post by jallain on 2016-01-12
You are correct.I have used this same setup since 14.04 without any issues whatsoever. I currently have 15.10 installed. Only with 16.04 have I encountered this issue. It will not install even though it boots up in UEFI mode. I can't seem to find a way around it. Any suggestions as to how to fix it?

---

### Post by cpatrick08 on 2016-01-19
> **jallain said:**
> You are correct.I have used this same setup since 14.04 without any issues whatsoever. I currently have 15.10 installed. Only with 16.04 have I encountered this issue. It will not install even though it boots up in UEFI mode. I can't seem to find a way around it. Any suggestions as to how to fix it?

Have the exact same problem as you, filed bug about problem. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1535540 ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1535540")

---

