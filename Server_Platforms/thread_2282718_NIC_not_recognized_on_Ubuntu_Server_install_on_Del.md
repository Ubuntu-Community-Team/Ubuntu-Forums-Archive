---
title: "NIC not recognized on Ubuntu Server install on Dell XPS 8300"
date: 2015-06-16
forum: Server Platforms
---

### Post by Marc-NJ on 2015-06-16
I am trying to install Ubuntu Server 14.04.2 LTS on a Dell XPS 8300 machine and having some issues getting it to recognize the integrated network card.  I believe the network card is a Broadcom BCM57788, and the machine also has a WLAN mini-PCI card (possibly the Dell DW1520).  I'm booting the Ubuntu Server install off of a CD that I burned the ISO to, and when I get to the part where it wants to configure the network, it only seems to find wlan0 (the wireless card), but then no matter what I do, it won't let me connect to any wireless networks.  I even tried a factory-reset WNDR4000 configured with wireless that had no security (entirely open wireless network) and after putting in the ESSID, telling it that the network was open, and then putting in nothing for the security password, it wouldn't connect.  


I actually don't even want it to connect via WiFi - I want to use the built-in network card, but if I pop out the mini-PCI WLAN card and reboot to start the installation again, and it gets to the network configuration part, it tells me it can't find any network adapters at all.


Any thoughts on what I can do to get it to recognize the built-in ethernet card?  I'm thinking of going out to just pick up another one and then setting it up on a PCIe slot, but if there's a better way to do this and be able to use the built-in network card, that'd be great.  Any help is greatly appreciated!  Thanks.

---

### Post by Marc-NJ on 2015-06-16
So I tried running Ubuntu Desktop 14.04.2 LTS in live mode, and my NIC worked fine; I then downloaded and tried Ubuntu Server 12.04.5 LTS, and it got to the point where it detected network cards, and perfectly detected eth0 and set me up and running on my LAN - so I have no idea what is going on with 14.04.2 LTS and why it isn't detecting my NIC??  I'm guessing I have to do something at some point like install some sort of driver, but am lost as to where to get a driver, what process to follow, etc. - anyhelp is greatly appreciated!

---

### Post by cariboo on 2015-06-16
If you post the output of:

```
sudo lshw -C network
```

we should be able to help you out.

---

### Post by Marc-NJ on 2015-06-16
To be honest, I'm not sure if that command would have worked in the reduced shell you're able to get when installing Ubuntu Server.  Either way, it doesn't matter since I went out and actually bought a PCIe NIC and got that to be recognized by Ubuntu 14.04.2 LTS Server install, but on idea why Ubuntu 12.04.5 LTS Server install had no issues recognizing the built-in NIC.  

So now I've got Ubuntu 14.04.2 LTS fully installed and am just starting to configure it, but it'd be great to figure out how to get the built-in NIC to be recognized and that way I can use it as a second NIC I guess?  Is there any benefits to having a second NIC?  Anything I can do with it that might be useful?

Here's the output of the command you requested:

```
root@Polaris:~# lshw -C network
  *-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:fe600000-fe603fff
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: p2p1
       version: 00
       serial: 68:05:ca:34:44:d8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.8-0 ip=192.168.79.251 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 memory:fe5c0000-fe5dffff memory:fe500000-fe57ffff ioport:e000(size=32) memory:fe5e0000-fe5e3fff memory:fe580000-fe5bffff
  *-network DISABLED
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: p3p1
       version: 01
       serial: 18:03:73:bf:44:1a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb latency=0 link=no multicast=yes port=MII
       resources: irq:19 memory:fe400000-fe40ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 38:59:f9:bb:dd:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.16.0-41-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11abgn

```



Thanks for the assistance!

---

### Post by Marc-NJ on 2015-06-19
It seems like all I had to do was edit the /etc/network/interfaces and add:

```
auto p3p1
iface p3p1 inet dhcp
```

then go plug in a network cable between the built-in network card and my switch, and then run: ifup p3p1 and boom - I got network connectivity through there - so weird that it didn't like that built-in network card during initial installation on 14.04 but had no issues with it on 12.04

Anyway, now that I have a separate gigabit PCIe card installed and configured, I might as well just use that.  I unplugged the network cable, and did a ifdown p3p1, but am I OK leaving that extra code in the /etc/network/interfaces, or will that cause issues later on?

Thanks!

---

### Post by darkod on 2015-06-19
No issues. The auto p3p1 will activate the card on each boot but without a cable connected to it, nothing happens. It can stay like that forever.

---

### Post by Marc-NJ on 2015-06-19
Great - thanks for the info!

---

