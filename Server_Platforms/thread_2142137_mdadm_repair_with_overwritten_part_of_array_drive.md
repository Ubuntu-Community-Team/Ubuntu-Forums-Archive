---
title: "mdadm repair with overwritten part of array drive"
date: 2013-05-04
forum: Server Platforms
---

### Post by underpen on 2013-05-04
I have a hypothetical about RAID setups that has me confused. Lets say you have a 4-6 drive software RAID 5 setup. If the beginning of one of the drives gets overwritten (e.g the first 512 bytes, first 1MB, first 10MB, or something similar) while the raid is offline, will a repair when it becomes active again detect this? And if it can detect it will it be able to fix it? I believe with striping it should be able to determine that data was corrupted, but I am not sure about recovery.

what would be better in this situation --- forcing a recovery of the array or marking the drive with overwritten data as failed and having it rebuild the whole drive?

---

### Post by darkod on 2013-05-04
If you delete the first 512B that means deleting the partition table and everything. So the disk will be like a brand new unpartitioned disk. First you would have to create new partition table and partitions (if you use partitions as members of mdadm), and then you add the disk to the array (md device).
Since the old table was gone including the mdadm superblock on it, the "new" partitions/disk are considered as new member and rebuilding of the md device will start.

Same like having a disk fail and replacing it with a brand new one.

Even if you don't delete the partition table on the disk, if you suspect corrupted data or what ever, you can zero the superblock on all partitions that you want to, that are members of array(s). Removing the superblock makes mdadm think they were never part of any md device. When you add it to the md device(s) later, it's like adding brand new disk and rebuilding will start.

```
sudo mdadm --zero-superblock /dev/sda1 (for example)
```

Before doing that make sure all members are present because if one member is missing, zeroing the superblock of another member will make a raid5 array with missing two members, which it can't handle. Raid5 works with only one member missing.

---

### Post by SaturnusDJ on 2013-05-04
Yep. And here some information about data corruption: [http://www.tldp.org/HOWTO/Software-RAID-HOWTO-6.html#ss6.4](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-6.html#ss6.4)

---

