---
title: "Vista Drivers?"
date: 2008-10-07
forum: Windows
---

### Post by ronnielsen1 on 2008-10-07
Yeah I know. Out of curiosity I installed it on another partition (Not looking for a replacement) and it works great but there's 3 things I can't find drivers for even after an extensive google search. Anyone know where I can find vista drivers for the following?

Ethernet controller
Multimedia Audio Controller
PCI modem (don't overly care about this one)

Lspci -v is as follows

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ed98 [size=8]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff80 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at ff60 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff20 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe900000-feafffff
        Prefetchable memory behind bridge: 60000000-600fffff
        Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
        Kernel driver in use: ata_piix
        Kernel modules: piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Dell Device 019d
        Flags: medium devsel, IRQ 22
        I/O ports at eda0 [size=32]
        Kernel driver in use: i801_smbus
        Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

01:00.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at dd00 [size=256]
        Memory at fe9fdc00 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at 60000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: tulip
        Kernel modules: tulip

01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
        Subsystem: Dell Device 1000
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 16
        Memory at fe9fe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at de00 [size=256]
        Capabilities: <access denied>
        Kernel driver in use: serial

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at dcc0 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: eepro100, e100



---

### Post by fiddledd on 2008-10-07
Have a look [here](http://www.xpvistasite.com/nc100_24883.htm). I've not searched the whole site, I'll leave that to you.:)

---

### Post by ronnielsen1 on 2008-10-07
Ok, I got to thinking I had 2 net cards installed because I couldn't get the onboard card to work with linux so I changed plugins and I was able to find all my drivers online automatically with radarsync. I couldn't get the net card that works with linux to work with windows or the other way around but that's alright.

---

