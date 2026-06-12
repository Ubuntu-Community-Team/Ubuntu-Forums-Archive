---
title: "test filesystem/partition on MD/RAID1"
date: 2008-07-25
forum: Server Platforms
---

### Post by davidmaxwaterman on 2008-07-25
Hi,

I've made an ext3 filesystem on an MD/RAID1 'device' made from two partitions each on it's own sata drive and sized to cover the entire drive :

Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext3        

(same for both drives)

I thought I'd test to make sure I can write to the whole partition without any problems so I did a :

sudo dd if=/dev/zero of=bigfile bs=1024K count=500M

This resulted in a somewhat predictable :

dd: writing `bigfile': No space left on device
472433+0 records in
472432+0 records out
495381721088 bytes (495 GB) copied, 8204.09 s, 60.4 MB/s

However, it also resulted in :

Jul 25 17:37:42 jeeves mdadm: Rebuild60 event detected on md device /dev/md0

and md is dutifully rebuilding it.

Clearly, this concerns me.

Could someone enlighten me as to what went wrong (if anything)?

Is there a better way to test the file system and partition/drive are writable in their entirety?

Thanks,

Max.

Using 8.04, btw.

---

