---
title: "Unknown error while re-sizing RAID1"
date: 2010-03-06
forum: Server Platforms
---

### Post by rocknrollmouse on 2010-03-06
> sudo resize2fs /dev/md0
Filesystem at /dev/md0 is mounted on /; on-line resizing required
Performing an on-line resize of /dev/md0 to 97169120 (4k) blocks.
resize2fs: Operation not permitted While trying to add group #384

Replaced drives in a server (2x 40G -> 2x 400G) using "[Resizing a RAID1 system partition]("http://mkfblog.blogspot.com/2007/11/resizing-raid1-system-partition.html")" as guide (without the gparted CD, so not having to down the server).

When issuing resize2fs /dev/md0 to resize the partitions the above error message is returned.  I've tried googling "Operation not permitted While trying to add group #384" but am unable to find a definition of the error, or how to fix it.

Anyone any idea what the #384 is, or even better how to resolve it?

---

### Post by rocknrollmouse on 2010-03-07
Discovered latest version of [gparted]("http://gparted.sourceforge.net/index.php") supports mdadm RAID drives natively.

This gave me the correct e2fsck command to fix the drive, and then run resize2fs to resize the volume.

*(Sorry to anyone with #384 error, I didn't find out any more about this.)*

---

