---
title: "What server distro should I use?"
date: 2009-09-13
forum: Server Platforms
---

### Post by Serpher on 2009-09-13
I'm beginning to learn about Open Source servers and I want to know what distro should I use? I've downloaded Fedora 11 and Ubuntu Server 9.04. I however can not even properly configure the DHCP settings on Ubuntu Server, which I assume is because it's only giving me eth0 and eth1 as hardware options when I actually connect to my router using a wireless card. It would be much appreciated if I could get some help on this issue to.



System specs for good measure:


Network Adapters

```
01:00.0 Network controller: RaLink RT2800 802.11n PCI
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
```



Everything

```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Network controller: RaLink RT2800 802.11n PCI
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
```

---

### Post by cariboo on 2009-09-14
I would suggest you use a wired network connection, you will be much happier with speed and reliability.

Make sure your wireless device is detected and the driver loaded by running the following command:

```
sudo lshw -C network
```

then run the following commands:

[list=1]
[*] sudo ifconfig wlan0 down
[*] sudo dhclient -r wlan0
[*]sudo ifconfig wlan0 up
[*]sudo iwconfig wlan0 essid "ESSID_IN_QUOTES", the essid is the name you have given your router, for instance if you have a Linksys and you haven't changed the essid, it would be Linksys
[*]sudo iwconfig wlan0 mode Managed
[*]sudo dhclient wlan0
[/list]

---

