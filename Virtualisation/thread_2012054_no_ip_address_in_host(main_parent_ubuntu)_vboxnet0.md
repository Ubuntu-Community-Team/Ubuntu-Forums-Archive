---
title: "no ip address in host(main parent ubuntu) vboxnet0 available"
date: 2012-06-28
forum: Virtualisation
---

### Post by vikkyhacks on 2012-06-28
I was using vmware for a while but now had to move to virtualbox ..... After installing I clearly have ip address inside the Virtual XP I installed but there is no IP address for vboxnet interface on main parent
parent(or maybe host) --> Ubuntu
guest (virtual os) --> XP SP3

here is the display of my ip add on ubuntu


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host 
valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
link/ether 00:19:21:05:6a:b6 brd ff:ff:ff:ff:ff:ff
3: vmnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
link/ether 00:50:56:c0:00:01 brd ff:ff:ff:ff:ff:ff
inet 172.16.187.1/24 brd 172.16.187.255 scope global vmnet1
inet6 fe80::250:56ff:fec0:1/64 scope link 
valid_lft forever preferred_lft forever
4: vmnet8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
link/ether 00:50:56:c0:00:08 brd ff:ff:ff:ff:ff:ff
inet 172.16.198.1/24 brd 172.16.198.255 scope global vmnet8
inet6 fe80::250:56ff:fec0:8/64 scope link 
valid_lft forever preferred_lft forever
5: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
6: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
link/ether de:84:18:1b:b9:a8 brd ff:ff:ff:ff:ff:ff
inet 192.168.42.242/24 brd 192.168.42.255 scope global usb0
inet6 fe80::dc84:18ff:fe1b:b9a8/64 scope link 
valid_lft forever preferred_lft forever

---

