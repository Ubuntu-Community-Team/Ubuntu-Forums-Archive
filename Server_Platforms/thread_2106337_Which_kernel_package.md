---
title: "Which kernel package?"
date: 2013-01-18
forum: Server Platforms
---

### Post by ranger12 on 2013-01-18
Sometime ago I got behind with the auto updates with the kernel on my Ubuntu **Server** 12.04 box because of the /boot directory getting full and I finally figured out how to delete some of the oldest kernels to free up space. Well now **aptitude** no longer is reporting the kernel updates under "Upgradable Packages". My question is if I do it manually with aptitude; which package under "Not Installed Packages -> kernel -> main" am I looking for. I would manage the auto update stopped because I got a few updates versions behind with the kernel. This is the output from uname -a

Linux server1 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux

Another reminder this is **Server** - **not** **Desktop** so mentioning using Synaptic or any gui tools is not an option. I am using aptitude.  It does mention about not installing the particular kernel package directly but installing one of the meta packages instead.

---

### Post by ranger12 on 2013-01-18
Okay, after doing some more research I found over at askubuntu.com something about another user having the same issue when using apt-get and it was suggested by someone that they might have accidentally removed the Linux meta-package and suggested doing a
apt-get install linux. I tried this and this is this is the output I receive:

administrator@server1:~$ sudo apt-get install linux
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image linux-image-3.2.0-36-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux linux-image linux-image-3.2.0-36-generic-pae linux-image-generic-pae
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.2 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

I want to make sure this is the correct course of action before I type "y".

---

### Post by steeldriver on 2013-01-18
I'm NOT a kernel expert but that looks OK to me - the way I understand it, linux-image is the overall meta package, then linux-image-generic-pae is the specific meta package for your architecture, then  linux-image-N.N.N-nn-generic-pae is the actual current kernel image for that architecture

```
$ apt-cache depends linux-image
linux-image
  Depends: linux-image-generic-pae
$ 
$ apt-cache depends linux-image-generic-pae
linux-image-generic-pae
  Depends: linux-image-3.2.0-36-generic-pae
  Depends: linux-firmware
$ 

```

---

### Post by ranger12 on 2013-01-19
Okay, I went ahead and did that. Upgrade went fine and I rebooted. It works fine.

---

