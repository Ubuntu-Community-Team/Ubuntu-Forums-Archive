---
title: "SnapRAID + ZFS on Media Server"
date: 2014-01-25
forum: Server Platforms
---

### Post by Mobile Data Solutions on 2014-01-25
I searched the forum before posting this question, but could not find anything directly relevant.

I've been working on a new media server for my home for the past couple of weeks. I have settled on using Ubuntu Server 12.04.3 LTS as the OS. I have 5 hard drives - 1 OS, 3 data, 1 parity. I'm using SnapRAID for redundancy/backup solution (1 drive for parity; aka similar protection to RAID5). Media will be streamed to various HTPC's and PC's in the house using SAMBA and NFS (mostly SAMBA). The house has a 1 GigE network. I don't anticipate more than 3 simultaneous connections reading files from the media server and sending over the network to local boxes.

My current quandary is whether or not to use ZFS as the underlying file system, and then setup SnapRAID on top of it. I've read some other posts indicating this can be done by assigning single-disk pools in ZFS.

I originally wanted to pool my drives, and rely on an underlying file system to manage which disk they are on. Reason: I only need to worry about filling the space on my entire pool of disks, versus having to worry about filling up a particular disk. For example, let's say that I've got 3 disks and each one has (respectively) my movies, tv shows, and music. If my movie disk fills up, I have to figure out what to do about it and potentially also deal with managing my network shares for all of my HTPC's and PC's in the house.

I have tried AUFS. I ruled it out because of its issues with ghost files that are not deleted from underlying disks. It also has similar issues in some cases when moving files. Regardless, I didn't like it and it's not for me.

I have tried mhddfs. The problem with this is the slow write speeds. Not a huge issue, but would be a PITA for initial hard drive population. Compared with stock Ubuntu file system (read/write directly to local HD), my write speed under mhddfs was approximately 15% of my stock Ubuntu write speeds. My read speed was 90% of the stock read speed.

Questions:
  - 1. Pros/Cons of using ZFS and SnapRAID together?
  - 2. Would I need to remove SnapRAID and install ZFS first (currently I have SnapRAID installed with default Ubuntu filesystem)
  - 3. Could I use ZFS to pool all the ZFS drives and share them via SAMBA and NFS as a single drive?
  - 4. Any pitfalls to be aware of when installing ZFS (other than possibly #2)?

If I don't install ZFS, my choices now are to use the stock Ubuntu FS and deal with possibility of filling up a disk, or installing mhddfs and dealing with slow write speeds (but knowing the server will be mostly reading and sending data over network connections).

I'm not convinced that ZFS is worth the effort for this particular scenario, so I appreciate any feedback.

---

### Post by TheFu on 2014-01-25
ZFS usually means you'll select RAIDz or RAIDz2.  Lots of reasons for this protection.
SnapRAID seems to be more about maximizing storage, having some level of protection (I guess) and minimizing hassles.

Both don't get you out of needing backups.  There is no substitute for having backups, definitely NOT RAID.

Because of the way that ZFS uses HDDs in RAID sets, there are certain numbers of disks that are better than others. I don't think your situation is one of the better choices.

ZFS has built-in CIFS and NFS and iSCSI sharing. You can mix and match CIFS and NFS. 

ZFS has lots of pitfalls.  Definitely read about those before moving forward. It wants/needs LOTS-OF-RAM.  I think they recommend 2G RAM for every 1TB of storage. Folks with less than 8G of RAM seem to have the most performance issues even with smaller storage connected. That is a bunch of hardware just to store movies.  I'd think if sharing storage with ZFS was the prime reason for the server, then deploying something like FreeNAS (or the forked, close, relative) would be wise - following their hardware guidelines.

I'd stay with EXT4 and good backups, if I were in your situation, at least for the media. For the OS/apps and my personal data, a mirror-like backup is NOT sufficient, IMHO. But that is a different question completely.

---

### Post by Mobile Data Solutions on 2014-01-25
Thanks. Forgot to mention my box has 4G RAM and using 3Tb WD Red drives for data storage and parity. To your point, sounds like ZFS may create more problems than it solves. I'll read up some more on other users' experiences.

Regarding backups, yes I understand. But IMHO, for a media server, SnapRAID is a good solution since the content will not change frequently.

mhddfs has acceptable read speeds for me (at least on local drives), but I'd like to find a faster write solution. I have read some posts from people who have supposedly boosted their write throughput after installing mhddfs, but none of the posts describe how they accomplished this feat.

I thought about using LVM, but I read some issues reported with larger disks (over 2 Tb), so I have shied away from that as a solution for pooling and drive mgmt.

---

### Post by rubylaser on 2014-01-25
SnapRAID will work fine with ZFS disks, but it's never made any sense to me to do that backed by a bunch of single disk ZFS pools.  ZFS will be able to indentify errors but not repair them because their are no other disks in the pool to pull the proper data from.  I would either do a ZFS pool or a SnapRAID array + a pooling solution.  SnapRAID has nothing to do with maximizing storage space, it's a way to provide RAID4-like (it actually allows up to 6 parity disks) snapshot RAID for data that doesn't change much, perfect for a home media server.

If you are concerned about write speeds for the initial sync, just use AUFS while you transfer the data, then switch over to mhddfs after you are done.  They are both interchangeable, because they just pool the underlying disks. On an i3-2100 (8GB of RAM, with a PCIe Intel NIC), I can write to my mhddfs pool around 60MB/s over NFS and read from it at 119MB/s on a 20GB testfile.  This is more than fast enough for regular usage. AUFS saturates gigabit reading and writing for me.

---

### Post by Mobile Data Solutions on 2014-01-25
This box has an AMD E-450 (dual core) and I'm getting (local disk i/o) about 140 MB/s read and 130 MB/s write to a specific, single disk. When I ran a test thru mhddfs, I got 135 MB/s read and 27 MB/s write. Terrible write performance. I can't understand why it is so poor, other than the fact it's not run at the kernel level.

Ruby, I'll try your suggestion for the initial setup via AUFS. Good idea. Thanks.  :)

---

