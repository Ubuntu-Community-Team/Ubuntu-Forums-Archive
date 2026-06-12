---
title: "ifconfig only showing lo"
date: 2011-10-03
forum: Server Platforms
---

### Post by Sock! on 2011-10-03
Hi guys,
Im configuring my linux box for vlans with my Cisco switch but im having some difficulty. With my interfaces config ifconfig only shows 'lo'. 
Any help would be greatly appreciated.

/etc/network/interfaces
[HTML]auto lo eth1 eth0 vlan450 vlan451
iface eth0 inet manual
iface lo inet loopback

auto eth1
iface eth1 inet static
    address 192.168.0.50
    netmask 255.255.255.0
    network 192.168.0.0
    gateway 192.168.0.3
    post-up iptables-restore < /etc/iptables.up.rules

iface vlan451 inet static
    address 10.123.123.2
    netmask 255.255.255.0
    vlan_raw_device eth1

iface vlan450 inet static
    address 10.0.1.1
    netmask 255.255.255.0
    vlan_raw_device eth1[/HTML]

---

### Post by Sock! on 2011-10-03
> **zackwasa said:**
> check the kernel logs and ensure that the eth1 NIC is actually detected and running

I found out that if a remove auto eth1 from line 5 everything comes up in ifconfig except eth0. Any ideas?

---

### Post by [S|G] on 2011-10-03
What did you mean by: "iface eth0 inet manual"? The manual method will NOT bring your interface up when the network scripts run. Didn't you actually wanted to use "iface eth0 inet dhcp" ?

---

