---
title: "Is it possible to have a volume size over 16TB"
date: 2014-09-21
forum: Server Platforms
---

### Post by MakOwner on 2014-09-21
Where Ubuntu server doesn't just **** itself and corrupt the whole file system?

I can build a files ystem more than 16TB in size, and I can mount it, but just the least random thing after the 16TB mark and Ubuntu 64 bit server installs will hopelessly corrupt the files system.

Any way to get around this other than another Linux distro or BSD?

---

### Post by matt_symes on 2014-09-21
Hi

I assume you are using a variant of the ext file system. 16Tb is the maximum partition size that can be mounted, IIRC ; or maybe that's file size - i forget.

If you want a larger partition sizes then pick another file system.

One of the developers of ZFS on Linux has gone on the record in the last week or 2 to say that he feels ZFS on Linux is now production ready; if your boxen has the memory. I'm thinking of playing with this myself in the next couple of weeks.

You also have BTRFS. You will have to gauge whether you feel this is production ready or not though. It's the default file system on OpenSuse at the moment. I've never really had a problem with BTRFS although i make very regular backups.

Other options include XFS although you will have to install xfsprogs and may have to load the xfs kernel module. I've never used XFS.

Use a 64-bit kernel.

Kind regards

---

### Post by nerdtron on 2014-09-21
Try XFS filesystem. Been using it on production systems and is very stable. The limit on filesystem size in XFS is higher, although I haven't reached 16TB yet.

---

### Post by rubylaser on 2014-09-21
If this is just home bulk storage (media, documents, pictures, etc.), another great option is SnapRAID plus a pooling solution.  My SnapRAID server at home is currently over 30TB, and I am continuously adding disks, or moving to larger disks.  Lots of people use XFS, but I have experienced bad corruption with it on mdadm in the past, so I don't use it anymore.  It's either ZFS for constantly changing data (VM storage) or SnapRAID for static files (Write Once Read Many).  If you are interested in SnapRAID, I have a tutorial in my signature.

---

### Post by MakOwner on 2014-09-21
I am currently using ext4 file system over a large mdadm RAID6 array.  Large enough to push the limits on ext4 with Ubuntu obviously.  Where I work we deal with much larger file systems with commercial distributions and custom builds of Linux and never have the sort of issues I'm having.  

I have tried XFS in the past.  Nice file system, but I'm not ready for it.  I could never get any size file system to complete a file system check without failing due to lack of memory.  I could just never trust that.
ZFS and BTRFS are still bit too far out on the edge for my comfort, however, given the experience I'm having with greater than 16TB volumes with ext4 I probably couldn't do much worse.

The last time I looked at anything like SnapRAID the only thing out there was "unRAID" -- and it was(is?) closed/proprietary.

SnapRAID may be the best answer I'm going to have with Ubuntu.

---

### Post by MakOwner on 2014-09-21
I'm pretty sure I get the big picture with SnapRAID, I read your tutorial and I also see there is now a PPA for SnapRAID 6.3.

I suspect my usage patterns on the data would match well with SnapRAID - I read the data many more times than I write it, and most of it moves only once after landing on the array.

A couple of concerns I have write off the bat:

I have not been able to find anything on the web about best practices for pooling.  
The clients for this data must see the data via NFS as one large volume.
This data is currently spread over many directory structures - the directory structures are an integral part of the client functions.
Let's say for example I was able to create a SnapRAID setup.  What happens when I fill a disk with content for a specific category and need to have that category span to another disk?

NFS exports.
Your tutorial has what appears to be a rather complicated set of workarounds with a suggestion that appears to add another layer on top of the SnapRAID setup.
With the SnapRAID pool feature has that now been overcome?

I had looked at your tutorial the last time I had this issue while running Ubuntu 12.04 LTS.  It was more complicated than I felt I could deal with in my spare time at that point.
The addition of a PPA changes that a bit, but the management and NFS aspect still concern me somewhat.

---

### Post by Michael_McKenney on 2014-09-22
Yes, you can get to 8 Exabytes in size using XFS.  Exabyte is 1,000,000 TB.   

I would suggest looking at a EMC or HP SAN for that huge of an array.  It would offer redundancy protection and performance that software RAID does not.  You want RAID 5 or 6 with spare drives for fail over.   Many controllers have drive number and array size limitations.

---

### Post by lukeiamyourfather on 2014-09-22
In my opinion ZFS is the best option at this point for large disk arrays on file servers. The maximum volume size is 256 ZB which is more data than there are physical drives in the world (ZB>EB>PB>TB>GB). It has many advantages over Linux software RAID and hardware RAID systems. Since it's both a volume manager and a file system when a drive dies it rebuilds only blocks with actual data because it knows where the data is unlike RAID, every block of data written has a 256-bit checksum to combat silent data corruption, two levels of caching (RAM and SSD), copy on write plus all the benefits of that like snapshots, high performance block level compression that's almost always higher performance than no compression, up to triple parity block arrays (RAID 6 has two parity blocks), ability to send complete file systems including snapshots over a network to another machine, storage pool design which is expandable in the same namespace, the list goes on...

There are some growing pains with ZFS on Linux like upgrades that don't go as smoothly as planned but in terms of the risk of data loss I'd say it's less so than Linux software RAID and ext4. Keep in mind that ZFS has been around for a decade and has widespread adoption. All of the underlying code is the same between platforms like BSD and Linux, it's just the SPL module that's new for Linux (which is production ready). For what it's worth I've been running a pair of servers with ZFS on Linux for about a year now, they have 144 TB of raw capacity which has been configured as six RAID Z2 arrays (about 96TB usable, can lose up to 12 drives total without loss of data). Over 10GbE I can get 400+ MB/s and I think the limitation there is the SSD on the workstation. When doing internal transfers on the server the array is capable of 2 GB/s so ZFS is no slouch even though it's software.

