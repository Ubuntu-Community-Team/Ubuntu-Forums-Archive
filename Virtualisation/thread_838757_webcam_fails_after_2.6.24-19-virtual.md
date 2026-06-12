---
title: "webcam fails after 2.6.24-19-virtual"
date: 2008-06-23
forum: Virtualisation
---

### Post by linux6994 on 2008-06-23
After updating to 2.6.24-19-virtual my /dev/video0 is not accessable by camorama or any other video like kopete. modprobe gspca does not work since gspca module is not present. If I fall back to 2.6.24-18-generic the webcam works yet my vm will not

Any ideas? 

 lsusb
Bus 004 Device 002: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08d7 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:1617 Hewlett-Packard LaserJet 3015
Bus 001 Device 001: ID 0000:0000

---

### Post by nexxus07 on 2008-07-01
I have a similar problem. Also using the 2.6.24-19-virtual and my wireless network card is not recognized anymore (Thinkpad x41). So either networking or vm.
Haven't tried an earlier virtual kernel yet though ..

> lshw:

           *-network
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:04:02.0
                logical name: wifi0
                version: 01
                serial: 00:14:a4:3a:05:9f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.2.26 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

