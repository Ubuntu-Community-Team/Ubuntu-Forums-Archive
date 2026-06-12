---
title: "Create software RAID on existing server install"
date: 2011-12-25
forum: Server Platforms
---

### Post by MAFoElffen on 2011-12-25
Re:
- Ubuntu 11.10 Server, Originally was installed 10.04, upgraded through 11.10.
- Adaptec 29160 SCSI, sees all 11 SCSI drives.
- Gateway DataStation Ultra-11, the 2 backplanes bridge as one.

dmraid is easy when you install a server. But, now I have an existing Server with a SCSI card that is not RAID and a SCSI RAID enclosure that depends on a SCSI RAID COntroller that isn't there...

I figured I'd install software RAID, create 11 drives as RAID 5 and mount it as a data volume.  I know how to do this as a new install...

but how do I do this with an existing install?  

Everyone's instructions on this is on a new / fresh install. If I let the partitioner start a Oneiric Server Install CD, it downloads a base system before it gets to the partitioner... Just nervous about that method on existing system.

---

### Post by rubylaser on 2011-12-25
I'm busy for Christmas, but you could follow my [tutorial]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm"). If you can't figure it out, I'll take a look tonight.

---

### Post by MAFoElffen on 2011-12-25
> **rubylaser said:**
> I'm busy for Christmas, but you could follow my [tutorial]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm"). If you can't figure it out, I'll take a look tonight.
Thank you so much. This one went without any troubles:[SIZE=1]
[Software RAID 5 in Ubuntu/Debian with mdadm]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm")[/SIZE]

---

### Post by rubylaser on 2011-12-25
Glad it worked out for you and Merry Christmas :)

---

