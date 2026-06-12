---
title: "kvm firewall"
date: 2010-03-29
forum: Virtualisation
---

### Post by cmug on 2010-03-29
Hi,

I have a VLAN capable switch. I am thinking about creating a kvm firewall and use vlan's to segregate the network traffic inside LAN and between firewall - ADSL modem.

What is the board's suggestion how should I do this, should I bring the VLAN all the way to the virtual host or leave it on the kvm host?

I am a bit new to KVM, so not sure about all the capabilities with kvm nic's.

I have one physical network interface on the kvm host, that would be used as a vlan trunk, and the switch then puts the packets either to WAN or LAN

Responses welcome

---

### Post by cmug on 2010-03-30
To give more info,

I am running a fresh install of Ubuntu 9.10 on a i5 650 CPU with 4GB memory.

Here is my /etc/network/interfaces on the kvm server:
```


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
address 192.168.0.2
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.254
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0

auto br1.100
iface br1.100 inet static
address 10.200.0.100
network 10.200.0.0
netmask 255.255.255.0
gateway 10.200.0.1
bridge_ports eth0.100
bridge_stp off
bridge_fd 0
bridge_maxwait 0

auto br1.200
iface br1.200 inet static
address 192.168.0.4
network 192.168.0.0
netmask 255.255.255.0
gateway 192.168.0.254
bridge_ports eth0.200
bridge_stp off
bridge_fd 0
bridge_maxwait 0

```This would try to indicate that br1.100 is the bridged interface that goes to the ADSL via eth0.200 which is a VLAN interface, and br1.200 is the interface with VLAN 200 tagged that goes to local network. Let me know if this is incorrect?

The VLAN interfaces were created with commands:
```
vconfig add eth0 100
vconfig add eth0 200
```I will do some testing on the actual VLAN setup itself tomorrow to make sure it works properly.

---

