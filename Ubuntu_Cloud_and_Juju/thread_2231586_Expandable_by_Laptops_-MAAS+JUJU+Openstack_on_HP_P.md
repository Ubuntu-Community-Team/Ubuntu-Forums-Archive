---
title: "Expandable by Laptops -MAAS+JUJU+Openstack on HP Proliant dl180 G6 -"
date: 2014-06-26
forum: Ubuntu Cloud and Juju
---

### Post by m-momr on 2014-06-26
Hello.

**About me:**
I am a 25 year old from Norway.
Have used linux on a hobby basis over the past 9 years, so i like to think i know the basics :P

**Intro:**
Im going to start my private cloud, starting with a HP proliant dl180 G6(already ordered).
And my idea is to expand the cloud with cheap used laptops (as openstack computing nodes for openstack)

**Specs:**
Processors: 	2x Intel Xeon L5630 Quad Core 2.13 GHz (12 MB Cache, Intel-VT)
Memory: 	24 GB RAM (PC3-10600R modules installed)
Hard disks: 	2x 146 GB SAS hot swap 2.5" hard disks, 10.000 rpm (25 hard disks possible)
Hard disk:         10x WD BLACK 2.5" 750GB 7200RPM SATA/600 16MB
Uplink: 75/75 fiber, (400/400 available, 1000/1000 coming in the future)
Network: Netgear GS724TP 24-Port Gigabit Smart Switch and PoE


**Build idea:**
0. Setup 2x146 gb SAS in raid 1 for OS and vm's running the core (I define the core as the complete system on a server, where laptops would be the expansion from the core)
0. Setup 10x750gb S-ATA in raid 10, for speed and safty, this will be storage for all openstack deployed machines.
1. Install ubuntu on the server
2. using libvirt, launtch a VM to be the new MAAS-server
3. installing all components (juju nodes) as vm's on the server (MAAS, juju, openstack-setup)
4. Expand by adding laptop nodes, (PXEbooting laptops, or Intel AMT if the laptop supports it)

**Why laptops?**
Laptops are great. They are cheap used, and even cheaper if the screen is broken.
They also got built-in UPS, are stackable and don't use much power.

All feedback, suggestions and insights will be appreciated :)

---

