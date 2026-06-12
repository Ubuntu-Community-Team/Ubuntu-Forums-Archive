---
title: "VMWare and access to host external hard disk"
date: 2011-01-02
forum: Virtualisation
---

### Post by wwynn on 2011-01-02
Ubuntu 9.10 64-bit host, VMWare Workstation 7.1.3, Windows 7 Ultimate 64-bit guest:

The external hard drive is in a dock that can be connected by eSata or USB. When the drive is connected by eSata and I try to add the drive in VMWare settings for the Win7 virtual machine, I get an error message that access is denied. Running VMWare as root solves the problem. If the drive is connected to the host by USB, there is no problem.

On the VMWare site, it was also suggested that making my user ID a member of the disk group would also work. It does not.

Is there any more to this issue? That is, is there a way to access a physical hard disk on the host without such special rights? It seems strange to me that USB is easily connected but an extra hard disk is not.

---

### Post by wwynn on 2011-01-03
Short answer: yes, there is more, but the issue is related to hardware and firmware rather than VMWare or Linux.

eSata has the  rights issue when the connection is through the onboard external  controller of the ASUS M4A79T Deluxe. eSata has no issues when  the connection is through a RocketRAID 2314 (4 ports, external only).

Further, when I put two drives in the VanTec NexStart  dual drive dock BOTH drives are recognized without issues. These were hot-swapped in while the system was running.

---

