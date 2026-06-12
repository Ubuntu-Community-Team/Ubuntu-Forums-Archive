---
title: "One partition, multiple drives - not RAID"
date: 2007-02-06
forum: Server Platforms
---

### Post by andrewsawyer on 2007-02-06
Hi all,

I have a media server sitting in my living room with 3x 300Gb drives.  They are used to store music, tv shows, videos and MythTV data.

My problem is that I have used an entire disk for movies and run out of space, while I have only 50Gb of music.  As such, I now have to have two Movie directories, one on one drive and the other on another drive.

Is it possible to have a partition span multiple drives if I don't have RAID?  I know that there is the new FS by Sun that can do this, but it's not Linux compatible, however I heard somewhere that it was possible to do this using standard logical partitions.  Not sure where or if I just read it wrong though.

Ideally I would like to have a 400Gb partition for movies, 200Gb for TV Shows, 60Gb for Music and 100Gb for MythTV, plus 40Gb for root and home etc.  This would leave 100Gb unpartitioned which I would then allocate (expand partitions) as needed.

Is this scenario possible?  And if so how would I go about it?  I've searched but can't find anything.  If someone could point me in the direction of a decent tutorial it would be much appreciated.

Thank you in advance for you help.

---

### Post by tribaal on 2007-02-06
Well you can't make a single partition span on two physical disks. That's not possible, regardless of what OS you use ( a partition is a "subset" of a disk...).

What you can do however, is "fake it" with the filesystem: you can mount a partition anywhere in the filesystem tree, so you could mount that new partition you'd have by resizing your music partition somewhere in the "TV shows", for example.

This way you'd solve your space problem without messing around too much with partitionning etc...

You should read "man fstab" and "man mount", I'm sure it'll give you enough info to proceed :)

Remember to backup your data before playing with partitions though :)

- trib'

---

### Post by jtc on 2007-02-06
Perhaps LVM (Logical Volume Manager) is what you are looking for?

---

### Post by andrewsawyer on 2007-02-06
Thinking about it, LVM does sound familiar.  Could you expand?

---

### Post by andrewsawyer on 2007-02-06
Don't worry - I've found this: [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

Thank you though.

---

### Post by chalex on 2007-02-06
Right, you just want to add your disks as physical volumes (PVs) to a single volume group (VG).  Then create a logical volume (LV) of whatever size you want, then format that LV with a filesystem (FS).  I suggest you choose an FS that you can resize without unmounting.  I think XFS can do that.

---

### Post by Brazen on 2007-02-07
> **chalex said:**
> Right, you just want to add your disks as physical volumes (PVs) to a single volume group (VG).  Then create a logical volume (LV) of whatever size you want, then format that LV with a filesystem (FS).  I suggest you choose an FS that you can resize without unmounting.  I think XFS can do that.

Yeah as Chalex said, you can have a partition span multiple drives by using LVM.  Unfortunately this will mean you have to move the files OFF your current partitions so you can wipe it out (LVM must be set up before the partition is created).

XFS would be a good file system to use.  As Chalex thought, XFS can be resized online.  In fact it MUST be online to resize.  Plus XFS is faster than the default ext3 anyway.  Ext3 can be resized, but you have to umount it first or use the experimental online ext3 resizer.

The logical volumes can also be expanded, though I'm not sure if they must be taken offline or not.  I've always used Webmin for messing with LVM and partitions.  Webmin can also handle resizing and makes things stupidly simple.

---

### Post by rmjb on 2007-02-21
Hi, I don't know if you're still working out what to do with this but I believe EVMS can do what you ask, i.e. just add more storage to the end of existing storage, and you wont have to remove your data and rebuild then put it back.

- rmjb

---

### Post by andrewsawyer on 2007-02-21
Thank you everyone for your help.

I've got a spare couple of drives lying around, and I figure it is about time I did a good clear up of the server (just moved house so now is as good-a-time as any).  I'll give LVM a go and get it all sorted that way.  I notice it's not possible to shrink a XFS file system, but only to expand it.  Not a problem for me, but anyone else reading this thread in the future might want to take note.

Cheers,

Andy

---

