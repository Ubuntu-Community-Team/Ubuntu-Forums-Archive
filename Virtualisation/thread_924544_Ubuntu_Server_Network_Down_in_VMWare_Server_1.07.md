---
title: "Ubuntu Server Network Down in VMWare Server 1.07"
date: 2008-09-19
forum: Virtualisation
---

### Post by jbhagan on 2008-09-19
I downloaded a VMWare appliance - Ubuntu 8.04 Server JeOS and configured it to my needs using VMWare Player 2.0.3. Loving it and all is good :) Then I moved it to a VMWare Server 1.0.7 host for production and I do not have network access.

In Player "ifconfig" shows eth1 and lo. In Server ifconfig shows lo only.  In both Player and Server "lspci" does show "Ethernet controller: Advanced Micro Devices...."

When I started the guest in VMWare Server I did select that I "copied" the files as opposed to moving them.

I'm using bridged networking in both. What am I missing? :confused:

Thanks!

---

### Post by jbhagan on 2008-09-19
I resolved the problem by re-copying guest OS files... wish I had tried that hours ago!!!

I now have eth1 and lo functioning on Ubuntu 8.04 as a guest OS in VMWare Server.

---

