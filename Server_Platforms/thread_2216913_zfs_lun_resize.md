---
title: "zfs lun resize"
date: 2014-04-14
forum: Server Platforms
---

### Post by frankerooney on 2014-04-14
Hi.
 Does anyone have any experience with resizing a zpool on top of an expanded iscsi lun? The filesystem (parted to be exact) can see the extra space after rescanning the iscsi target but zpool doesn't show the increase. I have tried setting autoexpand to on and doing
zpool online -e pool device
but it doesn't fill the space. It does however fix the gpt error which resizing produces in parted - something about the gpt table not being at the end, which is interesting.
anyone done this?

---

### Post by frankerooney on 2014-04-14
UPDATE : 
  I've been fiddling, and just for kicks decided to partition the space i'd been using first, instead of using the whole disk and letting zpool create a gpt partition on that disk. I'm not sure of the implications of this, but the partition and subsequent zpool resize work fine with the custom partition.
Anyone explain why?
Thanks
Andy

---

### Post by lukeiamyourfather on 2014-04-14
Did you enable "autoexpand" before swapping the drives in the pool? This must be done first, otherwise ZFS will ignore the additional disk space.

> The storage pool will not auto resize itself when all smaller drives in the pool have been replaced by larger ones. You MUST enable this feature, and you MUST enable it before replacing the first disk. Use "zpool set autoexpand=on tank" as an example.

[https://pthree.org/2012/12/13/zfs-administration-part-viii-zpool-best-practices-and-caveats/](https://pthree.org/2012/12/13/zfs-administration-part-viii-zpool-best-practices-and-caveats/)

---

### Post by frankerooney on 2014-04-15
Hi.
  Well I'm only interested at this point with a single drive - we're using an iscsi backend storage pool which allows us to change size on the fly. Most people would "create the storage" using zfs, but we're approaching it from a point of view of using zfs for snapshots, dedup, compression etc, whilst keeping a simple single backend.
Anyway I figured out (at midnight, the best time to figure stuff out) that if you give zfs a whole drive to play with it creates two partitions, one of type BF01 (zfs) and the other BF07, which is something else. Resizing the lun obviously gives free space at the end of the drive so unless you remove the 2nd partition, the only one you can actually expand is the second partition.
I've successfully used BF01 and ext4 partitions now instead of drives and put a zpool on them, then expanded them.
Haven't tried any zfs on top of the pool yet, but am hopefully that this will let us hot resize partitions.
Thanks
Andy

---

