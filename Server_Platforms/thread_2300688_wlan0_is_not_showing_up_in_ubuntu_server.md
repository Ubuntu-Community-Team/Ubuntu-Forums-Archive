---
title: "wlan0 is not showing up in ubuntu server"
date: 2015-10-27
forum: Server Platforms
---

### Post by Jake_Simmons on 2015-10-27
Hi,
i'm fairly new to Ubuntu, and 'ive just installed Ubuntu server into my windows 10 laptop. I have successfully set up a SSH server to fileshare on my local network on a separate machine, however on this machine i am unable to get the wlan0 interface up, or even see it. I cant see a way to solve this, and despite looking through the forums, my problem remains un-solved. if someone could help, and walk me through how to get wlan up, that would be great!

Thanks

for anyone else who can give me a hand, here is the device i'm trying to configure:


```
  *-network UNCLAIMED       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b7600000-b7607fff memory:b7400000-b75fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: em1
       version: 0c
       serial: 38:63:bb:ba:3f:66
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:3000(size=256) memory:b7800000-b7800fff memory:b7700000-b7703fff

```

---

### Post by cariboo on 2015-10-27
The first thing to do before we can give you any help is for you tp let us know what wireless device you are trying to configure. At the prompt type the following command:

```
sudo lshw -C network > network.txt
```

this will create a text file called network.txt, copy it to your windows drive, and paste it into your next post. The file should look similar to this:

```
*-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: b8:ee:65:8a:1b:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.2.0-16-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0700000-d077ffff memory:d0780000-d078ffff
```

---

### Post by Jake_Simmons on 2015-10-28
im sorry the reply took so long, i was struggling with getting the file off of ubuntu server, but here it is...

```
  *-network UNCLAIMED       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b7600000-b7607fff memory:b7400000-b75fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: em1
       version: 0c
       serial: 38:63:bb:ba:3f:66
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:3000(size=256) memory:b7800000-b7800fff memory:b7700000-b7703fff

```

Solved, i needed to install the relevant package fo the device to get a logical name etc.

---

