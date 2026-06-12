---
title: "Resize ext4 filesystem on LVM2..."
date: 2011-06-27
forum: Server Platforms
---

### Post by dmwyatt on 2011-06-27
I have an LVM that is 16TB in size.  I expanded one of the underlying RAID-5 arrays by 2TB.  After expanding the logical volume, I try to grow the filesystem.  This fails with this message:

```
 sudo resize2fs /dev/vg_pool/pool
resize2fs 1.41.12 (17-May-2010)
resize2fs: File too large while trying to determine filesystem size
```

I'm on 10.10 64-bit.  It's actually Desktop instead of Server, but I use it as a server, and I figured there would be more people with experience with this sort of setup here.

How do I expand my filesystem?

---

### Post by ian dobson on 2011-06-27
Hi,

Can you try reducing your lvm to abit less than 16Tb and retrying (1byte would be enough).

Regards
Ian Dobson

---

### Post by rubylaser on 2011-06-27
> **ian dobson said:**
> Hi,

Can you try reducing your lvm to abit less than 16Tb and retrying (1byte would be enough).

Regards
Ian Dobson
This is a good recommendation.  Currently, EXT4's maximum size is 16TiB, so it's likely that you're hitting that cap.

---

### Post by ruffEdgz on 2011-06-27
I agree with everyone else here but wanted to provide a link about the ext4 capacity and how they are working to make it bigger/better:

[http://kernelnewbies.org/Ext4#head-4e13646f1961f41bf99152eaf137d309723ac524](http://kernelnewbies.org/Ext4#head-4e13646f1961f41bf99152eaf137d309723ac524)

---

### Post by dmwyatt on 2011-06-29
> **ian dobson said:**
> Hi,

Can you try reducing your lvm to abit less than 16Tb and retrying (1byte would be enough).

Regards
Ian Dobson

Ok, well it's actually already a less than 16 TB...

```

 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md1              57673596  40296224  14447716  74% /
none                   2019656       868   2018788   1% /dev
none                   2027972      1184   2026788   1% /dev/shm
none                   2027972       832   2027140   1% /var/run
none                   2027972         0   2027972   0% /var/lock
/dev/mapper/vg_pool-pool
                     16756496480 16336689364 419807116  98% /media/LVM Pool

```

If you do the math that equals 15.6057034 terabytes I believe...


I noticed that 11.04 has a newer version of e2fsprogs (1.41.14 vs 1.41.12) so I went ahead and did a dist upgrade.  Now I get this:

```

 sudo resize2fs /dev/vg_pool/pool
resize2fs 1.41.14 (22-Dec-2010)
resize2fs: New size too large to be expressed in 32 bits
```

I'm not sure what to do here.  A google search for "New size too large to be expressed in 32 bits" just results in the source code for e2fsprogs where the error message is stored.

---

### Post by dmwyatt on 2011-06-29
I just heard back from Theodore T'so, the lead dev on e2fsprogs...

> There isn't a way to get around this issue, I'm afraid.  Support for >
16TB file systems is something that requires a fundamental change in
the file system format, and which is in late beta status.

It requires the pre-release, e2fsprogs 1.42 development branch, and
unfortunately, the file system must be reformatted to support larger
(greater than 32-bit) block numbers.  Certain on-disk data structures
(specifically, the block group descriptors) have to grow in size from
32 bytes to 64 bytes, so it's not something where we could upgrade a
file system in-place to support > 16TB.

Sorry, I'm afraid can't give you a magic solution to your problem....

Regards,

                                               - Ted

Looks like I'm going to have to figure out a new storage system.

Are there any filesystems that support more than 16TB and also support in-place conversion from ext4?

---

### Post by rubylaser on 2011-06-29
Unfortunately there's not a good solution to make that conversion for you right now.  In the future, btrfs will support this conversion, and will support much larger filesystems. Also, Linux with big filesystems, can be tricky sometimes.

- EXT4 is limited to 16TB due to e2fsprogs.
- JFS has a problem that does not allow expansion over 32TB.
- XFS has a bug in the fsck that causes the machine to use all available memory and crash when running the fsck on a disk that has a large amount of data (~20TB).
- BTRFS is a great idea, but with no fsck, it's currently experimental

I'm strongly considering expanding my mdadm array to >20TB, and I've been testing with Solaris 11 Express + napp-it for a while on ESXi.  This would be a big change for me, but ZFS filesystem size limitations are for all intents currently infinite. Plus, I love the snapshots built-in, the potential for mixed disk sizes in an array, and Copy on Write.

I'd love to hear other's ideas.

---

### Post by psusi on 2011-06-29
Yep, you have hit the upper limit of ext4.  Last I checked, 64bit support is experimental and doesn't support online resize.

---

