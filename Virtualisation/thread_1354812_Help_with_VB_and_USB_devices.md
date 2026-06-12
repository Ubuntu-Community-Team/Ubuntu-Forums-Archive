---
title: "Help with VB and USB devices"
date: 2009-12-14
forum: Virtualisation
---

### Post by bdws1975 on 2009-12-14
Hi all,

I've installed VB and am running windows xp on it.  It works great and no problems, except...

I can't seem to figure out how to access my thumbdrive in VB.  i have some files I need to put in the VB and can't get the thumbdrive to mount.

Thanks for your help,

Brett

---

### Post by fouadatmeh on 2009-12-15
Hello,

I found on another forum that running VirtualBox as root solved the problem:
Quote:
[http://www.linuxquestions.org/questi...ne-fc7-586575/](http://www.linuxquestions.org/questi...ne-fc7-586575/)

This is not a good solution to run as root, but if it works, it will be a step in the right direction..

Hope that helps

---

### Post by chipper_farley on 2009-12-15
Another option is to create a shared folder for the virtual machine.  You can do that either in the setup of the machine in order to make it permanent or do it while the machine is running.  The shared folders appear as network shares from within the guest.  My experience has been that navigating to them within the Network Neighborhood (if Windows) is pretty slow but once you're there, you can copy the files no problem.

---

### Post by bdws1975 on 2009-12-16
Thanks guys.  I decided to create a shared folder on my host and the create a network drive on my guest.  It works perfect and makes backup easier as I only have to set the backup for my host.

Thanks again!
Brett

---

