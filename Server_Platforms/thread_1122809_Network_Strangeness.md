---
title: "Network Strangeness"
date: 2009-04-11
forum: Server Platforms
---

### Post by drave on 2009-04-11
after installation the /etc/network/interfaces contains statements only for lo but ifconfig shows eth1 as well.
if i explicitly put an "iface eth0 inet dhcp" in there it is ignored and eth1 is still brought up.
if i "ifdown eth1" then it tells me that eth1 is not configured.<br>
if i "/etc/init.d/networking stop"  it doesnt

whats going on with this

dave

---

### Post by FrankT-Qc on 2009-04-11
could you post the output of 

```
ip address show
```

About/etc/network/interfaces, if you want eth1 to come up automatically, you want to have a line like "auto eth1" before you declare your configurations...

example :

```

#... other stuff. like lo

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.168.111.1
	netmask 255.255.255.0

#... other stuff. like wlan0 ...

```

---

### Post by drave on 2009-04-11
ip address show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 08:00:27:5b:e7:67 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global eth1
    inet6 fe80::a00:27ff:fe5b:e767/64 scope link 
       valid_lft forever preferred_lft forever


cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


sudo ifdown eth1
ifdown: interface eth1 not configured

---

