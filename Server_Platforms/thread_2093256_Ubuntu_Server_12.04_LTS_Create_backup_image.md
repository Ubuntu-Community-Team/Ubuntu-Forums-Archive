---
title: "Ubuntu Server 12.04 LTS Create backup image"
date: 2012-12-10
forum: Server Platforms
---

### Post by driekus77 on 2012-12-10
Hello,

I want to make an Ubuntu Server 12.04 LTS backup image.
I already tried clonezilla but it is giving me a gray screen.
Is there any software that i can use so it will automaticly make a full image every week. I use a Software raid. 
I hope you could help me

---

### Post by LHammonds on 2012-12-10
Yes, look into FSArchiver.  I use it for my servers.  Backs up all my partitions because I use LVM and have extra free-space so I can use LVM snapshots to create an online backup.  For the /boot, simply unmount /boot, archive it, then mount it back up.

LHammonds

---

