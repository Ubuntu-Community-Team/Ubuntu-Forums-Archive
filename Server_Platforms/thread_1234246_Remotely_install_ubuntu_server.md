---
title: "Remotely install ubuntu server"
date: 2009-08-07
forum: Server Platforms
---

### Post by bogdan_5844 on 2009-08-07
Hey

I know this has been asked before,but it either was pointing to how to install debian (it uses LILO,you will see why it's bugging me) or was not exactly my case.

So,I have 2 servers in my house.The first is a 2003 PC running Ubuntu Server,which I use for rtorrent and website hosting.It runs quite nice,no problem about it.

The second is my old laptop which has a burnt screen.It has Ubuntu 9.04 Desktop on it.I can ssh into it.I'd like to have an Ubuntu Server install on that as well (it has bigger RAM,and I want to use it to remotely use VBox + Windows XP for Flash and other sofware)

The problem is,the VGA output is broke,and the screen (as noted earlier) is burnt.How would I go to remotely install Ubuntu (or Debian,but not other Linux distro)on it? 

Tried to follow the Debian guide on remote install,but I saw something about using LILO (I know Ubuntu uses GRUB) and I am afraid it will conflict and probably make my installation broken.

What would be the safest way to do the aforementioned?I might do some webhosting on this server,too,so I'd like a small,20GB-ish partition for the OS,and the rest of 160 GB's to use for storage.

Can somebody help?:)

---

### Post by grantemsley on 2009-08-07
Does your broken laptop have a serial port?

---

### Post by cariboo on 2009-08-07
Have a look [here]("https://help.ubuntu.com/community/Installation"), it may help with your installation problems.

---

### Post by bogdan_5844 on 2009-08-08
Tried the "OverSSH" guide,failed at partitioning...

> mkfs.ext3 /dev/sda1
mke2fs 1.41.4 (27-Jan-2009)
mkfs.ext3: inode_size (128) * inodes_count (0) too big for a
	filesystem with 0 blocks, specify higher inode_ratio (-i)
	or lower inode count (-N).


Google doesn't help too much :(

---

### Post by regors86 on 2009-08-08
[FONT=Palatino Linotype]What is going on?:o:guitar:[/FONT]

---

### Post by regors86 on 2009-08-08
[list=1]
[*]ok
[/list]

---

### Post by bogdan_5844 on 2009-08-08
@regors86 - what were you trying to say?:confused:

---

