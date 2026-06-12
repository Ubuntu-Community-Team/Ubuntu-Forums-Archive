---
title: "Server rebbot itself after shutdown"
date: 2014-01-03
forum: Server Platforms
---

### Post by kinju on 2014-01-03
Hi,

I don't understand why, but when I active the Wake On Lan option on the BIOS, my Ubuntu Server reboots automatically after shutdown.

I tried to boot on Windows 7 or on a Fedora distrib, it does not appen, the machine shutdown and don't restarts, the WOL is available.

Why booting on my Ubuntu Server makes the server restart after I shutdown it ? Is it a normal behavior ?

Even if I disconnect the RJ45 connexion, it reboots itself..

My motherbord is : Gigabyte GA-Z87X-D3H
The ethernet card : Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 04)
Ubuntu : Linux my_server 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
   Distributor ID: Ubuntu
   Description:    Ubuntu 13.10
   Release:        13.10
   Codename:       saucy

If I do "sudo ethtool -s eth0 wol d", it does not reboot, but the wol functionality is unavailable. After a reboot, it puts the flag "Wake-on: g" automatically and the server restats after a shutdown.

I don't know if it could help you :
```
user@myserver:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 2
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off (auto)
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

```

```
user@myserver:~$ sudo lspci -vvx -nn -d8086:153b
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 04)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 43
        Region 0: Memory at f0400000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at f043d000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at f080 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee002f8  Data: 0000
        Capabilities: [e0] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: e1000e
00: 86 80 3b 15 07 04 10 00 04 00 00 02 00 00 00 00
10: 00 00 40 f0 00 d0 43 f0 81 f0 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 58 14 00 e0
30: 00 00 00 00 c8 00 00 00 00 00 00 00 05 01 00 00

```

Thanks for your help,

Kin

---

