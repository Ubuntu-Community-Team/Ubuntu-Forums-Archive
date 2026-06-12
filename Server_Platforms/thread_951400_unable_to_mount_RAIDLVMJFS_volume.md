---
title: "unable to mount RAID/LVM/JFS volume"
date: 2008-10-18
forum: Server Platforms
---

### Post by NarsilAnduril on 2008-10-18
Hi,

Bad news, my RAID volumes aren't up anymore (after sever crash).

My status : Running Hardy server i386, mdadm RAID5 with 3 LVM on it, one 100Gb ext3 and two 500Gb JFS. After crash, the JFS volumes don't mount anymore but the ext3 does.

Investigation 1 : The four 500Gb HD are physically ok

```
diego@pinguin:/mnt/movies$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0ce5d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00100000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x560a3dac

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/md0: 1500.3 GB, 1500323119104 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   fd  Linux raid autodetect

```

---

