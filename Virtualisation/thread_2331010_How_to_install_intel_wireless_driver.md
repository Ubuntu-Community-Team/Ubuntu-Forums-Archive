---
title: "How to install intel wireless driver?"
date: 2016-07-17
forum: Virtualisation
---

### Post by wolfrose on 2016-07-17
Hello,

I've been looking of how to setup my wireless card to Ubuntu, so I ran lspci -vvnn and didn't find my wireless driver with the other peripherals.

And this is the result of my peripherals search:

```
00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02)
 Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] [8086:7000]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01) (prog-if 8a [Master SecP PriP])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
 Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable)
 Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
 Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable)
 Region 4: I/O ports at d000 [size=16]
 Kernel driver in use: ata_piix
 Kernel modules: pata_acpi
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef] (prog-if 00 [VGA controller])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 11
 Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
 Expansion ROM at <unassigned> [disabled]
 Kernel modules: vboxvideo
00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
 Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64 (63750ns min)
 Interrupt: pin A routed to IRQ 10
 Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=128K]
 Region 2: I/O ports at d010 [size=8]
 Capabilities: <access denied>
 Kernel driver in use: e1000
 Kernel modules: e1000
00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH VirtualBox Guest Service [80ee:cafe]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 9
 Region 0: I/O ports at d020 [size=32]
 Region 1: Memory at f0400000 (32-bit, non-prefetchable) [size=4M]
 Region 2: Memory at f0800000 (32-bit, prefetchable) [size=16K]
 Kernel driver in use: vboxguest
 Kernel modules: vboxguest
00:05.0 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 01)
 Subsystem: Dell 82801AA AC'97 Audio Controller [1028:0177]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Interrupt: pin A routed to IRQ 11
 Region 0: I/O ports at d100 [size=256]
 Region 1: I/O ports at d200 [size=64]
 Kernel driver in use: snd_intel8x0
 Kernel modules: snd_intel8x0
00:06.0 USB controller [0c03]: Apple Inc. KeyLargo/Intrepid USB [106b:003f] (prog-if 10 [OHCI])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Interrupt: pin A routed to IRQ 11
 Region 0: Memory at f0804000 (32-bit, non-prefetchable) [size=4K]
 Kernel driver in use: ohci-pci
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 0
 Kernel modules: i2c_piix4
00:0d.0 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Interrupt: pin A routed to IRQ 11
 Region 0: I/O ports at d240 [size=8]
 Region 1: I/O ports at 0000
 Region 2: I/O ports at d250 [size=8]
 Region 3: I/O ports at 0000
 Region 4: I/O ports at d260 [size=16]
 Region 5: Memory at f0806000 (32-bit, non-prefetchable) [size=8K]
 Capabilities: <access denied>
 Kernel driver in use: ahci
 Kernel modules: ahci

```


Then, I ran lspci -nn and got this result:

```
00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02)
 Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 
00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] [8086:7000]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 
00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01) (prog-if 8a [Master SecP PriP])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
 Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable)
 Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
 Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable)
 Region 4: I/O ports at d000 [size=16]
 Kernel driver in use: ata_piix
 Kernel modules: pata_acpi
 
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef] (prog-if 00 [VGA controller])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 11
 Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
 Expansion ROM at <unassigned> [disabled]
 Kernel modules: vboxvideo
 
00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
 Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64 (63750ns min)
 Interrupt: pin A routed to IRQ 10
 Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=128K]
 Region 2: I/O ports at d010 [size=8]
 Capabilities: <access denied>
 Kernel driver in use: e1000
 Kernel modules: e1000
 
00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH VirtualBox Guest Service [80ee:cafe]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 9
 Region 0: I/O ports at d020 [size=32]
 Region 1: Memory at f0400000 (32-bit, non-prefetchable) [size=4M]
 Region 2: Memory at f0800000 (32-bit, prefetchable) [size=16K]
 Kernel driver in use: vboxguest
 Kernel modules: vboxguest
 
00:05.0 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 01)
 Subsystem: Dell 82801AA AC'97 Audio Controller [1028:0177]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Interrupt: pin A routed to IRQ 11
 Region 0: I/O ports at d100 [size=256]
 Region 1: I/O ports at d200 [size=64]
 Kernel driver in use: snd_intel8x0
 Kernel modules: snd_intel8x0
 
00:06.0 USB controller [0c03]: Apple Inc. KeyLargo/Intrepid USB [106b:003f] (prog-if 10 [OHCI])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Interrupt: pin A routed to IRQ 11
 Region 0: Memory at f0804000 (32-bit, non-prefetchable) [size=4K]
 Kernel driver in use: ohci-pci
 
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 0
 Kernel modules: i2c_piix4
 
00:0d.0 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64
 Interrupt: pin A routed to IRQ 11
 Region 0: I/O ports at d240 [size=8]
 Region 1: I/O ports at 0000
 Region 2: I/O ports at d250 [size=8]
 Region 3: I/O ports at 0000
 Region 4: I/O ports at d260 [size=16]
 Region 5: Memory at f0806000 (32-bit, non-prefetchable) [size=8K]
 Capabilities: <access denied>
 Kernel driver in use: ahci
 Kernel modules: ahci 

```


