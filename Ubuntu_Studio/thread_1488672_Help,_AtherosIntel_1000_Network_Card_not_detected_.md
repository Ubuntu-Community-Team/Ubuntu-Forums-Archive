---
title: "Help, Atheros/Intel 1000 Network Card not detected on Install - Was Fine in Wubi"
date: 2010-05-20
forum: Ubuntu Studio
---

### Post by tehowe on 2010-05-20
My network cards were fine under Wubi Lynx. I decided to upgrade to  Ubuntu Studio Lynx on its own partition, and the DVD install routine  failed to detect the network card. Where do I go from here?

***1 ) Machine Brand and Model (PC/Laptop):
Acer 1410 (dual amd64 netbook, about a year old)

***2) Network Interfaces

>lspci
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit  Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series

***3) Interface

>ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

>iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr ff   Fragment thr ff
          Power Management ff

***4) Modules

>lsmod | grep "wlan_module_name"
(nothing comes up)

***5) Kernel Messages

>dmesg | grep "wlan_module_name"
(Nothing comes up)

***6) Network Configuration

> sudo lshw -C network
*-network DISABLED      
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26 x x x x
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=yes multicast=yes  port=twisted pair
       resources: irq:16 memory:93500000-9353ffff ioport:2000(size=128 )
  *-network DISABLED
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e x x x x
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet  physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 memory:92500000-92501fff

***7) Scan for Networks

> iwlist scan | grep "wlan_module_name"
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

***8 ) Kernel

>uname -mr
2.6.32-21-preempt x86_64

***9) Ubuntu Version

>lsb_release -d
Description:    Ubuntu 10.04 LTS

***10) Network restart response

>sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...      [ OK ]

---

### Post by tehowe on 2010-05-21
I found something on this old thread about an HP card notebook problem  that helped...

[http://ubuntuforums.org/showpost.php...9&postcount=12]("http://ubuntuforums.org/showpost.php?p=9318319&postcount=12")

You plug in your ethernet and type 

> sudo dhclient eth0                                 

At this point, ethernet connected for me, though there's no panel indicator.

Then you 

> sudo apt-get update
> sudo apt-get install wicd                                 

The mysterious incantations worked. :smile: Wicd doesn't look like the  standard Lynx network manager, it seems to be some older Python app but  it works and so now both wired and wireless work.

---

