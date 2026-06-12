---
title: "Windows problems"
date: 2008-08-24
forum: Virtualisation
---

### Post by Living2007 on 2008-08-24
Yes.. I have a windows problems on VMs

One of my problems co-existes with Windows 98. I would like to know where to download the driver for a Intel 82545EM Gigabit Ethernet Controller (Copper)

And also, I have an .iso image of Windows 3.1 and it is not loading into my VM, (it is also picking up a 2nd IDE drive (1:1) This is a virtual CD drive) Windows 3.1 CD is problaly loaded into this.

---

### Post by Thelasko on 2008-08-26
You left out a critical piece of information.  What virtualization software are you using? 

[VirtualBox doesn't support 3.1]("http://www.virtualbox.org/wiki/Guest_OSes")

[VMWare Player]("http://www.vmware.com/pdf/vmware_player200.pdf") should work, page 16.

---

### Post by Living2007 on 2008-08-26
I figured out the problem with 3.1, I was using "PC User Virtual Machine Shop Lite 2", floppy drive wasn't avaliable, so i used "PC User Virtual Machine Shop Lite" and Floppy drive was avaliable, so  ticked it and i'm now able to install MS-DOS 6.22 (then 3.11 for Workgroups)

---

