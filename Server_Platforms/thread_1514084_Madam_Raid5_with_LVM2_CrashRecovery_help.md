---
title: "Madam Raid5 with LVM2 Crash/Recovery help"
date: 2010-06-20
forum: Server Platforms
---

### Post by speed32219 on 2010-06-20
I use this as a Video server and bakup of our mail/documents.
It is a 6TB server (4.1 showing useable) and the other day I was backing up a video when we had a power failuse.  I have a UPS but had not got around to installing it. :(

OK, my bad, when the power come back on I started the system and it went into recovery mode (E2fsk ?) maybe don't remember, all the disk lights were flashing and mdstat reported recovery or something like that.  This went on for about 12 hours, during this time the array was unavailable. (Could not be mounted) 

Current Status:
$cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdb[3] sdd[0] sdc[1] sde[2]
      4395415488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1e81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         790     6345643+  83  Linux
/dev/sda2             791         974     1477980   82  Linux swap / Solaris
/dev/sda3             975       60801   480560377+  83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50610834

**Disk /dev/sdb doesn't contain a valid partition table**

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50610834

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465138552   fd  Linux **raid autodetect**

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

**Disk /dev/sde doesn't contain a valid partition table**

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

**Disk /dev/sdd doesn't contain a valid partition table**

Disk /dev/md1: 4500.9 GB, 4500905459712 bytes
2 heads, 4 sectors/track, 1098853872 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

**Disk /dev/md1 doesn't contain a valid partition table**
```

When I try and start LVM2 this is the error.
$**sudo mount /dev/vg1/raid /mnt/raid**
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-raid,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$**dmesg | tail**
[   98.527873] EXT3-fs error (device dm-0): ext3_check_descriptors: Block bitmap for group 473 not in group (block 15171584)!
[   99.008947] EXT3-fs: group descriptors corrupted!

Where to go from here, it looks as if sdc drive is OK, but not sure.  I tried removing lvm2 and mdadm and re-isntalling it and doing an assemble for mdadm without error and it sees all the drives as shown above.

$**cat /etc/mdadm/mdadm.conf**

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=7e6f942e:fb608064:d66a740f:8642d62d

# This file was auto-generated on Sun, 20 Jun 2010 12:39:20 -0400
# by mkconf $Id$

```

**Output of mdadm detail**

```
~$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Sat Apr 17 09:03:07 2010
     Raid Level : raid5
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jun 20 12:59:38 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 7e6f942e:fb608064:d66a740f:8642d62d
         Events : 0.86754

    Number   Major   Minor   RaidDevice State
       0       8       48        0      active sync   /dev/sdd
       1       8       32        1      active sync   /dev/sdc
       2       8       64        2      active sync   /dev/sde
       3       8       16        3      active sync   /dev/sdb
gellex@Digi-Center:~$

```

Should I remove mdadm and try to isntall it using create instead of assemble?  Or sould I re-install lvm2 and try and setup another lvm replacing the existing so I can run a lvm type of mkfs on it?
help?

---

### Post by AdotB on 2010-06-20
I use mdadm, but I've never used lvm. So I'll offer what I can.

It looks like the problem is on the lvm side of things, since your mdadm status shows all drives as ok. And i think the reason all but the one drive shows `no valid partition table' is because of the use of lvm. If that is the case, then I don't think those are a problem.

If you're not worried about losing the contents of the raid/lvm drives, you could just do a fresh lvm setup, which will of course erase everything.

Sorry I dont know enough about lvm to help with the recovery , but hopefully I've provided at least a little insight.

Good luck

---

### Post by speed32219 on 2010-06-20
So after your post I decided that LVM was the problem also since it was giving me superblock errors and no partition errors. I have decided to run the following command on the lvm2 and we'll see what happens.  
sudo fsck -b [alternate superblock] /dev/vg1/raid 

Good news, got everthing back!

4.1T  2.3T  1.7T  58% /mnt/raid

---

### Post by AdotB on 2010-06-20
Glad it worked out for you.

---

