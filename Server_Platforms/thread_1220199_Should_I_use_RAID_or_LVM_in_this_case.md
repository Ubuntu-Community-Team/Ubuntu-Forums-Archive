---
title: "Should I use RAID or LVM in this case?"
date: 2009-07-22
forum: Server Platforms
---

### Post by iissmart on 2009-07-22
Hello all,

I have two 1TB drives connected to my server and I would like to access these drives through *one* mount point. I don't need data redundancy, so any RAID that has redundancy is out, since I'd like to use all 2TB. I also don't need any speed gain, so RAID-0 isn't necessary. Ideally, if one drive crashes, I'd like it to *not* take the other drives data along with it, so I'd only lose half the total data assuming both drives were full at the time.

I think I've narrowed it down to either LVM or RAID-JBOD (using mdadm). Which one would be better in this situation? With either of those, if one drive fails, will it take the other drives data with it? Or will I be able to continue to read/write to the mount point with one drive down? Even if I can't read/write to the other drive with one drive gone, hopefully I would still be able to put a new 1TB drive in and then be able to read/write to both, and still have the other drives data.

Thanks in advance!

---

### Post by redmk2 on 2009-07-22
> **iissmart said:**
> Hello all,

I have two 1TB drives connected to my server and I would like to access these drives through *one* mount point. 
I'm not sure exactly what you are trying to accomplish with the "*one* mount point" idea.  The notion of spreading the data across multiple spindles (disks) is a valid idea for data safety. Why do you feel your system should have a singular mount point?> 
I don't need data redundancy, so any RAID that has redundancy is out, since I'd like to use all 2TB. I also don't need any speed gain, so RAID-0 isn't necessary.

Ideally, if one drive crashes, I'd like it to *not* take the other drives data along with it, so I'd only lose half the total data assuming both drives were full at the time.
I think I've narrowed it down to either LVM or RAID-JBOD (using mdadm). 
Which one would be better in this situation? 
Neither, see [_[COLOR="DimGray"]here[/COLOR]_]("http://www.pcguide.com/ref/hdd/perf/raid/levels/jbod-c.html").> 
With either of those, if one drive fails, will it take the other drives data with it? 
Yes, both will.  See the above link.> 
Or will I be able to continue to read/write to the mount point with one drive down? Even if I can't read/write to the other drive with one drive gone, hopefully I would still be able to put a new 1TB drive in and then be able to read/write to both, and still have the other drives data.

I take another view of the situation.  I have 3 drives that are managed individually.  Each partition on the drive has a separate mount point, but they are similar.  I have a filesystem that starts at /smb and 3 mount points (directories) below that. They are /smb/backup /smb/share and /smb/pictures each has a partition (or a whole drive with a singular partition) that mounts to the appropriate spot.  The data on one drive is independent of the other drives data.> 

Thanks in advance!

---

### Post by iissmart on 2009-07-22
There will be multiple programs accessing this folder and they can only be configured to access a single folder, not two, so I need one mount point with 2TB total size.

The example you gave would not work for me, as I would need to point my programs to 3 folders in that case, otherwise they would be writing to /smb and not the 3 other drives.

I now realize that with any method, I'd need a filesystem spanned across the two disks, and if one fails it will most likely end up corrupting the file system entirely, thus making my data inaccessible on the other drive.

With that in mind, are there any benefits to using either LVM or JBOD as opposed to RAID-0? All three would have 2TB total size, but RAID-0 will have a speed increase, which isn't necessary but if I have to accept that when one drive fails I will lose the data on the other drive, I might as well take the speed increase.

Thanks for the response :)

---

### Post by redmk2 on 2009-07-23
> **iissmart said:**
> ...

With that in mind, are there any benefits to using either LVM or JBOD as opposed to RAID-0? All three would have 2TB total size, but RAID-0 will have a speed increase, which isn't necessary but if I have to accept that when one drive fails I will lose the data on the other drive, I might as well take the speed increase.

Thanks for the response :)

I agree and would go with RAID-0 then.  It appears you are going to be forced to create a single large partition.  There are going to be **NO** safe configurations.  It will be as if you have only 1 disk.  Backup often!

---

### Post by windependence on 2009-07-23
I disagree as LVM has features that will allow you to replace a disk (if you have space) and grow the filesystem if you put in a larger disk. This can be problematic with RAID0. The ONLY time I would use RAID0 is when I need absolute speed, and I would have a backup solution no matter what you do.

-Tim

---

### Post by dragos2 on 2009-07-23
> **windependence said:**
> I disagree as LVM has features that will allow you to replace a disk (if you have space) and grow the filesystem if you put in a larger disk. This can be problematic with RAID0. The ONLY time I would use RAID0 is when I need absolute speed, and I would have a backup solution no matter what you do.

-Tim

If he's low on budged and needs absolute speed RAID0 but a better solution would be
a 4 disk array in RAID1 and you get higher speed than RAID0 and redundancy.

---

### Post by windependence on 2009-07-23
I was thinking he just wanted the flexibility that LVM provides but I'm not really sure what his goals are. I have some boxes set up with hardware RAID and LVM on top and it works great, but I'm not a big fan of software RAID in the first place, and I think software RAID with LVM would add too much complexity to the system. Too many things to go wrong you know?

