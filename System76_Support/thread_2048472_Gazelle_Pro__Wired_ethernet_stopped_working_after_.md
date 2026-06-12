---
title: "Gazelle Pro : Wired ethernet stopped working after Ubuntu 12.04 upgrade"
date: 2012-08-26
forum: System76 Support
---

### Post by rajeevsingh on 2012-08-26
Hello all, 

After upgrading to Ubuntu 12.04 wired ethernet has stopped working on my System76 Gazelle Pro. Network manager displays eth0 connecting and disconnecting in a loop. It sometimes connects however then I am unable to navigate to any network site. 

The problem is with my laptop as I have tried wired connections with atleast 3 different routers with the same result.   

In the attached file I've included:  

+ ifconfig 
+ nm-tool
+ ethtool
+ lsmod
+ system logs 

Any help or pointers will be greatly appreciated! 

Regards, 
Rajeev

---

### Post by rajeevsingh on 2012-08-26
Output of lspci
===============
```
$ sudo lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GTX 460M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
04:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
```

---

### Post by danisam on 2012-08-27
I reinstall the network-manager i the same issue was solved.

---

### Post by danisam on 2012-09-10
for me the solution was this command : 

```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

The problem was that the network card after my update to precise Pangolin is allways in 10MPBS.

```
~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000020c6 (8390)
			       probe link rx_err tx_err hw
	Link detected: no


```
Regards

---

