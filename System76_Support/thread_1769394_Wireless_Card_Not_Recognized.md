---
title: "Wireless Card Not Recognized"
date: 2011-05-27
forum: System76 Support
---

### Post by Bleak888 on 2011-05-27
Hi, My wireless card does not seem to be recognized anymore. I upgraded to Natty a couple of months ago and havent had any issues with wireless in the past. There is not a wireless option available in my drop down menu and no wireless devices are detected. when I type ifconfig -a I no longer even have wlan0. I have a Pan. Any help appreciated. Thanks!

---

### Post by garvinrick4 on 2011-05-27
What does:
```
sudo lshw -C network
```
say

---

### Post by Bleak888 on 2011-05-27
[FONT=monospace]Thanks garvinrick4[FONT=Verdana].

Here is the output...

[/FONT][/FONT][FONT=monospace]*-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:06:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:ac:75:7c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=full ip=192.168.1.81 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 memory:f0304000-f0307fff ioport:4400(size=128) ioport:4000(size=256)

[/FONT]

---

### Post by garvinrick4 on 2011-05-28
Sorry, only thing I could think of would be starting and stopping the network manager but
do not want to lose your wired connection for you so I got to bow out. This will give it
a bump up to front again. Good luck.

---

### Post by Ebonwumon on 2011-05-28
This has happened to me a couple of times lately. A cold boot fixes it. Not a reboot, but fully shutdown your computer and turn it back on. Then everything's fine.

---

### Post by Bleak888 on 2011-05-28
Thanks Ebonwumon and garvinrick4!

The cold boot worked.  It would be nice to know why this happens but thanks for the fix Ebonwumon!

---

