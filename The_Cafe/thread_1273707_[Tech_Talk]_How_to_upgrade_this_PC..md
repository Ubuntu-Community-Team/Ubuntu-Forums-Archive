---
title: "[Tech Talk] How to upgrade this PC."
date: 2009-09-23
forum: The Cafe
---

### Post by cityrama on 2009-09-23
I am wanting to upgrade this PC but only one component at a time (little by little)

I ask you what would be the first part to renew, obviously the main goal is to increase speed and performance.

Now for me the tricky part is compatibility if I upgrade the processor and find out it's incompatible with the motherboard or that type of scenario.

PC

```
Desktop Computer
    product: 00000000000000000000000
    vendor: Packard Bell NEC
    version: P851001301
    serial: 029743720383
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=9CD4520D-61C7-D711-8000-4E45435F4349
  *-core
       description: Motherboard
       product: GA-8SIMLNF
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.0I (06/23/2003)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: P4
          size: 2600MHz
          capacity: 3067MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KiB
             capacity: 8KiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory:0 UNCLAIMED
          description: Flash Memory
          physical id: 27
          slot: System board or motherboard
          capacity: 256KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile 33 MHz (30.3 ns)
             physical id: 0
             slot: FLASH ROM
             size: 256MiB
             width: 8 bits
             clock: 33MHz (30.3ns)
     *-memory:1
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR 333 MHz (3.0 ns)
             physical id: 0
             slot: DDR1
             size: 1GiB
             width: 8 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR 333 MHz (3.0 ns)
             physical id: 1
             slot: DDR2
             size: 256MiB
             width: 8 bits
             clock: 333MHz (3.0ns)
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: SiS645DX Host & Memory & AGP Controller
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 440-SE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 14
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=12 mingnt=4 module=ohci1394
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
           *-disk
                description: ATA Disk
                product: WDC WD800JB-00JJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM9U345270
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00087859
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3ec853dd-3074-4d86-b812-922a7471b0d1
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-09-22 12:44:18 filesystem=ext3 modified=2009-09-23 18:48:58 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-09-23 13:31:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3153MiB
                   capacity: 3153MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3153MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDR8161B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0045
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD writer
                product: DVD-RW  DVR-105
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.20
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=32 maxlatency=11 mingnt=52
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 10
             serial: 00:0d:61:03:e1:3a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:f4:76:cb:cf:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Celeron(R) CPU 2.60GHz
stepping    : 9
cpu MHz        : 2589.216
cache size    : 128 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips    : 5178.43
clflush size    : 64
power management:

```

Any input appreciated ..:popcorn:

---

### Post by Skripka on 2009-09-23
Any meaningful upgrade you do on the mainboard basically necessitates replacing CPU/memory/mainboard all at once.

You're dealing with DDR memory, and a really outdated socket CPU/board.  Piece-by-piece upgrading can't really happen.

---

### Post by cityrama on 2009-09-23
> **Skripka said:**
> Any meaningful upgrade you do on the mainboard basically necessitates replacing CPU/memory/mainboard all at once.

You're dealing with DDR memory, and a really outdated socket CPU/board.  Piece-by-piece upgrading can't really happen.



i see, so then it will have to be that. :)

---

### Post by jerrrys on 2009-09-23
Skripka has a point.  PCI was replaced by AGP which was replaced by PCIE.  your a couple of generations behind, so not a good or easy upgrade.  better to get a new (old) box than upgrade... 

and should say that i run PCIX with xeon processors, so i know what your up against...

---

