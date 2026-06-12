---
title: "Need Help Troubleshooting Networking on New Pangolin Laptop"
date: 2010-09-13
forum: System76 Support
---

### Post by Kibitz on 2010-09-13
Hi All,

I just received my first System76 laptop and so far I've been really pleased with it. I have one one issue that I need some help resolving. When I got the laptop I immediately wiped the preinstallation of Ubuntu and installed from my own copy of the Alternate install CD, as I do full hard drive encryption (LVM). After installing the base system, all updates, and the System76 driver package, I'm still unable to get the wired network to function. The wireless functionality works flawlessly, but not the ethernet port. The wired Internet DID work on the preinstalled version of Ubuntu, so I must just be doing something wrong. 

Any help is much appreciated! I have the Pangolin Performance, model "panp7" with Ubuntu 10.04 Desktop 64-bit installed.

Scott

---

### Post by endotherm on 2010-09-13
what do you get from:
```

ifconfig -a
cat /etc/network/interfaces
sudo lshw -C Network

```

---

### Post by Kibitz on 2010-09-13
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:90:f5:a7:78:62  
          inet6 addr: fe80::290:f5ff:fea7:7862/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:660 (660.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:36 


/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

lshw:

 *-network               
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:a2:a1:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.107 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f0300000-f0301fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:a7:78:62
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:36 memory:f0400000-f0403fff ioport:4400(size=128) ioport:4000(size=256)

---

### Post by endotherm on 2010-09-13
try pugging in the cable and running 
```
sudo ifup eth0
```and then run ifconfig again to see if it has pulled an ip address

failing that, try restarting networking with:
```
sudo /etc/init.d/networking restart
```
do any errors or warnings appear?

---

### Post by Kibitz on 2010-09-13
ifup returns:

Ignoring unknown interface eth0=eth0.

---

### Post by endotherm on 2010-09-13
> **Kibitz said:**
> ifup returns:

Ignoring unknown interface eth0=eth0.

well, first, did you try adding an connection in network manager? if it does work, that would be the simplest answer. it looks like your hardware is there and running, but isn;t waking up. 

if network manager isn;t an option, 
try adding this to your /etc/network/interfaces below the lo definition:
```

auto eth0
iface eth0 inet dhcp

```save and restart networking.
the only problem with this approach is that you won't be able to use the network manager gui to control eth0.

here are some more details about configuring your interfaces file
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by Kibitz on 2010-09-13
No luck. I tried a few variations on manual configuration of the eth0 device but could not get it to work. I tried a couple different ethernet cables that I know to work. Still no luck. I tried both a 32-bit and 64-bit Ubuntu liveCD but it just does not work. I'm really disappointed, as everything else on the laptop has worked great so far.

Any other suggestions before I look into sending it back?

Scott

---

### Post by endotherm on 2010-09-13
well, before you send it back, definitely contact them. I've seen some of their guys around, and they seem pretty game to work with people. I'm just a dude on the forums (didn't even notice till now that this was a s76 subforum...). I'm sorry if I came off as someone affiliated with s76.

the next thing I would check, is to plug the cable back in. do the lights on each end of the connection spark up?
try installing ethtool and running it, ad post back the output
```

sudo apt-get install ethtool
sudo ethtool eth0
```

if you get "Link detected: no"
then it is time to check your cabling.

---

### Post by IAmWhatWasDavidBowman on 2010-09-14
Absolutely give System76 a shout. They've been really responsive with my emails. Have you tried maybe booting to the regular live Lucid cd and seeing if your ethernet port works there?

---

