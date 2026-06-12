---
title: "RAID 5 degraded"
date: 2014-12-25
forum: Server Platforms
---

### Post by Rick P. on 2014-12-25
Well Merry Christmas to me  :(

I had a glitch on my server that took it down (suspect it looked suspiciously like a little finger). Upon restarting it flagged one of my RAID 5 arrays as being degraded and started rebuilding. No worries i thought and watched it for the next few hours while it worked. At about 98% - 99% the rebuild failed punting 2 drives out (/dev/sdh1 and /dev/sdj1). /dev/sdh1 showed a read error in the logfile so i made a copy onto a new drive with ddrescue (2 sectors were unreadable so I'll have a bit of data loss). In the process /dev/sdj1 has been marked as a spare. In trying to rebuild it looks like when ddrescue copied the faulty disk but didn't copy the superblock information along with it so i tried rebuilding without it. 

```
root@rick-Server:/home/rick# mdadm --verbose --create /dev/md0 --level=5 --raid-devices=6 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 missing /dev/sdj1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Tue Dec 27 11:11:22 2011
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Tue Dec 27 11:11:22 2011
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Tue Dec 27 11:11:22 2011
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Tue Dec 27 11:11:22 2011
mdadm: /dev/sdj1 appears to contain an ext2fs file system
    size=1177632768K  mtime=Mon Dec 22 19:29:39 2014
mdadm: /dev/sdj1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Tue Dec 27 11:11:22 2011
mdadm: size set to 1953381888K
```


Note that there are 2 entries above for /dev/sdj1 so I aborted the create. I don't know where it got the idea that /dev/sdj1 should have a big ext2fs on it. The data on /dev/sdj1 should be correct, as is that on /dev/sdh1 less the two failed sectors that ddrescue couldn't copy. I have backups for just about everything on the array but it's in various locations and not available to me over the holidays so I'd rather spend a bit of time getting the existing array back. Thoughts on what I should do to get there? The data below is with the ddrescued copy of /dev/sdh1 installed. If I put the original /dev/sdh1 drive back in the system will start degraded and resync, then fail when almost complete because of the read errors on /dev/sdh1 so I either need to rebuild with the copied /dev/sdh1 or get it to start with /dev/sdj1 then add /dev/sdh1 to restore superblock info (i think). There's always the option of killing the resync and backing up the data from the degraded array but at 10 TB i don't have enough space to do so. Ideas?

Thanks
Rick

[HR][/HR]
Array details (it's /dev/md0 that I need to recover):

```

root@rick-Server:/home/rick# cat /etc/mdadm/mdadm.conf
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
#ARRAY /dev/md0 UUID=f5eb59ff:3e0105c9:4c993831:1bf84ec9

# This file was auto-generated on Sat, 27 Oct 2012 14:09:28 -0400
# by mkconf $Id$
#Modified to try to resolve boot issues
#DEVICE /dev/sd??
DEVICE /dev/sd[b-m]1
#DEVICE partitions
#update-initramfs -u

ARRAY /dev/md0 metadata=0.90 UUID=f5eb59ff:3e0105c9:4c993831:1bf84ec9
ARRAY /dev/md1 metadata=1.2 name=rick-Server:1 UUID=6e35700a:a2bf4530:5de8082f:4ef3db26
```



```
root@rick-Server:/home/rick# mdadm -E /dev/sd[cdefhj]1/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f5eb59ff:3e0105c9:4c993831:1bf84ec9
  Creation Time : Tue Dec 27 11:11:22 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 9767567360 (9315.08 GiB 10001.99 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Dec 23 14:32:46 2014
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5db2716b - correct
         Events : 140160

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      faulty   /dev/sdh1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f5eb59ff:3e0105c9:4c993831:1bf84ec9
  Creation Time : Tue Dec 27 11:11:22 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 9767567360 (9315.08 GiB 10001.99 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Dec 23 14:32:46 2014
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5db2717d - correct
         Events : 140160

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      faulty   /dev/sdh1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f5eb59ff:3e0105c9:4c993831:1bf84ec9
  Creation Time : Tue Dec 27 11:11:22 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 9767567360 (9315.08 GiB 10001.99 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Dec 23 14:32:46 2014
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5db2718f - correct
         Events : 140160

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      faulty   /dev/sdh1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f5eb59ff:3e0105c9:4c993831:1bf84ec9
  Creation Time : Tue Dec 27 11:11:22 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 9767567360 (9315.08 GiB 10001.99 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Dec 23 14:32:46 2014
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5db271a1 - correct
         Events : 140160

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      faulty   /dev/sdh1
mdadm: No md superblock detected on /dev/sdh1.
/dev/sdj1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f5eb59ff:3e0105c9:4c993831:1bf84ec9
  Creation Time : Tue Dec 27 11:11:22 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 9767567360 (9315.08 GiB 10001.99 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Dec 23 14:32:46 2014
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5db271e1 - correct
         Events : 140160

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     7       8      145        7      spare   /dev/sdj1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      faulty   /dev/sdh1
```

---

