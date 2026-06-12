---
title: "VMWare not installing"
date: 2008-11-11
forum: Virtualisation
---

### Post by bcbotha on 2008-11-11
i have downloaded VMWare 64bit bundle to install on my Ubuntu machine. how ever its not installing.

This is the command I tried: chmod +x VMWare-Workstation-6.5.0-118166.i386.bundle

and i was then going to type this command: ./VMWare-Workstation-6.5.0-118166.i386.bundle.

if there is another way or if im doing something wrong please help me.

---

### Post by Griz054 on 2008-11-11
Try 

sudo sh VMWare-Workstation-6.5.0-118166.i386.bundle

---

### Post by bcbotha on 2008-11-11
i found out what was wrong. the VMWare-Workstation-6.5.0-118166.i386.bundle was for 32bit computers, the bundle i needed was for 64bit. that ended up being VMWare-Workstation-6.5.0-118166.x86_64.bundle.

ive now got it working, thanks.

---

### Post by bcbotha on 2008-11-13
is there any other way of getting hold of the activation code from VMware? i requested the code for the 30 day trial version and was told id receive an e-mail with it.....ive got nothing. how can i get it?

---