Then, I just copied my wireless driver from device manager in windows 10, and searched for it in google, and found it in intel website. So, I copied the driver to Ubuntu and now I want to install it. How?

Thank you,

---

### Post by kurt18947 on 2016-07-17
> 00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH **VirtualBox Guest Service** [80ee:cafe]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 9
 Region 0: I/O ports at d020 [size=32]
 Region 1: Memory at f0400000 (32-bit, non-prefetchable) [size=4M]
 Region 2: Memory at f0800000 (32-bit, prefetchable) [size=16K]
 [B]Kernel driver in use: vboxguest
 Kernel modules: vboxguest[/B]

Is this running as a VirtualBox guest?  If so, you won't see a wireless adapter. As I understand it - and my understanding is imperfect (to say the least) VirtualBox guests establish an ethernet connection to the host's network connection, whether the host is using ethernet or wifi.

---

### Post by wolfrose on 2016-07-17
OK, so what to do?

---

### Post by howefield on 2016-07-17
Thread moved to the "*Virtualisation*" forum.

---

### Post by kurt18947 on 2016-07-17
> **wolfrose said:**
> OK, so what to do?

There isn't anything to do. The Operating system running as Vbox guest should have network connectivity via the ethernet connection to the host. Can you browse and do other networky things as is? If not there may be some issue with a virtual network adapter, there are 4. For example I could browse the web with the default network connection but couldn't print to a networked printer over a wifi connection. The solution was to make the second virtual network adapter bridged rather than the default NAT. Still no need for a wireless network adapter on the guest, the host did have a wifi connection.

---

### Post by wolfrose on 2016-07-17
Yes, of course wireless isn't so important for guest system. But it got me interested since I was the whole weekend setting and configuring my first Linux system.

There is one student in the institution I went last week I think he got it working, and should be also other students.

---

### Post by MAFoElffen on 2016-07-18
What they are trying to explain to you is the basic of virtualized networking...

Yes, you host is using wireless for it's connection right? That is why you thought to use that. But that is the host for your VM Guests.

A hypervisor, which VirtualBox is, uses the hosts network connections, and makes it transparent to it's VM Guest by using a virtual networking switch. What physical host device is used for which type of connection is configured in the main VM Manager. For instance you have internal, bridge or NAT. Defualt is usually NAT. So if you map NAT to your wireless device... then if you set your VM Guests to that (whatever you named it when you configure that), then you would give your VM Guests a connection to the internet.

To a VM Guest, the virtual machine thinks it has a wired ethernet card, of which type you can change in the VM Guest Settings. In the VM Guest settings, if you set the NIC to use NAT (or hte name you gave above), then you make the network connection from that virtual NIC, through the virtual switch setting through your host resource.

If you need that explained or translated in a less technical manner, just tell me.

Summary, you do not need to install a wireless driver in your VirtualBox VM Guest. A virtual wireless appliance is not available to a VirtualBox VM Guest machine.

---

