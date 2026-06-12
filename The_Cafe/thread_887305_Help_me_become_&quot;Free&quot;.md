---
title: "Help me become &quot;Free&quot;"
date: 2008-08-12
forum: The Cafe
---

### Post by NNNNNNNNNN1515 on 2008-08-12
Today I was very curious to know how much of my ubuntu set up is free and open, so I installed VRMS. And among some of the non-free packages I have installed included the linux restricted modules for x86/x86_64. Since I'm a beginner when it comes to linux, I was wondering if anyone could answer this question: Just because they are installed, does that mean my computer is using them? How can I tell whether my computer would run ok with out these modules? And if I find it possible to do without them, how do I uninstall them? I suppose if some of my hardware wont work without them, then I'll keep them on there. It's only one little non-free smudge on my other wise pure, clean open source dream. However if it were at all possible to unchain myself from the restricted modules, I could have something to brag about to my fellow nerds. 

Also... just out of curiosity... has anyone met RMS? Does he sign autographs?

---

### Post by LaRoza on 2008-08-12
> **NNNNNNNNNN1515 said:**
> Today I was very curious to know how much of my ubuntu set up is free and open, so I installed VRMS. And among some of the non-free packages I have installed included the linux restricted modules for x86/x86_64. Since I'm a beginner when it comes to linux, I was wondering if anyone could answer this question: Just because they are installed, does that mean my computer is using them? How can I tell whether my computer would run ok with out these modules? And if I find it possible to do without them, how do I uninstall them? I suppose if some of my hardware wont work without them, then I'll keep them on there. It's only one little non-free smudge on my other wise pure, clean open source dream. However if it were at all possible to unchain myself from the restricted modules, I could have something to brag about to my fellow nerds. 
Post your hardware to see if things will work without them.

If you want a totally free distro, try gNewSense. It is what RMS uses and is based on Ubuntu.


> 
Also... just out of curiosity... has anyone met RMS? Does he sign autographs?
I'd want to, just so I could tell him I use Vim.

---

### Post by TheConstruct on 2008-08-12
> **NNNNNNNNNN1515 said:**
> Also... just out of curiosity... has anyone met RMS? Does he sign autographs?
He does, although he's been known to charge for them in the past. :)

[http://digg.com/tech_news/Richard_Stallman_Charges_for_Autographs](http://digg.com/tech_news/Richard_Stallman_Charges_for_Autographs)
[http://www.linux.com/articles/54012](http://www.linux.com/articles/54012)

---

### Post by NNNNNNNNNN1515 on 2008-08-12
This is the hardware I'm using. Can I do without the restricted modules?

BTW Thanks for the tip about gNewSense. I have a spare computer in the back. I might try to install gNewSense for fun. :-)

> normloman-desktop         
    description: Computer
    product: Springdale-G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=A0550751-F5DE-11D8-84F6-00E018874439
  *-core
       description: Motherboard
       product: D865PERL
       vendor: Intel Corporation
       physical id: 0
       version: AAC27646-213
       serial: BTRL43501306
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: RL86510A.86A.0075.P15.0404021333 (04/02/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          slot: J2E1
          size: 2800MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid
          configuration: id=0
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 5
             slot: None
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
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
     *-memory
          description: System Memory
          physical id: 3d
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns) [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J5G1
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns) [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J5G2
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J5H1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:3
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J5H2
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:11:11:57:e8:03
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: Maxtor 6L080P0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BAJ4
                serial: L2637JWG
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c1d9c1d9
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: a5716e71-cff2-4a12-be80-0ae76a3d2e49
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-24 21:42:50 filesystem=ext3 modified=2008-08-11 12:27:03 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-11 12:27:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2204MiB
                   capacity: 2204MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2204MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GD-5000
                vendor: HITACHI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0213
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: 52MAXX 3252AJ1v2
                vendor: Memorex
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 2W$3
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0


---

### Post by FranMichaels on 2008-08-12
An easy way to check:

System -> Administration -> Hardware Drivers

If yours looks like this, you can safely run without restricted-modules (been that way for me on my laptop since the last Ubuntu release, where the intel wireless driver no longer needed the restricted module :D)

---

### Post by LaRoza on 2008-08-12
It looks like it will "Intel" anything is a good sign.

---

### Post by 3rdalbum on 2008-08-12
> **TheConstruct said:**
> He does, although he's been known to charge for them in the past. :)

Is his signature open-source? Are you allowed to copy it, modify it at will, and redistribute it without restriction? :)

---

### Post by LaRoza on 2008-08-12
> **3rdalbum said:**
> Is his signature open-source? Are you allowed to copy it, modify it at will, and redistribute it without restriction? :)

Then it wouldn't be a signature.

---

### Post by Canis familiaris on 2008-08-12
> **LaRoza said:**
> I'd want to, just so I could tell him I use Vim.

:lolflag:

---

### Post by dmn_clown on 2008-08-12
> **LaRoza said:**
> It looks like it will "Intel" anything is a good sign.

Intel wireless cards use non-free firmware. 
Mesa's GLX still includes non-free code.

---

### Post by master5o1 on 2008-08-12
> **TheConstruct said:**
> He does, although he's been known to charge for them in the past. :)

[http://digg.com/tech_news/Richard_Stallman_Charges_for_Autographs](http://digg.com/tech_news/Richard_Stallman_Charges_for_Autographs)
[http://www.linux.com/articles/54012](http://www.linux.com/articles/54012)



You mean his signature isn't Free?
Not BY-NC-SA?

---

### Post by NNNNNNNNNN1515 on 2008-08-13
Hey good news everybody: It looks like I'm not using any proprietary drivers. So tonight, **I say goodbye to restricted modules**. Thanks for your help.

---

### Post by original_jamingrit on 2008-08-13
Wow, that's actually pretty cool.  Are you doing this Ubuntu as planned, or are you using gnewsense?

---

