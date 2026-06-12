---
title: "LUN not showing up from SAN"
date: 2011-04-27
forum: Server Platforms
---

### Post by dtd646 on 2011-04-27
I am using NFS to mount large LUNs from my SAN. I have one lun already setup and configured. I am adding an additional partition from the same SAN but I am confused on the setup. I know the LUN is connecting to my NFS server correctly because I see it listed in my /proc/scsi/scsi as an additional LUN. What I don't see is the drive being displayed in fdisk -l.
 
I did notice one thing though, when I disable the host mapping from the SAN, I see it removed from the /proc/scsi/scsi file AND my fdisk information changes from /dev/sdb TO /dev/sdc (see changes below)
 
-------------------------------------------------------
fdisk -l without host mapping to SAN:
 
Disk /dev/sda: 13999.0 GB, 13999026470912 bytes
255 heads, 63 sectors/track, 1701951 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Device Boot Start End Blocks Id System
/dev/sda1 1 267350 2147483647+ ee GPT
/dev/sda2 1 97855 786019519+ 83 Linux
 
Partition table entries are not in disk order
 
Disk /dev/sdb: 146.0 GB, 145999527936 bytes
255 heads, 63 sectors/track, 17750 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000669e4
 
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2 32 17750 142325761 5 Extended
/dev/sdb5 32 17750 142325760 8e Linux LVM
 
---------------------------------------------------------------------
fdisk -l with host mapping to SAN:
 
Disk /dev/sda: 13999.0 GB, 13999026470912 bytes
255 heads, 63 sectors/track, 1701951 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Device Boot Start End Blocks Id System
/dev/sda1 1 267350 2147483647+ ee GPT
/dev/sda2 1 97855 786019519+ 83 Linux
 
Partition table entries are not in disk order
 
Disk /dev/sdc: 146.0 GB, 145999527936 bytes
255 heads, 63 sectors/track, 17750 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000669e4
 
Device Boot Start End Blocks Id System
/dev/sdc1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sdc2 32 17750 142325761 5 Extended
/dev/sdc5 32 17750 142325760 8e Linux LVM
 
So the drive is trying to show up a /var/sdb but not getting there? Are there any commands I can use to get this to show up as an addtional drive to use?
 
Thanks for any help.
 
Thanks in advance!

---

### Post by dtd646 on 2011-05-06
Found the solution to this.  Wasn't an OS problem.  The problem was on the SAN that I was using.  My SAN has 2 controllers but I am currently only using controller A.  So, when I created the new array and logical drive, the path was being defaulted to controller B, even though it wasn't plugged in.  The LUN information got passed to the OS through controller A, which is what I was seeing BUT the path to the LUN wasn't available.

---

