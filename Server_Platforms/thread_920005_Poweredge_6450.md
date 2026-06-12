---
title: "Poweredge 6450"
date: 2008-09-14
forum: Server Platforms
---

### Post by agentfubu on 2008-09-14
I already posted this in the installation section, but then I figured that in the server section people might be able to help more:

Thanks for reading this. I want to know if there's something special I need to install Ubuntu on this system:

2 PIII Xeons (32bit)
8gb of Ram
Perc-2 SCSI controller with 4 drives
1 raid array. 

I've tried the unbuntu desktop live disk to no avail, it just stop at the busybox initramfs prompt. 

Thanks!

---

### Post by JonnyJE on 2008-09-23
I get the same problem, can anyone help?

[IMG]http://i164.photobucket.com/albums/u31/JonnyJE/Other/server/IMG_3135.jpg[/IMG]

---

### Post by eric_stewart on 2008-09-24
> **JonnyJE said:**
> I get the same problem, can anyone help?



I have the same PowerEdge model server.  I didn't have that issue since I ended up installing Ubuntu as a guest OS on VMware Server v2.0 (a free download).  In fact I am running two Ubuntu 8.04 virtual machines, an Ubuntu 8.10 (Ibex) virtual machine and an Windows XP SP3 machine all in 2.5 GB RAM on the PowerEddge and with two PIII processors.  Works great.

I don't know if that's an option for you, but it certainly gives you a lot of flexibility plus the ability to play with Ubuntu in a virtual machine without worrying about messing up your "production" environment.

/Eric

---

