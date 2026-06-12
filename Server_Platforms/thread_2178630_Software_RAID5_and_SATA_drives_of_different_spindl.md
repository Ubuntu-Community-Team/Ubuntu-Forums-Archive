---
title: "Software RAID5 and SATA drives of different spindle speed"
date: 2013-10-04
forum: Server Platforms
---

### Post by MakOwner on 2013-10-04
I have a couple of mdadm raid arrays built on Seagate 5900 RPM drives - when I bought these, they were relatively cheap for the size and offered (some) power and cooling savings over their 7200 RPM counterparts, and offer more than sufficient performance for my needs.  I have one array of 8 x 1.5TB drives and another of 8 x 2.0TB drives.  

I have moved them from 8 bay to 16 bay enclosures and now have the opportunity to add more volumes to the arrays.  (From eSATA enclosure to a SAS enclosure behind an LSI1068E controller.)

These 5900 RPM drives are now hard to find at a price point I want to live with.


Just how ugly will it be if I put 7200 RPM drives in this array?  
Anyone have any experience running mdadm RAID 5 on drives with dissimilar spindle speeds?
I'm worried about dissimilar seek and access times causing the RAID to drop drives, but adding new drives one at a time is a lot more appealing that starting over with all new disks....

---

### Post by rubylaser on 2013-10-04
I have ran 5400 RPM and 7200 RPM drives in mdadm arrays in the past, they will work fine like that and the speed difference would not be the cause for a disk to be dropped from an array.  I hope these two arrays are mirrors of each other (one is a backup for the other), because an 8 disk RAID5 with the possibility of adding more disks in the future is just asking for a disk failure during a lengthy rebuild.

---

### Post by MakOwner on 2013-10-04
> **rubylaser said:**
> I have ran 5400 RPM and 7200 RPM drives in mdadm arrays in the past, they will work fine like that and the speed difference would not be the cause for a disk to be dropped from an array.  I hope these two arrays are mirrors of each other (one is a backup for the other), because an 8 disk RAID5 with the possibility of adding more disks in the future is just asking for a disk failure during a lengthy rebuild.

These two are currently acting as backup for a 15 x 2TB array, and the really critical stuff is copied off to Bluray media.

In your mdamd array with disks of different spindle speed, what was your configuraiton?
One of the reasons I'm so nervous about this is that I once had severe drop out issues with an mdadm array that had disks on two SATA controllers - delays on the motherboard bus or HBA appeared to be enough to cause the drives to drop from the array rather frequently.   That was a while ago and I have been careful since to both keep similiar drives in an array and to make sure they all use the same controller.

---

### Post by rubylaser on 2013-10-04
I had (9) 2TB in an mdadm RAID6 made up of (6) 2TB 7200rpm Seagate drives and (3) 5400rpm WD drives.  In the past, I have also run (14) 1TB WD Green drives in an mdadm array in RAID6 and never had a disk drop out of the array unless I had an actual hardware issue (failing disk, bad SATA cable, shotty HBA).

I have since migrated to SnapRAID + AUFS for large home media storage and ZFS (raidz2) for my mission critical stuff.  My SnapRAID array uses a mix of (8) 2TB disks and (4) 3TB disks (double parity), and my ZFS system has (6) 1TB Seagate Constellation SAS drives in raidz2.  This data is backed up to the SnapRAID server and then offsite to my collocated fileserver as well (pictures and home movies go one more step and get backed up to Amazon Glacier as well.  I couldn't deal with losing pictures of my family).  

Final thoughts, after helping numerous users troubleshoot mdadm arrays that have gone awry either by hardware issues or user error, I'm convinced that for large, home media storage, SnapRAID is a much better choice for almost all use cases.  mdadm is robust, it works great, and I've used it for years, but it's not as forgiving to user error/ disk issues as a RAID4 implementation like SnapRAID uses.

---

### Post by MakOwner on 2013-10-04
> **MakOwner said:**
> These two are currently acting as backup for a 15 x 2TB array, and the really critical stuff is copied off to Bluray media.

In your mdamd array with disks of different spindle speed, what was your configuraiton?
One of the reasons I'm so nervous about this is that I once had severe drop out issues with an mdadm array that had disks on two SATA controllers - delays on the motherboard bus or HBA appeared to be enough to cause the drives to drop from the array rather frequently.   That was a while ago and I have been careful since to both keep similiar drives in an array and to make sure they all use the same controller.

I have tinkered with some other setups, but in general so long as I'm not trying to use desktop hardware and stick to retired, last generation cast off data center level stuff I have had pretty good luck (knock on wood) with mdadm.
However, now would probably be a good time to look at alternatives - I typically install a bare minimal installation and add packages as I need them for the purpose of the server - so my NFS servers will have, on top of the minimal 64 bit install,  OpenSSH, the NFS packages and usually midnighrt commander, and the auto update packages to get security updates.  

How hard would it be to set up SnapRAID on such an installation?

---

### Post by MakOwner on 2013-10-04
I poked around at that (SnapRAID information) - it doens't present all of the drives as one large filesystem, does it?

---

### Post by rubylaser on 2013-10-04
I have directions in my signature to setup SnapRAID :)  Also, if you use AUFS or mhddfs it can be presented as one large filesystem.  This is exactly how I use it.

---

