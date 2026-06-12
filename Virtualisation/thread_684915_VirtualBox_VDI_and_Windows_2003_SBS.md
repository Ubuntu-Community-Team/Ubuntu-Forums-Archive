---
title: "VirtualBox VDI and Windows 2003 SBS"
date: 2008-02-01
forum: Virtualisation
---

### Post by mikes27 on 2008-02-01
I'm running Windows SBS 2003 on Ubuntu 7.04 using VirtualBox.  I would backup a running vdi file using rsync.  It seems to work.  I created a new Ubuntu box with VirtualBox installed and tried to run a copy of the rsync'ed vdi file.  The Vitrual Machine starts but I get errors with my services specifically (TCP/IP Services Application, which caused the DHCP server not too start) and I've been unable to repair them.  My question is, what is the most effective way to backup a running virtual machine?  My theory is that since a running Virtual machine constantly changes the vdi file there has to be some shadow copying of the vdi file in order to back it up.  Does anyone have any suggestions?

---

