---
title: "Clarification on Bootable Flag and its necessity for Ubuntu 10.04??"
date: 2013-04-12
forum: Server Platforms
---

### Post by cormu7 on 2013-04-12
Hello,

I recently installed Ubuntu 10.04 on an older server of ours. I have a RAID5 setup, consisting of 5 disks setup on sda.  I have two 2TB disks made into a logical volume (sdb and sdc). I also have the "/" drive on sdb1.

If my "/" directory is on sdb, why is the bootable flag indicated on the sda1 partition and not sdb1? Isn't grub installed on the "/" directory? I've been reading online where the bootable flag is unecessary for Linux. Is this correct?

Any help would greatly be appreciated.

Thank you.

here is the out from fdisk -l

```
Disk /dev/sda: 2000.0 GB, 1999957393408 bytes
255 heads, 63 sectors/track, 243147 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1be8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      243148  1953081345    5  Extended
/dev/sda5               1      243148  1953081344   8e  Linux LVM

Disk /dev/sdb: 2000.0 GB, 1999988850688 bytes
255 heads, 63 sectors/track, 243151 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1de9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3648    29295616   83  Linux
/dev/sdb2            3648        9727    48828416   8e  Linux LVM
/dev/sdb3            9727      243152  1874987009    5  Extended
/dev/sdb5            9727       10334     4881408   83  Linux
/dev/sdb6           10335       11550     9764864   83  Linux
/dev/sdb7           11550       13982    19529728   8e  Linux LVM
/dev/sdb8           13982       26139    97654784   8e  Linux LVM
/dev/sdb9           26139      243152  1743152128   8e  Linux LVM

Disk /dev/sdc: 2000.0 GB, 1999988850688 bytes
255 heads, 63 sectors/track, 243151 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025901

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243152  1953112065    5  Extended
/dev/sdc5               1      243152  1953112064   8e  Linux LVM


```

---

### Post by MAFoElffen on 2013-04-13
In the install the default for grub to install it's mbr is the 1st disk seen in the BIOS. Of course you can direct this to another disk in the install if you chose to. That MBR then points to which disk and which partition the disk /boot is located for the particular OS which grub is running from (primary OS).

So if you ran the testdisk script, it would probably say yours is following that layout- that the bootloader is loaded on disk /devs/sda and points to partion /dev/sdb1/boot, which for you is in /dev/sdb/ which is root (/). As for partitions being marked with a "boot" flag... Windows OS'es care. Some BIOS'es care Linux doesn't... until you start considering 3TB+ GPT disks, where things get a little less tolerant.

If From the install to later... if the order seen is then different, It really doesn't matter, as Grub2 goes by the UIDs over the HD hints, so if the order did change, it usually picks that up by using the UID's as a preference. Sometimes not, but that is now usually rare... As long as the BIOS Order still hits the disk with the MBR boot loader first, it's usually Okay.

Curious. I have to ask. Why are you doing RAID5 on a single disk... People have not believed me that this is possible with Linux software RAID, until I show them...  But I also know the drawbacks to that. Imagine that you are trying to stripe data across 5 physical drives for reads/writes. In many cases this extends the life of the drives and ends up faster. Plus, then you have parity and if a member fails... Now imagine trying to write 5 physically separate locations on the same single disk at essentially  the same time... mdadm can adjust for that, but still takes a performance hit. Seems to be hard on a disk. And if that single drive goes, all 5 members of that array are lost. Am I missing something there? Just wondering if I am not seeing something where than would be beneficial. Well I guess rebuild time would be faster. (See. Trying to see both sides.)

---

### Post by cormu7 on 2013-04-16
MAFoElffen,

Thanks for the detailed explanation. I have read about Windows only caring about the boot flag, but I just wasn't sure if that was true for Linux.

The RAID5 is just on the five 500 GB disks. I don't have the two 2 TB disks setup on anything.

My main issues/concern is making sure that I have grub,/,etc. on sdb, and not sda. I do. The older five 500 GB disks are on sda.  In the event of a crash on sda, i still want to be able to boot up ubuntu access other data on sdb. This is possible if "/"  and my other data directories are partitioned on sdb, no?

Thanks,

cormu7

---

