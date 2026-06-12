---
title: "VMware virtual networks"
date: 2009-03-22
forum: Virtualisation
---

### Post by tebbens on 2009-03-22
I'm working with vmware and 2 guests.
One guest is XPsp3 and the other Ubuntu 8.10

I'd like to have a virtual private network where
XP uses Ubuntu as the gateway, so I can monitor and log
all the network activity coming from the XP guest.

Can someone help me out on how to configure this in VMware
and the guest systems ?

Thanks!

---

### Post by Dedoimedo on 2009-03-22
The virtual machines are computers for all practical purposes.
You need forwarding enabled on the ubuntu guest and possibly firewall forwarding rules. The XP guests need to use the ubuntu as their gateway and dns.
Dedoimedo

---

### Post by veloce on 2009-03-23
> **tebbens said:**
> I'm working with vmware and 2 guests.
One guest is XPsp3 and the other Ubuntu 8.10

I'd like to have a virtual private network where
XP uses Ubuntu as the gateway, so I can monitor and log
all the network activity coming from the XP guest.

Can someone help me out on how to configure this in VMware
and the guest systems ?

Thanks!

Do you really mean a vpn or do you just want the vms on a separate subnet?

I used to have all by vms on the host-only virtual network and a virtual firewall to connect them to the host's network.  I actually used IPCop as the firewall because it used so little in the way of resources.

In this sort of setup, all the vms (except the firewall) have a virtual network card connected to the host only network.

The firewall has two virtual network cards, one connected to the host only network and the other bridged network.

The only trap was to turn off vmware's DHCP server on the host only network so that the firewall could provide all the right settings along with the ip address.

---

