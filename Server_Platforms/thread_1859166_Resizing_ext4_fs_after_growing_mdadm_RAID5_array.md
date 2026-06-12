---
title: "Resizing ext4 fs after growing mdadm RAID5 array"
date: 2011-10-13
forum: Server Platforms
---

### Post by szafran on 2011-10-13
Hi,

I'm having problems. I just finished adding/rebuilding my mdadm RAID5 array to 10 x 2TB HDDs. I'm trying to resize the ext4 fs with:

resize2fs -p /dev/md2

and all I'm getting is:

resize2fs 1.41.14 (22-Dec-2010)
resize2fs: _New size too large to be expressed in 32 bits_

Does anyone know how to fix this ? (from what I've read ext4 should work with drives/arrays/fs's up to 1EB - 1024TB) Or if it can't be fixed how to safely remove a drive from an mdadm RAID5 array ?

Regards
Szafran

---

### Post by Seq on 2011-10-13
> **szafran said:**
> Hi,

I'm having problems. I just finished adding/rebuilding my mdadm RAID5 array to 10 x 2TB HDDs. I'm trying to resize the ext4 fs with:

resize2fs -p /dev/md2

and all I'm getting is:

resize2fs 1.41.14 (22-Dec-2010)
resize2fs: _New size too large to be expressed in 32 bits_

Does anyone know how to fix this ? (from what I've read ext4 should work with drives/arrays/fs's up to 1EB - 1024TB) Or if it can't be fixed how to safely remove a drive from an mdadm RAID5 array ?

Regards
Szafran

The filesystem itself supports >16GB filesystems, but the tools do not yet. As of June, there are patches to allow mkfs.ext4 to create filesystems with 64-bit support. I am not sure if those are released yet, and are probably not in a version carried by distributions.

However, that doesn't yet seem to allow filesystems to grow beyond 16TB.

[http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/)

---

### Post by szafran on 2011-10-17
Is there any other FS that can support >16TB ?
And a way to convert from ext4 to it without loosing data ?

Szafran

---

### Post by rubylaser on 2011-10-17
XFS or JFS both support volumes > 16TB, but I've had nothing but bad luck from XFS, so I personally wouldn't trust it with my data.  About the only way you could convert would be to use Btrfs, but I wouldn't do that either, here's what Oracle (who purchase Sun and got Btrfs) says about it, " Btrfs is not suitable for any uses other than benchmarking and review.

Probably the easiest thing to do would be to put an LVM volume on the unused part of your array, and then join the two parts together with [mhddfs]("http://romanrm.ru/en/mhddfs") or [Greyhole]("http://www.greyhole.net/").

Personally, I use Solaris 11 with ZFS for anything that involves more that 16TB in a single filesystem.

Also, please add another disk of redundancy and a spare at a minimum.  10 disks in RAID5, is almost begging for trouble in the long run.

---

### Post by szafran on 2011-10-17
And what about ReiserFS ?

---

### Post by rubylaser on 2011-10-17
UnRAID uses ReiserFS, so that's a good thing.  I've never used ReiserFS, so I can't comment on it.

---

### Post by szafran on 2011-10-17
Maybe someone else is more experienced in ReiserFS.
It would be nice to get it over 16TB and convert to it from ext4 (without loosing data).

---

### Post by rubylaser on 2011-10-17
How do you plan on doing the conversion?  You'd need an equal amount of free space to be able to do this without backing up and restoring even with sparse files.

---

### Post by szafran on 2011-10-18
I was hoping for a tool that can do it without loosing data.
If not then that's what my df says about that array:
/dev/md2  16T  6,3T  9,5T  40%

So I have 9,5TB of free space (for now) on it.

---

