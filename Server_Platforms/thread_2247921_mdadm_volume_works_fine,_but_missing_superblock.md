---
title: "mdadm volume works fine, but missing superblock"
date: 2014-10-11
forum: Server Platforms
---

### Post by MakOwner on 2014-10-11
This is a non critical array that I was running in RAID5 with a cold-standby hot spare.  Upgraded the enclosure to one with enough slots to house all the disks, so I added the cold standby and reshaped to RAID6.
Reshape completed fine, filesystem passes fsck mdadm --detail and examination of all volumes show everything is consistent, however, mdadm -E reports no superblock.

It assembles at boot, the filesystem mounts with no issue.  I have just never seen one in this state.

If it were necessary to get this back into a production state, would the next step be to restore an alternate superblock? 
Is there a way to create the superblock from the existing filesystem without restoring an alternate superblock?
Just ignore it?


```

# fsck -f /dev/md2
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
md2: 813110/457859072 files (1.6% non-contiguous), 1831202785/1831427840 blocks

# mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Wed Jun 27 23:30:47 2012
     Raid Level : raid6
     Array Size : 7325711360 (6986.34 GiB 7501.53 GB)
  Used Dev Size : 732571136 (698.63 GiB 750.15 GB)
   Raid Devices : 12
  Total Devices : 12
    Persistence : Superblock is persistent

    Update Time : Sat Oct 11 06:14:24 2014
          State : clean 
 Active Devices : 12
Working Devices : 12
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : PE850-fs05:3
           UUID : f19b1ab1:b558f6a0:29097680:34c07f57
         Events : 333141

    Number   Major   Minor   RaidDevice State
      12       8      193        0      active sync   /dev/sdm1
      13       8      145        1      active sync   /dev/sdj1
       8       8      209        2      active sync   /dev/sdn1
      15       8      113        3      active sync   /dev/sdh1
      11       8       65        4      active sync   /dev/sde1
      17       8       97        5      active sync   /dev/sdg1
       6       8       33        6      active sync   /dev/sdc1
      14       8      129        7      active sync   /dev/sdi1
       9       8       81        8      active sync   /dev/sdf1
      10       8      177        9      active sync   /dev/sdl1
      18       8       49       10      active sync   /dev/sdd1
      19       8      161       11      active sync   /dev/sdk1

# mdadm -E /dev/md2
mdadm: No md superblock detected on /dev/md2.


```

---

