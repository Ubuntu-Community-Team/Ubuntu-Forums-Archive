---
title: "Ubuntu Server install problems."
date: 2016-07-09
forum: Server Platforms
---

### Post by bultiz2 on 2016-07-09
Been running ubuntu server 16.04 on this machine before.
Then ive installed xubuntu and used it as desktop for some months. 
Now when i try to install ubuntu server again, i get like an kernel panic at the first screen when you choose language, i had the same problem with xubuntu, but on xubuntu it was an timer, that choosed english after 30 secs, and then everything was fine and install went fine.

Its like the keyboard gets disconnected at that screen, ive tested USB keyboard, PS/2 keyboard, ubuntu server 14.04, 14.10, 16.04, 16.10, and netboot variants all got the same problem..

Ive looked into kickstart, but my only gui laptop is arch linux so i cant run the package to create the ks.cfg file..

Any1 got an basic ubuntu server 16.04 iso or some other smart solution to my problem?

---

### Post by bultiz2 on 2016-07-09
Basic kickstarter 16.04 iso.. i can install xubuntu 16.04 without a problem again if just waiting out the timer at language options...

---

### Post by MAFoElffen on 2016-07-09
Moved to the Server Support Section.

You said kernel panic while trying to install Ubuntu Server 16.04 LTS. You didn't say anything about your hardware:

System make & model, CPU, GPU, RAM, HDD, preferred keybaord type (you mentioned both), Display.

What was the install iso name, medai used and method of preparing the media?

Did you check the sh1 md5 checksums of the iso file?

---

### Post by bultiz2 on 2016-07-10
lshw of another machine with exact same hardware that is running Ubuntu Server 16.04 fine.

```

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3143MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 3200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe00000-cfe7ffff ioport:1800(size=8) memory:e0000000-efffffff memory:cff00000-cff3ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82915G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:cfe80000-cfefffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0000000-f01fffff ioport:f0500000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:f0200000-f04fffff ioport:f0700000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth0
                version: 01
                serial: 00:12:79:a6:bb:f9
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5751-v3.29a ip=192.168.0.210 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 memory:f0400000-f040ffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1440(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1460(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1480(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:14a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:cff40000-cff403ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:21 ioport:1000(size=256) ioport:1400(size=64) memory:f0900000-f09001ff memory:f0900200-f09002ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:14e0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1818(size=8) ioport:1830(size=4) ioport:1820(size=8) ioport:1834(size=4) ioport:14f0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:fc00(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             capabilities: audio dvd
             configuration: status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
bultiz@UbuntuServerMC:~$ sudo lshw
[sudo] password for bultiz: 
ubuntuservermc            
    description: Low Profile Desktop Computer
    product: HP Compaq dc7100 SFF(PE218ET)
    vendor: Hewlett-Packard
    serial: CZC5030ZTV
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=low-profile cpus=1 uuid=2CB68101-476B-D911-BBDA-79A6BBF90012
  *-core
       description: Motherboard
       product: 097Ch
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC5030ZTV
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786C1 v01.05
          date: 06/16/2004
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 3200MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 1MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
             configuration: level=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory:0
          description: System Memory
          physical id: 33
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: K
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 0
             serial: C2181C65
             slot: XMM1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: K
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 1
             serial: 37862B69
             slot: XMM2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: K
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 2
             serial: C21E1C67
             slot: XMM3
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: K
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 3
             serial: C21F1C67
             slot: XMM4
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 34
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe00000-cfe7ffff ioport:1800(size=8) memory:e0000000-efffffff memory:cff00000-cff3ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82915G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:cfe80000-cfefffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0000000-f01fffff ioport:f0500000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:f0200000-f04fffff ioport:f0700000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth0
                version: 01
                serial: 00:12:79:a6:bb:f9
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5751-v3.29a ip=192.168.0.210 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 memory:f0400000-f040ffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1440(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1460(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:14a0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:cff40000-cff403ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-28-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:21 ioport:1000(size=256) ioport:1400(size=64) memory:f0900000-f09001ff memory:f0900200-f09002ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:14e0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1818(size=8) ioport:1830(size=4) ioport:1820(size=8) ioport:1834(size=4) ioport:14f0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:fc00(size=32)
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             capabilities: audio dvd
             configuration: status=nodisc
     *-scsi:1
          physical id: 4
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HDS728040PLA320
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: A63A
             serial: PFDAT0SAUB0JWX
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=fcec9843
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 7119bafb-bec7-4baa-959a-2d1e4085dffd
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-07-07 10:07:09 mount.fstype=ext2 mount.options=rw,relatime,block_validity,barrier,user_xattr,acl mounted=2016-07-04 21:39:10 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 37GiB
                capacity: 37GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: xDG3cy-HP0f-3XQO-S5FJ-tokK-ce1I-gViaRz
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: multi lvm2

```

last 2 isos tried is ubuntu-14.10-server-i386.iso & ubuntu-16.04-server-i386.iso, using "sudo dd if=image of=usbdevice" md5 checked out fine on both..
And as said, keyboard ive been trying both ps/2 and usb, same problem on both.
There is one twist to the plot, machine doesnt boot usb, so im using plop boot manager to boot usb, installed to main HDD MBR.

What really would help me is an kickstarter prepared iso for ubuntu server 16.04, english, no additional packages, i guess, rest i can setup :)

---

### Post by MAFoElffen on 2016-07-10
Your hard should be no problem supporting that...

If in a terminal in the same directory as your iso file
```
md5sum ubuntu-16.04-server-i386.iso
```
you should get this:
> [COLOR=#000000]494c03028524dff2de5c41a800674692
Please verify that.[/COLOR]

---

### Post by bultiz2 on 2016-07-10
[bultiz@archbook:Hämtningar]$ md5sum ubuntu-16.04-server-i386.iso
494c03028524dff2de5c41a800674692  ubuntu-16.04-server-i386.iso
[bultiz@archbook:Hämtningar]$ 

As said, isos is correct.. Going to try burning it to dvd media now instead of usb and see if that works better..

---

### Post by bultiz2 on 2016-07-10
Okok, optical media solved the problem... its so strange, cause last time i installed server on any of these 2 systems, i used the same method, plop boot manager to boot from usb, that was burned from md5 verified iso... 
So somewhere between plop boot manager and the language selection screen is the Kernel Panic.. buntu dists with language timer will though still continue as normal when timer runs out.. None of the server installs have the timer though..


Over & Out BultiZ!

---

### Post by MAFoElffen on 2016-07-10
...Or possibly a write problem on the USB during the dd write. dd is great for writing raw, but does not do a verify of that write. Unfortunately, it was corrupt at a point where it could not get the the SELinux menu where you could have tested the media (Test Disk) to verify the image.

Glad you are going now.

---

