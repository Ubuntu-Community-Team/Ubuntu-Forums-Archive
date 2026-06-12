---
title: "Ubuntu 16.04 Server Networking"
date: 2017-12-15
forum: Server Platforms
---

### Post by prashant154 on 2017-12-15
Hi,
I am looking for to ip address automatically (dhcp) set on my ubuntu server without modifying /etc/network/interfaces.
Is there any way to achieve this? Do i need to make any changes in dhcp server also?

Thanks in advance

Regards,
Prashant M Bhushan

---

### Post by slickymaster on 2017-12-15
Thread moved to **Server Platforms** for a better fit

---

### Post by powersj on 2017-12-15
> **prashant154 said:**
> Hi,
I am looking for to ip address automatically (dhcp) set on my ubuntu server without modifying /etc/network/interfaces.


What release of Ubuntu are you running (e.g. `cat /etc/os-release`)?

If it is Artful are newer you can use netplan configuration, otherwise you might be able to put something in /etc/network/interfaces.d/. You could also run `dhclient eth0 -v` and replace eth0 with the name of whatever interface you would like, on the command line to get a DHCP address.

---

### Post by prashant154 on 2017-12-18
> **powersj said:**
> What release of Ubuntu are you running (e.g. `cat /etc/os-release`)?

If it is Artful are newer you can use netplan configuration, otherwise you might be able to put something in /etc/network/interfaces.d/. You could also run `dhclient eth0 -v` and replace eth0 with the name of whatever interface you would like, on the command line to get a DHCP address.

Its 16.04 server. i don't want to modify /etc/network/interfaces manually.
Depending on the no of NICs attached to ubuntu VM, /etc/network/interfaces should get populated accordingly for dhcp.

For e.g. if my ubuntu VM has 1 nic. /etc/network/interfaces should have below entry added automatically,

auto eth0
iface eth0 inet dhcp

If VM has 2 NICs attached, /etc/network/interfaces should have below entry added automatically,

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


Thank You,
Prashant

---

### Post by QIII on 2017-12-18
Just to be clear:  is the Ubuntu server running in a VM?  This seems to be implied by your last post.

---

### Post by prashant154 on 2017-12-18
> **QIII said:**
> Just to be clear:  is the Ubuntu server running in a VM?  This seems to be implied by your last post.

Yes, its Ubuntu server VM running on VMware hypervisor.

---

