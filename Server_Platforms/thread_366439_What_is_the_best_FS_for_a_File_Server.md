---
title: "What is the best FS for a File Server?"
date: 2007-02-20
forum: Server Platforms
---

### Post by caffienda on 2007-02-20
I'm building a server based on 6.10.  It is running 
5 500Gb SATA 
5 160Gb IDE drives in a RAID 5
1 36GB Raptor
1 8x DVD+-R/RW IDE

I have everything in NTFS now and will need to transfer to the new FS.  I'm not great with Linux FS's so I need some help here.  Thanks

---

### Post by lengau on 2007-02-21
Personally, I like ReiserFS for stuff like that, simply because it's nice and scalable, and Edgy doesn't have EXT4.

So my top two for you would be ReiserFS or XFS.

EDIT: On second thought, maybe XFS would be better, as there are rumours that ReiserFS will be taken out of the kernel.

---

### Post by Brazen on 2007-02-21
ReiserFS has been abandoned and it has been plagued with reliability problems in the past.  Ext3 is the most popular, most thoroughly tested, and most stable.  XFS has also proven itself very stable and reliable, though not as extensively used as Ext3, but it is much faster.  For a file server however, your bottleneck will be your network, so I would suggest sticking with Ext3.  90% of the time I use XFS, however for our file server's shared partition, I use Ext3 for that reason.

---

### Post by caffienda on 2007-02-21
> **Brazen said:**
> ReiserFS has been abandoned and it has been plagued with reliability problems in the past.  Ext3 is the most popular, most thoroughly tested, and most stable.  XFS has also proven itself very stable and reliable, though not as extensively used as Ext3, but it is much faster.  For a file server however, your bottleneck will be your network, so I would suggest sticking with Ext3.  90% of the time I use XFS, however for our file server's shared partition, I use Ext3 for that reason.

Thanks for the info.  I think I'll go with ext3.  Here is my question about creating partition tables in FDISK.  Is this the correct way to do it, for ext3?(Assume no current partitions)
```
sudo fdisk /dev/hdc
n
p
1
(enter-default)
(enter-default)
t
83
w

```
This was repeated for all 5 drives
This should leave me with a partition of ext3 on the entire space of the drive.?

I then did this:
```
cd dev
sudo  MAKEDEV md
sudo modprobe md
sudo mdadm --create --verbose /dev/.static/dev/md1 --level=5 --raid-devices=5 /dev/hdc1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
```

This took about 3 seconds and said that it was set up.

I then tried to add this code to my fstab:
```
/dev/md1 /media/raid5 ext3 defaults 0 2
```

When I re-booted, I got errors and I was automatically logged in as root to fix the error before preceeding.  

Am I way off on what I did in the above steps? Any ideas?

---

### Post by toorima on 2007-02-21
did you format the raid?
mke2fs -j /dev/md1

---

### Post by Brazen on 2007-02-21
yeah, it sounds like you got to the point of creating the raid array fine, but once the raid is created, it just appears like a single harddrive to the system.  That "harddrive" then needs a partition created on it and formatted as ext3.

---