Recently I wrote a blog post about ZFS. Towards the bottom there's a presentation which covers setting it up on Ubuntu Server. Maybe it'll be helpful if you decide to give ZFS a shot. Of course XFS is a good option too if you want to keep using Linux software RAID. XFS has been around for a long time and is production ready too.

[http://whenpicsfly.com/getting-to-know-zfs/](http://whenpicsfly.com/getting-to-know-zfs/)

---

### Post by Michael_McKenney on 2014-09-22
The problem with getting over 8 TB is performance and backups.  Most arrays start losing performance after 6 hard drives.  I have seen RAID 5 performance fall fast after 6 drives due to the complex parity writes.  In my data center at work, we have 9 TB.  It is on three RAID 10 arrays of 3 TB each.   It is in a HP P2000 G3 SAN.  I looked at the new 3Par SANs.  Data crashes at 8 TB can take weeks to restore.  We backup to both Tape drives and D2D.  I found RAID 10 has better write performance than RAID 5.  You lose 10% read performance.  On the SAN it still is 7GB/s reads.

---

### Post by rubylaser on 2014-09-22
> **MakOwner said:**
> I'm pretty sure I get the big picture with SnapRAID, I read your tutorial and I also see there is now a PPA for SnapRAID 6.3.

I suspect my usage patterns on the data would match well with SnapRAID - I read the data many more times than I write it, and most of it moves only once after landing on the array.

A couple of concerns I have write off the bat:

I have not been able to find anything on the web about best practices for pooling.  
The clients for this data must see the data via NFS as one large volume.
This data is currently spread over many directory structures - the directory structures are an integral part of the client functions.
Let's say for example I was able to create a SnapRAID setup.  What happens when I fill a disk with content for a specific category and need to have that category span to another disk?

NFS exports.
Your tutorial has what appears to be a rather complicated set of workarounds with a suggestion that appears to add another layer on top of the SnapRAID setup.
With the SnapRAID pool feature has that now been overcome?

I had looked at your tutorial the last time I had this issue while running Ubuntu 12.04 LTS.  It was more complicated than I felt I could deal with in my spare time at that point.
The addition of a PPA changes that a bit, but the management and NFS aspect still concern me somewhat.

I just suggested SnapRAID, because I didn't know what you where planning to use this for.  For example, how many users, what are your performance expectations, how often does the data change? As mentioned previously, I use ZFS for my constantly changing stuff (VM storage) or areas where I need to go beyond 100 MB/s, and SnapRAID for bulk WORM storage.  

Just some info: SnapRAID is actually very easy to manage (no complicated workarounds), is extremely flexible, allows you to add disks one at a time, has low system overhead, allows for up to six parity disks, and provides checksumming.  I use mhddfs for my pooling solution that presents all of my disks in one pool, and it works with NFS exports just like you would expect.  The SnapRAID pool solution is just a series of symlinks to your original data, so it's basically a read-only copy of your data set, probably not what you want, that's why I use a real pooling solution.  Instead of being monolithic, SnapRAID does one thing, snapshot RAID, really well, and then allows the user to decide what else they want to do with it (pooling, encryption, etc) with other software solutions.  It allows it to be very modular.  The PPA is okay, but I just compile SnapRAID, it has no dependencies and compiles in less than a minute. If you just tried out that tutorial in a virtual machine, it would probably take you less than 10 minutes to have a working pool, and you could really kick the tires to understand SnapRAID a little better.

---

### Post by MakOwner on 2014-09-22
I'm about to start testing this with 14.04.1 LTS server install and 9 storage disks.

Mind if I ask you dumb questions when I get to the pooling mechanism?

---

### Post by MakOwner on 2014-09-22
To answer your question on utilization:
The data is primarily additive in nature -- some of it is entertainment media and some of it is audio recording that is done on another system, then transferred in batch to this system for longer retention.
And the whole (currently) 26TB filesystem is duplicated to another system for recovery needs.  I don't expect to ever have more than a handful of clients on this system, with up to two systems doing writes at sporadic intervals.
Quarterly the audio is copied off to BD disks for long term storage - I have almost 7 years worth of audio taking up about 4.5TB at present - at some point I'll remove the older audio at some point, but I have plenty of space right now and the disk is spinning anyway...

---

### Post by rubylaser on 2014-09-22
> **MakOwner said:**
> I'm about to start testing this with 14.04.1 LTS server install and 9 storage disks.

Mind if I ask you dumb questions when I get to the pooling mechanism?

Sure, I'm happy to answer questions: )

---

### Post by rubylaser on 2014-09-22
> **MakOwner said:**
> To answer your question on utilization:
The data is primarily additive in nature -- some of it is entertainment media and some of it is audio recording that is done on another system, then transferred in batch to this system for longer retention.
And the whole (currently) 26TB filesystem is duplicated to another system for recovery needs.  I don't expect to ever have more than a handful of clients on this system, with up to two systems doing writes at sporadic intervals.
Quarterly the audio is copied off to BD disks for long term storage - I have almost 7 years worth of audio taking up about 4.5TB at present - at some point I'll remove the older audio at some point, but I have plenty of space right now and the disk is spinning anyway...

This sounds like a perfect use case for SnapRAID.

---

### Post by MakOwner on 2014-09-23
I have SnapRAID installed with 9 1.5TB disks.  Copying an 8.5TB/~1400 files/28 directories data set over to it from the system with a RAID6 volume.
How to balance across single volumes was the first issue. 
I was able to saturate a 1GB link at around 100-110MB/s running with four streams from an NFS export from the source - each stream writing to a different drive.

Wrote about half the data and then loaded mhddfs up to help balance the data across the drives better than I can do in my head.
I'm getting half the write performance on three streams -- 52MB/s at best.
Multiple writes to the virtual mhddfs filesystem all seem to be directed to the same volume - which isn't optimal but I get it - until you start getting low on space.
It then runs the volume down to 0% available space while the threads all seem to fight over who will own that last bit of free space.

This wouldn't happen in the normal course of events, but is there a way to tweak the performance a bit?

Oh, and these are not the best performing drives, so part of the performance issue in writing to a single drive. 5900RPM drive if I recall correctly.

---

### Post by rubylaser on 2014-09-24
> **MakOwner said:**
> I have SnapRAID installed with 9 1.5TB disks.  Copying an 8.5TB/~1400 files/28 directories data set over to it from the system with a RAID6 volume.
How to balance across single volumes was the first issue. 
I was able to saturate a 1GB link at around 100-110MB/s running with four streams from an NFS export from the source - each stream writing to a different drive.

Wrote about half the data and then loaded mhddfs up to help balance the data across the drives better than I can do in my head.
I'm getting half the write performance on three streams -- 52MB/s at best.
Multiple writes to the virtual mhddfs filesystem all seem to be directed to the same volume - which isn't optimal but I get it - until you start getting low on space.
It then runs the volume down to 0% available space while the threads all seem to fight over who will own that last bit of free space.

This wouldn't happen in the normal course of events, but is there a way to tweak the performance a bit?

Oh, and these are not the best performing drives, so part of the performance issue in writing to a single drive. 5900RPM drive if I recall correctly.

Well you dove right in :) mhddfs will intentionally use up all available space on one drive at a time.  This is ideal for a media server, because it only requires one disk to spin up to read all grouped files (like tv shows or your audio files).  What type of hardware is this running on (processor)?  I have an i3-2100 and have no problem writing around 80-90 MB/s, but my hard drives are all pretty fast.  Also, you wouldn't have the space fighting if you were only pushing one stream at a time, mhddfs normally reserves 4GB on the volume and then will roll over to the next disk.  So, when you are pushing with multiple streams at once onto a disk that is almost full, you will run into contention.  That being said, how well does a single stream perform?

