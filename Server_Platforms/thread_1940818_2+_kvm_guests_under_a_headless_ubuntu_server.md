---
title: "2+ kvm guests under a headless ubuntu server"
date: 2012-03-14
forum: Server Platforms
---

### Post by supermario87 on 2012-03-14
Hi, i would submit to you my project of a home server setup.


HP MICROSERVER -> 8GB RAM +  3 different GIGABIT NICs + 2TB of storage + 40GB SSD for base system.

My idea is this: in KVM set up 2+ different guests, one with IPCOP(or a similar firewall distro) and some other guest(ATM just for educational purposes) that can comunicate each other in a virtual lan. 

In this case:
1) all traffic from and to WAN must go trough firewall distro.
2) firewall distro must collet all the traffic trough LAN side and have routing functionalities(e.g. DHCP, ip forwarding etc etc.)
3) LAN side can see another guest VM on the server an comunicate with it(e.g. a winx xp guest with uTorrent: LAN clients can access the web interface or a VNC server on it).
4) third NIC can be used to manage de ubuntu server.

I need some tips to set up the virtual machines in KVM, create the virtual switch and make sure that all this stuff auto starts on system boot!

thanks for any help!

p.s. i've attached a logical sketch

---

### Post by cj13579 on 2012-03-15
This is a great step-by-step guide for setting up KVM in Ubuntu: [http://www.havetheknowhow.com/Configure-the-server/Configure-KVM.html](http://www.havetheknowhow.com/Configure-the-server/Configure-KVM.html)

---

### Post by rubylaser on 2012-03-15
Another is to use [Proxmox VE]("http://pve.proxmox.com/wiki/Main_Page") and use the simple web interface to setup and manage your virtual machines.

---

### Post by supermario87 on 2012-03-17
> **rubylaser said:**
> Another is to use [Proxmox VE]("http://pve.proxmox.com/wiki/Main_Page") and use the simple web interface to setup and manage your virtual machines.

ATM i would prefere not to use solutions like that(i mean also vmware esxi or similar)

> **cj13579 said:**
> This is a great step-by-step guide for setting up KVM in Ubuntu: [http://www.havetheknowhow.com/Configure-the-server/Configure-KVM.html](http://www.havetheknowhow.com/Configure-the-server/Configure-KVM.html)

yeah nice tut for ubuntu guests! also, i manage to build some guest and VNC into them.

now i would improve the networking part but i cant find any tutorial or guide on the web

i've tried this guide and it just works fine(with some changes)

[IPCOP UNDER VBOX HEADLESS]("http://greenpossum.awardspace.com/ipcop-in-vbox.html")

any chance to convert this setup in KVM?

---

### Post by rubylaser on 2012-03-17
Proxmox isn't Vmware.  It's based on Debian and supports KVM and OpenVZ with a nice web interface that makes setting up virtual switches like you're trying to do very easy.  If you want to do it all by hand, feel free :)

Yes, you could do this with KVM. Here's how to set up [Proxmox (KVM) with pfsense]("http://forum.proxmox.com/threads/2020-Proxmox-Pfsense-working-setup-solved-2-NIC").  This would be the same way you'd setup ipcop.

---

### Post by supermario87 on 2012-03-18
> **rubylaser said:**
> Proxmox isn't Vmware.  It's based on Debian and supports KVM and OpenVZ with a nice web interface that makes setting up virtual switches like you're trying to do very easy.  If you want to do it all by hand, feel free :)

Yes, you could do this with KVM. Here's how to set up [Proxmox (KVM) with pfsense]("http://forum.proxmox.com/threads/2020-Proxmox-Pfsense-working-setup-solved-2-NIC").  This would be the same way you'd setup ipcop.

You've convinced me!

I'll give it a try, but the boring thing is that i dont want to convert my two ext4 data HD to  NFS or similar setup, as required by vmware or other "hypervisor" distros.
The main reason is simple: i dont have transitional space :D 
The second main reason is: if i've to transfer some data to other PCs on the fly is impossible!

---

### Post by rubylaser on 2012-03-18
The good news is that anything you can do with Debian/Ubuntu, you can do with Proxmox.  It's just Debian underneath and works just like you'd expect.

---

