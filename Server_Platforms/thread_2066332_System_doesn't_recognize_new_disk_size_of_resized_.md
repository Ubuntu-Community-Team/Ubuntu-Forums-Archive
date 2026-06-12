---
title: "System doesn't recognize new disk size of resized disk"
date: 2012-10-04
forum: Server Platforms
---

### Post by watermark on 2012-10-04
I'm having a hard time getting ubuntu to see the new space on a newly resized disk.  I'm trying my best to do this hot, I haven't rebooted yet.

I have a Promise card handling the software raid.  I just expanded the raid using Promise's tools, so now the promise tools correctly report 10TB instead of 6TB.  Parted still reports the old size of 6TB.

I've used the rescan-scsi-bus tool and the partprobe tools, but it still shows the disk size at 6TB.  Is there any other commands I can try to get it to reread the size of the disk?

---

### Post by lukeiamyourfather on 2012-10-04
If you expand the size of a RAID volume that doesn't mean the partition size is also expanded. Is that what you mean? Can you post a screenshot of what you're getting from GParted?

---

### Post by darkod on 2012-10-04
+1

Expanding the disk does not automatically expand the partition.

And on top of that, depending how you actually expand the partition, the filesystem doesn't always expand with it, so you have to expand the filesystem as a final step (sometimes).

But if you are doing software raid, why Promise? Why not mdadm?

---

### Post by watermark on 2012-10-08
I said software raid, I meant hardware raid, stupid mistake.

```
Model: Promise  3+2 Disk RAID6 (scsi)
Disk /dev/sda: 6.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1018kB  1000kB                     bios_grub
 2      1018kB  257MB   256MB   ext2
 3      257MB   6001GB  6001GB                     lvm
```

The disk is actually 10TB now...and it's a 5+2.  I think I just need it to rescan the disk?  After more research, I'm thinking this can't be done hot.

---

### Post by darkod on 2012-10-09
Not sure how it talks to the Promise controller, it obviously still sees 6TB.

But even when the disk size says 10TB, you still have work to do. You never mentioned you have LVM, that makes the job easier.

The steps you will need, in general, are:
1. Make ubuntu see the whole 10TB disk. This is the crucial step and you can't continue without it.

2. Once you manage to do the above, your sda3 partition will still be 6TB. Create new sda4 partition in the rest of the unallocated space from 6TB to 10TB. Mark it as physical volume for LVM.

3. Add sda4 as physical device for LVM.

4. Expand the VG to include the newly created physical device.

5. Expand the LV to take the newly created free space in the VG.

6. Expand the filesystem. It can be done online, shrinking has to be done offline.

Here is a very similar link, even though it's for CentOS. If you are confused by something just ask.
[http://wiki.centos.org/TipsAndTricks/ExpandLV](http://wiki.centos.org/TipsAndTricks/ExpandLV)

---

### Post by watermark on 2012-10-09
> **darkod said:**
> 
1. Make ubuntu see the whole 10TB disk. This is the crucial step and you can't continue without it.


This is my main problem.  There is tons of documentation on LVM out there, I don't think that will be a problem.

---

### Post by darkod on 2012-10-09
Well, somehow Promise is not passing on the info, or ubuntu is not reading it.

Do one test: Get the desktop live cd and try booting the machine in live mode with Try ubuntu. Use fdisk or parted to display the disk. Does it see it as 6TB or 10TB?

If live mode sees it as 6TB also, that looks like Promise is not showing it as 10TB in effect. The current install might be "stuck" at 6TB because that's what it was when installed. But live mode is fresh and has never seen this disk, so the first time it sees it, does it say 6TB or 10TB. I think it's a good thing to know.

---

### Post by lukeiamyourfather on 2012-10-09
It looks like you need to expand the logical volume (currently says 6 TB in size). There are lots of guides out there for expanding (or extending is another word) logical volumes if you search for it.

---

### Post by darkod on 2012-10-09
> **lukeiamyourfather said:**
> It looks like you need to expand the logical volume (currently says 6 TB in size). There are lots of guides out there for expanding (or extending is another word) logical volumes if you search for it.

But it's not only the LVM. Look above, it says:
Disk /dev/sda: 6TB

Shouldn't it say 10TB? If the disk is not seen as 10TB (yet), there is no way to expand any volumes on it.

---

### Post by lukeiamyourfather on 2012-10-09
> **darkod said:**
> But it's not only the LVM. Look above, it says:
Disk /dev/sda: 6TB

Shouldn't it say 10TB? If the disk is not seen as 10TB (yet), there is no way to expand any volumes on it.

Can you photograph what the RAID controller BIOS is showing you? The volume configurations?

---

