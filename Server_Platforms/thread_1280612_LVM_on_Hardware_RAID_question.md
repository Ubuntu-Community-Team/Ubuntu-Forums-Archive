---
title: "LVM on Hardware RAID question"
date: 2009-10-02
forum: Server Platforms
---

### Post by wonderfullyrich on 2009-10-02
I've got a Dell Poweredge 6400 that I'm setting up with Ubuntu Server.  The Hardware RAID is setup with a 16Gb (two drive) Mirrored partition and a RAID5 101GB (six drive) partition.  

I'm experienced at Ubuntu, but more often in a Desktop scenario.  Most of the sysadmin work I've done on servers has been in Windoze.

I've got Ubuntu server installed using LVM on the 16Gb partition, but am reconsidering the whole configuration.  (This server isn't ready for production use yet, obviously) Does it make more sense to run the whole caboodle as a RAID5 drive (all eight drives) and utilize LVM on top?  Or perhaps it should stay with mirror and RAID5 drive split for the os and data.  

What's the most sensible configuration with a Hardware RAID device?  Should I be using LVM on top of it?

Thanks in advance,
Rich

P.S. I apologize if this is more of a Dell Hardware forum question.

---

### Post by Xianath on 2009-10-06
If you're using a hardware RAID controller, you'd be better off with LVM on top of a single RAID5 or preferably RAID6 array. You'll then only have to worry about one storage management and not two.

Cheers,
Peter

---

