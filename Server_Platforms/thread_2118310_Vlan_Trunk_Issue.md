---
title: "Vlan Trunk Issue"
date: 2013-02-20
forum: Server Platforms
---

### Post by rsaSean on 2013-02-20
So here is my situation:

I have 2 nics on a server (Ubuntu 12.04 Server)
[LIST]
[*]eth0 - has 2 vlans trunked to it (lets say vlan 15 and 16)
[*]eth1 - no vlans truncked, standard active port
[/LIST]

Here are the steps I followed:
```
sudo apt-get install vlan

sudo modprobe 8021q

sudo vconfig add eth0.15

sudo vconfig add eth0.16

sudo ip addr add 192.168.1.100 dev eth0.16

sudo ip addr add 192.168.5.100 dev eth0.15
```

I then appended '8021q' to the /etc/modules file and modified the interfaces file.

Here is my interfaces file:
```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0.16
iface eth0.16 inet static
	address 192.168.1.100
	netmask 255.255.255.0
	gateway	192.168.1.1
	dns-search domain.com
	dns-nameservers 192.168.1.2
#	vlan-raw-device eth0
	
auto eth0.15
iface eth0.15 inet static
	address 192.168.5.100
	netmask 255.255.255.0
#        vlan-raw-device eth0

auto eth1
iface eth1 inet static
	address 192.168.10.100
	netmask 255.255.255.0

```
On boot all interfaces come up, however I can only contact resources on 192.168.10.100 and 192.168.5.100 network. When I run tcpdump on eth0 I can see arps from the missing network segment on vlan 16. 

After some searching I found a similar issue in RHEL with intel based cards, the fix was to perfrom the following ethtool command.

```
sudo ethtool -K eth0 rxvlan off

sudo ethtool -K eth0 txvlan off

```
txvlan off works fine, rxvlan off returns: "Cannot set device flag settings: Operation not supported"

When I perform an ifconfig eth0, there are no RX packets...

:confused: Any ideas ??? I am stumped ](*,)

---

### Post by rsaSean on 2013-02-25
Bump...

FYI... This is a broadcom NetExtreme II Nic

---

