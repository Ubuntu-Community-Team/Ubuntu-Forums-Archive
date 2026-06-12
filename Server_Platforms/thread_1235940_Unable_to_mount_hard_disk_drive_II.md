---
title: "Unable to mount hard disk drive II"
date: 2009-08-09
forum: Server Platforms
---

### Post by Matsaki on 2009-08-09
I have 2 hard drives i my server and the 2'nd was used for oft raid before. The some dume XXX reconfigured the server and left out the 2'nd hard drive.

So now I only have one and I would like to mount the 2'n one. But don't know if it's possible as I can't do it on place as I am 3500Km from the server :(

> Disk name	Total size	Make and model	Partitions	Actions
SCSI device A	33.91 GB	COMPAQ BD036745A4	3	
SCSI device B	33.91 GB	COMPAQ BD036745A4	10

> Device name	Active?	RAID level	Usable size	Member disk devices
/dev/md0	Yes	Mirrored (RAID1)	133.25 MB	/dev/sdb1
/dev/md1	Yes	Mirrored (RAID1)	494.06 MB	/dev/sdb2
/dev/md2	Yes	Mirrored (RAID1)	3.73 GB	/dev/sdb5
/dev/md3	Yes	Mirrored (RAID1)	3.73 GB	/dev/sdb7
/dev/md4	Yes	Mirrored (RAID1)	964.69 MB	/dev/sdb8
/dev/md5	Yes	Mirrored (RAID1)	964.69 MB	/dev/sdb9
/dev/md6	Yes	Mirrored (RAID1)	4.67 GB	/dev/sdb10
/dev/md7	Yes	Mirrored (RAID1)	14.62 GB	/dev/sdb11

Any chanse to fix from here? I would like to make a fresh install of Ubuntu on the 2'nd disc and emigrate to that new OSm and also make a raid after that.

---