-Tim

---

### Post by dragos2 on 2009-07-23
> **windependence said:**
> I was thinking he just wanted the flexibility that LVM provides but I'm not really sure what his goals are. I have some boxes set up with hardware RAID and LVM on top and it works great, but I'm not a big fan of software RAID in the first place, and I think software RAID with LVM would add too much complexity to the system. Too many things to go wrong you know?

-Tim

I agree. LVM on hardware raid is the best in my opinion.

---

### Post by iissmart on 2009-07-23
I don't have the money to buy a hardware raid card, or 4 drives for that matter. I will only be using two at the moment. If I get a third drive I was planning on doing a RAID-5, but that won't be in the near future. Like I said data redundancy and backup isn't important for the data on these drives. I was hoping I could find a solution better than RAID-0 in the sense that one drive could fail and the other drive could still hold usable data (while still having 2TB of usable space).

Absolute speed is not necessary by any means, but if a RAID-0 is equivalent in benefits to a JBOD or LVM, I might as well take the speed increase.

I will probably be using XFS as the file system on these drives, which can grow if I add another drive in the future.

---

### Post by grantemsley on 2009-07-23
I've had this issue before, and here was my solution.

If you do LVM or RAID, you'll probably lose everything if one drive fails. (I could be wrong, but that is my understanding).

So I made three directories:

/storage/disc1
/storage/disc2
/storage/share

The drives are mounted as disc1 and disc2 as normal drives.  Inside /storage/share are symlinks to all the important directories on both discs.  So, if disc1 has "Documents" "Pictures" and "Misc" and disc2 has "Videos" and "Downloads", share will have symlinks to all 5 of those directories, and only the /storage/share directory is visible from samba shares.

You still have to manually make sure one disc doesn't get too full (in which case you move a directory to the less full disc, and update the symlink), but you can rearrange things, add more discs, etc without everyone else having to worry about where things are actually located.

I think you also have to add a line in smb.conf to allow it to follow symlinks...I forget exactly what.

---

### Post by iissmart on 2009-07-23
> **grantemsley said:**
> I've had this issue before, and here was my solution.

If you do LVM or RAID, you'll probably lose everything if one drive fails. (I could be wrong, but that is my understanding).

So I made three directories:

/storage/disc1
/storage/disc2
/storage/share

The drives are mounted as disc1 and disc2 as normal drives.  Inside /storage/share are symlinks to all the important directories on both discs.  So, if disc1 has "Documents" "Pictures" and "Misc" and disc2 has "Videos" and "Downloads", share will have symlinks to all 5 of those directories, and only the /storage/share directory is visible from samba shares.

You still have to manually make sure one disc doesn't get too full (in which case you move a directory to the less full disc, and update the symlink), but you can rearrange things, add more discs, etc without everyone else having to worry about where things are actually located.

I think you also have to add a line in smb.conf to allow it to follow symlinks...I forget exactly what.
Sounds like a lot of micromanagement. How does something like a Drobo or Windows Home Server do it? They let you add or remove drives from a "pool", and when a drive is removed it doesn't corrupt the data on the other drives.

Samba in Ubuntu 8.04LTS (Desktop) seems to be already configured to follow symlinks, as it "just works". I don't see anything in smb.conf to enable/disable this, however.

---

### Post by windependence on 2009-07-24
> **iissmart said:**
> Sounds like a lot of micromanagement. How does something like a Drobo or Windows Home Server do it? They let you add or remove drives from a "pool", and when a drive is removed it doesn't corrupt the data on the other drives.

Samba in Ubuntu 8.04LTS (Desktop) seems to be already configured to follow symlinks, as it "just works". I don't see anything in smb.conf to enable/disable this, however.

FYI, this is exactly what LVM lets you do. You add or subtract drives from the pool as needed. If the OP does some reading on LVM, I'm sure he will see the benefits. RAID0 will not work because if one drive fails all data is lost. 

-Tim

---

### Post by fjgaude on 2009-07-24
Go with LVM... check out this link and then decide:

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

Have fun!

---

### Post by iissmart on 2009-07-24
> **windependence said:**
> FYI, this is exactly what LVM lets you do. You add or subtract drives from the pool as needed. If the OP does some reading on LVM, I'm sure he will see the benefits. RAID0 will not work because if one drive fails all data is lost. 

-Tim

Once a drive is added to the pool and the partition and filesystem is expanded onto it, if the drive fails will it corrupt **all** the data on that filesystem?

> **fjgaude said:**
> Go with LVM... check out this link and then decide:

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

Have fun!

Here's something I notice on that page:

> The current implementation does not support write barriers. This means that the guarantee against filesystem corruption offered by journaled file systems like ext3 and XFS is negated under some circumstances.[1] Most distros, with the notable exception of SUSE, turn off protective barriers by default anyway, to prevent performance degradation.

I was planning on using XFS...what exactly does this mean?

---

### Post by fjgaude on 2009-07-25
Write barriers... see this link:

[http://lwn.net/Articles/283161/](http://lwn.net/Articles/283161/)

I wouldn't be concerned, but I'm not you. <smile>

---

