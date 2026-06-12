---
title: "Why LVM with mdadm?"
date: 2010-04-02
forum: Server Platforms
---

### Post by babooka on 2010-04-02
I'm setting up a DIY NAS system, running Ubuntu server from a CF and using 2 SATA drives.

I only need RAID1. so that should do.

Setting up RAID1 with mdadm is straightforward, and all of my tests with failure/recover scenario work fine in VirtualBox.


Most of the tutorials on the net are talking about using mdadm in conjunction with LVM2.

What is the reasoning behind LVM2 over mdadm?

---

### Post by HermanAB on 2010-04-03
If you want to grow the system, then you can add more disks transparently.

---

### Post by richardjh on 2010-04-06
LVM is not a requirement but allows you to later change the layout of the partitions.

You can shrink /home for example to make extra room on /var in the event that you are running low on space.

It is likely that you will never use the functionality of LVM but given that it is so easy to set up most guides include it anyway.

---

