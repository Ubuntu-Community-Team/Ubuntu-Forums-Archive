---
title: "RAID 5 shows missing device and spare?"
date: 2007-10-24
forum: Server Platforms
---

### Post by bobpaul on 2007-10-24
I have a 3 disk RAID 5 constructed from /dev/sd[bcd]

On rebooting, there were lots of errors from md while the kernel was loading. When the system came up, I *think* mdstat showed /dev/md0 missing /dev/sdb. After executing ```
mdadm /dev/md0 --add /dev/sdb
``` the following was shown:

```
#cat /proc/mdstat 
Personalities : [raid1] [raid6] [raid5] [raid4] 
md0 : inactive sdc[0] sdb[3](S) sdd[1]
      1465159488 blocks
       
unused devices: <none>

# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Oct 20 14:09:59 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Oct 24 13:13:22 2007
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 16e41c8a:d41c7e18:44aff814:01e3975e
         Events : 0.345651

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       0        0        2      removed

       3       8       16        -      spare   /dev/sdb

```

I'm not sure what to do with this and I can't get the array to re-activate. It would appear to me that sdc and sdd are fine, but why is there a non-existent failed device and why is sdb a spare? Shouldn't have sdb have replace the "removed" device when I added it back it?

---

### Post by bobpaul on 2007-10-24
Ok, so I tried all all combinations of two drives with the first driving missing, as follows:

```
mdadm --stop /dev/md0; mdadm --create /dev/md0 -l 5 -n 3 missing /dev/sd[cd]
```

where I replaced cd with bc, bd, etc. It always warned that it was part of an existing array and then partition on /dev/md0 showed invalid. (I have an encrypted partition on the array, so 'cryptsetup luksOpen /dev/md0 ... ' returned "not a valid luks partition"

Finally I did what I didn't think I should do. I used all three devices, doing

```
mdadm --create /dev/md0 -l 5 -n 3 /dev/sd[cd] /dev/sdb
```

This time, cryptsetup was able to open the partition and I was good to go. As expected, recovery started immediately on the array, which has me somewhat worried. What if the data on one of the drives was bad? Couldn't that corrupt my recovery? I was using just 2 devices before so it would show up as degraded and not make changes if I'd built it with the wrong 2 drives.

Another question I have; does the order matter? I did /dev/sd[cd] /dev/sdb because the array started with just the 2 disks sdc and sdd and only had /dev/sdb added recently. Might I have been successful in my 2 disk attempts if I'd preserved the proper order (/dev/sd[cd] missing ; missing /dev/sdd /dev/sdb; etc)? It was my understanding that mdadm could figure that out on it's own (or is that only in regards to raid autodetect and not the 'mdadm --create' command)?

---

