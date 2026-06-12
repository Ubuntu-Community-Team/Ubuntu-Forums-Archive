---
title: "Slow LAN Speeds"
date: 2008-08-22
forum: Server Platforms
---

### Post by chrisdeeley on 2008-08-22
I have an Ubuntu Server set up with Samba on my home office network (100mbps LAN). When I try to transfer files from the network onto my local machine, or access large files, the transfer speeds are slow. A 50mb file takes several minutes to transfer.

Is this normal? I understand that 100mbps is only theoretical and I am unlikely to achieve speeds this fast, but I can download files over the internet much faster than this. Is there a setting I need to tweak?

Thank you in advance!

---

### Post by windependence on 2008-08-22
It's probably not your OS. Could be as simple as your Nic card. Could be cabling, your switch, hub, ect. but most likely not Ubuntu. As a general rule, Unix/Linux is much better at netowrking than Windoze ever thought about.

-Tim

---

### Post by cdenley on 2008-08-22
> **windependence said:**
> It's probably not your OS. Could be as simple as your Nic card. Could be cabling, your switch, hub, ect. but most likely not Ubuntu. As a general rule, Unix/Linux is much better at netowrking than Windoze ever thought about.

-Tim

Unless you have my hardware configuration. 10x slower than windows, at least. I fixed it in gutsy by compiling the driver from linksys, but it wouldn't compile in hardy. There's a bug report for it somewhere, don't know why it hasn't been fixed yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/161778](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/161778)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159417](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159417)

---