---

### Post by MakOwner on 2014-09-24
> **rubylaser said:**
> Well you dove right in :) mhddfs will intentionally use up all available space on one drive at a time.  This is ideal for a media server, because it only requires one disk to spin up to read all grouped files (like tv shows or your audio files).  What type of hardware is this running on (processor)?  I have an i3-2100 and have no problem writing around 80-90 MB/s, but my hard drives are all pretty fast.  Also, you wouldn't have the space fighting if you were only pushing one stream at a time, mhddfs normally reserves 4GB on the volume and then will roll over to the next disk.  So, when you are pushing with multiple streams at once onto a disk that is almost full, you will run into contention.  That being said, how well does a single stream perform?

I have this on a Dell PE850 with a dual core PentiumD 3.0 GHZ, 8GB RAM and the 9 drives in an external drive enclosure off a quad port LSI1068E.
The OS runs on a pair of 7200 RPM laptop drives that are a mirrored mdadm raid - that may be slowing things down a bit.

I'll have to test the single stream into mhddfs and compare it to a direct write to a single drive.

I assumed the 4GB reservation would leave 4GB available on the drive, but it has managed to use several of them right up to 100%.

```

/dev/sdg1      1442015700 1427884908         0 100% /mnt/9XW06E43
/dev/sdh1      1442015700 1427944852         0 100% /mnt/9XW05B85
/dev/sdd1      1442015700 1429614420         0 100% /mnt/6YD05MN6
/dev/sdf1      1442015700 1429523404         0 100% /mnt/9XW06DVM
/dev/sdc1      1442015700 1437472004         0 100% /mnt/6XW0QL54
/dev/sdi1      1442015700  966561336 460786608  68% /mnt/6XW05PT6
/dev/sdj1      1442015700  822515528 604832416  58% /mnt/9XW04HNT

```

I dismounted mhddfs and I have snapraid running right now.

Do the snapraid.parity files always 534MB?
They haven't changed since it started syncing.

```

content /var/snapraid.content
content /mnt/6XW05PT6/snapraid.content1
content /mnt/9XW04HNT/snapraid.content2


# ls -alh /mnt/*/snap*
-rw------- 1 root root 534M Sep 24 20:04 /mnt/6XW05PT6/snapraid.content1
-rw------- 1 root root 1.4T Sep 24 20:22 /mnt/6XW0SK9Wp2/snapraid-2.parity
-rw------- 1 root root 1.4T Sep 24 20:22 /mnt/6XW0V05Fp1/snapraid.parity
-rw------- 1 root root 534M Sep 24 20:04 /mnt/9XW04HNT/snapraid.content2

```

---

### Post by rubylaser on 2014-09-24
No, the content files will grow as you have more entries.  For instance, my content files are over 1GB in size.  If you used that much of the disk, you must used tune2fs to set the reserved space to 0%.  I wouldn't suggest setting your reserved space to 0% unless your parity drives are larger than your data disks (i.e. 3TB parity drives and 2TB data disks), otherwise you run the risk of the parity file growing larger than your parity disk can accommodate due to the block_size that you have in your config file.  If you are using 2TB for your data and parity disks, I would suggest transferring enough off the disks at 100% usage to the remaining disks, and then reserving 2% with tune2fs on each disk, just so you have a slight buffer.

Also, there is no reason to unmount mhddfs, it won't effect the snapraid sync at all.  Also, you can still using your pool while it's syncing, just don't write to it during that time or the changes won't be captured.

---

