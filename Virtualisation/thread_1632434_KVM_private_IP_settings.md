---
title: "KVM private IP settings"
date: 2010-11-28
forum: Virtualisation
---

### Post by andrewn2010 on 2010-11-28
I am attempting to setup 2 VMs with a private ip similar to VMWare "Host Only" network card as a secondary network adapter while the primary one connects through a bridge.

I am not sure how to set up my interfaces file...can someone help out?  I want to use the virt-manager to add an additional network card for the private IP but it just keeps adding it into the bridged card.
```

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
allow-hotplug br0
iface br0 inet static
         address 192.168.1.15
         netmask 255.255.255.0
         gateway 192.168.1.1
         bridge_ports eth0
         bridge_stp off
         bridge_maxwait 15

```

---

### Post by gdahlm on 2010-11-28
Configure a bridge interface that does not use a source network card.

e.g. remove the "bridge_ports eth0"

---

