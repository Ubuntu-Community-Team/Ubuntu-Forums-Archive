---
title: "Recommend Raid setup"
date: 2009-09-21
forum: Server Platforms
---

### Post by btdown on 2009-09-21
Hi,
Not necessarily an Ubuntu question, but hopefully someone with some experience can make some recommendations.
 
I just purchased a 4-bay diskless NAS box (Synology CS407e) with **four 1TB Seagate drives **(Seagate Barracuda LP ST31000520AS 1TB 5900 RPM 32MB Cache SATA 3.0Gb/s 3.5" Hard Drives).
 
I realize these drives are "slow", but they were bought for low power consumption and quiet noise levels.
 
While I wait for it to arrive, I'm trying to figure out the best way to configure it. I really have no experience with raid or mirrored data, so I was hoping for some recommendations on how to most efficiently configure my system.
 
Here is my data:
 
Music: 190gb of music. Main purpose will be to stream to local gigabit lan desktop or laptop. Would be "nice" if the music was mirrored, but If the raid/mirroring will cause performance issues, It's not a necessity.
 
General incremental backups for one Vista desktop, one Ubuntu 9.04 desktop, and two vista laptops: I'd like these to be the most secure/available and protected.
 
100gb family pictures. I'd also like these to be the most secure/available and protected.
 
I was thinking of the following possible scenarios:
 
Music: Raid 1, with Drives 1 and 2 - "Music" volume (1tb total available)
All other data: Raid 1, Drives 3,4 - "BackupData" volume (1tb total available)
 
or perhaps:
 
Music: Single music volume, no raid, using drive 1. (1TB unprotected)
All other data: Drives 2,3,4 in Raid 5 configuration (2TB, I think..Raid 5)
 
or maybe:
 
All data on a single raid 5 volume (3TB mirrored available space...i believe).
 
Could anyone comment on these scenarios, or possibly suggest alternates? Any additional thoughts on reliability and recovery would be appreciated.
 
Thanks in advance,
BT

---

### Post by trundlenut on 2009-09-21
What is the box actually capable of in terms of raid?  I was looking at one recently and it could only do RAID 0 or 1, is 5 even an option.

---

### Post by btdown on 2009-09-21
The Synology website states the CS407e allows you to create RAID 0, RAID 1, RAID 5, or RAID 6 volumes on it.

[http://www.synology.com/enu/products/CS407e/index.php](http://www.synology.com/enu/products/CS407e/index.php)

---

### Post by trundlenut on 2009-09-22
RAID 5 will give you the most space while still having redundancy.

---

### Post by Lars Noodén on 2009-09-24
RAID 0 is striping, RAID 1 is mirroring.  RAID 0 will give you speed for playback, if that becomes an issue for CD-quality recordings.  RAID will protect you a little from unexpected hardware failure, but is not a substitute for backups.

Another option with 4 drives is RAID 10 - a stripe of mirrors.

---

### Post by 3L33T on 2009-09-24
My suggestion:

Setup DISK 1 and DISK 2 as RAID 0.  This will give you two 1TB disk space for music and movies (if any) without having to worry about performance.   Setup "rsync" and replicate your music and movie files to DISK

Setup DISK 3 and DISK 4 as RAID 1.   This will give you a single 1TB logical.   Any writes to this drive will be slower than the RAID 0 drives (disk 1 and disk 2).   Put your pics here.  "rsync" your DISK1 and DISK 2 music and movies folders to this drive.

HTH.

---