### Post by MakOwner on 2014-09-25
> **rubylaser said:**
> No, the content files will grow as you have more entries.  For instance, my content files are over 1GB in size.  If you used that much of the disk, you must used tune2fs to set the reserved space to 0%.  I wouldn't suggest setting your reserved space to 0% unless your parity drives are larger than your data disks (i.e. 3TB parity drives and 2TB data disks), otherwise you run the risk of the parity file growing larger than your parity disk can accommodate due to the block_size that you have in your config file.  If you are using 2TB for your data and parity disks, I would suggest transferring enough off the disks at 100% usage to the remaining disks, and then reserving 2% with tune2fs on each disk, just so you have a slight buffer.

Also, there is no reason to unmount mhddfs, it won't effect the snapraid sync at all.  Also, you can still using your pool while it's syncing, just don't write to it during that time or the changes won't be captured.

Each disk is 1.5TB and I created the filesystem with 1% reserved.
The two parity disk quickly filled.  it's only 56% done and the parity disks are at 100% each.

```

/dev/sdg1              1.4T  1.4T     0 100% /mnt/9XW06E43
/dev/sdh1              1.4T  1.4T     0 100% /mnt/9XW05B85
/dev/sdd1              1.4T  1.4T     0 100% /mnt/6YD05MN6
/dev/sdf1              1.4T  1.4T     0 100% /mnt/9XW06DVM
/dev/sdc1              1.4T  1.4T     0 100% /mnt/6XW0QL54
/dev/sdi1              1.4T  954G  408G  71% /mnt/6XW05PT6
/dev/sdj1              1.4T  785G  577G  58% /mnt/9XW04HNT
/dev/sde1              1.4T  1.4T     0 100% /mnt/6XW0SK9Wp2
/dev/sdk1              1.4T  1.4T     0 100% /mnt/6XW0V05Fp1

```

---

### Post by rubylaser on 2014-09-25
> **MakOwner said:**
> Each disk is 1.5TB and I created the filesystem with 1% reserved.
The two parity disk quickly filled.  it's only 56% done and the parity disks are at 100% each.

```

/dev/sdg1              1.4T  1.4T     0 100% /mnt/9XW06E43
/dev/sdh1              1.4T  1.4T     0 100% /mnt/9XW05B85
/dev/sdd1              1.4T  1.4T     0 100% /mnt/6YD05MN6
/dev/sdf1              1.4T  1.4T     0 100% /mnt/9XW06DVM
/dev/sdc1              1.4T  1.4T     0 100% /mnt/6XW0QL54
/dev/sdi1              1.4T  954G  408G  71% /mnt/6XW05PT6
/dev/sdj1              1.4T  785G  577G  58% /mnt/9XW04HNT
/dev/sde1              1.4T  1.4T     0 100% /mnt/6XW0SK9Wp2
/dev/sdk1              1.4T  1.4T     0 100% /mnt/6XW0V05Fp1

```

The parity disks will always big as big + some overhead of your most full disk.  Since all of your disks have 1.4TB on them, so will the parity disk.  This is perfectly normal.  My only concern is that you don't want to fill your data disks to 100% because you have no room to accommodate the slight overhead on your parity disks.  Like I said above, I normally reserve 2% on my data disks, and reserver 0% on my parity disks to leave some "wiggle room".

---

### Post by MakOwner on 2014-09-25
> **rubylaser said:**
> The parity disks will always big as big + some overhead of your most full disk.  Since all of your disks have 1.4TB on them, so will the parity disk.  This is perfectly normal.  My only concern is that you don't want to fill your data disks to 100% because you have no room to accommodate the slight overhead on your parity disks.  Like I said above, I normally reserve 2% on my data disks, and reserver 0% on my parity disks to leave some "wiggle room".

Will using the reserved block parameter (-m 2) when creating the filesystem be sufficient to hold the correct space reservation?

---

### Post by rubylaser on 2014-09-25
> **MakOwner said:**
> Will using the reserved block parameter (-m 2) when creating the filesystem be sufficient to hold the correct space reservation?

It certainly will :)  Or, you can adjust it after that fact by using tune2fs like this.

```

tune2fs -m 2 /dev/sdb1

```

---

### Post by MakOwner on 2014-09-25
> **rubylaser said:**
> It certainly will :)  Or, you can adjust it after that fact by using tune2fs like this.

```

tune2fs -m 2 /dev/sdb1

```

So, snapraid sync finally finished - I copied all of the data into this from an NFS mount, and I did it as root, so the reserve percentage was ignored.
I can simply move some of the files off the disks that 100% utilized to the two that are not, adjust the reservation, alter permissions to a normal user for future writes and then rerun 'snapraid sync' and things will be right with the world?


```

# snapraid sync
Self test...
Loading state from /var/snapraid.content...
Scanning disk d1...
Scanning disk d2...
Scanning disk d3...
Scanning disk d4...
Scanning disk d5...
Scanning disk d6...
Scanning disk d7...
Using 1362 MiB of memory.
Initializing...
Syncing...
Nothing to do

# df -h
Filesystem             Size  Used Avail Use% Mounted on
/dev/sdg1              1.4T  1.4T     0 100% /mnt/9XW06E43
/dev/sdh1              1.4T  1.4T     0 100% /mnt/9XW05B85
/dev/sdd1              1.4T  1.4T     0 100% /mnt/6YD05MN6
/dev/sdf1              1.4T  1.4T     0 100% /mnt/9XW06DVM
/dev/sdc1              1.4T  1.4T     0 100% /mnt/6XW0QL54
/dev/sdi1              1.4T  954G  408G  71% /mnt/6XW05PT6
/dev/sdj1              1.4T  785G  577G  58% /mnt/9XW04HNT
/dev/sde1              1.4T  1.4T     0 100% /mnt/6XW0SK9Wp2
/dev/sdk1              1.4T  1.4T     0 100% /mnt/6XW0V05Fp1

```

