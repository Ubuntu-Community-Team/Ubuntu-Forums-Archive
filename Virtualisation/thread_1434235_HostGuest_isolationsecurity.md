---
title: "Host/Guest isolation/security?"
date: 2010-03-20
forum: Virtualisation
---

### Post by memilanuk on 2010-03-20
Hello,

This might be a semi-silly question, but I'll ask anyway ;)

If I put together a physical machine with two ethernet cards, and load Ubuntu as the base operation system running something like KVM as the hypervisor, and set up a variety of virtual machines inside that (virtual router bridged over the eth0 interface to the ISP, connecting to an internal virtual network that has other VMs providing services, and then another router/firewall bridged between the internal virtual network and eth1 which connects to the rest of my 'physical' LAN... 

1) How 'vulnerable' is my base operating system?  In theory only the virtual router/firewall is presented to the outside world, but the physical interface is present also - would someone be able to hack in on eth0 to the underlying base operating system?

2) How would I be able to administer that base OS?  Would it be like a bridged interface in VirtualBox where the host OS gets one IP for the interface and the 'guest' OS gets another one - both on the same physical interface?

Thanks,

Monte

---

### Post by dcstar on 2010-03-21
> **memilanuk said:**
> Hello,

This might be a semi-silly question, but I'll ask anyway ;)

If I put together a physical machine with two ethernet cards, and load Ubuntu as the base operation system running something like KVM as the hypervisor, and set up a variety of virtual machines inside that (virtual router bridged over the eth0 interface to the ISP, connecting to an internal virtual network that has other VMs providing services, and then another router/firewall bridged between the internal virtual network and eth1 which connects to the rest of my 'physical' LAN... 

1) How 'vulnerable' is my base operating system?  In theory only the virtual router/firewall is presented to the outside world, but the physical interface is present also - would someone be able to hack in on eth0 to the underlying base operating system?

2) How would I be able to administer that base OS?  Would it be like a bridged interface in VirtualBox where the host OS gets one IP for the interface and the 'guest' OS gets another one - both on the same physical interface?


Physical Ethernet interfaces can have multiple IP addresses, what uses those addresses - VM or "real" hardware - is irrelevant.

VMs can use the host interface either with direct bridging (using VM IP addresses, single or multiple) or using the Host IP address via NAT - it's up to you.

You can have an Ethernet interface with no host IP protocol if you like, just IP addresses on the VMs that bridge to it.

---

