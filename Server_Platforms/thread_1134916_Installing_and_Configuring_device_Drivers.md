---
title: "Installing and Configuring device Drivers"
date: 2009-04-24
forum: Server Platforms
---

### Post by joselee on 2009-04-24
I had successfully installed Ubuntu server 8.10 on Dell PowerEdge 2850, just this morning the server stoped, I have moved the hard disck to dell poweredge 1850, NIC is not detected, how can I install the nic

---

### Post by Yashiro on 2009-04-24
[http://kmuto.jp/debian/hcl/DELL/PowerEdge+1850](http://kmuto.jp/debian/hcl/DELL/PowerEdge+1850)
[http://hardware4linux.info/modules/](http://hardware4linux.info/modules/)

The module controlling the ethernet ports is e1000.
So try *sudo modprobe e1000*

You may need to do alot more work if you previously had alot of things configured for a different machine.

---

