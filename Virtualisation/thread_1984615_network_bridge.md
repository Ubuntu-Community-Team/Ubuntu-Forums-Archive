---
title: "network bridge"
date: 2012-05-22
forum: Virtualisation
---

### Post by maya88r on 2012-05-22
Hello

this's my /etc/network/interfaces file :

```
auto eth0
iface eth0 inet static
address 99.198.100.146
network 99.198.100.144
netmask 255.255.255.248

auto eth0:0
iface eth0:0 inet static
address 99.198.100.147
network 99.198.100.144
netmask 255.255.255.248

auto eth0:1
iface eth0:1 inet static
address 99.198.100.148
network 99.198.100.144
netmask 255.255.255.248

auto eth0:2
iface eth0:2 inet static
address 99.198.100.149
network 99.198.100.144
netmask 255.255.255.248

auto eth0:3
iface eth0:3 inet static
address 99.198.100.150
network 99.198.100.144
netmask 255.255.255.248
```


-------------------------------

I use VirtualBox
[COLOR="Red"]**how can i give every vps one ip :confused:**[/COLOR]

by the way 
Gateway: 99.198.100.145
Broadcast: 99.198.100.151


and do i have to change anything in the virtual machine


Thanks for helping :-D

---

