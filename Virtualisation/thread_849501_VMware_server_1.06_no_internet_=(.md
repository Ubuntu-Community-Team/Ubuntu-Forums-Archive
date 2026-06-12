---
title: "VMware server 1.06 no internet =("
date: 2008-07-04
forum: Virtualisation
---

### Post by Beowulf.1000 on 2008-07-04
SOLVED !!!

I installed VMware server for Ubuntu 8.04 no problems, installed Windows XP Professional no problem. It looks like I should have internet in the vitualized WinXP environment but I do not. The Network settings in WinXP show a Local Area Connection, it is listed as "Enabled", and if I click on the icon for that LAN connection in the Network Connections it even shows thousands of bytes both sent and received, so there must be some sort of connection. But I can not get any websites with Internet Explorer, nor ping any sites (Windows Run: cmd, then e.g. ping yahoo.com). My Ubuntu system of course has full internet, through my wireless connection. (oh duh, do I need to somehow unblock my wifi 64-bit WEP encryption, is that what is blocking the virtualized Windows LAN? How can I get around this, since my laptop PC with Ubuntu and vmware is using wifi, the LAN cabled internet actually does not with with Ubuntu).

SOLUTION: in the bottom right of the VMware server console is an ethernet icon. I clicked it. Changed the default connection from "Bridged" to "NAT". Restarted the virtual machine (WinXP). Voila! Internet!

---

### Post by fjgaude on 2008-07-04
The Bridged connection works but you have to set your router or hub to recognize the IP address of the VM. With NAT the VM is given the same address as the Host, Ubuntu NIC has been given.

Glad you solved your own problem.

Enjoy the glories of virtualization!

---

