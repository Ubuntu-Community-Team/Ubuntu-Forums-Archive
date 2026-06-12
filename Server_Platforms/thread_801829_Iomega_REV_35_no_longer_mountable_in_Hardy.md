---
title: "Iomega REV 35 no longer mountable in Hardy"
date: 2008-05-20
forum: Server Platforms
---

### Post by DrJohn999 on 2008-05-20
Iomega REV 35 ATAPI drive was mountable as iso9660 type under 7.10. In a new 8.04 install on an ASUS K8N-LR board, the drive's filesystem type is not recognized:
```
root@K8NLR6:/home# mount -t iso9660 /dev/scd1 /media/rev0
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@K8NLR6:/home# dmesg | tail
[165483.737355] ISOFS: Unable to identify CD-ROM format.


```

I temporarily installed the drive in a WinXP Pro machine -- no problems! Recognized, readable, writable.

Back in the Ubuntu box, with a disk I don't mind overwriting in the drive, I deleted the existing partition and tried to create a new DOS partition:

```
...
Command (m for help): p

Disk /dev/scd1: 35.0 GB, 35002122240 bytes
255 heads, 63 sectors/track, 1063 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0xd789c09d

     Device Boot      Start         End      Blocks   Id  System

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x2ba3e987.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1063.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.

Error closing file
root@K8NLR6:/home# dmesg | tail
[166512.797981] ISOFS: Unable to identify CD-ROM format.
[166737.677455] Buffer I/O error on device sr1, logical block 0
[166737.677485] lost page write due to I/O error on sr1

```

A similar problem occurs if I try to create a regular partition (at p4).

The drive is physically attached to the second IDE port on the board and jumpered as the primary device. It's recognized by the BIOS as a REV drive. It's the only device on that port (there's a DVD/ROM on the first port that works fine).

From all of this I should conclude that there's a hardware problem between the motherboard and the REV drive, but this seems strange given that 1) Either IDE port works with the DVDROM; 2) Neither port works with the REV drive; 3) the REV drive works just fine on another system; and 4) the REV drive worked fine under 7.10.

As an aside, I read on the Iomega RDD Tools page on SourceForge that udffs is supported in Linux kernels past 2.6.7. As Hardy reports it's running 2.6.24-16-server, I'd expect to be able to mount a udffs type system once I get this problem worked out. Has anyone had experience with that?

Thanks,

DrJohn

---