One other question -- should the snapraid.content files be excluded in the snapraid.conf file?
I have three snapraid.content files -- one in /var, and two in the root of separate volumes of the 7 protected volumes.


ohh, ooh... one other.  With mhddfs is there any way to specify volume preference on write?
Of the data set that I have moved here, it's movie rips with accompanying .nfo files.
So, I have 5GB+ files along with 100k or so .nfo files of the same name.
I could use a single volume with a small block/inode size for the .nfo files and different sizes for the larger files.

---

### Post by rubylaser on 2014-09-25
> **MakOwner said:**
> So, snapraid sync finally finished - I copied all of the data into this from an NFS mount, and I did it as root, so the reserve percentage was ignored.
I can simply move some of the files off the disks that 100% utilized to the two that are not, adjust the reservation, alter permissions to a normal user for future writes and then rerun 'snapraid sync' and things will be right with the world?
Yes, that is exactly what you should do :)

> **MakOwner said:**
> 
One other question -- should the snapraid.content files be excluded in the snapraid.conf file?
I have three snapraid.content files -- one in /var, and two in the root of separate volumes of the 7 protected volumes.

Nope, there is no reason to exclude them, snapraid automatically manages the content files that you setup in the config file.


> **MakOwner said:**
> ohh, ooh... one other.  With mhddfs is there any way to specify volume preference on write?
Of the data set that I have moved here, it's movie rips with accompanying .nfo files.
So, I have 5GB+ files along with 100k or so .nfo files of the same name.
I could use a single volume with a small block/inode size for the .nfo files and different sizes for the larger files.

There isn't an option in mhddfs to prefer writing specific files to a certain disk automatically.  You could setup a BASH find piped to xargs to move certain files to certain locations, but I wouldn't worry about doing that.  I assume the .nfo files reside in the same folder and the 5GB + (media) files, so you would have duplicate folders spread across disks. Not that this matters to mhddfs, they will be combined correctly, but for you to manage it might be a pain.

---

### Post by MakOwner on 2014-09-25
In the snapraid.conf file the volumes are named "d1", "d2" and so on.
Is that just a label or does the configuration require one alpha, one numeric designators?

If I change them from "d1", "d2" to "d01" and "d02" for example - will that cause a complete rebuild?

---

### Post by rubylaser on 2014-09-25
> **MakOwner said:**
> In the snapraid.conf file the volumes are named "d1", "d2" and so on.
Is that just a label or does the configuration require one alpha, one numeric designators?

If I change them from "d1", "d2" to "d01" and "d02" for example - will that cause a complete rebuild?

The labels can be anything, but d1, d2, etc. is the typical naming convention.  You don't want to change the name or the order of the disks as they are used for parity.  Here's what the default config file says about the labels.

> 
# Defines the data disks to use
# The name and mount point association is relevant for parity, do not change it
# Format: "disk DISK_NAME DISK_MOUNT_POINT"


---

### Post by MakOwner on 2014-09-26
Will snapraid scrub have the same effect as a read/write over sectors in a "currently pending' status?
Or do do it the old way, I have to identify the sectors, move the file and force writes in order to have the drive reallocate?

---

### Post by rubylaser on 2014-09-26
If checksum errors are found during a scrub, and you run the fix command as result, SnapRAID will write the changes to a functioning area of your disks, without you needing to forceably move, then re-write the file.

---

### Post by MakOwner on 2014-09-26
So, I ran a  -p 100 -o 0 scrub and it reported 2 read errors.  
No idea what file as it didn't report that.  If I run snapraid fix it's just going to revert to the last snapshot isn't it?
Would a snapraid check tell me which files have the read errors?

the scrub took almost 8 hours to run at nice level of -20.  
check shows an ETA of just over 7 hours.

Interesting.  I have three pending sectors on a parity disk.  Delete and rebuild?

---

### Post by rubylaser on 2014-09-27
No need to rebuild, I would just run this to correct the files containing issues.

```

[COLOR=#000000]snapraid -e fix

```[/COLOR]

---

### Post by MakOwner on 2014-09-27
OK, I have played around with snapraid and mhddfs a bit.  I feel fairly comfortable with it, but I'm seeing some odd stuff with permissions in the mhddfs filesystem.

In this particular case I want to create a directory in the mhddfs mount point and I want to have a non-privileged user on the box have write permissions.
If I use cp -rv to copy in data from another location, I get write permissions errors in subdirectory creation.

Is the only way to get around this to completely build out the directory structure and permissions on every file system used as part of the mhuddfs mount?

---

### Post by rubylaser on 2014-09-27
How is your user writing to the share (local user, NFS, CIFS, etc.)?  It appears you are just copying.  All you would need to do is chown -R the path in question with a group that your user is a part of and then give the directory permissions that allow the group to write chmod -R 755 /path/

mhddfs will honor your permissions if you set them correctly, but to copy there in the first place, the user that you are trying to write with needs to have write permissions to the directory.

---

### Post by MakOwner on 2014-09-27
On the system as root, I created a directory in the mhddfs mountpoint and 'chown user:user' so the non privileged owner has permissions.
There is an NFS mount in another mount point, exported from my current media server - so the first attempt to do a single stream copy of all the media into the mhddfs mountpoint used 'cp -r' -- and it failed with subdirectory creation errors.
I then attempted the same thing using midnight commander and it (is) working with no complaints.  Haven't filled the first drive yet though.

Also -- if you don't specify a log file for mhddfs when mounting, does it write one?
Where?

---

