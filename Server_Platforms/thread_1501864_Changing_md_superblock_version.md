---
title: "Changing md superblock version"
date: 2010-06-04
forum: Server Platforms
---

### Post by k6rfm on 2010-06-04
I recently changed partition sizes (expanded one and shrank another) and built raid1 md mirrors on them; /dev/md0 is made up of /dev/sda1 and /dev/sdb1; /dev/md2 is made of /dev/sda3 and /dev/sdb3.  However, after getting everything set ok, the next reboot assembled /dev/md2 out of /dev/sda and /dev/sdb -- the whole device rather than the partitions.  Fortunately the file system wouldn't mount, and I was eventually able to stop the bad array and create a new one out of /dev/sda3 and /dev/sdb3.  However, I'm worried that I will fall back into the same problem.  If I examine superblocks with "mdadm -E" I see that apparently the superblocks on /dev/sda and /dev/sda3 are the same, as are sdb and sdb3.  Some searching around has made me think that this is a problem with using version 0.90 superblocks, which if the partitions are just the right sizes can not distinguish between a superblock for the whole device and a superblock for the last partition.

As a possible short term solution, I've changed mdadm.conf to specify "DEVICE /dev/sd[a-z][0-9]" instead of "DEVICE partitions", which I think means the md driver won't look at the base sda and sdb devices anymore.  I haven't tried rebooting to see, though, since I want the resync to finish first so I have a backup if things go bad.  Am I right in thinking this will help?

Again based on some reading, it looks like using version 1 superblocks would be a better solution, since they have enough information for the driver to tell that the superblock is describing a partition and not the whole disk.  However, I'd like a sanity check on how to convert.  Note that I can have this filesystem off line for a while.  The plan is:


[LIST=1]
[*]unmount  /dev/md2
[*]resize2fs the filesystem to minimal (or a little more than that)
[*]stop the array
[*]create new array with mdadm -C /dev/md3 -l 1 -n 2 -e 1.0 /dev/sda3 missing
[*]resize2fs back to maximum
[*]mount /dev/md3 where /dev/md2 was
[*]check filesystem looks good
[*]mdadm /dev/md3 --add /dev/sdb3, resync starts
[*]update /etc/fstab and mdadm.conf to consistently call new array /dev/md3
[/LIST]
Any obvious botches?  The basic idea is the new 1.0 superblock at the end of the partition is no doubt larger than the 0.90 superblock that is there, so it's important to resize2fs around it so the filesystem doesn't think it can write on the superblock.

---

