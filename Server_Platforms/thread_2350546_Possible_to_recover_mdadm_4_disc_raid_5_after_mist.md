---
title: "Possible to recover mdadm 4 disc raid 5 after mistaken sfdisk overwrite"
date: 2017-01-25
forum: Server Platforms
---

### Post by mingerz on 2017-01-25
What I think happened is this
I had a raid5 with following disks, I was replacing one of the disks for fail
sda1
sdb1
sdc1
sde1

I managed a faultly sfdisk restore to sde1 (due to typo) whilst a sync was in progress, the sync continued but the next reboot obviously things were NOT ok!

i.e sfdisk -d /dev/wrongdisk(?) | sfdisk /dev/sde 

I can force assemble a b c (assuming clean) and see an lvm which contains a filesystem that demand fsck which is "never ending" (corrupted?)

I still have sde1 and I think it's still 'good' aside from the superblock and parition being shot by my faulty sfdisk.

Can I take partition table from say sda1(again using sfdisk) restore it to sde1 and somehow 'recreate'  superblock so I can assemble all four discs back into array and allow them to error correct/resync?
ideally sfdisk -d /dev/sda |sfdisk /dev/sde
Do whatever I need to do for new superblock?
Reassemble raid and allow resync to take place.

Disks and mdadm examine results below
=========================

```
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EC392E3C-01EC-402C-984A-4A9C5881C6A8

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 5860531215 5860529168  2.7T Linux RAID

Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 78A0A509-C19D-45F2-9853-6E1639AE7FC4

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 5860531215 5860529168  2.7T Linux RAID

Disk /dev/sde: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6B0AC600-64F0-4A33-B6AA-FDF707189F62

Device     Start        End    Sectors  Size Type
/dev/sde1     34 5860533134 5860533101  2.7T Linux RAID

Partition 2 does not start on physical sector boundary.

Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EC392E3C-01EC-402C-984A-4A9C5881C6A8

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 5860531215 5860529168  2.7T Linux RAID

mdadm --misc --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : c50bbc40:7eda9be6:82bf4689:66d08c33
           Name : hoth:2  (local to host hoth)
  Creation Time : Thu Jul 30 22:00:24 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860267024 (2794.39 GiB 3000.46 GB)
     Array Size : 8790400512 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=16 sectors
          State : clean
    Device UUID : fe68f22b:a296f134:23d7d0db:0c444435

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Jul 30 23:17:25 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : cda1e15c - correct
         Events : 38

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.AA ('A' == active, '.' == missing, 'R' == replacing)

mdadm --misc --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : 59de608f:1eb8d318:c1cdd013:0692256a
           Name : hoth:2  (local to host hoth)
  Creation Time : Sun Mar 24 13:03:49 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860267024 (2794.39 GiB 3000.46 GB)
     Array Size : 8790400512 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 2317291840 sectors
   Unused Space : before=262056 sectors, after=16 sectors
          State : clean
    Device UUID : 5b81e4a4:25bb76cf:8827fbe1:9db58ddb

    Update Time : Thu Jul 30 09:57:05 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 6d263da0 - correct
         Events : 619131

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
mdadm --misc --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : c50bbc40:7eda9be6:82bf4689:66d08c33
           Name : hoth:2  (local to host hoth)
  Creation Time : Thu Jul 30 22:00:24 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860267024 (2794.39 GiB 3000.46 GB)
     Array Size : 8790400512 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=16 sectors
          State : clean
    Device UUID : 2b4400d5:8bf58982:3b9fa646:6d9818c8

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Jul 30 23:17:25 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : c1f237ee - correct
         Events : 38

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : A.AA ('A' == active, '.' == missing, 'R' == replacing)

mdadm --misc --examine /dev/sde1
/dev/sde1:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
```

---

### Post by darkod on 2017-01-25
The sfdisk operation overwrites only the partition table as far as I know, so putting the correct partition table back should help you a lot. But I am confused looking at your mdadm --examine results. If you look at the Events counter, it says:
sda1 - 38
sdb1 - 619131
sdc1 - 38
sde1 - no superblock

If you had one disk rebuilding and wrongly overwrote the partition table on another disk, that still means at least two disks would have the correct events counter. Are those sda1 and sdc1? Is the correct counter value 38, because that sounds little low, although it is possible.

Also, the array UUID of sdb1 is different from the one on sda1 and sdc1. Why is that?

---

### Post by TheFu on 2017-01-25
Welcome to the forums.

Ya know how people always stress that RAID is NOT a backup and that backups are still necessary?

RAID solves 3 problems.
Backups solve 1,000+ problems, like this one.

----
Does sfdisk work with GPT disks? If not, this could be bad. Many of the fdisk/cfdisk/sfdisk tools took a really long time to be updated and haven't been included as quickly in the releases as we'd all have liked. parted.

Please use "code tags" so things line up and are easier to read. Please.  Don't think that will help you with a solution to this one, but people are more likely to review easy to read stuff.  Wish I had more ideas.

---

