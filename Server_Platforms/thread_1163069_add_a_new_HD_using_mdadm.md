---
title: "add a new H/D using mdadm"
date: 2009-05-18
forum: Server Platforms
---

### Post by andyrowe on 2009-05-18
Hi all
I created a Raid1 disc array when seting up a storage server running ubuntu server. One of the two (1TB) Seagate hard drives was bad. My question is how to add a new hard drive to the existing array? Do I have to partition and format the drive first?

---

### Post by fjgaude on 2009-05-19
I believe you can partition the new drive. But first make you get the bad drive out of the existing array correctly. In mdadm --fail the drive then --remove it. The you will be able to add the new drive to the array. Notice, read these links:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

---

### Post by andyrowe on 2009-05-19
Thanks for replying fjgaude. I will follow the links. I've already failed and removed the drive. I'm getting pretty good with mdadm, but I didn't know if the drive would need pre formated and partitioned before I can add it using mdadm.
 
EDIT: are the RAIStools suite installed with mdadm? if I have the RAIDtools, can I use raidhotadd without partitioning the drive first? What tool can I use to partition the disk? sorry for noob questions

---

### Post by fjgaude on 2009-05-20
The RAIDtools are only techology, dont' use. Use only **mdadm**. Study its man pages... very powerful, but complex.

Use gparted to partition the drive. Yes, partition the drive and then add it using mdadm command.

---

### Post by andyrowe on 2009-05-21
> **fjgaude said:**
> Use gparted to partition the drive.
 I don't have a GUI, I'm using ubuntu with CLI only. Does anyone know of a command line tool I can use?

---

### Post by Alekz_ on 2009-05-21
Try `cfdisk` to make a new partition...

---

### Post by fjgaude on 2009-05-22
Yes, **cfdisk**, is what I use, much nicer than **fdisk**. You might have to do a search to find where to download it. I can't recall where I got mine.

---

### Post by Alekz_ on 2009-05-22
`cfdisk` is very nice! :)

The "old" linux(es) installations (Slackware in particular, because I remember that very well!) came with cfdisk.. I still use it nowadays because I don't have a GUI on my servers! :)

---

