---
title: "Poll on performance of Unity on your machine"
date: 2013-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by shantiq on 2013-11-02
i see for the last year and a bit many posts/threads about Unity and how well it performs on different folks' machines...     from perfection to gridlock mayhem and every shade in-between   and it seems RAM is not the issue
What i propose here is to see if there is a link between machine-specs/manufacturer/age/anything else  so on and see if any patterns emerge

**SO** please answer the poll **and** run ```
sudo lshw
``` and print results here

mine is

```
description: Desktop Computer
    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc600000-fe7fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe780000-fe7fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe77c000-fe77ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:fe8ff000-fe8fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=86.14.70.93 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8fe000-fe8fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0001219e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 686b43e4-2d7a-4c33-9c1d-c1b96a2ac679
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-19 14:05:55 filesystem=ext4 lastmountpoint=/ modified=2013-11-02 07:15:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-11-02 07:15:35 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512


```

---

### Post by rrnbtter on 2013-11-02
Greetings,
Here's mine. Running Trusty and loving it!

```
  rrnbtter-satellite-l305   
    description: Notebook
    product: Satellite L305 (Montevina_Fab)
    vendor: TOSHIBA
    version: PSLB8U-0JG037
    serial: 39339373Q
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=Intel_Mobile sku=Montevina_Fab uuid=7457A970-1025-11DE-BBA9-001E33A95B63
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: 2.20
          date: 12/09/2009
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 000000000000000000000000000000000000
             vendor: 7F7F9E0000000000
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 000000000000000000000000000000000000
             vendor: 7F7F9E0000000000
             physical id: 1
             serial: 00000000
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU             585  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 1e
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 2166MHz
          capacity: 2166MHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
        *-cache:0
             description: L2 cache
             physical id: 1f
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 21
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 20
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d3500000-d35fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:50e0(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:50c0(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:d6705c00-d6705fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:d6700000-d6703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=8192) memory:d5700000-d66fffff ioport:d0400000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:33:a9:5b:63
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:d4600000-d56fffff ioport:d1500000(size=16777216)
           *-network
                description: Wireless interface
                product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:d2:3a:23:f9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.12.0-1-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d4600000-d460ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:d3600000-d45fffff ioport:d2500000(size=16777216)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:50a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5060(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5040(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d6705800-d6705bff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:5108(size=8) ioport:511c(size=4) ioport:5100(size=8) ioport:5118(size=4) ioport:5020(size=32) memory:d6705000-d67057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d6706000-d67060ff ioport:5000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000BEVT-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WXC1AC048352
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=33ec33ec
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: d85c1249-346e-48e9-b26e-f1a97248068c
                size: 2860MiB
                capacity: 2860MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: Linux filesystem partition
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot
                version: 1.0
                serial: 30b02ef4-897f-4099-8523-d022058521d5
                size: 381MiB
                capacity: 381MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 modified=2013-11-01 18:40:27 mount.fstype=ext2 mount.options=rw,relatime,errors=continue,user_xattr,acl state=mounted
           *-volume:2
                description: Linux filesystem partition
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: b425858c-130d-4f84-b423-a86ac05fe435
                size: 4768MiB
                capacity: 4768MiB
                capabilities: primary extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 modified=2013-11-01 18:40:27 mount.fstype=ext2 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl mounted=2013-11-01 18:39:59 state=mounted
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 457GiB
                capacity: 457GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /usr
                   capacity: 13GiB
                   configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 443GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RW  DVRTD08A
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.54
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 7580MiB (7948MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=00057037
           *-volume
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/rrnbtter/WCSD
                version: 1.0
                serial: eac16a80-7bbf-45db-8bf6-47fb94cafbe1
                size: 7579MiB
                capacity: 7579MiB
                capabilities: primary extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 label=WCSD modified=2013-11-01 18:41:16 mount.fstype=ext2 mount.options=rw,nosuid,nodev,relatime,errors=continue,user_xattr,acl state=mounted
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define4
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define5
       serial: OEM_Define2
       capacity: 75mWh
 
```

---

### Post by Werne on 2013-11-02
Works like a charm for me.

lshw output:

