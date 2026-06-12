---
title: "Drive space solutions"
date: 2012-12-04
forum: Server Platforms
---

### Post by flycast on 2012-12-04
OK. Setting up some file servers on a budget. I am looking for some suggestions on how to get about 12Tb of storage with Raid that can rebuild on the fly. SANs look expensive but NAS seem a little consumer-ish.

Anybody out there with opinions (of course there are!) regarding storage and Ubuntu servers. One thing to note. What has happened in the past is we buy what seems like a ton of storage and then new software comes out and the company grows and we need more storage so somebody buys an external drive.

I am hoping to get a solution where I can start at the 8-12Tb range and then be upwardly expandable.

---

### Post by rubylaser on 2012-12-04
You're going to answer a bunch of questions to get a good answer, here are a few to get you started:

1. What's the budget?
2. How many users will access this?
3. What is the performance expectation?
4. Are you set on a particular RAID setup (hardware/software)?
5. What filesystem do you intend to use?

---

### Post by flycast on 2012-12-04
Good questions all..

1) Budget? There really isn't one meaning that no one is planning on spending the money. That is why less is better than more.

2) Number of users? Up to 20 connections, usually less. Some users may choose to work locally and then copy files to the file server when done.

3) Performance expectation. These are Photoshop/Illustrator type files. Some typical files sizes are 100Mb ranging up to 1TB - 1.5Tb. Most users will work and save to the file server through a 1Gb ethernet switch.

4) RAID? 5 or 6? Am open to suggestions here. I do like the idea of rebuild on the fly though. *Edit* After reading further RAID 6 or 10 may be what I want.

5) Filesystem? EXT4 seems to be the "stable" new kid on the block doesn't it? Again, I am open to suggestions here as well.

---

### Post by darkod on 2012-12-04
If you need this to be strictly NAS, then I would say FreeNAS with ZFS. Unfortunately zfs on linux is not yet quite recommended I believe, even though it has a stable version released.

FreeNAS might need some learning on your part, but it's very good for a machine that will be a NAS. It supports CIFS and NFS shares, most commonly used. It also has excellent AD integration in case you need it.

Expandability is great too.

Lets say you get a server with 16 hdd bays but only 8 disks to start with. If you use RAIDZ2 (which is zfs equivalent of RAID6), in other words two disks for parity, the others for data storage. That means out of 8 disks you have a total usable storage of 6 x disk size.
Then in the future you buy 8 disks more to fill the empty bays. You simply select the store you want to expand, configure new RAIDZ2 from these 8 disks, and the store space is doubled automatically. No partitions growing, filesystem growing, etc. The shares can use the new space automatically.

I know rubylaser likes zfs but lets wait for his "verdict".

---

### Post by rubylaser on 2012-12-04
ZFS is awesome:) But, it's only shortcoming for most people is that you can't expand disk-by-disk. You need to add a whole new similarly sized vdev to grow properly (safely and consistent performance). If you go with RAID10 in ZFS, you only need to add 2 disks at a time to grow (adding a new mirrored vdev each time). As long as you know this 1 shortcoming going in and plan accordingly, ZFS is VERY robust, and speedy.

Personally, I use ZFS on Openindiana + Napp-it because in the past, I couldn't get FreeNAS to get anywhere near the throughput that I could on native Solaris (I haven't tried FreeNAS in a long time, so this could be remedied by now).

Since you need 8-12TB, I would use ZFS and use raidz2 vdevs (RAID6) made out of (6) 3TB disks.  This would give you 12TB of usable space and allow you to survive 2 disk failures.  In the future, you  add more (6) disk vdevs to continue to grow the storage pool.

A case like the Norco 4224 would allow you to add up to (3) additional (6) disk vdevs in the future, and eventually (only using 3TB disks) would allow you to have 48TB of usable space and survive 2 disk failures per vdev.  As larger disks become more cost effective, you could use those in the future instead of 3TB disks and make that 48TB number much larger if needed.

Other software RAID options would be using mdadm or something like SnapRAID.  Finally, hardware RAID is certainly another option, at an additional cost.

---

### Post by flycast on 2012-12-05
Thanks for the replays so far...I'll read up on these software RAID options.

So...what about hardware RAID options?

---

### Post by flycast on 2012-12-05
ZFS - very interesting and very easy to use!

You both feel good about it on an Ubuntu server storing valuable data? This statement makes me squirm a bit:
> Unfortunately zfs on linux is not yet quite recommended I believe, even though it has a stable version released.

---

### Post by darkod on 2012-12-05
I didn't say to use it on ubuntu, I hope it didn't sound like that.

FreeNAS is a separate OS based on BSD/Unix, which has almost everything you need for a NAS machine. And it includes stable version of ZFS, which is much more stable on BSD I guess.

The freenas itself needs only about 2GB, so it's best to install it on 4GB or 8GB Compact Flash card or usb stick. This is because the disk with the OS can't be used for data, so using a larger disk is a waste. For example you can get one of those CF to SATA adapters, plug in a CF card and use that as small SATA disk for the OS. It's bootable and everything.

Personally I suck at BSD and Unix, but if I'm making a NAS machine now I would definitely consider FreeNAS to be my first, if not only choice. RAIDZ2 or RAIDZ3 depending on number of disks, and you're good to go.

---

### Post by flycast on 2012-12-18
FreeNas is interesting. I am trying it out now as a virtual machine. Very easy to set up and use.

---

