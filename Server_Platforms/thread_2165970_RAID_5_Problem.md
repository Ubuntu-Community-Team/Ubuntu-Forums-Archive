---
title: "RAID 5 Problem"
date: 2013-08-07
forum: Server Platforms
---

### Post by nuno2 on 2013-08-07
I have already Googled for 2 days now and haven't find a solution for this. I'm not a expert Linux user so...

the problem is... I lost access to my RAID 5 array... after 2 rebuilds (successful ones) I cant mount the array... One disk stopped working in one day, made the rebuild, ok, in the day after a second disk stopped, new rebuild... 

this is what I have:

```
# fdisk -l


Disk /dev/sda: 16 heads, 63 sectors, 1938021 cylinders
Units = cylinders of 1008 * 512 bytes


   Device Boot    Start       End    Blocks   Id  System
/dev/sda1             1       522    263087+  83  Linux
/dev/sda2           523       783    131544   82  Linux swap
/dev/sda3           784   1938022 976367952+  89  Unknown


Disk /dev/sdb: 16 heads, 63 sectors, 969021 cylinders
Units = cylinders of 1008 * 512 bytes


   Device Boot    Start       End    Blocks   Id  System
/dev/sdb1             1       522    263087+  83  Linux
/dev/sdb2           523       783    131544   82  Linux swap
/dev/sdb3           784    969022 487991952+  89  Unknown


Disk /dev/sdc: 16 heads, 63 sectors, 969021 cylinders
Units = cylinders of 1008 * 512 bytes


   Device Boot    Start       End    Blocks   Id  System
/dev/sdc1             1       522    263087+  83  Linux
/dev/sdc2           523       783    131544   82  Linux swap
/dev/sdc3           784    969022 487991952+  89  Unknown


Disk /dev/sdd: 255 heads, 63 sectors, 121504 cylinders
Units = cylinders of 16065 * 512 bytes


Disk /dev/sdd doesn't contain a valid partition table

```

```
# mdadm --examine /dev/md1
mdadm: No super block found on /dev/md1 (Expected magic a92b4efc, got 00000000)
# mdadm --examine /dev/md0
mdadm: No super block found on /dev/md0 (Expected magic a92b4efc, got e5933000)

```

I'm really lost here...

---

### Post by TheFu on 2013-08-07
I'm getting these answers on my array:

```
mdadm: ARRAY line /dev/md2 has no identity information.
mdadm: No md superblock detected on /dev/md1.
```

The arrays are working fine, so I wouldn't sweat it.
What does this show?
```
$ more /proc/mdstat 
```
and this:
```
$ sudo mdadm --detail /dev/md0
```

---

### Post by nuno2 on 2013-08-07
# cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid5] [raid10]
md1 : active raid5 sdc3[0] sdb3[2] sda3[1]
      975983744 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]


md0 : active raid1 sda1[0] sdc1[3] sdb1[2]
      262976 blocks [4/3] [U_UU]

unused devices: <none>
#

and:

# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Mon Oct  1 18:29:37 2007
     Raid Level : raid1
     Array Size : 262976 (256.81 MiB 269.29 MB)
    Device Size : 262976 (256.81 MiB 269.29 MB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug  7 16:46:45 2013
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : c6ae94f3:ccded50c:c6f9a2e4:42ad7f5a
         Events : 0.41315772

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        -      removed
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1
# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.01
  Creation Time : Wed Oct  3 10:51:20 2007
     Raid Level : raid5
     Array Size : 975983744 (930.77 GiB 999.41 GB)
    Device Size : 487991872 (465.39 GiB 499.70 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Aug  7 13:55:21 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 7c24942b:fee40edf:f8ebe46d:9ed3146e
         Events : 0.15210484

    Number   Major   Minor   RaidDevice State
       0       8       35        0      active sync   /dev/sdc3
       1       8        3        1      active sync   /dev/sda3
       2       8       19        2      active sync   /dev/sdb3
#

---

### Post by SaturnusDJ on 2013-08-07
Please use code tags for large outputs.

The --examine flag is for array members only. You can use them at /dev/sd[a-c]. Please post that output for both arrays.

---

