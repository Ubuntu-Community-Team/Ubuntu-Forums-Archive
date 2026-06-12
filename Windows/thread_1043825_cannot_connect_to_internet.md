---
title: "cannot connect to internet"
date: 2009-01-18
forum: Windows
---

### Post by r4z0rw0lf on 2009-01-18
alright, heres my problem... i have a computer windows/linux trying to connect to a wireless unsecured router, BUT whenever i try to connect it kicks me out and ive tried connecting to the router using a computer that WAS connected, and for some reason, the router isnt 192.168.0.1 or routerlogin.net which usually works in my other places where i can connect to the interwebs... the router is a linksys Wireless-g WAP54G. cable provides internet. but i cant connect!!? im getting driven MAD!

---

### Post by melojo on 2009-01-18
post the output of the commands below.

```

lspci
sudo lshw -C nework
ifconfig
iwlist scan

```

This will give us more info

---

### Post by r4z0rw0lf on 2009-01-18
thank god for jumpsticks!
```

nick@nick-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
nick@nick-laptop:~$ sudo lspw -C network
[sudo] password for nick: 
Sorry, try again.
[sudo] password for nick: 
Sorry, try again.
[sudo] password for nick: 
sudo: lspw: command not found
nick@nick-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:a0:cc:dd:b6:a4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:24:03:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:b2:78:09:ea:4f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
nick@nick-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:dd:b6:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122088 (122.0 KB)  TX bytes:122088 (122.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:24:03:9f  
          inet6 addr: fe80::290:4bff:fe24:39f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:129165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8429491 (8.4 MB)  TX bytes:18108 (18.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-24-03-9F-33-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nick@nick-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:12:2B:87
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=73/100  Signal level:-30 dBm  Noise level=-52 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000101ead9718d
                    Extra: Last beacon: 48ms ago

pan0      Interface doesn't support scanning.

nick@nick-laptop:~$ 

```
there, oh and thanks for the quick response before!:)

---

### Post by r4z0rw0lf on 2009-01-18
this may be pointless but i just fell off my chair and got my head bumped!

---

### Post by r4z0rw0lf on 2009-01-19
bump

---

