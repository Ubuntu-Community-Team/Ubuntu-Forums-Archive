---
title: "Mount: Unknown filesystem type ' '"
date: 2009-08-15
forum: Server Platforms
---

### Post by albengy on 2009-08-15
Hi all,

I have an array raid 5, I did fdisk -l and it shows the array, but I can't mount the array. The error says unknown filesystem type ''. Please help. I appreciate in advance. Thanks!

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000892e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59861   480833451   83  Linux
/dev/sda2           59862       60801     7550550    5  Extended
/dev/sda5           59862       60801     7550518+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c8bef7a

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf612128

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x202b9d61

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c8bef7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1           1         512    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sde3               1           1         512    0  Empty
Partition 3 does not end on cylinder boundary.

Disk /dev/md0: 4500.9 GB, 4500905459712 bytes
2 heads, 4 sectors/track, 1098853872 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x1c8bef7a

    Device Boot      Start         End      Blocks   Id  System
beta@bubuntu:~$ sudo mount /dev/md0
mount: unknown filesystem type ''

---

### Post by Bachstelze on 2009-08-15
You need to create a filesystem on your array before you can mount it. ;)

---

### Post by albengy on 2009-08-15
would it delete my data if you do that? I did have some data before, but when I install new version of the server, the system recognizes the array but doesn't allow me to mount. BTW, is the command to create filesystem
sudo mke2fs -j /dev/md0 ? Sorry for the silly questions. I'm new at this. Thanks.

---

### Post by Bachstelze on 2009-08-15
> **albengy said:**
> would it delete my data if you do that? I did have some data before, but when I install new version of the server, the system recognizes the array but doesn't allow me to mount.

If you *already* have a filesystem on your array, you just need to specify it (and the mountpoint) on the command-line. For example:

```
sudo mount -t ext3 /dev/md0 /mnt/raid
```

Or add a line to your fstab...

---

### Post by albengy on 2009-08-15
in my fstab I added:

/dev/md0 /media/samba  auto defaults 0 3

When I created the array before the new server version, I did create file system using the command sudo mke2fs -j /dev/md0

When I enter the command
sudo mount -t ext3 /dev/md0 /media/samba, I got the following error:
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Bachstelze on 2009-08-15
Then there's a good chance your data got lost when you reinstalled...

---

### Post by albengy on 2009-08-15
I hope not, because when I reinstalled the new server edition, it recognized the array after reboot, and the array seems OK. I did command 
beta@bubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde[3] sdd[2] sdb[0] sdc[1]
      4395415488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]


and

beta@bubuntu:~$ sudo mdadm -E /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 15181fa0:e0b47e28:b62cfa25:81e9a18b (local to host bubuntu)
  Creation Time : Sat Aug  8 16:22:42 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Aug 15 10:06:46 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c368bb1b - correct
         Events : 4

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde


and sudo fdisk -l     shows that /dev/md0 is there. How can I lost the data?

---

### Post by albengy on 2009-08-15
I did use command
sudo e2fsck -f /dev/md0 

and the system fixed inodes and group counts and I'm able to mount /dev/md0 and more importantly, I get my data back. Thanks!

---

### Post by fjgaude on 2009-08-16
Create a mountpoint? Did you do that and then try to mount the array?

---

