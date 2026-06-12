---
title: "Showing Ubuntu Server to the Airport"
date: 2011-08-13
forum: Server Platforms
---

### Post by qupodogbark on 2011-08-13
I've installed the Ubuntu 10.04 Server onto a PPC G4 Mac just for the experience of setting up a server. 
During the installation process Ubuntu couldn't auto-configure my DHCP Network.
I'm using the airport card on a wireless network.
How can I manually configure the network once Ubuntu is installed.
(I know very little command line...:???:)

Thanks smart folk!

---

### Post by Idefix82 on 2011-08-13
By "configuring the network" you mean accessing the wireless network from your computer? We need to know more about the wireless card. Please type in
```

lspci
lshw -C network

```
and paste the output from both commands here (ideally between ```
...
``` tags). From the first command, you don't really have to paste everything, just the line containing your wireless card.

---

### Post by qupodogbark on 2011-08-13
something about my ubuntu install is corrupt. going to reburn the iso, and if that doesn't work redownload it.
as soon as i can actually boot into ubuntu i'll post information on the wireless card.
thanks, i appreciate the help

---

### Post by qupodogbark on 2011-08-14
```

...
rob@rob-desktop:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:16.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth 2 ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 01)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM)
rob@rob-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 16
       bus info: pci@0001:10:16.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16 module=ssb
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:0a:95:9f:78:dc
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=sungem driverversion=0.98 latency=16 maxlatency=64 mingnt=64 module=sungem multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:93:87:9d:2f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
rob@rob-desktop:~$ ...

```

I've gone another route. I was able to install a desktop version of Ubuntu 8 (Hardy, i think) and once I can get the internet working then I'm going to find a way to turn it into a LAMP Server. 

In the mean time I think I'm missing the right packages or drivers for my wireless card to work, and because the computer won't get internet I'm not sure where/how to get them. Any thoughts?

---

### Post by dFlyer on 2011-08-14
I'm not sure, but I don't think 8 is supported any more.

---

### Post by qupodogbark on 2011-08-14
I think the things I need are on this site- [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")
But I'm not sure exactly how to implement it.

---

### Post by qupodogbark on 2011-08-14
> **dFlyer said:**
> I'm not sure, but I don't think 8 is supported any more.

Sorry for being painfully new, but supported by who?
Versions 11 and 10 failed to install. I assumed they were too recent.

---

