---
title: "need to switch hd"
date: 2010-01-10
forum: Server Platforms
---

### Post by kwickcut on 2010-01-10
i have some bad sectors on the primary hd and want to move everything to a new hd ... what would be the steps to do this .. i have 5 running websites on the server. the hd are the same make and model 

my current hd setup is


```
[1]("https://kwickservers.com:10000/fdisk/edit_part.cgi?disk=0&part=0") [Linux LVM]("https://kwickservers.com:10000/fdisk/edit_part.cgi?disk=0&part=0") [IMG]https://kwickservers.com:10000/fdisk/images/gap.gif[/IMG][IMG]https://kwickservers.com:10000/fdisk/images/gap.gif[/IMG] 232.65 GB 1 30370 [LVM VG server1]("https://kwickservers.com:10000/lvm/")  
[2]("https://kwickservers.com:10000/fdisk/edit_part.cgi?disk=0&part=1") [Extended]("https://kwickservers.com:10000/fdisk/edit_part.cgi?disk=0&part=1")  243.17 MB 30371 30401 
[5]("https://kwickservers.com:10000/fdisk/edit_part.cgi?disk=0&part=2") [Linux]("https://kwickservers.com:10000/fdisk/edit_part.cgi?disk=0&part=2")  243.17 MB 30371 30401 

```

thank you for any help



kwick

---

### Post by CharlesA on 2010-01-10
You could try something like clonezilla to clone the drive onto the new one.

---

### Post by kwickcut on 2010-01-10
this wont copy the bad sectors?

---

### Post by kwickcut on 2010-01-11
i was told by a system admin that cloning the hd  there would be problems with linux and  all the symlinks



kwick

---

### Post by CharlesA on 2010-01-11
I haven't had any problems cloning my linux server using clonezilla.

Not quite sure what they were refering to.

---

### Post by cariboo on 2010-01-11
Partimage should do what you want, it won't clone the empty space on the drive. Partimage is in the repositories.

---

