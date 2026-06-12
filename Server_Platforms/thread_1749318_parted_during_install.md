---
title: "parted during install ?"
date: 2011-05-04
forum: Server Platforms
---

### Post by lightninhopkins on 2011-05-04
For large partitions, for example 20TB, anyone know the trick to getting it to format and boot properly during an install?  I should probably just install the OS on a regular drive and do the large partition afterwards, but I should learn this method anyway. 

I've used the parted command before to create a GPT disklabel but can't seem to do it during an install. 

Thanks

---

### Post by srs5694 on 2011-05-04
I've not investigated this carefully, but based on posts to this forum, it seems that disks larger than 1 or 2 TiB get used as GPT by default. Perhaps that's not the case if there's an existing MBR on the disk, though.

Personally, I'd switch to a text-mode console and use parted or gdisk to create the GPT data structures (if possible) before getting to the Ubuntu GUI partitioner; or boot into "live CD" mode and do that before running the installer.

BTW, I do *not* recommend installing Ubuntu to a 20 TiB partition. On a disk (presumably a RAID array) that big, you should *definitely* split off a smallish (~20 GiB) partition for Ubuntu and use the rest as /home, /var, or whatever separate partition is appropriate for your use.

---

### Post by lightninhopkins on 2011-05-04
Great point. I usually just do a raid 1 with the first two drives, but thought I'd try it with one big array. I chucked that plan and just put a single drive as it's safer for raid failures anyway. 

During the install when I went to console and did an fdisk, it showed a GPT already made, which was cool. It just wouldn't let me make an ext4 during the install. 

So now with a single boot drive /dev/sda and the 20TB on /dev/sdb, it still wouldn't let me format the 20TB portion even though it saw it properly. I tried to make it ext4 but was denied. 

Well, I'll try again once I'm in the OS. I've installed on GPT for years (after the initial install), but I figure a simple partition should work during install too. 

Thanks again.

---

### Post by srs5694 on 2011-05-04
I just recalled that there's currently a 16 TiB limit on ext4fs because of limitations in mke2fs. Presumably that limit will be raised in the future, since ext4fs's theoretical limit is 1 EiB, but you may be running into that limit. If so, you can either split your 20 TB partition in two or use another filesystem, such as XFS or JFS, both of which should be able to handle your 20 TB partition. Btrfs is also a possibility, but only if you don't value your data, since it's still considered experimental.

---

### Post by aphatak on 2011-05-04
For a 20TB partition, I would suggest xfs, considering it has better performance with large files and large number of files.

---

### Post by lightninhopkins on 2011-05-04
thanks srs5694, and aphatak. Didn't know about the ext4 limit of 16TB. Makes sense. I remember one install where the GUI automatically split up a 17TB into 2x 8TB setups by itself. I was wondering why it did that.

The reason I was trying to do ext4 was that I heard it performs better in a cloud setup (installing the Eucalyptus cloud).  Only heard that from person, so it may not be valid. 

Well, I'll be doing xfs on this install then. 

Thanks. Great forum here BTW.

---

