---
title: "MDADM RAID1 of boot devices not working"
date: 2016-08-30
forum: Server Platforms
---

### Post by courtney2 on 2016-08-30
I am at my wits end trying to set up RAID 1 for my OS devices. I feel like I have tried everything but I always get some sort of failure back. Here's what I have done so far that has gotten me the furthest:

Both devices:
2GB /boot (yes it's big but I really don't care)
42GB /
12GB swap

That is done on both devices (side note: setting the boot flag never works, it always remains in the off position)
Next, I go to configure software RAID and I set RAID 1, 2 disks, 0 spares and choose the partitions accordingly. Once finished, I have my 3 RAID devices, my first one I set to /boot, second is / and third is swap. I get down to the point where it fails to install GRUB on the second disk. I have also tried setting the 2GB volume I have to reserved BIOS boot and either setting the RAID device to /boot or leaving it alone and it still fails with installing GRUB. I have absolutely no idea how to get this working and no other solution online has worked for me so far

---

### Post by darkod on 2016-08-31
Have you double checked the partition types on both disks? The older type msdos table should be OK, but if you are using the newer gpt table then grub2 doesn't fit on its MBR (it's smaller compared with msdos). That can make grub2 install fail.

Is it possible disk 2 is with gpt table?

---

### Post by courtney2 on 2016-09-01
> **darkod said:**
> Have you double checked the partition types on both disks? The older type msdos table should be OK, but if you are using the newer gpt table then grub2 doesn't fit on its MBR (it's smaller compared with msdos). That can make grub2 install fail.

Is it possible disk 2 is with gpt table?

Turns out it was GPT, and now it is an MBR device. I was able to follow the tutorial again on some Ubuntu documents

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

The only thing I don't know now is whether or not it works. They say unplug a device and see if it boots into degredation mode. For me it pulls up an initramfs shell. Is that right?

---

### Post by darkod on 2016-09-01
No, it's not. It should boot even with one disk if bootdegraded=true is used.
If it boots into initramfs it's not booted in fact.

But few people have reported this lately so I wonder if there is some mdadm bug around, or simply people didn't use bootdegraded=true. You can add it as one time option in the grub entry to test. Search on google where exactly to add it if you want to try.

---