```

    description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=9402DE03-8004-7A05-6706-B60700080009
  *-core
       description: Motherboard
       product: 970A-UD3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: FC
          date: 01/28/2013
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD FX(tm)-8320 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-8320 Eight-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 4200MHz
          capacity: 4200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr tbm topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=8 enabledcores=8 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: JM1333KLN-2G
             vendor: Transcend
             physical id: 0
             serial: 0009F318
             slot: Node0_Dimm0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 533 MHz (1.9 ns)
             product: Q1010074
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: Node0_Dimm1
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: JM1333KLN-2G
             vendor: Transcend
             physical id: 2
             serial: 0009F7C5
             slot: Node0_Dimm2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 533 MHz (1.9 ns)
             product: Q1010074
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: Node0_Dimm3
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices [AMD] nee ATI
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: RD990 I/O Memory Management Unit (IOMMU)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 ioport:e000(size=4096) memory:fea00000-feafffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Cape Verde [Radeon HD 7700 Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:77 memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:fea40000-fea5ffff
           *-multimedia
                description: Audio device
                product: Advanced Micro Devices [AMD] nee ATI
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:76 memory:fea60000-fea63fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 memory:fe900000-fe9fffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:74 memory:fe900000-fe907fff
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:53 ioport:d000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 06
                serial: 94:de:80:7a:67:b6
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:73 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:3
             description: PCI bridge
             product: RD890 PCI to PCI bridge (external gfx1 port A)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:54 memory:fe800000-fe8fffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:75 memory:fe800000-fe807fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0b000-feb0b3ff
           *-disk:0
                description: ATA Disk
                product: Hitachi HDS72101
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JP4O
                serial: JPS930N12BW3XL
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 sectorsize=512 signature=000a240e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /home
                   version: 1.0
                   serial: bbdb3193-d49f-4469-afea-ac85bf043227
                   size: 881GiB
                   capacity: 881GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2013-07-22 16:08:46 filesystem=ext4 label=home lastmountpoint=/home modified=2013-11-02 15:49:17 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noatime,nodiratime,user_xattr,barrier=1,data=ordered mounted=2013-11-02 15:02:25 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 32564f60-4062-467b-b598-884071d5307c
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-07-24 17:52:44 filesystem=ext4 label=Debian lastmountpoint=/ modified=2013-11-02 15:50:24 mount.fstype=ext4 mount.options=rw,noatime,nodiratime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2013-11-02 15:50:24 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: d1935543-a673-4944-84ef-adf70f0fabc5
                   size: 1441MiB
                   capacity: 1441MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7243S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom5
                logical name: /dev/cdrw5
                logical name: /dev/dvd5
                logical name: /dev/dvdrw5
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: Hitachi HDT72103
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: ST2O
                serial: STF202ML367TLP
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 sectorsize=512 signature=5332bf10
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 5c1c-a8a2
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2013-10-14 06:16:10 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: 30aea98e-0669-7d40-8d92-7595fc4d76af
                   size: 297GiB
                   capacity: 297GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2013-10-14 06:16:12 filesystem=ntfs state=clean
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb0a000-feb0afff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb09000-feb090ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb08000-feb08fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb07000-feb070ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fe700000-fe7fffff
           *-network
                description: Wireless interface
                product: AR9227 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: wlan1
                version: 01
                serial: a0:f3:c1:87:0f:7b
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-4-amd64 firmware=N/A ip=192.168.1.2 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:21 memory:fe700000-fe70ffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:05:0e.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:22 memory:fe710000-fe7107ff ioport:c000(size=128)
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb06000-feb06fff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by BigSilly on 2013-11-02
Well, I voted great and all seemed well, but suddenly I'm finding the Dash really peculiar. If I launch programs from the sidebar they launch quickly, but when launching them from within the dash there's a bit of a delay. Some programs just aren't performing as well as 13.04 too. Lots of hangs, leaving me having to force quit a few times. I've tried both the current Nvidia driver and the update one, but performance is the same. Spec below. Can I change my vote to "There are some holdups ... things do not feel all in sync/smooth"...?

:(

---

### Post by shantiq on 2013-11-02
hmmmm    i am definitely going to keep an eye on the RAM of the guys who say all fine ...   still feel it might be of import here   mine  size: 2.5GiB

so far
size: 4GiB
size: 8GiB
size: 4GiB


Please vote **and** add > sudo lshw results   thanx

---

### Post by Gyokuro on 2013-11-03
It's got faster but the old memory problem remains - Debian Wheezy with Gnome(v.3.4) never swaps - same machine with Unity and it's swaps after some minutes (8GB RAM) and it feels more sluggish - stay with Gnome.

---

### Post by echotech2 on 2013-11-03
Only one very slight bump (I think).  I'll post a question in the appropriate forum in a while.

```
scamper                   
    description: Desktop Computer
    product: EP43-DS3L ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-001FD08E7DF2
  *-core
       description: Motherboard
       product: EP43-DS3L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6
          date: 07/22/2008
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU
          slot: Socket 775
          size: 2500MHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 3MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:ec000000-eeffffff ioport:d8000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GK106 [GeForce GTX 650 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:ec000000-ecffffff memory:d8000000-dfffffff memory:e0000000-e1ffffff ioport:b000(size=128) memory:e2000000-e207ffff
           *-multimedia
                description: Audio device
                product: GK106 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:ee000000-ee003fff
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e100(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:e200(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e000(size=32)
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f1104000-f11043ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f1100000-f1103fff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:f1200000-f13fffff ioport:f1400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:ef000000-efffffff ioport:f1600000(size=2097152)
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm pciexpress bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:16 ioport:c000(size=8) ioport:c100(size=4) ioport:c200(size=8) ioport:c300(size=4) ioport:c400(size=16)
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:f0000000-f0ffffff ioport:f1000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:d0:8e:7d:f2
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:44 ioport:d000(size=256) memory:f1010000-f1010fff memory:f1000000-f100ffff memory:f1020000-f102ffff
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e300(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e400(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e500(size=32)
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f1105000-f11053ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:e600(size=8) ioport:e700(size=4) ioport:e800(size=8) ioport:e900(size=4) ioport:ea00(size=32) memory:f1106000-f11067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f1107000-f11070ff ioport:500(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG SP2504C
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: VT10
             serial: S09QJ1JL305282
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=d209820e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 748850a4-9582-4274-969d-c4a41aa2d59a
                size: 23GiB
                capacity: 23GiB
                capabilities: primary bootable journaled extended_attributes large_files recover extents ext4 ext2 initialized
                configuration: created=2008-11-02 13:02:55 filesystem=ext4 lastmountpoint=/ modified=2013-11-01 16:55:22 mount.fstype=ext4 mount.options=rw,noatime,errors=remount-ro mounted=2013-11-01 16:55:23 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: a38261d1-6941-4fca-95e5-8dd70a23bc9a
                size: 9789MiB
                capacity: 9789MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: f628646e-d2b5-4966-8fd0-781054179573
                size: 48GiB
                capacity: 48GiB
                capabilities: primary journaled extended_attributes large_files recover extents ext4 ext2 initialized
                configuration: created=2008-11-02 13:03:00 filesystem=ext4 lastmountpoint=/home modified=2013-11-01 16:55:23 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,noatime mounted=2013-11-01 16:55:23 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sda4
                logical name: /media/sda4
                version: 1.0
                serial: bdc434fa-1fae-429d-931a-c94b9bd40bf5
                size: 10001MiB
                capacity: 10001MiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-03-20 10:49:16 filesystem=ext4 label=caches lastmountpoint=/media/sda4 modified=2013-11-01 16:55:24 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,noatime mounted=2013-11-01 16:55:24 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Backup+ BK
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             version: 0409
             serial: NA52M4GW
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 sectorsize=512 signature=00050e93
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/sdb1
                version: 1.0
                serial: ee94a57b-777c-4b55-b0bd-336783121283
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-03-30 09:10:54 filesystem=ext4 lastmountpoint=/media/sdb1 modified=2013-11-01 16:55:23 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,noatime,data=writeback mounted=2013-11-01 16:55:23 state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GH22LS30
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:3
          physical id: 5
          logical name: scsi6
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250310AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 3.AA
             serial: 6RYAHEDC
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000221f0
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/sdc1
                version: 1.0
                serial: 2cc15ef2-164e-464a-8fb8-d4af8087b7ad
                size: 223GiB
                capacity: 223GiB
                capabilities: primary bootable journaled extended_attributes large_files recover extents ext4 ext2 initialized
                configuration: created=2008-10-31 16:57:14 filesystem=ext4 label=data lastmountpoint=/media/sdc1 modified=2013-11-01 16:55:24 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,noatime mounted=2013-11-01 16:55:24 state=mounted
dave@scamper:~$ 
 
```

---

### Post by Werne on 2013-11-03
@Shantiq It's not the RAM that matters, it's the way Ubuntu swaps. Once you hit 40% RAM usage (which I often do since I compile in tmpfs) it will start swapping, even though I have more than 4GB RAM free. On 2 GB that's 800MB, if it comes close to it, it will swap. That affects performance since all that stuff in the swap partition needs to be moved back to RAM when you need it, instead of staying there in the first place since there's plenty of room available. I set swap to 5%, so when I hit 7.6GB it'll start swapping.

Then there's the CPU and graphics, back when i had a Core 2 Duo E4500, Radeon 4350 and 2GB RAM it would get abused by Unity, each one of those effects would yank up the CPU usage to 50-70% because Compiz was very CPU heavy when fglrx is installed and all those fancy effects didn't help one bit. Unity worked smoother with radeon than fglrx due to that high CPU usage, which doesn't matter one bit on an octa-core though.

@Gyokuro Check mount, see how much space has been mounted as tmpfs and where, that tends to happen when those locations get filled up. If it affects your performance, adjust the swappiness to your liking and/or change the tmpfs size.

---

### Post by SantaFe on 2013-11-03
Tried Unity, laptop didn't like it for some reason.  Switched to Kubuntu 13.10 & added LXDE & KDE and runs like a champ.

```

santafe-studio-1745       
    description: Portable Computer
    product: Studio 1745 (Null)
    vendor: Dell Inc.
    version: A04
    serial: 4Y7FMK1
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=portable cpus=2 family=Studio sku=Null uuid=44454C4C-5900-1037-8046-B4C04F4D4B31
  *-core
       description: Motherboard
       product: 0G914P
       vendor: Dell Inc.
       physical id: 0
       version: A04
       serial: .4Y7FMK1.CN129619A60681.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A04
          date: 03/22/2011
          size: 118KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1066 MHz (0.9 ns)
             product: M471B5673EH1-CF8
             vendor: Samsung
             physical id: 0
             serial: 6270D497
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1066 MHz (0.9 ns)
             product: M471B5673EH1-CF8
             vendor: Samsung
             physical id: 1
             serial: 6270D491
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-generic UNCLAIMED
          physical id: 2
          bus info: parisc@1
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:f2400000-f27fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f2100000-f21fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:f2a04800-f2a04bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:f2a00000-f2a03fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:5000(size=4096) memory:f2200000-f22fffff ioport:c0400000(size=2097152)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:fb:9f:d0:58
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-13-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:49 memory:f2200000-f2201fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:6000(size=4096) memory:c0600000-c07fffff ioport:c0800000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:7000(size=4096) memory:f2300000-f23fffff ioport:c0a00000(size=2097152)
           *-firewire
                description: FireWire (IEEE 1394)
                product: 1394 OHCI Compliant Host Controller
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:f2301000-f2301fff memory:f2300000-f23007ff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 0.1
                bus info: pci@0000:14:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:f2303800-f2303bff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/MSPRO/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 0.2
                bus info: pci@0000:14:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f2302000-f2302fff memory:f2303000-f23037ff memory:f2300800-f2300fff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:2000(size=4096) memory:f4000000-f5ffffff ioport:f0000000(size=33554432)
        *-pci:5
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:3000(size=4096) memory:c0c00000-c10fffff ioport:f2000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:20:00.0
                logical name: eth0
                version: 03
                serial: 00:24:e8:da:24:ea
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:47 ioport:3000(size=256) memory:f2004000-f2004fff memory:f2000000-f2003fff memory:f2020000-f203ffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f2a04c00-f2a04fff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f2a04000-f2a047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c1100000-c11000ff ioport:1c00(size=32)
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9500420AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0003
             serial: 5VJ1C1F8
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=7c293560
           *-volume:0
                description: Windows FAT volume
                vendor: Dell 8.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT16
                serial: 3030-3030
                size: 39MiB
                capacity: 39MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=DellUtility
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 3287-75f2
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-08-25 12:36:06 filesystem=ntfs label=RECOVERY state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /media/santafe/OS
                version: 3.1
                serial: 4e75dec2-0317-cf46-a332-85ed7f796f4c
                size: 260GiB
                capacity: 260GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-08-25 12:36:10 filesystem=ntfs label=OS modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 190GiB
                capacity: 190GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 186GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 4055MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 4
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GA11N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: A101
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
  *-battery
       description: Lithium Ion Battery
       product: Dell
       vendor: Dell
       physical id: 1
       slot: Rear
       capacity: 57720mWh
       configuration: voltage=11.1V


```

And yes, I have a 64 bit system & a 32 bit O/S.  Downloaded the wrong version, but seems to run fine so see no reason to reformat. ;)

---

### Post by shantiq on 2013-11-03
> **Werne said:**
> @Shantiq It's not the RAM that matters, it's the way Ubuntu swaps. Once you hit 40% RAM usage (which I often do since I compile in tmpfs) it will start swapping, even though I have more than 4GB RAM free. On 2 GB that's 800MB, if it comes close to it, it will swap. That affects performance since all that stuff in the swap partition needs to be moved back to RAM when you need it, instead of staying there in the first place since there's plenty of room available. I set swap to 5%, so when I hit 7.6GB it'll start swapping.

Then there's the CPU and graphics, back when i had a Core 2 Duo E4500, Radeon 4350 and 2GB RAM it would get abused by Unity, each one of those effects would yank up the CPU usage to 50-70% because Compiz was very CPU heavy when fglrx is installed and all those fancy effects didn't help one bit. Unity worked smoother with radeon than fglrx due to that high CPU usage, which doesn't matter one bit on an octa-core though.

@Gyokuro Check mount, see how much space has been mounted as tmpfs and where, that tends to happen when those locations get filled up. If it affects your performance, adjust the swappiness to your liking and/or change the tmpfs size.


thanx for ALL  input guys  ....    it really helps understand what is going on here   ..    Werne this is technical but i kind of get the gist ...     and what you say makes much sense ....

---

### Post by bobblex on 2013-11-03
Doesn't work so well on my old Dell.

```
 
description: Desktop Computer
    product: Dimension 2350
    vendor: Dell Computer Corporation
    version: A02
    serial: 7WZL521
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=44454C4C-5700-105A-804C-B7C04F353231
  *-core
       description: Motherboard
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Mitac International
          physical id: 1
          version: A02
          date: 03/24/2003
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 1800MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1536MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d8000000-dbffffff
        *-display UNCLAIMED
             description: Display controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d7ffffff memory:e0000000-e007ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e0080000-e00803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:dc000000-dfffffff memory:b0000000-cfffffff
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: NVIDIA Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:dc000000-dcffffff memory:80000000-9fffffff memory:dd000000-ddffffff memory:b0000000-b001ffff
           *-network
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:01:06.0
                logical name: eth0
                version: 10
                serial: 00:e2:8c:50:2f:c1
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
                resources: irq:18 ioport:c000(size=256) memory:df000000-df0000ff memory:b0020000-b003ffff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:60000000-600003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:e0081000-e00811ff memory:e0082000-e00820ff
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: WDC WD800BB-75JH
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 06.0
             serial: WD-WCAM9N537649
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=76577657
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: e4ad4eec-3163-b240-a11b-452a8656452f
                size: 74GiB
                capacity: 74GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-01-12 03:58:38 filesystem=ntfs state=clean
        *-disk:1
             description: ATA Disk
             product: Maxtor 98196H8
             vendor: Maxtor
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: ZAH8
             serial: V80B5A9C
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ebd6d
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                logical name: /boot
                version: 1.0
                serial: 8277ccba-d5e7-4a64-af9d-b6ff1720e8fd
                size: 475MiB
                capacity: 475MiB
                capabilities: primary bootable journaled extended_attributes recover ext3 ext2 initialized
                configuration: created=2013-10-24 19:47:18 filesystem=ext3 modified=2013-11-02 12:34:58 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered mounted=2013-11-02 12:34:58 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sdb2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 1952MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sdb6
                   logical name: /
                   capacity: 19GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sdb7
                   logical name: /home
                   capacity: 53GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NS90
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: IN01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```

---

### Post by shantiq on 2013-11-03
yes Bobblex and RAM size: 1536MiB ;   so i am listening to the no it is not RAM-related info 
but like myself low RAM for 2013 and not a smooth experience  ,,,     see what we get we have many more in   ,,,

---

### Post by mörgæs on 2013-11-03
Bobblex, your problem is not memory but a weak graphics card not suitable for Ubuntu. Lubuntu 13.10 is a good choice.

As this is not for support please open a new thread if you need more advice.

---

### Post by richardsdma on 2013-11-03
on my machine, unity works good,

a have a dell inspiron 1521 amd dual core 1.9 ghz and ati mobility radeon 1270. only ONE GB of ram. 

be very carefull, sometimes, not so often, compiz use at very start, 50 % of cpu.....in this case, unity is unuseable. you need to restart lightdm to solve the problem (at least in my case!)
 
so, whan unity seems sluggish, just open the terminal and check using "top" command. in idle, you should have 0-1%.

---

### Post by Gyokuro on 2013-11-03
> **Werne said:**
> @Shantiq It's not the RAM that matters, it's the way Ubuntu swaps. Once you hit 40% RAM usage (which I often do since I compile in tmpfs) it will start swapping, even though I have more than 4GB RAM free. On 2 GB that's 800MB, if it comes close to it, it will swap. That affects performance since all that stuff in the swap partition needs to be moved back to RAM when you need it, instead of staying there in the first place since there's plenty of room available. I set swap to 5%, so when I hit 7.6GB it'll start swapping.

Then there's the CPU and graphics, back when i had a Core 2 Duo E4500, Radeon 4350 and 2GB RAM it would get abused by Unity, each one of those effects would yank up the CPU usage to 50-70% because Compiz was very CPU heavy when fglrx is installed and all those fancy effects didn't help one bit. Unity worked smoother with radeon than fglrx due to that high CPU usage, which doesn't matter one bit on an octa-core though.

@Gyokuro Check mount, see how much space has been mounted as tmpfs and where, that tends to happen when those locations get filled up. If it affects your performance, adjust the swappiness to your liking and/or change the tmpfs size.

Thank you but I'm able to fix problems myself but maybe I was not clear - Unity is a big resource hog as Gnome3 is using much less memory as Compiz/Unity and I have checked launchpad reports and it's a known problem but even with the latest Unity the problem remains (e.g. [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1127959](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1127959)) nor in this regard I can see that anything got fixed.

---

### Post by pqwoerituytrueiwoq on 2013-11-03
it does run just fine for me, dont use unity but it does run just fine, used the open source driver.
i am not using a entry level system though (Phenom II 965 @4.2GHz w/ Nvidia GTX 550 TI)
```
m4a79xtd-evo              
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=0059001E-8C00-003D-1ECB-BCAEC5B31F76
  *-core
       description: Motherboard
       product: M4A79XTD EVO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0X
       serial: MT700CK19501272
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 2102
          date: 06/17/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 965 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 965 Processor
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 4200MHz
          capacity: 4200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
          configuration: cores=4 enabledcores=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci:0
          description: Host bridge
          product: RD780 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RX780/RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:f8000000-fbdfffff ioport:d4000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF116 [GeForce GTX 550 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:43 memory:f8000000-f9ffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:cc00(size=128) memory:fbd00000-fbd7ffff
           *-multimedia
                description: Audio device
                product: GF116 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:fbdfc000-fbdfffff
        *-pci:1
             description: PCI bridge
             product: RX780/RD790 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fbe00000-fbefffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:fbeff800-fbefffff ioport:d800(size=256)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:f7fffc00-f7ffffff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:f7ffd000-f7ffdfff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:f7ffe000-f7ffefff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f7fff800-f7fff8ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f7ffb000-f7ffbfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f7ffc000-f7ffcfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:f7fff400-f7fff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f7ff4000-f7ff7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-network
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:03:06.0
                logical name: eth0
                version: 10
                serial: 00:e0:4c:78:37:ce
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.50 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:21 ioport:e800(size=256) memory:fbfffc00-fbfffcff memory:fbfc0000-fbfdffff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f7ffa000-f7ffafff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Corsair Nova 2 S
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 1.3.
             serial: 12036509000013450523
             size: 27GiB (30GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ef58a
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: d842f936-1037-4cd8-96b1-b43e104b4bb0
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-05-01 11:31:02 filesystem=ext4 label=Root lastmountpoint=/ modified=2013-10-25 21:16:56 mount.fstype=ext4 mount.options=rw,noatime,discard,errors=remount-ro,data=ordered mounted=2013-10-25 21:17:00 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 15.0
             serial: WD-WCAYUY966338
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=1e38adcd-cdf7-4355-a43c-276becf26c5e sectorsize=512
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /var
                version: 1.0
                serial: 3d1dd4e3-d423-4802-b52a-aa74d6fdc8bd
                size: 2557MiB
                capacity: 2557MiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-05-01 11:53:00 filesystem=ext4 label=Var lastmountpoint=/var modified=2013-10-28 03:49:18 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-25 21:17:00 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                logical name: /home
                logical name: /root
                version: 1.0
                serial: b8362e2b-2cdb-40f4-a2a8-a9ed1207cb81
                size: 230GiB
                capacity: 230GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-05-01 11:40:48 filesystem=ext4 label=Home lastmountpoint=/root modified=2013-10-28 12:59:11 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-28 12:59:11 state=mounted
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sdb3
                logical name: /var/cache/apt/archives
                version: 1.0
                serial: 39fbf8c6-5d6f-49b2-8433-c06f58278d36
                size: 1536MiB
                capacity: 1537MiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-05-03 09:35:55 filesystem=ext4 label=Archives lastmountpoint=/var/cache/apt/archives modified=2013-10-28 12:59:14 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-28 12:59:14 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@4:0.0.0,4
                logical name: /dev/sdb4
                logical name: /mnt/virtual_box
                version: 1.0
                serial: 03cc0da7-dc02-4f82-832a-805f8c2e6c4d
                size: 183GiB
                capacity: 183GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-05-03 02:27:43 filesystem=ext4 label=VirtualBox lastmountpoint=/mnt/virtual_box modified=2013-10-28 12:59:14 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-28 12:59:14 state=mounted
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@4:0.0.0,5
                logical name: /dev/sdb5
                logical name: /mnt/iso
                version: 1.0
                serial: 156f2dd4-0bfe-414c-95a8-080973d9bedc
                size: 31GiB
                capacity: 31GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-05-03 09:34:26 filesystem=ext4 label=DiskImages lastmountpoint=/mnt/iso modified=2013-10-28 12:59:14 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-28 12:59:14 state=mounted
           *-volume:5
                description: Linux swap volume
                vendor: Linux
                physical id: 6
                bus info: scsi@4:0.0.0,6
                logical name: /dev/sdb6
                version: 1
                serial: edcffc51-e736-474e-b338-18182e372f87
                size: 16GiB
                capacity: 16GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4096
```

---

### Post by bobblex on 2013-11-04
> **mörgæs said:**
> Bobblex, your problem is not memory but a weak graphics card not suitable for Ubuntu. Lubuntu 13.10 is a good choice.



Yep...That's what I did after trying Unity.  Lubuntu 13.10 with some tweaks is what I run now.

---

### Post by philinux on 2013-11-04
If swap is a problem turn down swappiness to say 10%. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Forgot. Unity slick on my acer 1410. Not at home so no lshw.

---

### Post by Old_Grey_Wolf on 2013-11-04
On my laptop, after a boot the applications are slow to load the first time. After the first start the applications load fine.

```
    
description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5864MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:49 memory:d0705000-d070500f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d070a000-d070a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:d0700000-d0703fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:d0600000-d06fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1030 [Rainbow Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 34
                serial: 4c:eb:42:6e:0c:3f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-55-generic firmware=18.168.6.1 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:47 memory:d0600000-d0601fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:d0500000-d05fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:d0500000-d0501fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) ioport:d0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 05
                serial: 84:8f:69:d0:ea:45
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.12 latency=0 multicast=yes port=MII speed=100Mbit/s
                resources: irq:46 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0709000-d07093ff
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:d0708000-d07087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0704000-d07040ff ioport:efa0(size=32)

```

---

### Post by monkeybrain20122 on 2013-11-04
> **Gyokuro said:**
>  Unity is a big resource hog as Gnome3 is using much less memory as Compiz/Unity and I have checked launchpad reports and it's a known problem but even with the latest Unity the problem remains (e.g. [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1127959](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1127959)) nor in this regard I can see that anything got fixed.

Not in my experience. Compiz uses ~ 0.2% cpu in my system when idle. The only DE which is obviously hogging resources is KDE on my machines.

---

### Post by mbeltov on 2013-11-05
Unity works fine on my machine and I'm happy with the performance of the system. 
```
ubuntu
    description: Desktop Computer
    product: P35-DS4 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-001A4D4563C7
  *-core
       description: Motherboard
       product: P35-DS4
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F14
          date: 06/19/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU
          slot: Socket 775
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 4MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1,2 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 800 MHz (1,2 ns)
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:f4000000-f5ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Turks XT [Radeon HD 6670/7670]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:46 memory:e0000000-efffffff memory:f5000000-f501ffff ioport:b000(size=256) memory:f4000000-f401ffff
           *-multimedia
                description: Audio device
                product: Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:47 memory:f5020000-f5023fff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e100(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:e200(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e000(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f8205000-f82053ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f8200000-f8203fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:a000(size=4096) memory:7ff00000-800fffff ioport:80100000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:f8000000-f80fffff ioport:80300000(size=2097152)
           *-storage
                description: SATA controller
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:16 memory:f8000000-f8001fff
           *-ide
                description: IDE interface
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:c000(size=8) ioport:c100(size=4) ioport:c200(size=8) ioport:c300(size=4) ioport:c400(size=16)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:f6000000-f7ffffff ioport:80500000(size=3145728)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 01
                serial: 00:1a:4d:45:63:c7
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:44 ioport:d000(size=256) memory:f7000000-f7000fff memory:80500000-8050ffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e300(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e400(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e500(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f8204000-f82043ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f8100000-f81fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:18 memory:f8104000-f81047ff memory:f8100000-f8103fff
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) ioport:f100(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f8206000-f82060ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:e700(size=8) ioport:e800(size=4) ioport:e900(size=8) ioport:ea00(size=4) ioport:eb00(size=16) ioport:ec00(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000ABYS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 12.0
             serial: WD-WCAPW2606542
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00020fba
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 3679-e0ac
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-01-23 23:42:00 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: b2a36850-76b4-794f-8667-213d213eafac
                size: 279GiB
                capacity: 279GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-01-23 23:42:04 filesystem=ntfs state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                size: 186GiB
                capacity: 186GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2044MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 184GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD-RW  DVR-110D
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.41
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
```

---

### Post by mc4man on 2013-11-06
Hey shantiq, 
running quite well here on my latest laptop (i7),  which is less than a yr. old,  vs. my 5+ yr. old one (core2duo),  where unity session is starting to get slow.
The difference is from top to bottom, all apps open in a sec. or less, installing, compiling, ect. is is not even close.

The laptop has a gtx 660m but I don't bother with it in Ubuntu, the intel 4000 works absolutely fine for everything I'd do on the laptop, plus have enabled vdpau for intel (vaapi) for use with mplayer & hardware accelerated flash.

(- haven't even bothered to install internally as I have some significant uses of win 7 so am running ubuntu thru  high speed/quality external ssd (angelbird

---

### Post by shantiq on 2013-11-07
thanx mc4man  

 this in a way is where i think the whole issue of runs well or doesnt is located
> running quite well here on my latest laptop (i7),  which is less than a  yr. old,  vs. my 5+ yr. old one (core2duo),  where unity session is  starting to get slow.

i always wondered with every new version of ubuntu ;   how long can i do this until the software has become too slick for my hardware ?    [average Packard Bell 2005]

the answer is a few years back;  i realize now usin lxde  everything loads shuts downs snaps like a well-trained Alsatian all processes take a fraction of the time they used to  [and i use Rosegarden which uses virtually all cpu]   that even recent Gnome was too heavy for my specs   and Unity off the scales for my machine

So far in the smooth-running voters only one has less than 4Gig of Ram   which means machines are fairly recent     mine 2,5 with a maximum of 3

i wish i had understood that 3 or so years ago;   would have saved a lot of hours!

What you say about your 2 machines here reinforces my understanding of this DE issue   

On Linux you find things out through trial and error ::]]    Simple equation is: default newer versions of the distro are really best suited to newer machines; but can work extremely well with a lighter DE [xcfe4; openbox; lxde]     ...    der!!   should have worked it out before but did not ..   ::]]

---

### Post by Werne on 2013-11-07
> **shantiq said:**
> i always wondered with every new version of ubuntu ;   how long can i do this until the software has become too slick for my hardware ?    [average Packard Bell 2005]

the answer is a few years back;  i realize now usin lxde  everything loads shuts downs snaps like a well-trained Alsatian all processes take a fraction of the time they used to  [and i use Rosegarden which uses virtually all cpu]   that even recent Gnome was too heavy for my specs   and Unity off the scales for my machine

So far in the smooth-running voters only one has less than 4Gig of Ram   which means machines are fairly recent     mine 2,5 with a maximum of 3

I see you've been mostly fixated on the RAM, but thing is, the RAM alone is not the thing you should be looking at, it's the entire PC.

The CPU usage on an old processor is high, because the CPU can do less work per cycle. On my FX 8320 @4.2GHz with 8GB DDR3-1333 the total CPU usage is around 2-3% on idle, just the DE and two conky windows. On my wife's i5-3570K @4.1GHz with 32GB DDR3-1600 the CPU usage is nearly the same, even though it has 4 cores, because it can do over 50% more work per cycle. Ye olde AMD Athlon 64 3200+ with 4GB DDR-400 can barely run Unity. On my old Core 2 Duo E4500 @2.86GHz with 2GB DDR2-800 the CPU usage is 8-16%, because those jobs that are spread evenly among 8 cores on my FX, were crammed into two 50% weaker cores than the Piledriver's, which resulted in less CPU power for other programs.

GPU also gets stressed by Compiz effects, especially with transparency and blur. Those are real-time 3D processes which can bog down low-end cards and chipsets and also stress the CPU, even my overclocked Radeon 7770 has trouble with Compiz once I turn on transparency and blur and my old Radeon 4350 was running it decently with a lot of effects disabled. But the problem for my 7770 are the power states and the slight stutter happens once card switches from it's lowest power state to the highest, I'm already familiar with that and I know it can't be avoided since I can't turn the pstates off like I do on the CPU.

RAM also plays a role, newer more fancy DEs like Unity tend to be RAM heavy as well as CPU/GPU heavy, meaning that they will sooner reach the point at which the system will begin swapping, which I already said is 40% RAM. On a machine with 2GB RAM the swapping begins one RAM usage hits 800MB (which is more than what Unity and Compiz use on my machine), on a 4GB machine it will begin at 1.8GB and on an 8GB machine that happens at 3.6GB. RAM frequency and latency affect system performance as well, but not by a large margin when compared to faster/slower memory in the same generation.

Lighter DEs like LXDE, XFCE, GNOME 3 Classic, MATE, etc. will use less resources because they are built that way. Debian 7.2 LXDE uses some 84MB RAM in a live session on my PC, uses about 0-1% total CPU (some cores are at 1%, some at 0% at nearly all times) and the graphics card is barely even used. That's why LXDE/XFCE and so on are snappy, they deliver almost all CPU cycles and resources to the program you use and a more resource-intensive desktop can't perform the same.

On a PC like mine (octa-core AMD FX 8320, 8GB DDR3-1333 RAM, Radeon 7770 1GB GDDR5), difference between LXDE/XFCE and Unity/GNOME Shell are minimal due to a lot of spare room in every department, but on an older machine or a newer low-end one, the performance difference will be clear. I see you have a single-core 2.2GHz AMD Athlon 64 3400+ with 2.5GB DDR-333 RAM and Nvidia GeForce 8400 256/512MB DDR2, which is weak in every regard - old single-core CPU, slow RAM, slow low-end card, it was slow 5 years ago and it's not getting any faster.

Your problem with bad GUI performance is not the RAM size, the entire PC is the problem. A first-gen Athlon 64 is far behind a second-gen Intel Core (even low-end C2Ds are over 200% faster), not to mention a second-gen Bulldozer or a second/third/fourth-gen i7 (which are likely over 1500% faster). 2.5GB DDR-333 and DDR-400 are a lot slower than DDR2-400, DDR2-667 and DDR2-800 (by 50% or more), DDR2-800 is even slower than DDR3-800 and higher (by 50% or more). A GeForce 8400 GS is slower than today's HTPC cards like Radeon 5450 and Radeon 6450 (by 50% or more).

You can't expect a modern GUI to run the same on a single-core Athlon and octa-core Piledriver, or any of your components compared to modern ones. It's like trying to match the top speed of a Pagani Zonda with a 50$ bicycle - not gonna happen.

---

### Post by philinux on 2013-11-07
My old desktop pc has 2 gig ram. And this 3 year old acer 1410 has 2 gig ram. Both ddr2. Unity runs just fine on both. The system is using less ram now than 2 years ago at startup.  (both 64 bit by the way).

My guess is the devs have tuned up compiz and unity.

---

### Post by shantiq on 2013-11-07
yep   Werne    i only talk about RAM   because that is the only indicator i half understand  :::]]]   not much of a techy


thanx for all detailed explanations   it really helps to hear from guys who understand those things


i have now come to the same conclusion    > Your problem with bad GUI performance is not the RAM size, the entire PC is the problem


it is now too bloody old is the problem :KS   [for the default DE]       but probably good for 5 more years on a lighter one   


ps    would it not be good to say that on the Ubuntu download page?  say if your machine is over five years old maybe use LXDE, XFCE, etc...   since new guys might install and think   well this does not move too well back to windows or wherever

---

### Post by mörgæs on 2013-11-08
> **philinux said:**
> 
My guess is the devs have tuned up compiz and unity.

They have indeed, Ubuntu 13.10 performs better than 12.04. It's a pity that people asking for advice here are often recommended to install 12.04.

---

### Post by Johan De Cauwer on 2013-11-08
On my computer, 12.04 works like a charm and 13.10 is so slow I'm considering to remove it. Dual-boot, identical hardware. I guess the latest editions push the graphical performance to the limit. And it's not necessary: a few of us, mostly with relatively older machines live happely without compiz or plasma or wathever. 

In fact, that may be a suggestion for developpers: ask during installation if the user wants features or performance. I know my personal answer.

And yet, my machine is not the worst: I don't know how to insert code but a few of the lines of lshw  are:

 *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+
          
 *-memory:
          size: 4GiB

This problem is not only one of Ubuntu or Unity. All newer distributions share the same filosophy. I'll wait till 14.04 but my guess is that - unless I have to buy new hardware - I'll have to switch to xubuntu. Or simply stay with 12.04...

---

### Post by craig10x on 2013-11-08
Actually, 13.10 runs with less ram and system resources then even 13.04 did...they keep streamlining unity and make adjustments to compiz to make unity run more efficiently (they HAVE to for the phone/tablet/touch interface so we get the benefit on the desktop as well) strange that 13.10 doesn't run as well for you...

---

### Post by BigSilly on 2013-11-09
> **craig10x said:**
> Actually, 13.10 runs with less ram and system resources then even 13.04 did...they keep streamlining unity and make adjustments to compiz to make unity run more efficiently (they HAVE to for the phone/tablet/touch interface so we get the benefit on the desktop as well) strange that 13.10 doesn't run as well for you...

Exactly what I thought about my machine. I fully expected 13.10 to run better after some good reviews but it doesn't for me sadly. 13.04 was stunning. I've moved to Kubuntu 13.10 and that runs great, though it was a little buggy to start with.

---

### Post by craig10x on 2013-11-09
@BigSilly: perhaps it will be better for you when they switch to mir and drop compiz...though you probably should give 14.04 a go when it finalizes in April...one never knows :D

---

### Post by Bushcraft Bill on 2013-11-09
works great until I go online and upload or download then it may as well be my duo core puter I cant do anything else as it just takes forever to load a program and any other commands just take forever to do/finish 
other than that its a rocket is their a way to set ubuntu 13.10 so internet does not use up so much resorces so I can do other things on this puter?

```
         capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: b
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 8
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5173QH0-YK0
             vendor: Samsung
             physical id: 0
             serial: D15E30C4
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 16KTF1G64HZ-1G6E1
             vendor: Micron Technology
             physical id: 1
             serial: E98D8717
             slot: Bottom-Slot 2(under)
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:d2000000-d2ffffff ioport:a0000000(size=536870912)
           *-display UNCLAIMED
                description: 3D controller
                product: GK208M [GeForce GT 740M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128) memory:b2000000-b207ffff
        *-display
             description: VGA compatible controller
             product: 4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:6000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:d3710000-d3713fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:d3700000-d370ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:45 memory:d3718000-d371800f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d371d000-d371d3ff
        *-multimedia:1
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:d3714000-d3717fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:9fb00000-9fcfffff ioport:9fd00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:d3600000-d36fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 2230
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: c4
                serial: 68:17:29:d9:54:68
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-13-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:46 memory:d3600000-d3601fff
        *-pci:3
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:4000(size=4096) memory:d1000000-d1ffffff ioport:d0000000(size=16777216)
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:43 memory:d1000000-d1000fff
        *-pci:4
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:d3500000-d35fffff ioport:d3400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0f:00.0
                logical name: eth0
                version: 0c
                serial: 9c:b6:54:43:c7:cb
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.109 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:44 ioport:3000(size=256) memory:d3500000-d3500fff memory:d3400000-d3403fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:d371c000-d371c3ff
        *-isa
             description: ISA bridge
             product: HM87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:6088(size=8) ioport:6094(size=4) ioport:6080(size=8) ioport:6090(size=4) ioport:6060(size=32) memory:d371b000-d371b7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d3719000-d37190ff ioport:6040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS541010A9
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: JA0O
             serial: JB100013107ZXP
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=680f7b99-e2e4-4cd2-9738-7fabb2426287 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 00b7-2c80
                size: 398MiB
                capacity: 399MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2013-09-28 22:21:13 filesystem=ntfs label=WINRE modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: f46c-7606
                size: 239MiB
                capacity: 259MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: 8be7fa12-5e6d-4fe6-af2f-f5d1aedd54b8
                capacity: 127MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 18fe932e-7c82-3942-bc2f-f5e770fec1d6
                size: 452GiB
                capacity: 452GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-05-24 12:49:31 filesystem=ntfs label=Windows name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: b8fce7cb-03e5-e64c-a384-22d5d237b181
                size: 450GiB
                capacity: 450GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-11-04 22:02:57 filesystem=ntfs label=DATA modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: 3e1b6bb4-35f2-b649-93c0-ed6e10d0016a
                size: 27GiB
                capacity: 27GiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2013-09-28 22:21:03 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SU-208CB
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: HH00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS541010A9
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: JA0O
             serial: JA1000101SWH6M
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=d8a26941
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: 2acd0e76-b0ea-4c0f-b6d6-ebec25bf8257
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-11-05 16:37:32 filesystem=ext4 lastmountpoint=/ modified=2013-11-09 08:29:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-11-09 08:29:48 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                version: 1
                serial: 7d0cdefe-14a1-450f-9bb4-639938d9ef97
                size: 199MiB
                capacity: 199MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh

```

---

### Post by andrew.46 on 2013-11-19
Hi Shantiq :)

I have had a few life changing events this year and my computer activities have been drastically reduced, not such a bad thing as it turns out. Having packed away the 8 core beast I built in my glory days I am simply using an old Latitude D520 which was built I believe in 2006. This machine laboured with Unity in previous iterations and now runs a full kde desktop with Slackware 14.1 so I guess I qualify as someone who bailed out from the Unity experience. Perhaps newer versions of Unity would run better, I have seen such comments around, but the latest KDE runs very, very well on this setup and I will probably remain with it...

```

root@skamandros/home/andrew# lshw -sanitize
computer                  
    description: Portable Computer
    product: Latitude D520
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=portable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0NF743
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06
          date: 05/28/2007
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium M
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 1667MHz
          capacity: 2160MHz
          width: 64 bits
          clock: 166MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 0000000000000000
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 0000000000000000
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff memory:efec0000-efefffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:eff80000-efffffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:efebc000-efebffff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:e4000000-e41fffff ioport:e4200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:efd00000-efdfffff ioport:e4400000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:efdfc000-efdfffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:bf80(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:bf60(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:bf40(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bf20(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:ffa80000-ffa803ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:4000(size=4096) memory:efc00000-efcfffff ioport:e0000000(size=67108864)
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:17 memory:efcfe000-efcfffff
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:e8000000-e8000fff ioport:4000(size=256) ioport:4400(size=256) memory:e0000000-e3ffffff memory:f8000000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@0000:02:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:19 memory:efcfd000-efcfdfff memory:efcfc800-efcfcfff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
        *-serial
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:17 ioport:10c0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HM321HI
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AJ1
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0006146d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 294GiB
                capacity: 294GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2012-12-01 10:05:33 filesystem=ext4 lastmountpoint=/ modified=2013-11-19 07:30:01 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-11-19 07:30:01 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 3812MiB
                capacity: 3812MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7590A
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdr
             logical name: /dev/cdr0
             logical name: /dev/cdrom
             logical name: /dev/cdrom0
             logical name: /dev/cdrw
             logical name: /dev/cdrw0
             logical name: /dev/cdwriter
             logical name: /dev/cdwriter0
             logical name: /dev/dvd
             logical name: /dev/dvd0
             logical name: /dev/dvdr
             logical name: /dev/dvdr0
             logical name: /dev/dvdrw
             logical name: /dev/dvdrw0
             logical name: /dev/dvdwriter
             logical name: /dev/dvdwriter0
             logical name: /dev/sr0
             version: 1.52
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdr
  *-battery
       product: DELL HD9417A
       vendor: Panasonic
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 51000mWh
       configuration: voltage=11.1V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.10.17 firmware=508.1084 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg
root@skamandros/home/andrew# 

```

I am pretty sure though that my purpose built computer would have eaten Unity and come back for seconds though :)

---

### Post by shantiq on 2013-11-19
interesting Andrew ...   pray tell why is the beast packed away [if not too personal]?  is it safe...    does it get fed  :)   :)   

> would have eaten Unity and come back for seconds   will be my favourite line from 2013    so thank you

---

