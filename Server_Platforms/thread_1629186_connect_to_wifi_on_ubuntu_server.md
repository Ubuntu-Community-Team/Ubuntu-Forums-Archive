---
title: "connect to wifi on ubuntu server"
date: 2010-11-23
forum: Server Platforms
---

### Post by ShatPank on 2010-11-23
I'm trying to connect to a wifi network using Ubuntu Server 10.04 but i'm having trouble.

The wifi adapter is a USB ALFA AWUS036H on wlan0

The routers details are

BTHomeHub-840B
WEP (default key)   D1DDFCB8FB

For some reason, when scanning (all in terminal) it keeps reporting no nework.
Instructions for a newbie please, when networking in windows I'm fine, but linux networking is all new to me.

Stuart

---

### Post by cariboo on 2010-11-23
Linux networking works the same way as in Windows. You need a driver for your wireless device, in most cases it is included with the kernel. Could you please post the output of:

```
sudo lshw -C network
```

the above command will tell us if your device is detected and if the driver is loaded.

I'd really advise against using wireless for a network connection for your server, if at all possible use a cable to connect to your router, as network speeds will be much higher and more reliable.

---

### Post by ShatPank on 2010-11-23
As far as I'm aware the driver is something like RLT8187L under standard ubuntu.

Sadly, I can't connect to ethernet, the connection is a shared one with a friend as I'm currently living in a block of flats i dont plan on staying in for too long, and cant therefore tie to a contract.

The response to your command was this:


*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:eb:50:ca
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.137.160 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:27 ioport:1000(size=256) memory:90100000-90100fff memory:90000000-9000ffff(prefetchable) memory:90020000-9003ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:ca:3f:8c:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Thanks :)

---

