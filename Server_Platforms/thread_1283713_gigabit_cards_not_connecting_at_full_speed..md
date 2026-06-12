---
title: "gigabit cards not connecting at full speed."
date: 2009-10-05
forum: Server Platforms
---

### Post by timuckun on 2009-10-05
I have two servers. Both of them are running in a remote location. Both of them are Dell servers. Both of them have Broadcom NetXteme cards (different models) and both of them are plugged into the same gigabit switch.

Neither of the machines is connected at gigabit speeds though. Here is the output from lshw -C network and ethtool eth0

Machine 12 

sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 12
       serial: 00:22:19:a0:2f:36
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=1.8.1 duplex=half firmware=4.4.1 ipms 1.6.0 latency=64 link=yes mingnt=64 module=bnx2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:22:19:a0:2f:34
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=1.8.1 duplex=full firmware=4.4.1 ipms 1.6.0 ip=192.168.4.12 latency=32 link=yes mingnt=64 module=bnx2 multicast=yes port=twisted pair speed=100MB/s


ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes


Machine 11


lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth3
       version: 0c
       serial: 00:0e:0c:b6:39:f4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 11
       serial: 00:14:5e:2a:28:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5721-v3.29a, ASFIPMI v6.08 ip=192.168.4.11 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 11
       serial: 00:14:5e:2a:28:0d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=half firmware=5721-v3.29a, ASFIPMI v6.08 latency=0 link=yes module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5703 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:09:01.0
       logical name: eth2
       version: 10
       serial: 00:10:18:16:1f:e2
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=half firmware=5703-v2.35 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair


ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes



So what do I have to do in order to get these machines to connect at giagbit speeds.

BTW I probably can't work on this immediately because I am afraid to cut myself off from them. I need to schedule for hands on support to be when I attempt to modify the network connections.

---

### Post by scorp123 on 2009-10-06
Faulty cables?

---

### Post by HarshReality on 2009-10-06
Could throw out a couple of things Im curious about.. and a couple of comments..

1. (Comment) Doesnt matter if they are GB and the switch is GB.. multiple simultanious hits from a GB connection is shared. So if both are running you'll at best only get partial GB.

Which brings me to question

1. You have gigabit NIC, and gigabit switch.. but what is the switch feeding off of?

---

### Post by dragos2 on 2009-10-06
> **scorp123 said:**
> Faulty cables?

For the OP:
Faulty cables can be checked in windows with pathping,
and in Linux with ping -f.

Also 1 Gbps = 0.125 GBps (at most 125 MB/per second)

But as more computers plugged into the switch -> less bandwidth.

Just to be clear.

---

### Post by timuckun on 2009-10-06
> **HarshReality said:**
> Could throw out a couple of things Im curious about.. and a couple of comments..

1. (Comment) Doesnt matter if they are GB and the switch is GB.. multiple simultanious hits from a GB connection is shared. So if both are running you'll at best only get partial GB.

Which brings me to question

1. You have gigabit NIC, and gigabit switch.. but what is the switch feeding off of?

The switch is ultimately connected to a firewall which is connected to the internet.

Most of the traffic on the network is between machines though and that's what I am mostly concerned about. I want to be able to move data between the machines at gigabit speeds.

---

### Post by timuckun on 2009-10-06
> **scorp123 said:**
> Faulty cables?

Doesn't seem likely. They do work.

When I originally installed the software there was a hundred megabit switch so I suspect that's where the cards got configured. 

How do I tell the cards to switch to a higher speed?

---

### Post by novaraz on 2009-10-19
I am having the same problem with the same card.  ethtool reports links of 1000 Mbps available, but a link speed of 100 Mbps is established.  Also, the switch indicates a 100, not 1000 connection.

I have the SAME desktop sitting 3 feet running windows and it connects at 1Gb. 

Any luck resolving this?

---

### Post by timuckun on 2009-10-19
> **novaraz said:**
> I am having the same problem with the same card.  ethtool reports links of 1000 Mbps available, but a link speed of 100 Mbps is established.  Also, the switch indicates a 100, not 1000 connection.

I have the SAME desktop sitting 3 feet running windows and it connects at 1Gb. 

Any luck resolving this?


Sorry no.

Nobody has suggested anything useful so I am stuck at 100 Mbit.

---

### Post by cariboo on 2009-10-20
Have you actually checked to see what your real connection speeds are? Iperf is the tool to check connection/bandwidth speeds. Iperf is in the repositories. You start iperf on one computer as the server:

```
iperf -s
```

and on the second system:

```
iperf -c <servername>
```

I get results that look like this:

```
iperf -c chilanko
------------------------------------------------------------
Client connecting to chilanko, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.225 port 42355 connected with 192.168.1.210 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.5 Mbits/sec
```

both ways.

---

### Post by novaraz on 2009-10-20
Thanks for the iperf tip.

My setup is as follows (all computers have 1Gbps hardware and are connected to a SMC gigabit-switch):
IBM T60, Ubuntu 9.04 @ 1Gb
Microway Opteron workstation, Ubuntu 8.04 @ 100Mb
Microway Opteron workstation, Xubuntu 8.10 LiveUSB-stick @ 1Gb

Using iperf confirms all these speeds, so its not just a label.  The 1st Microway is being used as a remote X-server for our group, so we absolutely need 1Gbps.  The Microway's have the exact same hardware (Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 21)), which works in 8.10 but not in 8.04.  I'd prefer not to do a dist-upgrade since everything else is stable and working.

---

### Post by novaraz on 2009-10-20
Ahh. I got it working.  It was the cable, only 2-pair instead of 4-pair.  So silly, sorry for the trouble :)

---

