---
title: "[SOLVED] Folder Permissions and Problems mounting new hard drives"
date: 2008-05-13
forum: Security
---

### Post by roblloyd on 2008-05-13
Hi,

I'm having trouble sorting out file permissions for the new hard drives i have installed in my computer. I'm running ubuntu 8.04.

I recently bought a 500Gb SATA drive and 120Gb IDE drive. I can copy and change files as long as I'm root, but for day to day use I need read and write access as a normal user.

I have given the output of cat /etc/fstab below. The 120Gb drive is /dev/sdb1 mounted at /media/space and the 500Gb drive is /dev/sdc1 mounted at /media/server.

```

rob@Johnny5:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=de4a3782-a7f5-452b-a483-0f1d4f8a7d56 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=82a45b01-7ad9-47ff-ab19-6f443bc5c523 /home           ext2    defaults        0       2

/dev/sdb1	/media/space	vfat	user,rw,suid,dev,exec,auto,async	00
/dev/sdc1	/media/server 	vfat	user,rw,suid,dev,exec,auto,async	00

```

I have tried to follow HowTo's dealing with changing permissions and mount options, but nothing seems to work. I'm sure that its probably something stupidly simple, but its only easy when you know the answers!

thanks in advance,

Rob

---

### Post by hermes0710 on 2008-05-14
Replace suid with nosuid and try again. Is it ok?

---

### Post by roblloyd on 2008-05-14
> **hermes0710 said:**
> Replace suid with nosuid and try again. Is it ok?

Hi hermes,

Thanks for the quick reply, I tried changing to nosuid, no change after a restart. 

Just to clarify, the drives mount in the right place, but only root has permissions to access them... tedious to say the least!

Attached is a screenshot of my problem

---

### Post by hermes0710 on 2008-05-14
Check this:

[http://linux.die.net/man/8/mount]("http://linux.die.net/man/8/mount")

Also, i think that there should be a space/tab between the "00" in the last to lines of your file

---

### Post by roblloyd on 2008-05-14
Hi,

It's all sorted now, I used a page i found on the ubuntu community documentation, here:[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"). It seems to have done the trick!

I changed /etc/fstab to:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=de4a3782-a7f5-452b-a483-0f1d4f8a7d56 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=82a45b01-7ad9-47ff-ab19-6f443bc5c523 /home           ext2    defaults        0       2

/dev/sdb1	/media/space	vfat	user,auto,fmask=0177,dmask=0077,uid=1000		0	0
/dev/sdc1	/media/server 	vfat	user,auto,fmask=0177,dmask=0077,uid=1000		0	0
```

The lines; user,auto,fmask=0177,dmask=0077,uid=1000 were the key!

---

