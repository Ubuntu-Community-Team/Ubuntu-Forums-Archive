---
title: "mdadm superblock mount issue"
date: 2012-09-11
forum: Server Platforms
---

### Post by d3berger on 2012-09-11
Hello everyone,

I am having an issue getting my mdadm raid 5 to mount. It seems like it has gotten a bad superblock or lost the filesystem somehow. This happened after a reboot, the raid was working before and I have about 1.8TB of data on it.

```

# fdisk -l

Disk /dev/sda: 2000 GB, 2000396321280 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   fd  Lnx RAID auto

Disk /dev/sdb: 2000 GB, 2000396321280 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243191  1953431676   fd  Lnx RAID auto
Warning: Partition 1 does not end on cylinder boundary.

Disk /dev/sdc: 2000 GB, 2000396321280 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243191  1953431676   fd  Lnx RAID auto
Warning: Partition 1 does not end on cylinder boundary.

Disk /dev/sdd: 8 GB, 8217054720 bytes
255 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1000     8032468    b  FAT32
Warning: Partition 1 does not end on cylinder boundary.
Error: /dev/md127: unrecognised disk label

```

```

# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md127 : active (auto-read-only) raid5 sdc1[3] sdb1[0] sda1[1]
      3906858624 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

```

```

# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sun Sep  9 01:19:43 2012
     Raid Level : raid5
     Array Size : 3906858624 (3725.87 GiB 4000.62 GB)
  Used Dev Size : 1953429312 (1862.94 GiB 2000.31 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 20:39:11 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : ubuntu:1  (local to host ubuntu)
           UUID : c1d3dc22:591547b6:9f40b25e:7cd7a3d9
         Events : 26

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       3       8       33        2      active sync   /dev/sdc1

```

```

# mount -t ext3 /dev/md127 4tb
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```

# dmesg | tail
[   20.413469] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.862008] r8169 0000:02:00.0: eth0: link up
[   21.868215] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.576026] eth0: no IPv6 routers present
[ 8031.632455] EXT3-fs (md127): error: can't find ext3 filesystem on dev md127.
[ 8031.652402] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[ 8031.672284] FAT-fs (md127): bogus number of FAT structure
[ 8031.672290] FAT-fs (md127): Can't find a valid FAT filesystem
[ 8031.696268] SQUASHFS error: Can't find a SQUASHFS superblock on md127
[ 8040.053649] EXT3-fs (md127): error: can't find ext3 filesystem on dev md127.

```

Please let me know if you have any solutions. I would like to be able to retrieve the data. If there is a way to somehow copy the data to a spare disk let me know.

Thanks for any help that you may have.

---

### Post by rubylaser on 2012-09-11
Your array looks like it is assembled correctly, other than it's in a auto-read-only state.  Can you provide the output of these commands?

```
cat /etc/mdadm/mdadm.conf
```
```
mdadm -E /dev/sd[abc]1
```

---

### Post by d3berger on 2012-09-11
Thanks for the reply. Here is the output:

```

# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Wed, 25 Apr 2012 15:33:29 +0000
# by mkconf $Id$

```

```

# mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1d3dc22:591547b6:9f40b25e:7cd7a3d9
           Name : ubuntu:1  (local to host ubuntu)
  Creation Time : Sun Sep  9 01:19:43 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 7813717248 (3725.87 GiB 4000.62 GB)
  Used Dev Size : 3906858624 (1862.94 GiB 2000.31 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d592753f:693b26eb:5d2220e1:94295b7d

    Update Time : Sun Sep  9 20:39:11 2012
       Checksum : 550993df - correct
         Events : 26

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)

```

```

# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1d3dc22:591547b6:9f40b25e:7cd7a3d9
           Name : ubuntu:1  (local to host ubuntu)
  Creation Time : Sun Sep  9 01:19:43 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906859008 (1862.94 GiB 2000.31 GB)
     Array Size : 7813717248 (3725.87 GiB 4000.62 GB)
  Used Dev Size : 3906858624 (1862.94 GiB 2000.31 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ef22e82a:61e32f41:4007bbf3:e6a71f61

    Update Time : Sun Sep  9 20:39:11 2012
       Checksum : 8ce2b2a2 - correct
         Events : 26

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)

```

```

# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1d3dc22:591547b6:9f40b25e:7cd7a3d9
           Name : ubuntu:1  (local to host ubuntu)
  Creation Time : Sun Sep  9 01:19:43 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906859008 (1862.94 GiB 2000.31 GB)
     Array Size : 7813717248 (3725.87 GiB 4000.62 GB)
  Used Dev Size : 3906858624 (1862.94 GiB 2000.31 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c91d2d77:1302678f:8f8a882e:2ef337c6

    Update Time : Sun Sep  9 20:39:11 2012
       Checksum : c7449ac8 - correct
         Events : 26

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)

```

---

### Post by rubylaser on 2012-09-11
Well, you mdadm.conf file is basically empty, but that's not causing the problem (I would populate it with a proper entry though like this).

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Next, you can fix the auto-read-only error like this.
```
mdadm --readwrite /dev/md127
```

Finally, this actually appears to be a filesystem issue. Are you certain the filesystem is ext3?  It appears from your logfile that you tried mounting with a number of different filesystem types (could it be XFS, JFS, etc.). In the past, have you mounted the array manually, or via an /etc/fstab entry?

---

### Post by d3berger on 2012-09-11
Thanks again for the reply.

I ran the code you provided for the mdadm.conf and the readwrite.

I created the filesystem as ext3 and only mounted it myself not with fstab. Here are the commands I used:

```

mkfs -t ext3 /dev/md1
mkdir /mnt/4tb
mount /dev/md1 /mnt/4tb/

```

This was back when it was /dev/md1 before the system rebooted and I got this problem.

---

