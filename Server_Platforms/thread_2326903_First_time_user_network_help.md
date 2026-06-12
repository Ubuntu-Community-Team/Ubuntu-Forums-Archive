---
title: "First time user network help"
date: 2016-06-05
forum: Server Platforms
---

### Post by Phantom329 on 2016-06-05
Hi Ubuntu forums,

I recently got an extra computer that I want to turn in to a server primarily for gaming. I also want to learn how to setup and maintain the server.

I installed Ubuntu Server (latest) and need help connecting to the internet. I skipped over the network config in the initial install and now I can't figure out how to enable it.

I looked around at some threads and all I figured out was sudo lshw -c network
```
*-network: DISABLED
description: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controler
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@oooo:02:00.0
logical name: enp2s0
version: 06
serial: f0:4d:a2:f7:6b:df
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capcbilities: pm msi pciexpress msix vpd bus_master cap_list ehternet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
```

Thanks for the help.

---

### Post by TheFu on 2016-06-06
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) is probably what you seek.

Welcome to the forums.  Don´t forget to have the appropriate amount of fun.

---

### Post by einom on 2016-06-06
try using the next command:

sudo ifconfig ethx up

the ethx is the name for the network card if is a PCI is eth0, if is a wireless card would be wlan0

---

### Post by TheFu on 2016-06-06
Actually, the device name is enp2s0 according to the output above, so the cmd would be:

```
sudo ifconfig enp2s0 up
```
Doubt it will work and it isn´t a permanent solution.  Definitely worth trying. Can´t hurt.
Really need to setup the static IP config files so this is solved forever, in the way you want. Servers need static IPs to be most useful.

---

