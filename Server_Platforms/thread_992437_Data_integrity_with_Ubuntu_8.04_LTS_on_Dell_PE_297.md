---
title: "Data integrity with Ubuntu 8.04 LTS on Dell PE 2970"
date: 2008-11-24
forum: Server Platforms
---

### Post by ryandball on 2008-11-24
Hi all,

I've been 'round and 'round with this and have been bitten for the final time.  Either I'm switching off Dell hardware or I'm moving OS's on our servers, and I'd rather stay with Ubuntu at this point.

The server in question is a PowerEdge 2970 that's less than a year old (with many years left on warranty).  It's an AMD Opteron dual core model with 4 GB RAM, (1) 80 GB RAID1 array for OS, (1) 160 GB RAID1 array for data, and (1) 1 TB RAID0 array for data (don't care about data loss on that one).  SATA 7200 RPM drives.  They are all plugged into a PERC/5i RAID controller.

It seems that on this particular machine, almost every time I reboot it corrupts all the data in the / partition on the hda drive.  Fsck'ing in single-user mode only screws it up more, giving "bad magic number in superblock" messages.  I tried copying magic numbers with offsets, those are bad too.  This has happened several times in the <1 year we've had this and I've had to reinstall each time.  The data on the other volumes are left ok.  I am shuttdown / rebooting properly (I think).  If I boot to a Knoppix USB drive, the data on all the hard disks are there.

We have many other Dell PE servers running Windows 2000 and Windows 2003 servers, and other non-Dell servers running Ubuntu 6.06, 7.10 and 8.04 server editions (both AMD 64-bit and x386) and none of them have done this ever, even with forced shutdowns, or at least not beyond what a simple fsck fixed.

What in the world am I missing here?  This kind of thing is too critical.  Dell support says "oh it's not supported" and "try debian, it's better" - not a good answer IMO.  I also posted on their company forum for support but they pulled my post because I complained about how long tech support takes.  Eesh.

Also I'm wondering if it could be hardware failure on the 80 GB array, even though the RAID controller should tell me that when I go into its BIOS, or failure in the RAID controller itself.

I don't trust this thing but I need to get it back online.  Any ideas?

Thanks
Ryan
Portland, OR

---

