---
title: "Will dual-booting Windows Vista Premium with Ubuntu 9.04 cause problems?"
date: 2009-04-30
forum: The Cafe
---

### Post by gymophett on 2009-04-30
Will Ubuntu run just like it would without Windows on the other. Windows Vista Premium is pre-installed, and I may need it for a few things, but I will only give it around 15GB of my 320GB. Will it suck up my 3GB ram and lower my Ubuntu performance? I need to know. Ubuntu is my main OS, and Windows is for boot for games.

---

### Post by kernelhaxor on 2009-04-30
you can boot into only one OS at a time .. so yeah Vista will not have any impact on Ubuntu and the other way round ..
The only thing that will be shared is your disk space like you said .. not RAM, CPU or anything else

---

### Post by SunnyRabbiera on 2009-04-30
No there should be no major issues, but I would try to split the partitions 50/50
160GB for windows and 160GB for linux

---

### Post by lisati on 2009-04-30
The laptop I'm using at the moment has both Vista Home Premium and Ubuntu 8.10 on it in a "dual boot" configuration. Each starts up independently of the other in a way that has only one active at a time, and each has an area of the disk drive set aside for its own use.

The only ways I know of that Windows could impact on Ubuntu's performance is if you use "Wubi" to install Ubuntu "within" Windows or if you use a "virtual machine" to run one within the other.

---

### Post by Icehuck on 2009-04-30
> **gymophett said:**
> Will Ubuntu run just like it would without Windows on the other. Windows Vista Premium is pre-installed, and I may need it for a few things, but I will only give it around 15GB of my 320GB. Will it suck up my 3GB ram and lower my Ubuntu performance? I need to know. Ubuntu is my main OS, and Windows is for boot for games.

The only thing you need to be careful of is the fact that the Vista bootloader does not like Grub. It will whack your MBR if you do not set it up correctly and leave you with a system that does not boot into either OS.

---

### Post by forrestcupp on 2009-04-30
When you set up your partitions, remember this.  Ubuntu can read and write to NTFS drives out of the box, but Windows cannot read or write to Ext drives out of the box.  So you might want to give Windows more than 15 GB since it can be shared between what you do in Windows *and* Linux.

> **Icehuck said:**
> The only thing you need to be careful of is the fact that the Vista bootloader does not like Grub. It will whack your MBR if you do not set it up correctly and leave you with a system that does not boot into either OS.

If Vista is already installed first, there won't be any problem at all.  It's only when Linux is installed first and then you try to install Vista that you run into that kind of trouble.  Even then, it can be fixed.

The only other time you run into that kind of trouble is when you have a dual boot setup and you remove Linux.  Then you're stuck with GRUB trying to access it's settings folder that doesn't exist anymore.  In that case, there are ways to fix the Vista bootloader.

But generally, there shouldn't be any trouble at all with a normal dual boot setup.

---

### Post by gymophett on 2009-05-01
Thanks you helpful community! :D

---

