---
title: "RAID 6 Considerations"
date: 2014-09-15
forum: Server Platforms
---

### Post by KillerKelvUK on 2014-09-15
Hi, firstly if I've posted into the wrong section, apologies please move me to a more appropriate location.

I currently run a home server/nas with software RAID 10 (mdadm) across 4x 2TB Seagate DM001's...a combination of age and storage capacity is leading me to consider upgrading the disks to the Seagate 4TB NAS drives and so I'm researching the considerations.  My intentions would be to maintain the software RAID deployment using mdadm but move to RAID 6 instead of persist 10...my logic being that I may increase the number of disks at a later date and r6 gives me more usable storage than r10.  I realise however that the performance characteristics of 6 are different from 10 and so I was looking for any recommendation/experience that might make me reconsider, such as...are there any known issues with RAID 6 using mdadm e.g. recovery procedures, maintenance, stability etc?

My home server is a basic Ivy Bridge desktop with Core i7 CPU, the usage is pretty low i.e. I'm not running intensive DB tasks and concurrently I max at around 4 user tasks the bulkiest being a samba share streaming media content.  The only remaining point to note is that I also intend to relocate my KVM disk images onto the RAID storage instead of the single SSD they operate from now, my VMs are a mix of server apps, Windows 7 desktop and Asterisks/FreePBX...generally nothing intensive.

I realise this won't compare with the true server usage this forum usually deals with but I thought my use case requirements might be better served here.

Thanks in advance,

K

---

### Post by lukeiamyourfather on 2014-09-15
Consider RAID Z2 with ZFS on Linux instead of RAID 6 with md. It's easy to use and provides many features that RAID 6 doesn't like 256-bit checksums for every block of data on disk, snpashots, high performance compression, on the fly repair of file system errors and online disk scrubbing, only actual data on disk gets rebuilt in the event of a disk failure, the list goes on... Not to be confused with the FUSE implementation which has been around for a while, ZFS on Linux is a kernel level implementation of ZFS and is high performance.

[http://zfsonlinux.org/](http://zfsonlinux.org/)
[http://open-zfs.org/wiki/Main_Page](http://open-zfs.org/wiki/Main_Page)
[http://en.wikipedia.org/wiki/ZFS](http://en.wikipedia.org/wiki/ZFS)

---

### Post by KillerKelvUK on 2014-09-15
> **lukeiamyourfather said:**
> Consider RAID Z2 with ZFS on Linux instead of RAID 6 with md. It's easy to use and provides many features that RAID 6 doesn't like 256-bit checksums for every block of data on disk, snpashots, high performance compression, on the fly repair of file system errors and online disk scrubbing, only actual data on disk gets rebuilt in the event of a disk failure, the list goes on... Not to be confused with the FUSE implementation which has been around for a while, ZFS on Linux is a kernel level implementation of ZFS and is high performance.

[http://zfsonlinux.org/](http://zfsonlinux.org/)
[http://open-zfs.org/wiki/Main_Page](http://open-zfs.org/wiki/Main_Page)
[http://en.wikipedia.org/wiki/ZFS](http://en.wikipedia.org/wiki/ZFS)

Didn't expect some Vader wisdom if I'm being honest, but I'll take it ;).

I was "aware" of ZFS in that I'd looked at FreeNAS and that's about it, so based on your post I've started to visit this as a serious option and am liking the idea so far.  One question I have early on is around expansion, the wiki article has the following statement albeit without citation...

[COLOR=#252525][FONT=sans-serif]> [/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]It is not possible to change the number of drives in an existing vdev (Block Pointer Rewrite will allow this, and also allow defragmentation), but it is always possible to increase storage capacity by adding a new vdev to a zpool. It is possible to swap a drive to a larger drive and resilver (repair) the zpool.[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]
[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]
[/FONT][/COLOR]My understanding of ZFS given my scenario is that I would create a vdev from my 4 physical disks using RAID-Z2 to give 2 disk redundancy...this would be roughly equivalent to a RAID6 deployment but with the added benefits ZFS has.  However as one of my requirements has an eye on future expansion i.e from 4 to 6 disks the quote above gives a contradictory view of what ZFS can/cannot do in this regard.  I understand the point about adding a new vdev into the zpool but wouldn't this be inefficient in comparison to expanding a RAID6 array?  Obviously the contradictory part of the quote suggests to me you can add more disks to a vdev, but without citation or reference, can you confirm whether this IS possible?

---

### Post by rubylaser on 2014-09-15
> **KillerKelvUK said:**
> My understanding of ZFS given my scenario is that I would create a vdev from my 4 physical disks using RAID-Z2 to give 2 disk redundancy...this would be roughly equivalent to a RAID6 deployment but with the added benefits ZFS has.  However as one of my requirements has an eye on future expansion i.e from 4 to 6 disks the quote above gives a contradictory view of what ZFS can/cannot do in this regard.  I understand the point about adding a new vdev into the zpool but wouldn't this be inefficient in comparison to expanding a RAID6 array?  Obviously the contradictory part of the quote suggests to me you can add more disks to a vdev, but without citation or reference, can you confirm whether this IS possible?

Yes, this is a limitation of ZFS.  You can either add another vdev or replace all disks in an existing vdev to expand it.  In your case, moving to an mdadm RAID6 would probably be the most flexible for your use case.  It's very easy to expand in the future, and the only "inefficiency" you will introduce is the added overhead of calculating the double parity for RAID6 vs. no parity calculations with RAID10.  If you didn't want to store VM's on the array, I would have encouraged to you look into SnapRAID, but it's not suited for storing things that are constantly changing like VMs.  For your reference, I use ZFS for my VM storage, and SnapRAID for all my bulk storage.  The combination has served me very well.

---

### Post by lukeiamyourfather on 2014-09-15
With ZFS it shares an underlying storage pool for the file systems. The pool is made up of one or more VDEV. The VDEV could be a mirror, RAID Z, RAID Z2, RAID Z3, etc. Disks can be added to the storage pool only in the form of another VDEV. From there the file systems using that pool have access to the new VDEV and free space it provides. However existing VDEV can't be changed or removed from a pool. With traditional RAID you can do OCE (online capacity expansion) to add more disks to an array (or VDEV in this case) but this feature doesn't exist in ZFS at this point and may never. Mainly because doing so would make the code so complicated and unmaintainable it might prevent future development of other features. This video with some of the original authors of ZFS discusses it which might be more than you wanted to know about the subject.

[https://www.youtube.com/watch?v=G2vIdPmsnTI#t=44m53s](https://www.youtube.com/watch?v=G2vIdPmsnTI#t=44m53s)

With ZFS if you wanted to go from a four disk RAID Z2 to a six disk RAID Z2 you'd have to move the data elsewhere, delete the pool and VDEV, create a new one with all six disks, put everything back on the disks. On the plus side if you have one four disk RAID Z2 and you add another then you are doubling the performance of the pool. ZFS will load balance and stripe data across all VDEV in the pool automatically. For some folks this is a deal breaker but in my opinion it's well worth the trade off for the other features and benefits. Not saying RAID 6 is dead or anything but if you can live with the few caveats I think ZFS is a much better option in most cases.

---

