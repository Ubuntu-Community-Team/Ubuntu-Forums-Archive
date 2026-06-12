---
title: "problems eth0"
date: 2016-02-22
forum: Server Platforms
---

### Post by Kevin_Ruiz on 2016-02-22
current setting
auto eth0
iface eth0 inet static
address 192.168.3.232
netmask 255.255.255.0
gateway 192.168.3.232



when my server Http much time unused network cards do not allow me to query internet
I can not even make apt- get update that says he has no connection with the mirror
dnd not respond to google.com


I would appreciate your help

---

### Post by Bucky Ball on 2016-02-22
*Thread moved to **Server Platforms**.*

---

### Post by chili555 on 2016-02-22
> auto eth0
iface eth0 inet static
address 192.168.3.232
netmask 255.255.255.0
gateway 192.168.3.232
First of all, the gateway cannot be the same as the ethernet interface itself. The gateway is usually the router, switch or other access point to which the ethernet cable is attached. I suspect it is something like 192.168.3.1.

Second, you will need a valid DNS nameserver here. You can select the router, 192.168.3.1 perhaps, or a public DNS nameserver. I suggest you amend your file to something like this; do not change or remove the required loopback stanza:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.232
netmask 255.255.255.0
gateway 192.168.3.1
dns-nameservers 8.8.8.8 192.168.3.1

```Of course, substitute your gateway (router or switch) if not 192.168.3.1.

Restart the interface:```
sudo ifdown eth0 && sudo ifup -v eth0
```Test:```
ping -c3 www.ubuntu.com
```If you get ping returns, you are all set.

---

