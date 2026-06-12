---
title: "Do file system errors act over RAID?"
date: 2009-10-07
forum: The Cafe
---

### Post by kevin11951 on 2009-10-07
If I use ext4 on a raid 1 setup, and ext4 has one of its little errors you hear so much about, will it affect both hdds or just one.  I guess both since the entire array is formatted as ext4, not individual hdds.

---

### Post by toupeiro on 2009-10-07
It *shouldn't*...  If you were doing RAID-0, I would say yes, but Raid-1 are two separate filesystems with either a hardware controller, or software, syncing writes to both drives.  These are file writes to independent filesystems of the same type.  This is how I believe it would traditionally be handled with RAID-1 and just about any filesystem not spanning multiple disks (e.g. RAID 0+1 may yield different results, potentially corrupting a filesystem striped across 2 disks, but your mirror should still be good).  Unless there is some hidden voodoo in EXT4 I do not know about, filesystem-0 has no knowledge about filesystem-1, your RAID controller and/or software does.

---

### Post by psusi on 2009-10-07
> **toupeiro said:**
> It *shouldn't*...  If you were doing RAID-0, I would say yes, but Raid-1 are two separate filesystems with either a hardware controller, or software, syncing writes to both drives.  These are file writes to independent filesystems of the same type.  This is how I believe it would traditionally be handled with RAID-1 and just about any filesystem not spanning multiple disks (e.g. RAID 0+1 may yield different results, potentially corrupting a filesystem striped across 2 disks, but your mirror should still be good).  Unless there is some hidden voodoo in EXT4 I do not know about, filesystem-0 has no knowledge about filesystem-1, your RAID controller and/or software does.

No, there is ONE filesystem that is stored in exact duplicate on two disks.  This protects against something going wrong with one of the disks, but anything that goes wrong with the filesystem will be written to both disks.

Of course, you can intentionally synchronize the raid every once in a while when you feel the system is ok, then remove one disk from the array until the next day or whenever you sync again.  Then if something screws up while the second disk is out of the set, you can fall back to that disk and only loose things you changed since you last synced them.

---

### Post by toupeiro on 2009-10-08
> **psusi said:**
> No, there is ONE filesystem that is stored in exact duplicate on two disks.  This protects against something going wrong with one of the disks, but anything that goes wrong with the filesystem will be written to both disks.

Of course, you can intentionally synchronize the raid every once in a while when you feel the system is ok, then remove one disk from the array until the next day or whenever you sync again.  Then if something screws up while the second disk is out of the set, you can fall back to that disk and only loose things you changed since you last synced them.

RAID-1 is mirroring via synchronised active disk writes. Scheduled synchronization between two disks to make them exact duplicates is **_NOT_** RAID-1.  In all cases RAID, you end up with a logical disk where all of your data is written.  If you just want synchronization, you can do this with the dd command on two Non-RAIDED disks and cron.  RAID-1 can mirror whole disks with one partition and/or multiple individual partitions.  Those partitions can be any filesystem.  The RAID logical disk configuration is stored at the BEGINNING of each physical disk, containing the pertinent information about the partitions and filesystems and how they are laid out on each disk.  With higher RAID levels, this is all handled differently e.g. if you are working with parity.  This is how mirrors are able to be broken and recreated hot, and how parity arrays are able to completely initialise a brand new disk with the parts of the active filesystem it needs.  If a filesystem suddenly crashes in a RAID-1 array, it crashes on the active disk.  The nature of the filesystem crash can have some determination on your mileage of recovering hot. It can almost always be repaired by making your secondary disk active if its a software RAID.  In some cases, this may be done hot and you wouldn't even know it unless you've checked your array to see if its failed over.  If the filesystem error causes the system to freeze, make the secondary disk the primary, boot, and resync a new disk, or the old disk if the hardware is good.  Once the disks are fully initialised, they are both committing writes at the same time.  This has worked plenty of times for me in the past on windows, UNIX, Linux, on both hardware and software RAID sets.  Examples of filesystems that have more logic involved would be something like ZFS, that may render even these steps ineffective.  I don't know how advanced EXT4 is, but if its like its predecessors this method will work fine.

RAID-1 is intended to reduce downtime.  If you want mirroring and can afford downtime, then a dd/rsync script may be more up your alley.  If I am wrong about ext4, and the corruption is written to your other disk because of an active RAID mirror, you're toast.  If you're doing a non-RAID-1 mirror, you'd still have a chance.

---

### Post by toupeiro on 2009-10-08
Here is a non-RAID mirroring script using dd and rsync thats pretty similar to some I've used in the past.  In some ways this one is better than the one I've used for a long time.  Mine was originally written for solaris 8.

[http://www.anthonyldechiaro.com/blog/archives/11](http://www.anthonyldechiaro.com/blog/archives/11)

---

