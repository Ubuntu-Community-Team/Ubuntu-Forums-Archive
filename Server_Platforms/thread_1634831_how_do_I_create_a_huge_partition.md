---
title: "how do I create a huge partition?"
date: 2010-12-01
forum: Server Platforms
---

### Post by Wej on 2010-12-01
I have an array of 20 2TB hard drives and I created a single RAID5 array using mdadm, for a total of 38 terabytes (lost one to parity). I have created a label on the disk as GPT to support large partitions, but I don't know which file system I should use, or what the best way is to do it. On our previous system I created two RAID5 arrays with 10 drives in each, and each drive was only 1.5TB, so I stayed under the 16TB limit of EXT4 with two 13TB (I think it was a 32-bit OS install), but now we are working with some huge data sets and a single set is getting hard to move around to keep all the data on a single partition that is only 13TB in size. This new system is running 64-bit 10.04 LTS. So the questions:

1. What is the best file system that is supported by Ubuntu (not beta, this is critical data) that can handle 38TB on a single partition. File size limits aren't as much of an issue, as each individual file will be no more than 200-300GB in size.

2. Is samba going flip out with that big of a partition? Will Ubuntu flip out? Has anyone done this before?

Thanks

---

### Post by srs5694 on 2010-12-02
Technically, ext4fs can handle filesystem sizes of up to 1 EiB; the 16 TiB limit is one in the current e2fsprogs utilities (mainly mke2fs). There may be patched or beta versions that can handle bigger filesystems, but I've not been following this closely. I wouldn't worry too much about using a patched or beta mke2fs, although if e2fsck has problems with a big filesystem, that could potentially bite you, so it might be wisest to steer clear of ext4fs for such a big filesystem for the moment.

Overall, for your needs I'd recommend XFS, which has a maximum filesystem size of 16 EiB and a maximum file size of 8 EiB (both figures according to [Wikipedia.](http://en.wikipedia.org/wiki/Xfs) I've never heard of the Linux support utilities having lower limits, but I can't promise that they don't. XFS seems to be pretty well-supported in Linux, and in my experience it's a bit more reliable than JFS, the other advanced filesystem that might work for your needs. (Btrfs looks very promising, too, but it's still officially experimental, so I can't recommend it for your mission-critical data.) That said, my own experience is with much smaller filesystems than yours, the biggest being a ~1.2 TiB filesystem that holds my MythTV recordings.

---

