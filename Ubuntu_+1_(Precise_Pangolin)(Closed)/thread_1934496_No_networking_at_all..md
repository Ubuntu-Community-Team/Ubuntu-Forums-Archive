---
title: "No networking at all."
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cespinal on 2012-03-02
Hello all, 

I just updated to the Precise beta. Everything works perfectly except networking: wifi is absent although the broadcom driver is activated and the system will not connect via ethernet. 

What is the situation in these matters? I would love to give a han reporting bugs, but network connectivity is a must..

lspci lists my devices, drivers and kernel modules.

Edit: Ethernet is working properly. Wifi is not working. The wifi led in my computer remains off althoughthe card, drivers and modules seem to be listed.

Edit2: *-network               
      description: Ethernet interface
      product: NetLink BCM57780 Gigabit Ethernet PCIe
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:03:00.0
      logical name: eth0
      version: 01
      serial: 00:26:2d:af:6e:7b
      size: 1Gbit/s
      capacity: 1Gbit/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb ip=192.168.1.22 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
      resources: irq:45 memory:d0100000-d010ffff
 *-network
      description: Network controller
      product: BCM43225 802.11b/g/n
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:06:00.0
      version: 01
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list
      configuration: driver=bcma-pci-bridge latency=0
      resources: irq:17 memory:d0200000-d0203fff

Solved using the solutions in here: [http://ubuntuforums.org/showthread.php?p=11732891&posted=1#post11732891](http://ubuntuforums.org/showthread.php?p=11732891&posted=1#post11732891)

---

