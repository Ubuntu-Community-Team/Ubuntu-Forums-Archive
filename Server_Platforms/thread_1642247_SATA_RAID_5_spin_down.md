---
title: "SATA RAID 5 spin down"
date: 2010-12-10
forum: Server Platforms
---

### Post by Powderking on 2010-12-10
Hi all!

I'm planning to set up a headless ubuntu 10.04LTS AMD64 server for MythTV.

I want to have 4 SATA disks in a RAID5.
Since I wont use the data on these disks every day I want to spin them down and up again automatically.

Hdparm seems the right thing for that.
But can it also handle SATA drives in a RAID5?
The hdparm.conf files writes that I should to "read /usr/share/doc/hdparm/README.Debian for notes about known issues, especially if you have an MD array." Unfortunately I can't find this file.

I read several different things about that. The german Ubuntu wiki has no entry for hdparm but for DMA and it says that it isn't necessary for SATA drives?
Or would sdparm be better?

And most of the information seems to be outdated.
Can you please help me finding some information?

---

### Post by Powderking on 2010-12-10
I think I've just found what I was looking for:
[http://www.mythtv.org/wiki/Power_saving#Hard_Drive_Spin_Down](http://www.mythtv.org/wiki/Power_saving#Hard_Drive_Spin_Down)

---

### Post by sjhupp on 2010-12-10
Sorry, but could someone please clarify if this is done for all drives (sda, sdb etc) or just the raid drive (md0)?
I have a raid5 setup also, and should spin down drives but don't want to get them out of sinc etc.

---

### Post by Powderking on 2010-12-11
I think you have to put in an entry in rc.local for each Raid array and drive you want with maybe different times to wait until spinning down.

But I haven't tested it.
When I have my stuff I will try...

---

### Post by sjhupp on 2010-12-11
If you could post back when you try, that'd be great, thanks.

---

### Post by Powderking on 2010-12-11
I will but it'll take some time.
At least untill christmas...

---

### Post by SaturnusDJ on 2010-12-11
I am interested in this also, for use with RAID5 with LVM.

Wonder what the RAID array will do when one of the disks is still busy spinning up...will such a case kill the array or will it wait for the drive to be ready?

---