### Post by MakOwner on 2014-09-27
Now that I have what I think is a good handle on snapraid/mhddfs (still have a few failure scenarios to test..) I want to look at ZFS.

Quick google doesn't show me any readily found instructions for the complete newb - all I have found so far is how simple it is, and to "just create a tank" and some command examples.
How should the drives be prepared? Raw disk with no partition information at all?  Have yet to find a really good laymans explanation of the "zn" levels, or discussion of features such as deduplication.

Dedupe is of great interest, is it a fixed or variable block dedupe?  Inline or post process?

---

### Post by rubylaser on 2014-09-27
ZFS is another great option. Here are some [basic instructions]("http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.htmlhttp://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html") to get you started.  Just replace the mirrored tank with raidz (zpool create raidz ...) or raidz2 (zpool create raidz2 ...) You just work with the raw disks (no partitions). raidz is the equivalent of RAID5 without the write hole and raidz2 is like RAID6. 

Dedupe is a MASSIVE memory hog with you 16TB of data.  You need roughly 20GB of RAM for every 1TB that is deduped.  Here is some [more info]("http://constantin.glez.de/blog/2011/07/zfs-dedupe-or-not-dedupe") if you are interested. I would avoid it like the plague for home use.  The dedupe is inline as and FYI.  FYI, SnapRAID has a dup command that can find duplicates.  You could easily cook up a script to find the duplicates and replace them with symlinks.  Good luck with your investigations :)

---

### Post by MakOwner on 2014-09-27
> **rubylaser said:**
>  [basic instructions]("http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.htmlhttp://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html") 

I get a 404 on that link.

---

### Post by rubylaser on 2014-09-28
Somehow it pasted the link twice.

[http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html](http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html)

---

### Post by MakOwner on 2014-09-28
> **rubylaser said:**
> Somehow it pasted the link twice.

[http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html](http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html)

Ah, thanks -- I had run across that one earlier and that's what made me wonder what disk format to use.

If you use raw disk volumes, what keeps other things - such as me - from seeing these as available drives?
Wouldn't it be better to use partitions of some type on the drives?

---

### Post by rubylaser on 2014-09-28
> **MakOwner said:**
> Ah, thanks -- I had run across that one earlier and that's what made me wonder what disk format to use.

If you use raw disk volumes, what keeps other things - such as me - from seeing these as available drives?
Wouldn't it be better to use partitions of some type on the drives?

That's how ZFS works, it works best with raw disks :)  I would keep track of your disks-by-id so you know which ones are in use.

---

