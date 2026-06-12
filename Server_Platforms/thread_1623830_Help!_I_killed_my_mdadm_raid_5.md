---
title: "Help! I killed my mdadm raid 5"
date: 2010-11-17
forum: Server Platforms
---

### Post by Intrepid_Chuck on 2010-11-17
Arrg, Major goof. I managed to kill my raid 5 through my own stupidity. Here is the chain of events, Your help is greatly appreciated.

I added disk #6 to my working 5 disk array, after about 24 hours it was done but i did not see the extra space (I now know all I needed to do was fsck and resize).
I failed and removed the new disk from the array then somehow also failed and removed drive # 5 from the array. At this point the array was still running so I added drive #5 & 6 back to the array but they got added as spares instead of active components. next I rebooted and could not assemble the array. I tried every possible way to reassemble the array without any success. Several posts have suggested I create the array again but I am hesitant to do this as I do not want to lose my data.Before I mess it up any more here's where I am.

/proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid0 sdh1[1] sdg1[0]
      488391808 blocks 64k chunks
```

mdadam --examine /def/sda2,b2,c2,d2,e,f
```
server2@server2:~$ sudo mdadm --examine /dev/sda2
[sudo] password for server2: 
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
  Creation Time : Sat Feb  6 17:37:20 2010
     Raid Level : raid5
  Used Dev Size : 1952537920 (1862.09 GiB 1999.40 GB)
     Array Size : 9762689600 (9310.43 GiB 9996.99 GB)
   Raid Devices : 6
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Nov 16 14:29:15 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 0
       Checksum : aacb71b5 - correct
         Events : 382240

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
server2@server2:~$ sudo mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
  Creation Time : Sat Feb  6 17:37:20 2010
     Raid Level : raid5
  Used Dev Size : 1952537920 (1862.09 GiB 1999.40 GB)
     Array Size : 9762689600 (9310.43 GiB 9996.99 GB)
   Raid Devices : 6
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Nov 16 14:29:15 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 0
       Checksum : aacb71c7 - correct
         Events : 382240

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
server2@server2:~$ sudo mdadm --examine /dev/sdc2
/dev/sdc2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
  Creation Time : Sat Feb  6 17:37:20 2010
     Raid Level : raid5
  Used Dev Size : 1952537920 (1862.09 GiB 1999.40 GB)
     Array Size : 9762689600 (9310.43 GiB 9996.99 GB)
   Raid Devices : 6
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Nov 16 14:29:15 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 0
       Checksum : aacb71d9 - correct
         Events : 382240

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       34        2      active sync   /dev/sdc2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
server2@server2:~$ sudo mdadm --examine /dev/sdd2
/dev/sdd2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
  Creation Time : Sat Feb  6 17:37:20 2010
     Raid Level : raid5
  Used Dev Size : 1952537920 (1862.09 GiB 1999.40 GB)
     Array Size : 9762689600 (9310.43 GiB 9996.99 GB)
   Raid Devices : 6
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Nov 16 14:29:15 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 0
       Checksum : aacb71eb - correct
         Events : 382240

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       50        3      active sync   /dev/sdd2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
server2@server2:~$ sudo mdadm --examine /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
  Creation Time : Sat Feb  6 17:37:20 2010
     Raid Level : raid5
  Used Dev Size : 1952537920 (1862.09 GiB 1999.40 GB)
     Array Size : 9762689600 (9310.43 GiB 9996.99 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0

    Update Time : Tue Nov 16 14:22:42 2010
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 2
  Spare Devices : 1
       Checksum : aacb70b7 - correct
         Events : 382232

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       64        6      spare   /dev/sde

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       64        6      spare   /dev/sde
server2@server2:~$ sudo mdadm --examine /dev/sdf
/dev/sdf:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
  Creation Time : Sat Feb  6 17:37:20 2010
     Raid Level : raid5
  Used Dev Size : 1952537920 (1862.09 GiB 1999.40 GB)
     Array Size : 9762689600 (9310.43 GiB 9996.99 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Nov 16 14:20:02 2010
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : aacb7088 - correct
         Events : 382228

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       80        6      spare   /dev/sdf

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       80        6      spare   /dev/sdf
   7     7       8       64        7      spare   /dev/sde
server2@server2:~$ 

```

/etc/mdadm/mdadm.conf
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
MAILADDR xxxxxxxxxxxx
# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid5 num-devices=5 UUID=b7390ef0:9c9ecbe0:abcb3798:f53e3ccc
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=559552c6:b54f0dff:0dc726d6:bae63db2

# This file was auto-generated on Mon, 15 Mar 2010 22:25:29 -0400
# by mkconf $Id$
MAILFROM xxxxxxxxxxx
```

fdisk -l
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e37a

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00048a02

   Device Boot      Start         End      Blocks   Id  System

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243202  1953514583+  ee  GPT

Disk /dev/sdg: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b4a57df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdh: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x174b0f87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/md1: 500.1 GB, 500113211392 bytes
2 heads, 4 sectors/track, 122097952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

---

### Post by Medwyyn42 on 2010-11-17
There is a way in mdadm to re-assemble arrays using the encoded array meta-tag, and then regrow the array. I think it's in raid.wiki.kernel.org. Good luck. Managed to recover my array after some hunting with no data loss. Try mdadm --assemble --force. See if the superblocks don't match (my issue).

---

### Post by Intrepid_Chuck on 2010-11-18
Thanks for the suggestions but --assemble --force does not work, It thinks sde is a spare and ignores sdf.

mdadm --assemble --force /dev/md0 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 /dev/sde /dev/sdf
returns mdadm: /dev/md0 assembled from 4 drives and 1 spare - not enough to start the array.

raid.wiki.kernel.org suggests using mkraid --force. I believe mkraid is deprecated and it also requires "an up to date /etc/raidtab" which does not exist on my system.

---

### Post by SaturnusDJ on 2010-12-16
Are you still having this problem or did you give up hope?

Find out why mdadm rejects sde and sdf. Add verbose to the command.


I wonder why is fdisk reporting this:
sda1: GPT
sdb1: GPT
sdc1: GPT
sdd1: GPT
sde: no partitions
sdf: no partitions

And why is fdisk talking about sd*1 and mdadm about sd*2?

Edit:
Oh ok, so the partition part should be nothing to worry about. But I still think it is strange to have sda2,sdb2,sdc2,sdd2 in an array with sde and sdf.

---

### Post by rubylaser on 2010-12-16
Your pastes seem to reflect that mdadm is showing the array active and clean.  I'm not sure why you're trying to force assemble it.  It's assembled.  If you'd like to add the two disks back, you'll just want to tell mdadm to use the new "spares".  

```
sudo mdadm --grow /dev/md0 --raid-devices=4
```

If cat /proc/mdstat is showing the array inactive and not started, please paste in new info so that we can help...unless, you've already fixed or rebuilt the array ;)

SaturnusDJ, fdisk doesn't work with GPT partitions, so that's not a big deal, you can use parted to work on them.

---

