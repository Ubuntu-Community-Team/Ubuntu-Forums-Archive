---
title: "Creating RAID1 on a running Ubuntu 10.04"
date: 2010-07-29
forum: Server Platforms
---

### Post by Frankk on 2010-07-29
Hello I have a running system (Ubuntu 10.04 installed and configured by someone else) with two identical hard drives, but where only one is in use by the OS.

I would like to activate the second hard drive to build a raid1 setup. I know it is possible as I read a [guide]("http://www.howtoforge.com/software-raid1-grub-boot-debian-etch") that explains how to build the raid array, modify fstab and the required files to make it boot correctly using the raid device. But I see that ubuntu 10.04 is using LVM and i'm not very pratical with this. Is it possible to use the second hard drive in a raid1 fashion with LVM? or can I simply create the raid device with mdadm, modify fstab and boot files to point to the new device and LVM will work on top of the new configuration?

Please tell me the correct way to achieve a mirroring configuration with the setup I have.

This is the output of fdisk -l:

```
Francesco@serverftp:~$ sudo fdisk -l
[sudo] password for Francesco:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020654

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       30402   243947521    5  Extended
/dev/sda5              32       30402   243947520   8e  Linux LVM

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```


Thank you,
Francesco

---

### Post by rubylaser on 2010-07-29
Yes, you can follow those directions from howtoforge.  I'm not really sure why you have LVM setup if you didn't set it up for a purpose.  I see you don't have a swap configured which is also strange.  Either way, though, those directions should work just fine.

---

### Post by ruffEdgz on 2010-07-29
I read the guide as well and it should work but I would be caucious about the LVM setup compared to what the guide has.

If you want to have the same setup as the guide (no LVM) then you will want to make the RAID similar to what it said in the guide (you will have to substitude some devices with logical volumes).

If you want to have the setup with LVM, you will have to think about it a bit differently and I can try to help modify the guide you supplied to incorperate setting up a RAID1 with LVM.

Best of luck!

---

