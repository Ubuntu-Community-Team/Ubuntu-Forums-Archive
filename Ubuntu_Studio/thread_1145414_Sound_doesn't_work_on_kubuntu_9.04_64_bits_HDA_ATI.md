---
title: "Sound doesn't work on kubuntu 9.04 64 bits HDA ATI SB, ALC88"
date: 2009-05-01
forum: Ubuntu Studio
---

### Post by Black-Cat on 2009-05-01
Hi, the sound of my motherboard doesn't work, i have ASUS M2A-VM HDMI with Realtek ALC883, HDA ATI SB 600.
 
 - aplay -l
 **** Lista de PLAYBACK Dispositivos Hardware ****
 tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
 Subdispositivos: 1/1
 Subdispositivo #0: subdevice #0
 
 - lspci -v
 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
 Subsystem: ASUSTeK Computer Inc. Device 826d 
 Flags: bus master, 66MHz, medium devsel, latency 64
 
 00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
 Flags: bus master, 66MHz, medium devsel, latency 99 
 Bus: primary=00, secondary=01, subordinate=01, sec-latency=68 
 I/O behind bridge: 0000d000-0000dfff 
 Memory behind bridge: fda00000-fdbfffff 
 Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff 
 Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+ 
 Capabilities: [b0] Subsystem: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
 Kernel modules: shpchp 
 
 00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
 Flags: bus master, fast devsel, latency 0 
 Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
 I/O behind bridge: 0000e000-0000efff 
 Memory behind bridge: fdf00000-fdffffff 
 Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff 
 Capabilities: [50] Power Management version 3 
 Capabilities: [58] Express Root Port (Slot-), MSI 00 
 Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
 Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 826d 
 Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+ 
 Capabilities: [100] Virtual Channel <?> 
 Kernel driver in use: pcieport-driver 
 Kernel modules: shpchp 
 
 00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22 
 I/O ports at ff00 [size=8] 
 I/O ports at fe00 [size=4] 
 I/O ports at fd00 [size=8] 
 I/O ports at fc00 [size=4] 
 I/O ports at fb00 [size=16] 
 Memory at fe02f000 (32-bit, non-prefetchable) [size=1K] 
 Capabilities: [60] Power Management version 2 
 Kernel driver in use: ahci 
 
 00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16 
 Memory at fe02e000 (32-bit, non-prefetchable) [size=4K] 
 Kernel driver in use: ohci_hcd 
 
 00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17 
 Memory at fe02d000 (32-bit, non-prefetchable) [size=4K] 
 Kernel driver in use: ohci_hcd 
 
 00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18 
 Memory at fe02c000 (32-bit, non-prefetchable) [size=4K] 
 Kernel driver in use: ohci_hcd 
 
 00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17 
 Memory at fe02b000 (32-bit, non-prefetchable) [size=4K] 
 Kernel driver in use: ohci_hcd 
 
 00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18 
 Memory at fe02a000 (32-bit, non-prefetchable) [size=4K] 
 Kernel driver in use: ohci_hcd 
 
 00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19 
 Memory at fe029000 (32-bit, non-prefetchable) [size=256] 
 Capabilities: [c0] Power Management version 2 
 Capabilities: [e4] Debug port: BAR=1 offset=00e0 
 Kernel driver in use: ehci_hcd 
 
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: 66MHz, medium devsel 
 I/O ports at 0b00 [size=16] 
 Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
 Kernel driver in use: piix4_smbus 
 Kernel modules: i2c-piix4 
 
 00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16 
 I/O ports at 01f0 [size=8] 
 I/O ports at 03f4 [size=1] 
 I/O ports at 0170 [size=8] 
 I/O ports at 0374 [size=1] 
 I/O ports at f900 [size=16] 
 Kernel driver in use: pata_atiixp 
 
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
 Subsystem: ASUSTeK Computer Inc. Device 8249 
 Flags: bus master, slow devsel, latency 64, IRQ 16 
 Memory at fe020000 (64-bit, non-prefetchable) [size=16K] 
 Capabilities: [50] Power Management version 2 
 Kernel driver in use: HDA Intel 
 Kernel modules: snd-hda-intel 
 
 00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
 Subsystem: ASUSTeK Computer Inc. Device 81ef 
 Flags: bus master, 66MHz, medium devsel, latency 0 
 
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
 Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
 Bus: primary=00, secondary=03, subordinate=03, sec-latency=64 
 I/O behind bridge: 0000c000-0000cfff 
 Memory behind bridge: fde00000-fdefffff 
 Prefetchable memory behind bridge: fdd00000-fddfffff 
 
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
 Flags: fast devsel 
 Capabilities: [80] HyperTransport: Host or Secondary Interface 
 
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
 Flags: fast devsel 
 
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
 Flags: fast devsel 
 
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
 Flags: fast devsel 
 Capabilities: [f0] Secure device <?> 
 Kernel driver in use: k8temp 
 Kernel modules: k8temp 
 
 01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
 Subsystem: ASUSTeK Computer Inc. Device 826d 
 Flags: bus master, fast devsel, latency 64, IRQ 18 
 Memory at d0000000 (64-bit, prefetchable) [size=256M] 
 Memory at fdbf0000 (64-bit, non-prefetchable) [size=64K] 
 I/O ports at de00 [size=256] 
 Memory at fda00000 (32-bit, non-prefetchable) [size=1M] 
 Capabilities: [50] Power Management version 2 
 Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
 
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 
 Subsystem: ASUSTeK Computer Inc. Device 81aa
 Flags: bus master, fast devsel, latency 0, IRQ 2302
 I/O ports at ee00 [size=256]
 Memory at fdfff000 (64-bit, non-prefetchable) [size=4K]
 [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
 Capabilities: [40] Power Management version 2
 Capabilities: [48] Vital Product Data <?>
 Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
 Capabilities: [60] Express Endpoint, MSI 00
 Capabilities: [84] Vendor Specific Information <?>
 Capabilities: [100] Advanced Error Reporting <?>
 Capabilities: [12c] Virtual Channel <?>
 Capabilities: [148] Device Serial Number 68-81-ec-10-00-00-00-1a
 Capabilities: [154] Power Budgeting <?>
 Kernel driver in use: r8169
 Kernel modules: r8169
 
 03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
 Subsystem: ASUSTeK Computer Inc. Device 81fe
 Flags: bus master, medium devsel, latency 64, IRQ 22
 Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
 I/O ports at cf00 [size=128]
 Capabilities: [50] Power Management version 2
 Kernel driver in use: ohci1394
 Kernel modules: firewire-ohci, ohci1394
 
 Anyone have an idea how to solve this problem?
 
 Sorry for my bad english
 Thank you

---

