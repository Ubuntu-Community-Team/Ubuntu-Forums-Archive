---
title: "Network problem with upgrade from 16.04 to 16.10"
date: 2016-10-29
forum: Server Platforms
---

### Post by Keith_Beef on 2016-10-29
Tried to upgrade a few days ago, hardware is a dell R610 that had been working flawlessly but not being used much (I bought it second hand to learn about server hardware and administration, mostly). The upgrade seemed to go OK at first, but then I got messages about packages being unavailable. I had to stop, shutdown and go off and do other things (like work) for a few days and now I'm back to try to fix the problem.

It looks like the network interface has gone down and I can't find a way to get it back up.

# ifup em1
Usage dhclient  [a load of options are described here]
Failed to bring up em1

That interface is present:
# ls -al /sys/class/net
lwrxwrxwrx root root 0 Oct29 08:00 em1 --> ../../devices/pci0000:00/0000:00:01/0000:00:01/em1

# cat /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet dhcp

Following advice on [this thread]("https://ubuntuforums.org/showthread.php?t=2339477&highlight=network+interface+problem+16.10"), I tried 

# ping -c 4 8.8.8.8

connect: Network is unreachable.

# lshw -C network
  *-network:0              
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet Controller
       vendor: Broadcomm Corporation.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: em1
       version: 20
       serial: xx:xx:xx:xx:xx:xx
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.6 duplex=half firmware 5.0.13 bc 5.0.11 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:d6000000-d7ffffff memory:f9900000-f990ffff

# ls -l /sys/class/net/em1/device/driver
lrwxrwxrwx 1 root root 0 Oct29 08:00 em1 /sys/class/net/em1/device/driver -> ../../../../bus/pci/drivers/bnx2
# ls -l /sys/class/net/eth0/device/driver/module
lrwxrwxrwx 1 root root 0 Oct29 08:00 /sys/class/net/em1/device/driver/module -> ../../../../module/bnx2

# lsmod | grep bnx2
bnx2  89120 0

So the module is loaded, but no networking.
What's the next step? I'm far from knowledgeable about this, but it looks like something to do with dhclient, right?

---

### Post by darkod on 2016-10-29
Just a note, if you are planning to run ubuntu server even if it's only for home use, better to stick with LTS releases only. Ubuntu has a LTS release each 2 years and the current one is 16.04 LTS. They have 5yrs of support and security updates as opposed to only 9 months for the other releases.

I always consider the "standard" releases like work in progress to try to have the next LTS as stable as possible when it comes out. Linux servers are for stability, not to have the latest version and upgrade every 6 months when new ubuntu comes out. Most people only upgrade from LTS to LTS and never to a standard release.

---

