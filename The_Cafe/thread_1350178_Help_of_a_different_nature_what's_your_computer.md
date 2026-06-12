---
title: "Help of a different nature: what's your computer?"
date: 2009-12-09
forum: The Cafe
---

### Post by BlueCanary9999 on 2009-12-09
Hai guyz,

If you recently purchased the parts of your computer separately and for less than (but near) $1300 in total, I need your help.  It's really simple.  Just tell me the parts you bought; that's all I ask.  You probably want to know why, and you rightfully should: I'm doing an idiotic project for my "computer technology" class.  (To demonstrate how terrible this class is, our material is all on DOS, and for this virtual purchasing projects, we're only allowed to buy Windows OS's.  I hope that gets your blood boiling as it does mine.)

Generally, I'm very honest when it comes to academic work---more so than any of my peers.  But this class and project is just pathetic, and I really don't have the free time needed to collect all the details. If it's not too tedious, can you tell me the pieces you bought?  Just the name of each would be enough.  Also, how does your system run?  Why did you pick that set of pieces?

I know, it feels like I'm asking you to do my project, but there's a lot more involved.  And, really, my teacher has taught us so little that finding these pieces could take me 10 times longer than it should for a more technologically literate person---and I have an insane amount of work to get done for other classes.  I'm sorry if this sounds like I'm begging you to do my work, but I just need a little help.  I would *infinitely* appreciate it, and end up loving this forum more than I already do.

---

### Post by MaindotC on 2009-12-09
Mobo, ram, and video card are in my sig.  I have it encased in a [tower](http://is.gd/5gBSf) and [power supply](http://is.gd/5gBU9) both by Rosewill.  Everything works great except the sound card.

---

### Post by 3rdalbum on 2009-12-09
We're not allowed to do your homework for you on Ubuntu Forums. Just do a search and you'll find loads of people asking "Does this configuration look alright, what would you change?".

---

### Post by fancypiper on 2009-12-09
```
Sun Apr 26 06:42 PM root@tinwhistle ~ # lshw
tinwhistle
    description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.2 dmi-2.2 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: NF4K8AC
       vendor: Winfast
       physical id: 0
       serial: UYKJ60200490
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/20/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3500+
          slot: Socket 939
          size: 2211MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 Processor 3500+
          slot: Socket 939
          size: 2211MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:10 ioport:fc00(size=32) ioport:1c00(size=64) ioport:1c40(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:febff000-febfffff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:feb00000-feb000ff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi4
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e800(size=16)
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DH20A1P
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 6X16
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          logical name: scsi1
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d400(size=16) memory:febfc000-febfcfff
        *-disk:0
             description: ATA Disk
             product: WDC WD10EADS-00L
             vendor: Western Digital
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCAU48009352
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ee220
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 5e5030b1-a8f3-4d71-ba26-8f5f4d90c4df
                size: 20GiB
                capacity: 20GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2009-12-06 04:48:33 filesystem=ext4 lastmountpoint=/h]Trï¿&#339;ï¿&#339;ï¿&#339;=aï¿&#339;8]Trï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;7ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;I}ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;7ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ïï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;P#K}ï¿&#339; modified=2009-12-06 05:03:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-12-06 09:37:53 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: 4e610d5e-a3d9-4c50-b107-0eddd5e62c1e
                size: 2055MiB
                capacity: 2055MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: 7a41c2a6-ed35-4226-bd67-ca3af704efd0
                size: 909GiB
                capacity: 909GiB
                capabilities: primary journaled extended_attributes large_files recover extents ext4 ext2 initialized
                configuration: created=2009-04-22 07:18:19 filesystem=ext4 lastmountpoint=/homehï¿&#339;ï¿&#339;qï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;=78ï¿&#339;ï¿&#339;qï¿&#339;ï¿&#339;ï¿&#339;]ï¿&#339;7ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ajï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;Irï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ïï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;pU modified=2009-12-06 09:37:56 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2009-12-06 09:37:56 state=mounted
        *-disk:1
             description: ATA Disk
             product: ST3160023AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 3.00
             serial: 5MT177LD
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=fafc581b
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /pub
                version: 1.0
                serial: b53429db-2943-4662-b2f8-965ed4fe59b0
                size: 149GiB
                capacity: 149GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2009-11-08 15:51:00 filesystem=ext4 lastmountpoint=/pubhï¿&#339;Cï¿&#339;ï¿&#339;ï¿&#339;*ï¿&#339;ï¿&#339;s8ï¿&#339;Cï¿&#339;ï¿&#339;ï¿&#339;S{ï¿&#339;ï¿&#339;ï¿&#339;@ï¿&#339;ï¿&#339;1ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;5ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ïï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;Ë‘ modified=2009-12-06 09:37:53 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2009-12-06 09:37:53 state=mounted
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c000(size=16) memory:febfb000-febfbfff
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
          resources: ioport:a000(size=4096) memory:fe900000-fe9fffff memory:fea00000-feafffff(prefetchable)
        *-multimedia:0
             description: Multimedia video controller
             product: Bt878 Video Capture
             vendor: Brooktree Corporation
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
             resources: irq:19 memory:feaff000-feafffff(prefetchable)
        *-multimedia:1 UNCLAIMED
             description: Multimedia controller
             product: Bt878 Audio Capture
             vendor: Brooktree Corporation
             physical id: 7.1
             bus info: pci@0000:01:07.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: latency=32 maxlatency=255 mingnt=4
             resources: memory:feafe000-feafefff(prefetchable)
        *-multimedia:2
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
             resources: irq:18 ioport:ac00(size=32)
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: a.1
             bus info: pci@0000:01:0a.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32
             resources: irq:0 ioport:a800(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:01:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
             resources: irq:19 memory:fe9ff000-fe9ff7ff memory:fe9f8000-fe9fbfff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:15:58:0e:84:0f
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=184.0.3.160 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:23 memory:febfa000-febfafff ioport:bc00(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:9000(size=4096) memory:fe800000-fe8fffff ioport:fe700000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:8000(size=4096) memory:fe600000-fe6fffff ioport:fe500000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26 ioport:7000(size=4096) memory:fe400000-fe4fffff ioport:fe300000(size=1048576)
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:27 ioport:6000(size=4096) memory:fb000000-fdffffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G70 [GeForce 7800 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable) memory:fc000000-fcffffff ioport:6c00(size=128) memory:fd000000-fd01ffff(prefetchable)
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

```

> Also, how does your system run? Why did you pick that set of pieces?Very well indeed.  These parts, except for the case, mouse, keyboard and soundcard were handed up to me from my gamer son.

When I buy hardware, I make sure it is supported by Linux.

---

### Post by BlueCanary9999 on 2009-12-10
Thanks SO much for your help, guys!

And sorry, 3rdalbum, I wasn't aware of that policy.  I just figured that since this was the Community Cafe, this would be okay.  Won't do it again.

---

