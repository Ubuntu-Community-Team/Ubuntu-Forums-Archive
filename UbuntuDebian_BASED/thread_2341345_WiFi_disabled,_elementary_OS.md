---
title: "WiFi disabled, elementary OS"
date: 2016-10-27
forum: Ubuntu/Debian BASED
---

### Post by kiina on 2016-10-27
How to enable WiFi?

```
$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: cd:c1:6a:af:32:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bs multicast=yes wireless=unassociated
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwp0s10u1
       serial: dc:5d:cc:bf:a7:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 3
       logical name: enx00e04c212247
       serial: 01:c0:3c:42:33:23
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=dm9601 driverversion=22-Aug-2005 duplex=full firmware=Davicom DM96xx USB 10/100 Ether ip=10.0.0.39 link=yes multicast=yes port=MII speed=100Mbit/s

```

---

### Post by coffeecat on 2016-10-27
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by kiina on 2016-10-27
Not sure what was broken, but got it work by building drivers again..

```

sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/hadess/rtl8723as.git
cd rtl8723as
make
sudo make install
sudo depmod -a
sudo modprobe -r r8723bs
sudo modprobe r8723bs

```

---

