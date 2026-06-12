---
title: "Problem to check and repair ext3 disk??"
date: 2008-04-23
forum: Server Platforms
---

### Post by rado3105 on 2008-04-23
Hi I have problem to repair ubs disk with ext3 filesystem, before I tried to check i umount that disk. It is device: dev/sda1

This showed me:
[IMG]http://img214.imageshack.us/img214/9589/18611799vx5.jpg[/IMG]

the filesystem is ext3 made by gparted in ubuntu desktop 7.10
I have there data and I dont want to lost them

---

### Post by bluefrog on 2008-04-23
Have you tried what it suggested you? Copy the (spare) superblock 8193 with e2fsck

e2fsck -b 8193 /dev/sda1

What is weird is that you say you unmounted the disk. I am surprised this disk could be mounted in the first place if the first superblock is damaged.

James Dupin

---

### Post by rado3105 on 2008-04-23
I am little affraid of lost data, is that safe?
I need before executing that command umount disk or leave it mounted?

---

### Post by bluefrog on 2008-04-23
breathing is not safe will all the pesticide in the air...

I do not understand how your /dev/sda1 can be mounted with a bad first superblock.

Please confirm that /dev/sda1 is really mounted.

mount | grep sda1

James Dupin

---

### Post by rado3105 on 2008-04-23
/dev/sda1 on /media/WD1TB type ext3 (rw)

not just pesticides, breathing oxygen is causing olding biological system(creating free radicals O, OH, that destroy mitochondria - later cell, problems with reparation of DNA that leads to mutations in genome -that leads to - the apoptosis of damaged cell):D

---

### Post by bluefrog on 2008-04-23
So can you access what is on the partition?

If yes, it is time to make backup of your data and then try the e2fsck -b...

James Dupin

---

### Post by bluefrog on 2008-04-23
paste your /etc/fstab by the way please.

---

### Post by rado3105 on 2008-04-23
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/WD1TB    ext3    defaults        0       0

I changed 6. column to 0(not to check after bootup.

---

### Post by bluefrog on 2008-04-23
indeed the move I was to propose you.

doesn't solve the problem but is less annoying.

Anyway back up your data and:
e2fsck -b 8193 /dev/sda1

if it is stil not working then reformat will be the only solution I can suggest you (it is maybe not the only one that exists, but the only one I can think of with my limited knowledge)

James Dupin

---

