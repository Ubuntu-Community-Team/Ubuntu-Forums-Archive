---
title: "Cant mount drive in Ubuntu Server 11.04 64-bit"
date: 2011-07-25
forum: Server Platforms
---

### Post by GOSSSAMER on 2011-07-25
I just upgraded to 11.04 from 10.10. I have all my VMs on the second drive I need to mount, however I get the below errors when trying to mount the drive:
 
 
sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062264
Device Boot Start End Blocks Id System
/dev/sda1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2 32 60802 488134657 5 Extended
/dev/sda5 32 60802 488134656 8e Linux LVM
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d1599
Device Boot Start End Blocks Id System
/dev/sdb1 1 182401 1465136001 83 Linux
Disk /dev/dm-0: 491.5 GB, 491480154112 bytes
255 heads, 63 sectors/track, 59752 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Disk /dev/dm-0 doesn't contain a valid partition table
Disk /dev/dm-1: 8313 MB, 8313110528 bytes
255 heads, 63 sectors/track, 1010 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Disk /dev/dm-1 doesn't contain a valid partition table
 
> sudo mount /dev/sdb1 /media/Tera
[COLOR=darkred]mount: unknown filesystem type 'LVM2_member'[/COLOR]
 
> sudo blkid
/dev/sda1: UUID="68865a4d-32fb-48f8-883a-bb6e286b6d10" TYPE="ext2"
/dev/sda5: UUID="9BCjvJ-nJUa-UJTr-HWyB-WjEK-dXv0-7kU1zO" TYPE="LVM2_member"
/dev/sdb1: UUID="pdpfsq-5aUw-X4Ov-4qzo-NHjy-1SQo-q1d2RT" TYPE="LVM2_member"
/dev/mapper/ubu-root: UUID="28a419be-4cb0-47e1-89e2-b961a13bef80" TYPE="ext4"
/dev/mapper/ubu-swap_1: UUID="cba225a3-6c7d-4c0a-bb62-f29d718d44c0" TYPE="swap"
 
 
 
Any help would be greatly appreciated.

---

