---
title: "Is my computer any good?"
date: 2011-03-01
forum: The Cafe
---

### Post by slashwannabe94 on 2011-03-01
Hey guys, i got a new machine today and wanted your opinions. 

```
sudo lshw

          version: 6.00 PG (10/07/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          slot: Socket 775
          size: 2800MHz
          capacity: 3066MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 3275MiB
        *-bank:0
             description: DIMM DDR Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM DDR Synchronous
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 2800MHz
          capacity: 2800MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:d0000000(size=268435456)
           *-display:0
                description: VGA compatible controller
                product: RV516 [Radeon X1300/X1550 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:25 memory:d0000000-dfffffff(prefetchable) memory:fdef0000-fdefffff ioport:de00(size=256) memory:fde00000-fde1ffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV516 [Radeon X1300/X1550 Series] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress cap_list
                configuration: latency=0
                resources: memory:fdee0000-fdeeffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdff8000-fdffbfff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fe00(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fc00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
           *-multimedia:0
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 1
                bus info: pci@0000:02:01.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84
                resources: irq:17 memory:fddff000-fddff7ff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b2:f3:13
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:18 ioport:ec00(size=256) memory:fddfe000-fddfe0ff memory:fdc00000-fdc0ffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32
                resources: irq:19 memory:fddfd000-fddfd7ff ioport:ef00(size=128)
           *-multimedia:1
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 4
                bus info: pci@0000:02:04.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84
                resources: irq:20 memory:fddfc000-fddfc7ff
           *-communication UNCLAIMED
                description: Communication controller
                product: Lucent V.92 Data/Fax Modem
                vendor: Agere Systems
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: ioport:ea00(size=256)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fb00(size=16)
           *-cdrom
                description: DVD writer
                product: DVD RW DW-Q31A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: LYS2
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:fa00(size=8) ioport:f900(size=4) ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=16)
           *-disk
                description: ATA Disk
                product: Hitachi HDT72502
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: V5DO
                serial: VFL104R630MEZX
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00004803
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7090-72d4
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-01-27 05:53:47 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: e0b456a6-93e6-c74e-958e-0279fb6a8604
                   size: 124GiB
                   capacity: 124GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-01-27 05:54:09 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sda3
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 103GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4547MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM_GSA-H60N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: CA01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi:0
          physical id: 2
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 1600BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.04
             serial: WD-WXEX07I05094
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=000d6e33
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/NTFS
                version: 3.1
                serial: 0cd85213-fe93-46f7-a42e-a83f8de861bc
                size: 149GiB
                capacity: 149GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-12-17 19:35:04 filesystem=ntfs label=NTFS mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@1:1
          logical name: scsi17
          logical name: scsi18
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@17:0.0.0
             logical name: /dev/cdrom2
             logical name: /dev/scd2
             logical name: /dev/sr2
             logical name: /media/T-Mobile
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom2
                logical name: /media/T-Mobile
                capabilities: partitioned partitioned:mac
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 1KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000000800
                   size: 29MiB
                   capacity: 29MiB
                   capabilities: hfsplus initialized
                   configuration: checked=2010-01-14 11:01:03 created=2010-01-14 11:01:03 filesystem=hfsplus lastmountedby=LSDf modified=2010-01-14 11:01:04 state=unclean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@18:0.0.0
             logical name: /dev/sdc
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:bf:51:95:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by IWantFroyo on 2011-03-01
Could you please just post the name of the computer? That's all we need to know.

---

### Post by slashwannabe94 on 2011-03-01
It's custom mate :) 

RAM = 4GB DDR2

---

### Post by wormyblackburny on 2011-03-01
Not too bad, its a dual core with hyperthreading, 256ATI graphics (so-so), 3 GB RAM.... How much did you pay, what size screen, and what brand is it, those are the big questions that will determine how "good" it is (at least in my opinion)

---

### Post by IWantFroyo on 2011-03-01
OK thanks. I've built computers before. I just list the parts I used though.
From what I see, that will run well with Ubuntu.

---

### Post by gamebusterzade on 2011-03-01
i think it will be fine for ubuntu 

just that u may what to just spec out your computer with what you know about it next time

if you need to know that it will run fine on your computer install it on a zip(USB) if BIOS supports it

if not test with the livecd

otherwise just jump in and start

---

### Post by slashwannabe94 on 2011-03-01
£100  man. 22 inch lcd came with it. Can this run ubuntu 10.4 LTS 64bit ?

---

### Post by Joe of loath on 2011-03-01
Um, no s**t ;)

I've run Ubuntu on 1.8ghz boxes with 512mb of RAM...

---

### Post by slashwannabe94 on 2011-03-01
I know it will run the 32 bit version. Just will it run the 64bit?

---

### Post by Joe of loath on 2011-03-01
>   description: Logical CPU
             physical id: 0.1
             **width: 64 bits**


:lol:

---

### Post by slashwannabe94 on 2011-03-01
> **Joe of loath said:**
> :lol:


Yayyyyyyyy :P 

Thanks dude. I would have found this out time ago if i had good eyes haha.

---

### Post by ajmc on 2011-03-01
I am using amd64 on my system with no problem.  I think you should try it :D

---

### Post by wormyblackburny on 2011-03-01
X64 has worked fine for me. There have been a couple small bumps along the way, but nothing major. Have at it :)

---

### Post by Yellow Pasque on 2011-03-01
> **IWantFroyo said:**
> Could you please just post the name of the computer? That's all we need to know.

NO. I would much rather have a meaningful parts list than a meaningless brand name that I probably won't bother to google.

---

