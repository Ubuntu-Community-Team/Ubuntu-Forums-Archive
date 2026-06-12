---
title: "Network button monitoring wrong network card"
date: 2006-08-08
forum: Ubuntu System Panel
---

### Post by mssever on 2006-08-08
I'm not sure what's causing this problem: I have two netcards on my machine. eth0 is a wired card that I only use rarely. eth1 is a wireless card that is my main card. I set /apps/usp/network_interface to eth1 (in gconf), but the network button in USP says: ```
**Network**
Wired network
Device not configured
```
So it appears that it's trying to monitor eth0 despite the gconf setting. I don't know it it's relevant, but I've logged out and in and rebooted several times since setting the gconf key.

---

### Post by orb9220 on 2006-08-08
try ath0 for wireless it's what I had to use.

---

### Post by mssever on 2006-08-08
> **orb9220 said:**
> try ath0 for wireless it's what I had to use.

Didn't work for me. Probably because I don't have a device named ath0 on my system. ifconfig only reports eth0, eth1, and lo.

---

### Post by chanders on 2006-08-08
> **mssever said:**
> Didn't work for me. Probably because I don't have a device named ath0 on my system. ifconfig only reports eth0, eth1, and lo.

What does 'ip -o addr' give you in a terminal?

---

### Post by mssever on 2006-08-09
```
[COLOR="Gray"]~:$[/COLOR] ip -o addr
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue \    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
1: lo    inet 127.0.0.1/8 scope host lo
1: lo    inet6 ::1/128 scope host \       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000\    link/ether 00:0b:cd:56:00:81 brd ff:ff:ff:ff:ff:ff
2: eth1    inet 192.168.1.100/24 brd 192.168.1.255 scope global eth1
2: eth1    inet6 fe80::20b:cdff:fe56:81/64 scope link \       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000\    link/ether 00:0b:cd:8a:b2:d4 brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop \    link/sit 0.0.0.0 brd 0.0.0.0
```

Earlier today, it was reporting the correct IP address (but calling it wired). Now, it's back like it was when I first posted this thread.

---

