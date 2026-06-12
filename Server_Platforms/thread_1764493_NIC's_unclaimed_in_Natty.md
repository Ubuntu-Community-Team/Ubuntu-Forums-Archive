---
title: "NIC's unclaimed in Natty"
date: 2011-05-21
forum: Server Platforms
---

### Post by dbnettle on 2011-05-21
I am upgrading a Dell e521 with two DP83820 NIC 's to Ubuntu Server 11.04 from server 9.04. lshw shows that these two cards are "unclaimed.". Just to check, I put the original OS disk with 9.04 on it back in and the NIC's worked just fine. What should I do to troubleshoot this?
 
-dbnettle
 
 
Update: I'm attaching several outputs below.
 
```
*************************************************************************************************************
Output from lspci
*************************************************************************************************************
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Ethernet controller: National Semiconductor Corporation DP83820 10/100/1000 Ethernet Controller
04:09.0 Ethernet controller: National Semiconductor Corporation DP83820 10/100/1000 Ethernet Controller
*************************************************************************************************************
*************************************************************************************************************
 
*************************************************************************************************************
Output from lshw
*************************************************************************************************************
server-vm1
    description: Desktop Computer
    product: Dimension E521 ()
    vendor: Winbond Electronics
    serial: 3GKQ3D1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=44454C4C-4700-104B-8051-B3C04F334431
  *-core
       description: Motherboard
       product: 0UW457
       vendor: Winbond Electronics
       physical id: 0
       version: A04
       serial: ..CN6986174M1F30.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 1
          version: 1.1.10
          date: 06/11/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 8
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 15.11.1
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 1GHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: e
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: f
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905429-002.A00LF
             vendor: Kingston
             physical id: 0
             serial: 81CC1804
             slot: DIMM_4
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905429-002.A00LF
             vendor: Kingston
             physical id: 1
             serial: 82CC2804
             slot: DIMM_3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905429-002.A00LF
             vendor: Kingston
             physical id: 2
             serial: 81CC3504
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905429-002.A00LF
             vendor: Kingston
             physical id: 3
             serial: 80CC1D04
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 2
          bus info: [EMAIL="cpu@1"]cpu@1[/EMAIL]
          version: 15.11.1
          size: 1GHz
          capacity: 1GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: [EMAIL="pci@0000:00:00.0"]pci@0000:00:00.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: [EMAIL="pci@0000:00:00.1"]pci@0000:00:00.1[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: [EMAIL="pci@0000:00:00.2"]pci@0000:00:00.2[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: [EMAIL="pci@0000:00:00.3"]pci@0000:00:00.3[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: [EMAIL="pci@0000:00:00.4"]pci@0000:00:00.4[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: [EMAIL="pci@0000:00:00.5"]pci@0000:00:00.5[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: [EMAIL="pci@0000:00:00.6"]pci@0000:00:00.6[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: [EMAIL="pci@0000:00:00.7"]pci@0000:00:00.7[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: [EMAIL="pci@0000:00:02.0"]pci@0000:00:02.0[/EMAIL]
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:a000(size=4096) memory:fdd00000-fddfffff ioport:fda00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: [EMAIL="pci@0000:00:03.0"]pci@0000:00:03.0[/EMAIL]
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:8000(size=4096) memory:fd900000-fd9fffff ioport:fde00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: [EMAIL="pci@0000:00:04.0"]pci@0000:00:04.0[/EMAIL]
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:b000(size=4096) memory:fa000000-fcffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G72 [GeForce 7300 LE]
             vendor: nVidia Corporation
             physical id: 0
             bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:fb000000-fbffffff memory:fc000000-fc01ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: [EMAIL="pci@0000:00:09.0"]pci@0000:00:09.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: [EMAIL="pci@0000:00:0a.0"]pci@0000:00:0a.0[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: [EMAIL="pci@0000:00:0a.1"]pci@0000:00:0a.1[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: [EMAIL="pci@0000:00:0a.2"]pci@0000:00:0a.2[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: [EMAIL="pci@0000:00:0b.0"]pci@0000:00:0b.0[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: [EMAIL="pci@0000:00:0b.1"]pci@0000:00:0b.1[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: [EMAIL="pci@0000:00:0e.0"]pci@0000:00:0e.0[/EMAIL]
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
        *-disk
             description: ATA Disk
             product: WDC WD1001FALS-0
             vendor: Western Digital
             physical id: 0
             bus info: [EMAIL="scsi@0:0.0.0"]scsi@0:0.0.0[/EMAIL]
             logical name: /dev/sda
             version: 05.0
             serial: WD-WMATV4359586
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0002e19d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: [EMAIL="scsi@0:0.0.0,1"]scsi@0:0.0.0,1[/EMAIL]
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 1c6cb107-7686-43ed-8400-553bf5c51a04
                size: 46GiB
                capacity: 46GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-05-21 15:05:50 filesystem=ext4 lastmountpoint=/ modified=2011-05-21 15:19:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-21 15:23:48 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: [EMAIL="scsi@0:0.0.0,2"]scsi@0:0.0.0,2[/EMAIL]
                logical name: /dev/sda2
                size: 4093MiB
                capacity: 4093MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4093MiB
                   capabilities: nofs
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: [EMAIL="scsi@0:0.0.0,3"]scsi@0:0.0.0,3[/EMAIL]
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: 34eb17ed-7311-4253-8ed5-9e5adebdb506
                size: 880GiB
                capacity: 880GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-05-21 15:05:52 filesystem=ext4 lastmountpoint=/home modified=2011-05-21 15:40:45 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-05-21 15:40:45 state=mounted
        *-cdrom
             description: DVD writer
             product: DVD+-RW TS-H653A
             vendor: TSSTcorp
             physical id: 1
             bus info: [EMAIL="scsi@1:0.0.0"]scsi@1:0.0.0[/EMAIL]
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: D500
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: [EMAIL="pci@0000:00:0f.0"]pci@0000:00:0f.0[/EMAIL]
          logical name: scsi2
          logical name: scsi3
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
        *-disk:0
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 0
             bus info: [EMAIL="scsi@2:0.0.0"]scsi@2:0.0.0[/EMAIL]
             logical name: /dev/sdb
             version: 51.0
             serial: WD-WMAZA4052398
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0006514b
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: [EMAIL="scsi@2:0.0.0,1"]scsi@2:0.0.0,1[/EMAIL]
                logical name: /dev/sdb1
                version: 3.1
                serial: 82ee-30f9
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary multi ntfs initialized
                configuration: clustersize=4096 created=2011-05-13 14:45:17 filesystem=ntfs label=New Volume state=clean
        *-disk:1
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 1
             bus info: [EMAIL="scsi@3:0.0.0"]scsi@3:0.0.0[/EMAIL]
             logical name: /dev/sdc
             version: 51.0
             serial: WD-WMAZA4007694
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=bee081dc
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: [EMAIL="scsi@3:0.0.0,1"]scsi@3:0.0.0,1[/EMAIL]
                logical name: /dev/sdc1
                capacity: 1863GiB
                capabilities: primary multi
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: [EMAIL="pci@0000:00:10.0"]pci@0000:00:10.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:9000(size=4096) memory:fdc00000-fdcfffff memory:fdb00000-fdbfffff
        *-network:0
             description: Ethernet interface
             product: BCM4401-B0 100Base-TX
             vendor: Broadcom Corporation
             physical id: 7
             bus info: [EMAIL="pci@0000:04:07.0"]pci@0000:04:07.0[/EMAIL]
             logical name: eth0
             version: 02
             serial: 00:1a:a0:44:14:81
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.3 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:19 memory:fdcfc000-fdcfdfff
        *-network:1 UNCLAIMED
             description: Ethernet controller
             product: DP83820 10/100/1000 Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 8
             bus info: [EMAIL="pci@0000:04:08.0"]pci@0000:04:08.0[/EMAIL]
             version: 00
             width: 32 bits
             clock: 66MHz
             configuration: latency=64 maxlatency=52 mingnt=11
             resources: ioport:9c00(size=256) memory:fdcff000-fdcfffff memory:fdb00000-fdb0ffff
        *-network:2 UNCLAIMED
             description: Ethernet controller
             product: DP83820 10/100/1000 Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 9
             bus info: [EMAIL="pci@0000:04:09.0"]pci@0000:04:09.0[/EMAIL]
             version: 00
             width: 32 bits
             clock: 66MHz
             configuration: latency=64 maxlatency=52 mingnt=11
             resources: ioport:9800(size=256) memory:fdcfe000-fdcfefff memory:fdb10000-fdb1ffff
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: [EMAIL="pci@0000:00:18.0"]pci@0000:00:18.0[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: [EMAIL="pci@0000:00:18.1"]pci@0000:00:18.1[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: [EMAIL="pci@0000:00:18.2"]pci@0000:00:18.2[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: [EMAIL="pci@0000:00:18.3"]pci@0000:00:18.3[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

*************************************************************************************************************
*************************************************************************************************************
 
*************************************************************************************************************
Output from ifconfig -a
*************************************************************************************************************
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:44:14:81  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe44:1481/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9615829 (9.6 MB)  TX bytes:1309528 (1.3 MB)
          Interrupt:19 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88 (88.0 B)  TX bytes:88 (88.0 B)

*************************************************************************************************************
*************************************************************************************************************
 

*************************************************************************************************************
/etc/network/interfaces
*************************************************************************************************************

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
*************************************************************************************************************
*************************************************************************************************************

*************************************************************************************************************
Output from lsmod
*************************************************************************************************************
Module                  Size  Used by
nouveau               626066  1 
dcdbas                 14054  0 
ttm                    65184  1 nouveau
joydev                 17322  0 
psmouse                59039  0 
k8temp                 12872  0 
serio_raw              12990  0 
drm_kms_helper         40745  1 nouveau
drm                   184133  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
nv_tco                 13331  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  1 lp
raid10                 30261  0 
raid456                61718  0 
b44                    35301  0 
async_raid6_recov      12832  1 raid456
async_pq               12847  2 raid456,async_raid6_recov
usbhid                 41704  0 
hid                    77084  1 usbhid
ns83820                21989  0 
ssb                    45942  1 b44
sata_nv                23208  5 
raid6_pq               88205  2 async_raid6_recov,async_pq
async_xor              12738  3 raid456,async_raid6_recov,async_pq
xor                    21860  1 async_xor
async_memcpy           12481  2 raid456,async_raid6_recov
async_tx               13123  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  30167  1 
raid0                  17126  0 
multipath              13011  0 
linear                 12822  0 

*************************************************************************************************************
*************************************************************************************************************
```

---

### Post by dbnettle on 2011-05-25
Bump

---

