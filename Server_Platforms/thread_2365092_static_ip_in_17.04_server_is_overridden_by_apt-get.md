---
title: "static ip in 17.04 server is overridden by apt-get install lxqt"
date: 2017-07-02
forum: Server Platforms
---

### Post by ryanswan on 2017-07-02
Installed Ubuntu Server 17.04
```
edited /etc/network/interfaces

auto enp2s0
iface enp2s0 inet static
address 192.168.1.20
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.254
dns-nameservers 8.8.8.8 8.8.4.4 192.168.1.254

```
did apt-get update and dist-upgrade
rebooted. ip is still .20

apt-get install lxqt
during the install my IP changed to .230, before it was complete the IP switched

```
enp2s0: <BROADCAST,MULTICAST,DYNAMIC,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:23:54:a9:bf:d2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.230/24 brd 192.168.1.255 scope global enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::223:54ff:fea9:bfd2/64 scope link 
       valid_lft forever preferred_lft forever

```
No matter what I do, I can't force my enp2s0 to actually be STATIC nor have .20

---

### Post by wildmanne39 on 2017-07-02
*Thread moved to **Server Platforms**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

