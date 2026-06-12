---
title: "Samba server issues - storage space"
date: 2017-10-20
forum: Server Platforms
---

### Post by gales29 on 2017-10-20
so im getting some samba errors. i have ubuntu 17.04 running with samba installed an running. i attached a copy of my conf page. i have a 5tb external drive attached to my computer. and it is mounted to my /mnt drive. but i have an issue with windows not detecting the correct file size. it doesnt see my drive at 1 tb it only sees the size of my ssd drive where my OS is. so i would like to be able to transfer things of the 100 gb size. 
[ATTACH=CONFIG]277176[/ATTACH][ATTACH=CONFIG]277177[/ATTACH][ATTACH=CONFIG]277178[/ATTACH][ATTACH=CONFIG]277179[/ATTACH]

---

### Post by LHammonds on 2017-10-20
I doubt that /mnt = your external HD.  You are sharing /mnt which is part of your base install...local HD.

If you mounted that external HD to /mnt/extdisk1, then add that exact path to your SMB config instead of /mnt

LHammonds

---

### Post by darkod on 2017-10-20
Also to add, you have 4 partitions on the ext hdd (why?) and usually you would mount each partition to different mount point. So I also doubt you have the whole disk mounted at /mnt.

---

