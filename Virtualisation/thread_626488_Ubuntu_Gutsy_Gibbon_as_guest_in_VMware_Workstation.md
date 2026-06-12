---
title: "Ubuntu Gutsy Gibbon as guest in VMware Workstation"
date: 2007-11-29
forum: Virtualisation
---

### Post by 4integration on 2007-11-29
I am trying to install Ubuntu Gutsy Gibbon as guest OS in VMware Workstation 5.5.0.

Have allocated 30 GB disk, splitted in 2 GB files and have 1 GB RAM configured (2 GB in the host).

When starting the installation (using a mounted x86 alternate ISO image) the interface is very slow but it makes through the installation, when done I unmount the ISO and it reboots.
When the Ubuntu logo appears it freezes almost directly and it's not possible to proceed.

I would really need to have this working on my work PC. (at home there are Ubuntu-only :) )

Do you have any idea?

EDIT: the host is Windows XP Pro SP2

---

### Post by lmcfadden on 2007-12-01
> **4integration said:**
> I am trying to install Ubuntu Gutsy Gibbon as guest OS in VMware Workstation 5.5.0.
Do you have any idea?

EDIT: the host is Windows XP Pro SP2

Although I do not have VMWare Workstation, I am using the latest free version of VMWare Server, running on XP Home with Gutsy running in a VM.  I had a few challenges getting it installed, and they seemed to be around the display options. 

I am not sure if it is due to my dual monitors, or what, but I would not get a good install past the Ubuntu screen unless I chose Safe Graphics mode (or whatever) before booting.  However this was only during the Live CD boot and install, after installed it seemed to run fine with my setup.  I had to run it at 1024x768 to get it to work well, have not tried other resolutions in a while.

System specs :
XP Home SP2 Host 2gb - 40 gd C 250 gd D
VMWare Server 1.0.4 build-56528
Ubuntu 7.10 Gutsy Gibbon (latest update) in a 512mb 16gbvhd VM

---

