---
title: "System crashes when i run virtual box!"
date: 2010-11-11
forum: Virtualisation
---

### Post by slashwannabe94 on 2010-11-11
Greetings all, i have recently installed the oracle virtual box, directly from the site and have created a virtual windows XP Pro machine.
 
My computer has 512MB DDR RAM, a 250GB SATA HDD, and an intel dual core CPU. 
 
I gave 256MB of RAM to my virtual machine, and 256MB to ubuntu. when i open the windows XP virtual machine, my entire system slows to a halt. i have configured Windows XP to performance over aesthetics, thus reducing RAM usage, but still have had no luck!
 
i do not know why my machine is crashing when i load Virtual Box, but i do have a hunch that it may be down to the minute quantity of RAM installed. 
 
If anyone can help me and send me in the right direction, please.... do so.
 
:guitar::guitar::guitar::guitar:

---

### Post by gordintoronto on 2010-11-11
Yes, you are short of RAM. You can run Lubuntu in 256 MB, but Ubuntu, not so much.

---

### Post by CharlesA on 2010-11-11
What are the full specs of the machine?

It's kinda hard to believe that a dual core machine would only have 512MB of RAM.

---

### Post by slashwannabe94 on 2010-11-13
It definitely has only 512MB of RAM, one RAM chip, just stopped working one day haha. 

i ran the "sudo lshw" command and received this output. 

Hope this helps man :D 

```
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
          physical id: 1a
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
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
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 2800MHz
          capacity: 2800MHz
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
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
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
           *-cdrom:0
                description: DVD writer
                product: DVD RW DW-Q31A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: LYS2
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM DDU1615
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: FYS2
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:fa00(size=8) ioport:f900(size=4) ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=16)
           *-disk
                description: ATA Disk
                product: ST3250823AS
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/sda
                version: 3.03
                serial: 5ND1JRHW
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007151e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 72d69b20-5868-4210-9f4c-b336bdd92754
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-11-11 04:00:30 filesystem=ext4 lastmountpoint=/&#65533;V&#65533;2&#65533;HJl&#65533;4+&#1940;^&#65533;&#65533;&#65533;k &#65533;j/&#65533;&#65533;^&#65533;&#1598;!&#65533;h&#65533;M&#65533;h&#65533;M&#1984;2&#65533;&#65533;^&#65533;&#1584;^&#65533;&#65533;mn modified=2010-11-13 13:23:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-13 13:25:25 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.1.0,2
                   logical name: /dev/sda2
                   size: 1450MiB
                   capacity: 1450MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1450MiB
                      capabilities: nofs
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
          bus info: usb@1:7
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
             logical name: /dev/sdb
     *-scsi:1
          physical id: 3
          bus info: usb@5:2
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdc
             size: 978MiB (1025MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=2bdefa74
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@10:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/Puppy_Linux
                version: 1.0
                serial: f97664e6-7de0-45e4-af2b-e2d8b594076b
                size: 977MiB
                capacity: 977MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-11-13 01:25:05 filesystem=ext4 label=Puppy_Linux modified=2010-11-13 13:26:18 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2010-11-13 13:26:18 state=mounted
     *-scsi:2
          physical id: 5
          bus info: usb@4:1
          logical name: scsi11
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 1600BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@11:0.0.0
             logical name: /dev/sdd
             version: 1.04
             serial: WD-WXEX07I05094
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=000de739
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@11:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/External Disk
                version: 3.1
                serial: 3016ec26-c3c9-47bf-83bb-973aca46e9c2
                size: 149GiB
                capacity: 149GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-09-16 01:35:10 filesystem=ntfs label=External Disk mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

### Post by CharlesA on 2010-11-13
replace the bad stick of RAM then.

It's running out of memory and causing problems.

---

### Post by lmarmisa on 2010-11-13
Try to install [xfce4]("http://www.xfce.org/about/screenshots") as an alternative to Gnome.

Xfce4 is a lightweight desktop environment that uses less memory than Gnome.

The installation is very simple:

```

sudo apt-get install xfce4

```

Then logout.

Finally, select xfce in the login options.

Maybe you will be able to improve the performance of your system with this solution.

In any case, consider to add more memory to your system.

P.S. Xfce4 does not uninstall Gnome. So, you will have both desktop environments available.

---

### Post by slashwannabe94 on 2010-11-13
[FONT=monospace]thanks allot guys, i came to the right place :D 
[/FONT]

---

