---
title: "Issue with Atheros wireless card in AP mode."
date: 2009-01-20
forum: Server Platforms
---

### Post by C-King on 2009-01-20
Hello,

My server has a NetGear WPN311FS with an Atheros AR5001X-1 chip. I followed the [HOWTO]("http://madwifi-project.org/wiki/UserDocs/SimpleAccessPoint")  on the madwifi.org wiki to set up the card in AP mode and bridge it with my wired ethernet interface, an onboard VIA VT6102 [Rhine-II]. This worked on my previous Debian install, but last weekend I got a new harddisk and decided to install Ubuntu Intrepid Ibex. 

When I use the same configuration and restart the network (or reboot the server), my server hangs and responds to nothing. I don't see a kernel panic on the screen though. 

My /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Wireless card
auto ath0
iface ath0 inet manual
       pre-up wlanconfig ath0 destroy || true
       pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
       post-down wlanconfig ath0 destroy
       wireless-mode master
       wireless-channel 11
       wireless-essid DataNet

#Bridge
auto br0
iface br0 inet static
       address 192.168.1.2
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.1.255
       gateway 192.168.1.1
       bridge-ports eth0 ath0

```Does anyone have an idea on how to fix this?

---

