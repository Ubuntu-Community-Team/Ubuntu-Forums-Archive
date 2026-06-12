---
title: "How do I install eGeforce 6200 on Ubuntu Server 9.04?"
date: 2009-07-07
forum: Server Platforms
---

### Post by xandones on 2009-07-07
Hi!
I recently installed Ubuntu Server 9.04 and I couldn't install the Nvidia drivers eGeforce 6200 256 MB (128 bits). I tried through "Hardware Drivers", "Synaptic" and even trought that application from Nvidia site (it asks for the Kernel). I easily installed it on Desktop edition. What do I need to do? :mad:

P.S. : I already installed Gnome, Firefox, NTFS, and some Kernell apps. Internet works fine.

---

### Post by Vegan on 2009-07-08
Servers do not have a GUI so any old garbage video card is fine. Try you luck in the desktop forums.

---

### Post by cariboo on 2009-07-08
You may have to install dkms and build-essential before you can install a driver for your video card. Although as Vegan says, you don't need a gui on a server. If you do need a graphical application have a look at [Webmin]("http://www.webmin.com/"). it is a web based server administration interface.

---

### Post by xandones on 2009-07-09
> **cariboo907 said:**
> You may have to install dkms and build-essential before you can install a driver for your video card. Although as Vegan says, you don't need a gui on a server. If you do need a graphical application have a look at [Webmin]("http://www.webmin.com/"). it is a web based server administration interface.

"dkms" and "build-essential" were already installed prior to installing the video drivers. The machine will be used as a backup server and needs the graphic interface to facilitate it. If the desktop version is better for this, please tell me. Anyway, thanks for your help. For everyone. ;)

---

### Post by cariboo on 2009-07-09
If all you are using it for is backups, it shouldn't matter whether it has a gui or not. If you intend to use it as a desktop computer, then by all means install the desktop version.

---

