---
title: "Migrate Lucid server OFF from LVM partition"
date: 2010-06-15
forum: Server Platforms
---

### Post by SantaFox on 2010-06-15
Hello all,

I need to transfer my production server from old disk with LVM partition to new disk, but WITHOUT LVM. Clonezilla may clone disk with LVM, so it's not a solution. Even if I could copy my filesystem to new disk I still have to clean my installation from all LVM stuff, edit /etc/fstab and so on... but I have no enough Linux skills unfortunately. Could you help me with step-by-step guide (or with reference to some manual)?

My fdisk -l (I'd like to move from sda to sdb):

Disk /dev/sdb: 146.8 GB, 146815737856 bytes
178 heads, 63 sectors/track, 25570 cylinders
Units = cylinders of 11214 * 512 = 5741568 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd51e31a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25570   143369887+   7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000945c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        9730    77899777    5  Extended
/dev/sda5              32        9730    77899776   8e  Linux LVM

---

