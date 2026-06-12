---
title: "Ubuntu Server 16.04 LTS 64Bit with Chelsio T3 10gbe NIC"
date: 2018-08-09
forum: Server Platforms
---

### Post by mcapaldo on 2018-08-09
I have a new build running Ubuntu Server 16.04 64 Bit using Samba and mdadm for 3x6td sata6 drives.  I installed a Chelsio T3 dual port 10GB  Nic.  I see that when it is booting it sees the card and the CXGB3 name it renames it from eth0.  I already have a Dell 6424 Switch with 24 10/100/1000 and 4 10GB ports.  I added that to /etc/network/interfaces and a static ip address also, did a stop and restart of networking, but restart failed until I commented my chnanges out.  I used "sudo etc/init.d/networking stop" and "sudo etc/init.d/networking RESTART".  I tried IFUP CXGB3 and IFUP eth0 and no luck.  So I am guessing the drivers are not loaded.  Where to I find the drivers and how do I load them?  I can across using s a HWE kernel.  Hardware Enablement Kernel  To install I might use....  sudo apt-get install --install-recommends linux-generic-hwe-16.04   Is this a BAD idea?  At any rate I plan to make an ISO of the boot ssd before I start anything.  I tried to install 18 LTS and it choked after seeing both the 10GB and the 1GB Nic.  Somewhere after drive partitioning.  So I used 16.04 and it installed fine.

---

