---
title: "Install server 16.04 ubuntu-desktop on ESXi 5.5 U1"
date: 2018-08-23
forum: Server Platforms
---

### Post by dhlao on 2018-08-23
Need to confirm can Ubuntu Server 16.04 desktop can be install/run on ESXi 5.5 U1.
I encounter packages dependency issue when trying to install ubuntu-desktop.
Anyone know? Thanks.

---

### Post by darkod on 2018-08-24
1. Linux server is not used with a GUI.
2. Package dependency issue inside the OS wouldn't be related to the ESX hypervisor usually.
3. If you want ubuntu with the desktop GUI, install the Ubuntu Desktop version straight up. Why installing Ubuntu Server and then complicating by adding the desktop GUI?

But anyway, if you are adding the desktop then it is not a server...

---

