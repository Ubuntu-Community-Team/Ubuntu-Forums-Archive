---
title: "ubuntu server 13.04 empty /etc/udev/rules.d/70-persistent-net.rules"
date: 2013-05-23
forum: Server Platforms
---

### Post by gillecaluim on 2013-05-23
When installing ubuntu server 13.04 and got to network setup, the installer gave me options of iface p9p1 and p10p1 rather than the usual eth0, eth1. I picked one and proceeded onwards without difficulty thinking that I could change the names afterwards in the 70-persistent-net.rules file.   But that file is completely empty???  Every version of ubuntu I've worked with prior has this file populated with network macaddr, names, etc.
so where are the names defined now?

---

### Post by Hadaka on 2013-05-23
Hi, a simple re-boot should generate the file.
if not ..then do..
```
sudo udevadm trigger --action=add
```
to view..
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Server Platforms**.*

---

### Post by gillecaluim on 2013-05-23
> **Hadaka said:**
> Hi, a simple re-boot should generate the file.
if not ..then do..
```
sudo udevadm trigger --action=add
```
to view..
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

neither of those suggestions work...other ideas

---

