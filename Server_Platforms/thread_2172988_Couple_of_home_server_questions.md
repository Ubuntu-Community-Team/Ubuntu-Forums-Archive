---
title: "Couple of home server questions"
date: 2013-09-07
forum: Server Platforms
---

### Post by dave-6 on 2013-09-07
I know this gets asked again and again, I am searching but there is a lot to go through.

I am aiming to build a home HTPC/File-media Server.  It's built around an AMD Trinity APU that supports virtualization, 160 Gb HDD for OS and a storage drive.  Running just PS3MediaServer right now.

Want to build it around Ubuntu, using 12.04 right now.  XBMC up front, and VM's running LAMP/PS3MediaServer/Samba possibly administered via WebMin.  I know I'm doing things twice and overkilling a lot of stuff, however my goal is as much to learn about the technology as it is provide the server.  If it fails it's just media on the drive, critical files will be backed up elsewhere.

Been reading Ubuntu Docs, guides like this [http://www.havetheknowhow.com/](http://www.havetheknowhow.com/) and this [http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/).

I'd consider myself something of an advanced beginner, comfortable in the console but not by any means a power user.

My Questions:

[B]Which virtualization technology?
[/B]

[LIST]
[*]Some guides say KVM, others Xen, others Virtual Box.  Buddy who does Remote Desktops and Virtualization for a living says ESX (Not familliar).  With a goal of learning how to use VM's as much as end result, it's difficult to decide based on this produces better results and that does something better.
[/LIST]

[B]Partitioning Scheme?

[/B]
[LIST]
[*]Every guide says something different.  Seeking to understand why rather than just following tutorials.  Any suggestions?
[/LIST]

Cheers.

---

### Post by dave-6 on 2013-09-07
Oh and no plans to put any of it on the Internet at the moment.

---

### Post by Bucky Ball on 2013-09-07
*Thread moved to **Server Platforms**.*

Welcome. You may have more luck here. ;)

---

### Post by sandyd on 2013-09-07
> **dave-6 said:**
> I know this gets asked again and again, I am searching but there is a lot to go through.

I am aiming to build a home HTPC/File-media Server.  It's built around an AMD Trinity APU that supports virtualization, 160 Gb HDD for OS and a storage drive.  Running just PS3MediaServer right now.

Want to build it around Ubuntu, using 12.04 right now.  XBMC up front, and VM's running LAMP/PS3MediaServer/Samba possibly administered via WebMin.  I know I'm doing things twice and overkilling a lot of stuff, however my goal is as much to learn about the technology as it is provide the server.  If it fails it's just media on the drive, critical files will be backed up elsewhere.

Been reading Ubuntu Docs, guides like this [http://www.havetheknowhow.com/](http://www.havetheknowhow.com/) and this [http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/).

I'd consider myself something of an advanced beginner, comfortable in the console but not by any means a power user.

My Questions:

[B]Which virtualization technology?
[/B]

[LIST]
[*]Some guides say KVM, others Xen, others Virtual Box.  Buddy who does Remote Desktops and Virtualization for a living says ESX (Not familliar).  With a goal of learning how to use VM's as much as end result, it's difficult to decide based on this produces better results and that does something better.
[/LIST]
[B]If your looking for open source, dont go for XenServer or ESX/i
If your looking for something that can be administrated without touching the command line, look for proxmox (supports kvm/openvz)
If you install debian first, then proxmox, you can do custom partitioning (i.e. raid, .etc .etc), Proxmox sets up LVM by default
If your looking to just install it in ubuntu, I say check out KVM/Xen as OpenVZ requires a patched kernel
virt-manager is a nice app that can be used to graphically manage KVM VMs
[/B]
[B]Partitioning Scheme?

[/B]
[LIST]
[*]Every guide says something different.  Seeking to understand why rather than just following tutorials.  Any suggestions?
[/LIST]
**lvm - its flexible, you can online resize partitions when needed, and you can easily add more disks on the fly**
Cheers.
.

---

### Post by Kevin_Arnold on 2013-09-07
I can't answer most of your questions as I've never used XMBC but I can tell you what ESX is. It is the hypervisor from VMWare and is used in lots of commercial installations. ESXi is free to download but you install it straight on the hardware, not inside a linux distro.

In this case, it doesn't sound like that is what you want.

---

### Post by trundlenut on 2013-09-07
I found VirtualBox was easy to get up and running on the desktop version of 12.04, and I found it very useful in terms of being a beginner at virualisation.

@Sandyd, I hadn't come across Proxmox before and it looks interesting, I shall have to find out more.

---

### Post by nerdtron on 2013-09-08
If the server has a GUI, just install VirtualBox and XBMC. It will be easy for a beginner.
If the server has no GUI, install ubuntu-virt-server to be able to run KVM virtual machines. Now on your desktop computer install ubuntu-virt-manager to be able to manage the VMs on the server remotely.

Proxmox is good too. It has a nice web GUI but it's a full blown OS based on debian and maybe a little bit harder to setup than virt-manager or virtual box.

---

### Post by sandyd on 2013-09-08
> **nerdtron said:**
> If the server has a GUI, just install VirtualBox and XBMC. It will be easy for a beginner.
If the server has no GUI, install ubuntu-virt-server to be able to run KVM virtual machines. Now on your desktop computer install ubuntu-virt-manager to be able to manage the VMs on the server remotely.

Proxmox is good too. It has a nice web GUI but it's a full blown OS based on debian and maybe a little bit harder to setup than virt-manager or virtual box.

not a complicated setup,
just install from the cd, and thats it, unless you need to have some weird partitioning scheme

Setup VMs to bind to vmbr0 (mine is more complicated since its actually on the net, and has two vyatta firewalls....), and inside the VM, set a static IP.
You should then be able to access the VM from computers on the network using the static ip

simple

---

