---
title: "network setting on guess os"
date: 2008-08-30
forum: Virtualisation
---

### Post by lime4x4 on 2008-08-30
here is a copy of my /network/interfaces.What settings do i use in the guest os which is xp i created a bridge network


auto br0
iface br0 inet static
address 192.168.1.109
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
bridge_ports eth1

---

