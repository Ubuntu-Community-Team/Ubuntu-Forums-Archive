---
title: "Issues Bonding interfaces after reboot"
date: 2013-09-25
forum: Server Platforms
---

### Post by edge87 on 2013-09-25
I'm having a problem bonding network interfaces during boot. When the system gets fully up, you can't ping anything on the network, but everything reports being ok :

> 
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

802.3ad info
LACP rate: fast
Min links: 0
Aggregator selection policy (ad_select): stable
Active Aggregator Info:
        Aggregator ID: 1
        Number of ports: 1
        Actor Key: 17
        Partner Key: 1
        Partner Mac Address: 00:00:00:00:00:00

Slave Interface: eth0
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: d8:9d:67:24:65:28
Aggregator ID: 1
Slave queue ID: 0

Slave Interface: eth3
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: d8:9d:67:24:65:2b
Aggregator ID: 2
Slave queue ID: 0

Slave Interface: eth1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: d8:9d:67:24:65:29
Aggregator ID: 3
Slave queue ID: 0

Slave Interface: eth2
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: d8:9d:67:24:65:2a
Aggregator ID: 4
Slave queue ID: 0



Most of the time to fix this, I simply issue an *ifconfig bond0 down && ifconfig bond0 up && route add default gw 172.16.12.1 *, and everything just starts working again. 

This is what the bonding interface reports during start up: (network-interface-bond0.log) 
> 
Waiting for a slave to join bond0 (will timeout after 60s)


And one of the bonding interfaces (ETH0):
> 
Waiting for bonding kernel module to be ready (will timeout after 5s)
Waiting for bond master bond0 to be ready
Waiting for bond master bond0 to be ready
Waiting for bond master bond0 to be ready
Waiting for bonding kernel module to be ready (will timeout after 5s)


The kernel module "bonding" is part of the /etc/modules

Specs:
[LIST]
[*]Ethernet controller: Broadcom Corporation NetXtreme BCM5719 Gigabit Ethernet PCIe
[*]Kernel : 3.12.0 R2
[*]ifslave : 1.1.0-20ubuntu3
[/LIST]

/etc/networking/interface configuration:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
bond-master bond0

auto eth1
iface eth1 inet manual
bond-master bond0

auto eth2
iface eth2 inet manual
bond-master bond0

auto eth3
iface eth3 inet manual
bond-master bond0

auto bond0
iface bond0 inet static
address 172.16.12.90
netmask 255.255.254.0
gateway 172.16.12.1
bond-mode 802.3ad
bond-slaves eth0 eth1 eth2 eth3
bond-miimon 100
bond-lacp-rate fast

dns-nameservers 172.16.10.2



---

### Post by Robert_Brooks on 2013-09-30
Hi,

I beleive we may be seeing a similar issue. Does the problem go away if you remove eth2 and eth3 as slaves?

---

