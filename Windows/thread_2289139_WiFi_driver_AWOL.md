---
title: "WiFi driver AWOL"
date: 2015-08-01
forum: Windows
---

### Post by globetrotterdk on 2015-08-01
I use Win 7 only very rarely and this has created a problem. I have misplaced the stupid CD with the driver for my "new" WiFi card on my homebuilt tower computer. Here is what I can find out using Ubuntu 14.04:
```
$ lspci -vvnn | grep -A 9 Network
07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 87
	Region 0: Memory at fe100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
```
Any ideas on narrowing down a driver for this? I think the card is Gateway branded.

---

### Post by Frogs Hair on 2015-08-14
The following command should indicate the card brand name. 
```
lspci 
``` 

Example:```
Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
```

If it is intel as in your output navigate to their driver page.

---

