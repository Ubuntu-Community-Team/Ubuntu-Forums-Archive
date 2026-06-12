---
title: "Best VM software."
date: 2009-08-19
forum: Virtualisation
---

### Post by A_M_S on 2009-08-19
Hi

What is the best virtualization software to use under ubuntu?

I'm using VirtualBox for some time, and i would like to know if other VM (VMware for example) offer any advantage.

tnx

---

### Post by SolarOnline on 2009-08-19
You can run virtualized programs directly on your desktop using the latest (version 1.5.0) rdesktop package that comes with Ubuntu 7.04.

There are lots of other options on Ubuntu including VirtualBox, KVM, or VMware Workstation (which i havn't tried yet on Ubuntu)

---

### Post by bodhi.zazen on 2009-08-19
If you are running a desktop and want to run / test iso and/or windows, I would say Virtualbox.

If you are running servers I would say OpenVZ or KVM. Xen is nice, but you have to watch which host your are using.

---

### Post by Nburnes on 2009-08-19
I prefer VirtualBox.

---

### Post by mpsii on 2009-08-19
VMWare Player for testing ISO and such.

VirtualBox for persistent virtual environments on a desktop.

Citrix XenServer 5.5 is AWESOME for server environments. Management console is a windows msi file, but it installed and functioned just fine in the latest wine.

---

### Post by jocampo on 2009-08-19
Virtualization software is like colors :-) ... each person has its own preference and experience usually depends of your guest choice and selected host's hardware ...

I've tested VMware and VirtualBox, using Windows and Linux as guest. From both, I think VirtualBox is the best. Why? easy to use and good performance. I think VMware learning curve is a bit higher at least for me and if you want to run one machine or a small lab, it uses more machine resources. One thing is missing from VirtualBox is built in support for Clusters. If you want to setup a Windows or MS-SQL cluster on VirtualBox is a real pain...you need to tweak and play a bit the the virtual disks.

GO for VirtualBox, you won't regret it :-)

---

### Post by A_M_S on 2009-08-20
Tnx for the input guys!

---

### Post by fishy6969 on 2009-08-21
I'd second that re openvz and KVM. There's a debian based bare metal installer - proxmox VE, that combines the two.

---

### Post by ad_267 on 2009-08-21
I'd recommend using VirtualBox 3.0 from the VirtualBox website rather than the version from the Ubuntu repositories. There were a few new features in 3.0 including support for OpenGL.

---

### Post by jkzubu on 2009-08-21
Thank you for this post.  Is KVM only for servers or will it run on a desktop (AMD+Virtual)?

---

### Post by bodhi.zazen on 2009-08-21
KVM will run on desktops.

You should probably start a new thread if you are having a problem with it.

---

