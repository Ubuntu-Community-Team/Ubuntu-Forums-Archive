---
title: "Issue with creating DRDB block device"
date: 2016-11-10
forum: Server Platforms
---

### Post by brandon_2 on 2016-11-10
I'm trying to play with DRBD in Ubuntu 16.04.1LTS

Not getting far at all. The program requires a block device, so I zero out the drive, create the partition, and forego a file system. This results:

```
root@alpha:/etc/drbd.d# sudo lshw -short | grep "sd[bc]"/0/b0/0.0.0    /dev/sdb   disk        1TB Samsung SSD 850
root@alpha:/etc/drbd.d# dd if=/dev/zero of=/dev/sdb1 bs=1024
dd: error writing '/dev/sdb1': No space left on device
8125273+0 records in
8125272+0 records out
8320278528 bytes (8.3 GB, 7.7 GiB) copied, 8.43444 s, 986 MB/s
root@alpha:/etc/drbd.d# drbdadm create-md r0
open(/dev/sdb1) failed: Invalid argument
could not open with O_DIRECT, retrying without
'/dev/sdb1' is not a block device!
open(/dev/sdb1) failed: Invalid argument
could not open with O_DIRECT, retrying without
'/dev/sdb1' is not a block device!
Command 'drbdmeta 0 v08 /dev/sdb1 internal create-md' terminated with exit code 20



```

I have no clue how to move on from here. They are samsung 850 EVO 1TB SSDs, identical gear on both servers. Neither will execute the command with success. Any clues?

---

### Post by deadflowr on 2016-11-11
*Thread moved to **Server Platforms**.*
Even though you might be new to Ubuntu.
the people who would have a clue as to what to do will more likely be here.

---