### Post by MakOwner on 2014-09-28
Found this ZFS information.  [http://solarisinternals.com/wiki/index.php/ZFS_Best_Practices_Guide]("http://solarisinternals.com/wiki/index.php/ZFS_Best_Practices_Guide")

---

### Post by rubylaser on 2014-09-28
Yes, that's been around for years, but it's written for Solaris/Illumos/OmniOS/Openindiana/etc.  The disk labeling is totally different that Ubuntu's.  The ideas in there are all valid though.

---

### Post by lukeiamyourfather on 2014-09-29
This is the best documentation available currently for ZFS on Linux.

[https://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/](https://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/)

The overwhelming majority of the documentation from Oracle and other sources is compatible but there are a few differences like drive paths. If you have any ZFS on Linux questions I'd be happy to help.

---

### Post by matt_symes on 2014-09-30
Hi

> **rubylaser said:**
> 
Dedupe is a MASSIVE memory hog with you 16TB of data.  You need roughly 20GB of RAM for every 1TB that is deduped.  Here is some [more info]("http://constantin.glez.de/blog/2011/07/zfs-dedupe-or-not-dedupe") if you are interested. I would avoid it like the plague for home use.  The dedupe is inline as and FYI.  FYI, SnapRAID has a dup command that can find duplicates.  You could easily cook up a script to find the duplicates and replace them with symlinks.  Good luck with your investigations :)

Just a general addendum to to rubylaser's solid advice. 

There is an ongoing discussion on the freenas forum about whether it's sensible NOT to use ECC memory on a system running ZFS, especially when it is re-silvering.

Here's one of many links....

[http://forums.freenas.org/index.php?threads/ecc-vs-non-ecc-ram-and-zfs.15449/](http://forums.freenas.org/index.php?threads/ecc-vs-non-ecc-ram-and-zfs.15449/)

However, ECC memory and compatible motherboards are more expensive than non ECC memory and motherboards.

I suspose it depends on how much you value your data.

Rubylaser, are you using ECC memory for your ZFS pools ?

Kind regards

---

### Post by Michael_McKenney on 2014-09-30
Does your board fully support ECC memory?  I use ECC RAM on my Tyan Thunder and Supermicro server boards at work.  ECC RAM is very expensive and designed for production servers to maintain a higher level of protection of data.  I would not use it in a home environment.  It is not worth having ECC enabled on a home server.   I doubt you will get many bit level errors that will cause lose of data.  It is used to protect SQL servers from data corruption.  

My concern with your setup is power and power supply.  I would be more concerned about your RAID dropping a drive from a power sag from another device on your circuit coming online.  A hard drive can drop, if your circuit sags and you don't have a line conditioner capable of holding power up.  Most consumer grade UPS units lack quick power sag protection that a Tripp Lite Line Conditioner provides.  Is your power supply large enough to maintain wattage to all your hard drives during full usage.   8+ hard drives requires a huge current and voltage load to be maintained.  If you have a higher end video adapter or CPUs, it can cause issues during heavy IO calls.  All your hard drives in RAID are used at the same time.  So you have to maintain your load point.   Do you have adequate spacing and cooling on your hard drives?  I have seen many SATA drives fail due to inadequate spacing for heat dissipation and cooling.

---

### Post by matt_symes on 2014-09-30
Hi

> Does your board fully support ECC memory?

Who are you asking ?

On the off chance you are asking me then, no, i am not using ECC memory. 

I have multiple redundant copies of all my most important data though and the data that is not important i can reacquire without too much hassle. It would just take quite a long time.

That being said, when i upgrade my hardware it will be with the intention of getting error correcting memory and a compatible motherboard.

My most important concern after getting a new laptop though, is getting a UPS.

Kind regards

---

### Post by rubylaser on 2014-09-30
> **matt_symes said:**
> Hi



Just a general addendum to to rubylaser's solid advice. 

There is an ongoing discussion on the freenas forum about whether it's sensible NOT to use ECC memory on a system running ZFS, especially when it is re-silvering.

Here's one of many links....

[http://forums.freenas.org/index.php?threads/ecc-vs-non-ecc-ram-and-zfs.15449/](http://forums.freenas.org/index.php?threads/ecc-vs-non-ecc-ram-and-zfs.15449/)

However, ECC memory and compatible motherboards are more expensive than non ECC memory and motherboards.

I suspose it depends on how much you value your data.

Rubylaser, are you using ECC memory for your ZFS pools ?

Kind regards

Yes, I am using ECC memory with ZFS.  I know many users run without it, but one bad stick of RAM could jeopardize my data, so I only use ZFS with ECC RAM.

---

### Post by Michael_McKenney on 2014-09-30
HP and IBM are moving away from ECC technology on servers and blades.  Bit errors are not as common any more on memory.  Technology has gotten much better.   The problem with consumer grade UPS is the square wave vs. sine wave.  At home, I use Tripp Lite Line Conditoners instead of a UPS.  I don't need 24x7 uptime of a UPS.  Instead, I was clean sine wave power of a line conditioner.  Tripp Lite can keep my voltage around 118V.  From 97V to 140V input will provide 118V output.  This keeps my hardware running cooler.  They make EU versions that can keep your power clean.  It takes spikes and sags to ground.  I install them on refrigerators, A/V hardware, workstations and toys.

---

### Post by rubylaser on 2014-09-30
> **matt_symes said:**
> Hi



Who are you asking ?

On the off chance you are asking me then, no, i am not using ECC memory. 

I have multiple redundant copies of all my most important data though and the data that is not important i can reacquire without too much hassle. It would just take quite a long time.

That being said, when i upgrade my hardware it will be with the intention of getting error correcting memory and a compatible motherboard.

My most important concern after getting a new laptop though, is getting a UPS.

Kind regards

UPS is a great idea.  When you get around to upgrading hardware, I would strongly suggest getting a Supermicro motherboard with IPMI.  Once you've used nice IPMI setup, it's hard to consider going back to traditional motherboards.

---

### Post by Michael_McKenney on 2014-09-30
My last Supermicro board would fry a BIOS everytime I upgraded it to fix a problem that Supermicro support said was in the BIOS fix.  I replaced 3 BIOS chips at $25 each.  I ended up pulling the board.  It sits in a box with a pair of E5430s and 16GB of RAM.  I sent it to Supermicro and they could not figure out why it fries the BIOS on upgrades.  Even the replacement board did not help.   I found the Intel i7 had same MIPS as dual E5340s.

---

### Post by lukeiamyourfather on 2014-09-30
> **Michael_McKenney said:**
> Does your board fully support ECC memory?  I use ECC RAM on my Tyan Thunder and Supermicro server boards at work.  ECC RAM is very expensive and designed for production servers to maintain a higher level of protection of data.  I would not use it in a home environment.  It is not worth having ECC enabled on a home server.   I doubt you will get many bit level errors that will cause lose of data.  It is used to protect SQL servers from data corruption.

I respectfully disagree. ECC memory is not very expensive and it's perfectly suitable for a home server - especially one running ZFS. For example see below are the cheapest 8 GB modules on Newegg for DDR3 1600, one has ECC and the other does not. The difference with a set of two DIMM would be roughly $36 (non-ECC being about 20% cheaper). 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820148703](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148703)
[http://www.newegg.com/Product/Product.aspx?Item=0B1-00KT-00001](http://www.newegg.com/Product/Product.aspx?Item=0B1-00KT-00001)

Regardless of location or purpose I wouldn't run ZFS without ECC memory. It's not just me saying that there are lots of people saying this and for good reason if you look further into how ZFS works. Don't know if it's even relevant though because the original poster seems to have gone with SnapRAID.

[https://pthree.org/2013/12/10/zfs-administration-appendix-c-why-you-should-use-ecc-ram/](https://pthree.org/2013/12/10/zfs-administration-appendix-c-why-you-should-use-ecc-ram/)

I find it pretty amazing that ECC memory isn't standard in every computer. Every other buffer, transport, cache, or bus in modern computers has some sort of error detection and/or correction capability ranging from the networking protocols all the way down to the cache on the processor die. I very much agree with this from James Hamilton. Basically that everything should have ECC memory.

[QUOTE=James Hamilton]I continue to believe that client systems should also be running ECC and strongly suspect that a great many kernel and device driver failures are actually the result of memory fault. We don’t have the data to prove it conclusively from a client population but I’ve long suspected that the single most effective way for Windows to reduce their blue screen rate would be to require ECC as a required feature for Windows Hardware Certification.[/QUOTE]

[http://mvdirona.com/jrh/work/](http://mvdirona.com/jrh/work/)

---

### Post by rubylaser on 2014-09-30
> **lukeiamyourfather said:**
> 
Regardless of location or purpose I wouldn't run ZFS without ECC memory. It's not just me saying that there are lots of people saying this and for good reason if you look further into how ZFS works. Don't know if it's even relevant though because the original poster seems to have gone with SnapRAID.


+1 on the ZFS + ECC.  The OP tried out SnapRAID and got a handle on it, and now is trying out ZFS as well.  I think his idea testing and exploring is a great idea to make sure that he goes with the best solution for his use case.

---

### Post by Michael_McKenney on 2014-09-30
Every IBM, HP, Tyan, and Supermicro board I have ever owned recommended only certain ECC ram that they supported. They had a list on their web sites for supported and tested memory.  $140-$300 a GB stick.  If you want manufacturer's help with issues on the boards, you have to stay with what they recommend.  You can't get Axiom ECC sticks.  You call Tyan or Supermicro, they ask about your RAM first.  Yes, you can buy non-supported ram but you will not get motherboard support with it installed.   You can void your HP Carepaq support.

---

### Post by rubylaser on 2014-09-30
I use Crucial ECC RAM on all of my Supermicro boards with no issue, and they are on the supported list.  Typically around $80 - $90 each for a 8GB stick.

---

### Post by MakOwner on 2014-10-03
> **rubylaser said:**
> +1 on the ZFS + ECC.  The OP tried out SnapRAID and got a handle on it, and now is trying out ZFS as well.  I think his idea testing and exploring is a great idea to make sure that he goes with the best solution for his use case.

Quick question on snapraid -- "snapraid status" is currently showing this:
```

Files: 2973
Fragmented files: 3
Excess fragments: 69
Files size: 8604 GiB
Parity size: 1339 GiB

```

Are the fragments an issue of concern?  If so how should they be addressed?

In regards to server memory - I'm using Dell 850 PowerEdge servers, with Dell ECC memory, but they max out at 8GB.  Will that amount of memory be an issue?

---

### Post by rubylaser on 2014-10-03
> **MakOwner said:**
> Quick question on snapraid -- "snapraid status" is currently showing this:
```

Files: 2973
Fragmented files: 3
Excess fragments: 69
Files size: 8604 GiB
Parity size: 1339 GiB

```

Are the fragments an issue of concern?  If so how should they be addressed?

In regards to server memory - I'm using Dell 850 PowerEdge servers, with Dell ECC memory, but they max out at 8GB.  Will that amount of memory be an issue?

No, the fragments are common and not an area of concern.  In regards to memory, you can see how much is being used during a sync.  With 8.6TB of used, you would have to increase you dataset's size many times before you wouldn't have enough RAM to complete a sync. Here's how much RAM is needed for your system (taken from the SnapRAID manual).
> [COLOR=#000000][FONT=Times]In more details SnapRAID requires about TS*28/BS bytes of RAM memory to run. Where TS is the total size in bytes of your disk array, and BS is the block size in bytes.[/FONT][/COLOR][COLOR=#000000][FONT=Times]For example with 4 disk of 3 TiB and a block size of 256 KiB (1 KiB = 1024 bytes) you have:[/FONT][/COLOR]
RAM = (4 * 3 * 2^40) * 28 / (256 * 2^10) = 1.4 GiB
[COLOR=#000000][FONT=Times]Another reason to use a different blocksize is if you have a lot of small files. In the order of many millions.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]In details, for each file, even of few bytes, a whole block of parity is always allocated, and with many files this may result in a lot of unused parity space. And when you completely fill the parity disk, you are not allowed to add more files in the data disks. But note that wasted parity doesn't sum between data disk. Wasted space resulting from a high number of files in a data disk, limits only the amount of data in such data disk and not in others.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]As approximation, you can assume that half of the block size is wasted for each file. For example, with 100000 files and a 256 KiB block size, you are going to waste 12 GiB of parity, that may result in 12 GiB less space available in the data disk.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]To avoid to problem, you can use a bigger partition for parity. For example, if you have the parity partition bigger than 12 GiB than data disks, you have enough extra space to handle up to 100000 files in each data disk.[/FONT][/COLOR]

---

### Post by MakOwner on 2014-10-03
> **rubylaser said:**
> No, the fragments are common and not an area of concern.  In regards to memory, you can see how much is being used during a sync.  With 8.6TB of used, you would have to increase you dataset's size many times before you wouldn't have enough RAM to complete a sync. Here's how much RAM is needed for your system (taken from the SnapRAID manual).

Ah, sorry -- the questions about memory is in regards to ZFS.
I'm going to attach another shelf with some disks on a comparable server to test ZFS.

Edit:  Dell PE850 with 8GB memory, root on two internal SATA disks using mdadm for mirror, with the ZFS disks in an external shelf - LSI1068E controller to a SAS expander in the shelf.

---

### Post by rubylaser on 2014-10-03
8GB is fine for ZFS.  More RAM is always better, but 8GB is enough to get started.  That LSI controller is old (slow) and depending on if your SAS Expander is SAS1 or the newer SAS2, you may have some throughput / reliability issues, but time will tell.  Our work C6100's came with the LSI1068, and we quickly moved on to newer LSI 9260's to get better performance.

---

### Post by MakOwner on 2014-10-12
mhddfs question regarding the amount of free space that should be maintained on a volume - 

If I read the material about mhddfs correctly, the default is 4GB.  Regardless of what I set it to, some of the volumes wind up at 0% free space.
Is there a way to enforce free space?

It appears that the root reserved space is ignored too -- since the mhddfs setting seemed to be ignored, I set the reserved space percentage very high on each of the component volumes, mounted them into a single volume using mhddfs.
I created a directory in the mhddfs mount space with write privelages for a non root user and began to fill the mhddfs space.  My assumption is that the volume is mounted as root with mhddfs, the writes are accomplished as root, then permissions are applied.  This would make sense as the directories are created on the fly in the underlying volumes...

---

