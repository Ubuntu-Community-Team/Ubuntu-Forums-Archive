---
title: "[Kali] My wireless card intel 7260 isn't detectable"
date: 2014-08-09
forum: Ubuntu/Debian BASED
---

### Post by Ilumizi on 2014-08-09
Hi! After reading thousands of tutorials about how to make my wireless card work I gave up trying alone and decided to ask for help. Please and thanks!

My info:

```

########## wireless info START ##########

Report from: 09 Aug 2014 22:36 BRT -0300

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Debian
Description:    Debian GNU/Linux Kali Linux 1.0.8
Release:    Kali Linux 1.0.8
Codename:    n/a

##### kernel #####

Linux 3.14-kali1-amd64 #1 SMP Debian 3.14.5-1kali1 (2014-06-07) x86_64 unknown unknown GNU/Linux

Parameters: ro, initrd=/install/initrd.gz, quiet

##### desktop #####

default

##### lspci #####

02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
    Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]
    Kernel driver in use: e1000

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

./wireless_script: line 100: pccardctl: command not found

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

iwlwifi                87784  0 
cfg80211              436618  1 iwlwifi

##### interfaces #####

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.72.133  Bcast:192.168.72.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feb7:5fa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10368917 (9.8 MiB)  TX bytes:1345160 (1.2 MiB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.72.2    0.0.0.0         UG    0      0        0 eth0
192.168.72.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #####

domain localdomain
search localdomain
nameserver 192.168.72.2

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unmanaged
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (N/A, 20)
    (2457 - 2482 @ 40), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos #####

[iwlwifi]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     34D396A2F7E52E6EF4D97D7
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005412bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00001170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00001070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

##### module parameters #####

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

##### /etc/modules #####

loop

##### blacklists #####

[/etc/modprobe.d/blacklist-libnfc.conf]
blacklist nfc
blacklist pn533

[/etc/modprobe.d/kali-blacklist.conf]
blacklist snd_pcsp
blacklist pcspkr

##### udev rules #####

egrep: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory

##### dmesg #####

[    1.515247] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    2.285490] e1000 0000:02:01.0 eth0: Intel(R) PRO/1000 Network Connection
[    4.919756] platform microcode: firmware: direct-loading firmware intel-ucode/06-45-01

########## wireless info END ############


```

---

### Post by dave131 on 2014-08-10
is it an internal adapter or a usb adapter?

If it's usb, post back the output of:

lsusb

---

### Post by dave131 on 2014-08-10
Never mind the above - I found a solution in this thread:

[http://ubuntuforums.org/showthread.php?t=2176911](http://ubuntuforums.org/showthread.php?t=2176911)

---

### Post by coffeecat on 2014-08-10
Kali Linux - *Thread moved to **Other Operating Systems and Projects**.*

@dave131, the OP had already posted the output of the wireless script which includes the output of lsusb.

---

### Post by dave131 on 2014-08-10
Sorry - I didn't know that.  Hopefully the link I posted will help.

---

### Post by Ilumizi on 2014-08-10
I already read that thread and not worked for me.

---

### Post by Ilumizi on 2014-08-10
oh I just installed Kali because in Debian and Ubuntu the card didn't work as well. I will make another script in Ubuntu if this make things easier.

---

### Post by coffeecat on 2014-08-10
> **Ilumizi said:**
> I will make another script in Ubuntu if this make things easier.

No, it will just complicate things. You need to run the script in the operating system you want help for. The Kali kernel is compiled differently from the Ubuntu one, and this may make a difference to the way the device performs and to any possible fix. Hopefully, someone with experience of that device will be able to help you.

---

### Post by Ilumizi on 2014-08-10
Can you please delete the thread?

---

