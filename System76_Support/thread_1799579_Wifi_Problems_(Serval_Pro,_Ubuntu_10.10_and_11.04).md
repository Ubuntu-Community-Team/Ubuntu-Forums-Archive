---
title: "Wifi Problems (Serval Pro, Ubuntu 10.10 and 11.04)"
date: 2011-07-07
forum: System76 Support
---

### Post by xvedejas on 2011-07-07
I bought a Serval Pro back in April, and things had been working just fine since then. The wifi was working perfectly, with speed of up to 15Mbps. But a week or two ago, in Ubuntu 10.10, my wifi stopped working correctly, probably due to an update.

The download speed has been very slow, below 1Mbps speeds (but the upload speed is mostly unaffected, and usually around 2.5Mbps). The shown signal for my wireless is a bit lower than usual, but not by a significant amount. At first I thought it was a problem with my router, so I replaced it, to no luck. Then I read a few forum posts about wifi issues, saying they had been fixed by upgrading to 11.04, which I had not done yet. Now I've upgraded, and my wireless Internet is no better than before.


Here is some relevant information:

```
lspci | grep Network

Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```

```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:b7:89:a2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:56 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:90:e0:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=9.221.4.1 build 25532 ip=192.168.1.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:54 memory:f6200000-f6201fff

```

Doing a simple ping shows lots of latency. Last time I tried this, most pings were lost as well.

```
ping google.com

PING google.com (74.125.93.147) 56(84) bytes of data.
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=1 ttl=53 time=5055 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=2 ttl=53 time=4217 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=3 ttl=53 time=5528 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=4 ttl=53 time=5058 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=5 ttl=53 time=5035 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=6 ttl=53 time=5093 ms

--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 4217.110/4998.073/5528.088/389.085 ms, pipe 6
```

---

