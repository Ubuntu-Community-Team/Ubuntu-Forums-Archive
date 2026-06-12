---
title: "iSCSI boot from single image file"
date: 2009-10-01
forum: Server Platforms
---

### Post by tinkerbox on 2009-10-01
Hi,
I run a Internet Cafe. All the computers is diskless (iSCSI boot from single image file) except for servers. I use **[iSCSI Cake]("http://www.iscsicake.com/")** software to host the image runs on windows server. *"iSCSI Cake uses copy-on-write mechanism to handle client write requests which means client can write, delete, format and repartition iSCSI disk without changing any bytes in servers storage resource."* But I dont really like the idea of using windows as server and I have to restart (flush cache) the iscsicake service if the cache file is too big and this software is not stable to me for my purpose. I know there is software like **[ccboot]("http://www.ccboot.com/")** or there is more similar windows software out there, but I have no fun using them :roll:

So I install Ubuntu Server 9.04 and install iscsitarget, I followed **[this]("http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target")** guide. After done with necessary configurations, i booted a single machine and it boot faster than when the image was hosted using iscsicake :P

Before I booting more machines, I changed few configurations. I have set the OS image file as read-only, I dont want the image file get corrupted when I fire up those machines. I tried IOMode, /etc/ietd.conf:
```
Lun 0 Path=/storage/winxp.img,Type=fileio
or
Lun 0 Path=/storage/winxp.img,Type=fileio,IOMode=wb
```

but when more than one machines booting together, some of them will crash or has system file corrupted..

How to solved this problem?
Is there a way where I can control a machine that can write to image file directly, and the rest of other machines write to cache file while all machine is turned ON?

I'm linux newbie so please help. Any help is much appreciated!!!

---

### Post by tinkerbox on 2009-10-12
:bumb:

I'm hopeless...I know this is possible, i just dont know how or what application must I used. So I cant just google without knowing what must i do first...

I tried cluster storage, ocfs2, still the same...

---

### Post by Perfect Storm on 2009-10-13
Thread moved

---

### Post by kingbelrik on 2009-10-22
You can do this using AoE which is meant to be a bit more performant and supports WinXP 

[http://www.etherboot.org/wiki/appnotes/cow]("http://www.etherboot.org/wiki/appnotes/cow")

---

