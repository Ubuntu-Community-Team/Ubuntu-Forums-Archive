---
title: "vlan configuration"
date: 2008-06-25
forum: Server Platforms
---

### Post by ub007 on 2008-06-25
Hi,

I configured vlan on my switch.Its got 3 PCs connected to it ,but no longet able to ping the switch.One of them has got dhcp server installed.Do i have to make configuration changes in /etc/network/interfaces to get the network running.It was working fine prior to configuring the vlans...

Thanks in advance.

David

---

### Post by yogensha on 2008-06-30
Most VLAN aware switches that I've seen permit you to change which VLAN the switch's management interface are in.  The switch's management interface must be in the same VLAN as the host that you want to administer it from.

---

