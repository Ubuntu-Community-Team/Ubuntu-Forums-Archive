---
title: "Slow network Tx"
date: 2010-03-09
forum: Server Platforms
---

### Post by mathx on 2010-03-09
Hello,

I have an Ubuntu 9.10 server with several services installed (Firebird Database, Oracle Database, Apache, Samba, rails applications). We've switched to it from FreeBSD because of software incompatibilities.

The problem is *very* slow upload throughput from the server to the clients. This seems to affect all applications (I even installed an FTP server and this also happens). But it only affects transfers from the server to clients (sending a file to the server is fast and fills the 100MBIT network interface). 

The network interface currently connected to the local network is a PCI card, with RTL 8139 chipset. I have an onboard RTL 8102 card, which is currently disabled in linux.

Output from lshw -C net:
```
  
*-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:24:21:c5:c8:ab
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: eth1
       version: 10
       serial: 00:30:4f:55:0d:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.252 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:febffc00-febffcff

```

Output from mii-tool:
```

eth1: negotiated 100baseTx-FD, link ok

```

Output from IfConfig:
```

eth1      Link encap:Ethernet  HWaddr 00:30:4f:55:0d:ac
          inet addr:192.168.0.252  Bcast:192.168.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1998646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2370227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:664154548 (664.1 MB)  TX bytes:2718864499 (2.7 GB)
          Interrupt:17 Base address:0xe800

```

Output from uptime:
```
11:32:16 up  3:26,  4 users,  load average: 0.06, 0.30, 0.27
```

Output from uname -a:
```
Linux giga 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

```

In 3 hours up, the server has sent 2.7GB of data, but the total output throughput rate never exceeded 400KB/s (measured from bwm-ng). 

I have already disabled IPv6, I've checked dns servers in resolv.conf. I swapped to an off-board network card because I tought that would solve the problems, but it didn't.

---

