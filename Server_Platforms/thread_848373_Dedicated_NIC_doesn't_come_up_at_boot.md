---
title: "Dedicated NIC doesn't come up at boot"
date: 2008-07-03
forum: Server Platforms
---

### Post by robgolding63 on 2008-07-03
Hi,

I'm running Ubuntu Server 8.04 with VMware installed - but I think the virtualization software is somewhat irrelevant to this post.

Basically I have a NIC that is used by only one VM - as it is on a separate network to the host and all other VMs. As a result, the host does not have an IP configured for this NIC.

This means that unfortunately Ubuntu does not bring the NIC online at boot time - I have to enter
```

ifconfig eth1 up

```
to bring it online, before I can access the VM remotely.

I have added this command to **/etc/init.d/rc.local**, but I am unsatisfied with this fix and I wonder if there is a way of achieving this without such a hack?

Thanks for any help,

Rob

---

### Post by cariboo on 2008-07-03
You should add eth1 to you etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

# the secondary network interface
auto eth1
iface eth1 inet dchp

```

This is from my desktop. you will probably have to set it up with a static ip. See

```
man interfaces
```

to see how to do this.

Jim

---

