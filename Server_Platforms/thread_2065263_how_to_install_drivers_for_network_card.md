---
title: "how to install drivers for network card"
date: 2012-10-01
forum: Server Platforms
---

### Post by buffchick on 2012-10-01
How do you install drivers for a NetXtreme II BCM57810 10 Gigabit Ethernet [14e4:168e] card on 10.04?

---

### Post by buffchick on 2012-10-01
looks like I need firmware-bnx2x which is part of linux-firmware and installed by default but not sure if I have to backport to get it to work on lucid... suggestions?

```
lspci | grep 'network|ethernet'
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
06:00.0 Ethernet controller: Broadcom Corporation Device 168e (rev 10)
06:00.1 Ethernet controller: Broadcom Corporation Device 168e (rev 10)
```

---

### Post by buffchick on 2012-10-01
updated drivers using [http://ubuntuforums.org/archive/index.php/t-1851008.html](http://ubuntuforums.org/archive/index.php/t-1851008.html) as a base. now it's showing the interfaces but, they're numbered weird. Is this normal? I'm not even sure I did it right...

```
ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 14:fe:b5:d7:a1:ee brd ff:ff:ff:ff:ff:ff
3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 14:fe:b5:d7:a1:f0 brd ff:ff:ff:ff:ff:ff
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 14:fe:b5:d7:a1:f2 brd ff:ff:ff:ff:ff:ff
5: eth3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 14:fe:b5:d7:a1:f4 brd ff:ff:ff:ff:ff:ff
6: eth9: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 00:10:18:e2:37:70 brd ff:ff:ff:ff:ff:ff
7: eth8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 00:10:18:e2:37:72 brd ff:ff:ff:ff:ff:ff

```

---

