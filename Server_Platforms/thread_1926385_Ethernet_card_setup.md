---
title: "Ethernet card setup"
date: 2012-02-16
forum: Server Platforms
---

### Post by lrinetti on 2012-02-16
When i run the command "lshw" on my Ubuntu 9.10 server i get:
...
-network:0
          description: Ethernet interface
          product: NetXtreme BCM5703X Gigabit Ethernet
          vendor: Broadcom Corporation
          physical id: 1
          bus info: pci@0000:02:01.0
          logical name: eth0
          version: 02
          serial: 00:0b:cd:ee:67:15
          size: 100MB/s
          capacity: 1GB/s
          width: 64 bits
          clock: 66MHz
          capabilities: pcix pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 **duplex=half **firmware=5703-v2.22 ip=213.144.92.209 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s


with half duplex setup, but if i run the command "mii-tool" command, i get a full duplex setup:

#  mii-tool -v eth0
eth0: 100 Mbit, **full duplex**, link ok
  product info: vendor 00:08:18, model 22 rev 2
  basic mode:   100 Mbit, full duplex
  basic status: link ok
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

What is the reason of this difference ? What is the real duplex setup of the Ethernet card ?

Regards

---

