---
title: "Another Computer Saved by Xubuntu!"
date: 2008-11-12
forum: Testimonials &amp; Experiences
---

### Post by starcannon on 2008-11-12
Xubuntu 8.04
700mhz, 13gb hdd, 256mb ram, Radeon 32mb 7xxx AIW video card.
While this machine shows its age and is no speed demon, it is very acceptable for watching youTube, checking email, running Open Office 3.0, and posting to forums like I'm doing right now with the machine at this very moment. I revived this for a buddy who isn't into computers, but found that win98 wasn't working on the internet any longer, and he really didn't need a "new" computer, he just needed this one made functional again.

I think I actually enjoy reviving these old machines more than I enjoy building new ones. I like the "green" aspect, and I like the fact that a machine like this can do everything that the average end user would expect from a $300~400.00 budget machine, and do it well.

Thanks yet again Canonical, 2 neighbors down, 120+ to go.

Heres the lshw for any that are interested:
```

gasoline@gasoline-alley:~$ sudo lshw
[sudo] password for gasoline: 
gasoline-alley            
    description: Computer
    product: XPST700
    vendor: Dell Computer Corporation
    version: MT
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
    configuration: uuid=2A075753-C80D-11D3-ADD5-08000918C607
  *-core
       description: Motherboard
       product: SE440BX-3
       vendor: Intel Corporation
       physical id: 0
       version: AA722396-112
       serial: 00067RYC1246101B00DF
       slot: LINE OUT
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: 4S4EB2X0.10A.0026.P08 (11/05/1999)
          size: 1MiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: J4J1
          size: 700MHz
          capacity: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: None
             size: 32KiB
             capacity: 32KiB
             capabilities: non-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: None
             size: 256KiB
             capacity: 512KiB
             capabilities: external write-back
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 256MiB
          capacity: 768MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: J6J1
             size: 128MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: J6J2
             size: 64MiB
             width: 32 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: J7J1
             size: 64MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon R100 QD [Radeon 7200]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
           *-disk
                description: ATA Disk
                product: IBM-DPTA-371360
                vendor: IBM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: P74D
                serial: JHTJHGS3946
                size: 12GiB (13GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ea1aa9c7
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: fbb83a1a-d242-4174-8fc6-9a50e83c520c
                   size: 4290MiB
                   capacity: 4290MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-12 03:48:47 filesystem=ext3 modified=2008-11-12 05:20:13 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-12 05:20:13 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 2ea86fbb-90ff-47d5-8505-96d9b7093a28
                   size: 494MiB
                   capacity: 494MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 9af814ef-1bbc-444a-b38e-8fcf5a2370d4
                   size: 8252MiB
                   capacity: 8252MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-12 03:48:59 filesystem=ext3 modified=2008-11-12 05:20:14 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-11-12 05:20:14 state=mounted
           *-cdrom
                description: DVD reader
                product: DVD-ROM GD-5000
                vendor: HITACHI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0212
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: e.1
             bus info: pci@0000:00:0e.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=64 module=emu10k1_gp
        *-network
             description: Ethernet interface
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth0
             version: 00
             serial: 00:a0:24:e0:26:da
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.114 latency=64 link=yes maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=100MB/s
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax/Voice/Spkp Modem
             vendor: Conexant
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64
gasoline@gasoline-alley:~$ 

```

---

### Post by wolfen69 on 2008-11-12
great job.  i installed xubuntu on a machine with the same specs and the speed was barely acceptable. i am now using debian with xfce, or better yet, puppy on machines with 256 or less. anyway, keep up the good work.

---

### Post by starcannon on 2008-11-12
> **wolfen69 said:**
> great job.  i installed xubuntu on a machine with the same specs and the speed was barely acceptable. i am now using debian with xfce, or better yet, puppy on machines with 256 or less. anyway, keep up the good work.

I hear ya, and if it was a "keeper" that is, one for me, I'd just throw fluxbuntu or DSL on there and call it a speed demon; however, its for someone who needs point and click, and after what he was dealing with he's gonna feel like he's on a brand new computer :lolflag:
It would run Ubuntu, but Xubuntu is much smother while still offering up a decent GUI for the uninitiated, he won't have full screen video, but he had no video before. Anyway, for this guy it will probably extend the life of the machine another 5 years.

---

### Post by wolfen69 on 2008-11-12
yeah, you're probably right. he should be happy that it at least works now.

---

### Post by ugm6hr on 2008-11-12
> **starcannon said:**
> I hear ya, and if it was a "keeper" that is, one for me, I'd just throw fluxbuntu or DSL on there and call it a speed demon; however, its for someone who needs point and click, and after what he was dealing with he's gonna feel like he's on a brand new computer :lolflag

I ended up putting Xubuntu on my old computer, which I had originally revived as a Linux test machine.  After becoming 99.9% Ubuntu on my main laptop, I had no need to "experiment" any more.

So Xubuntu (7.10 I think) went on it, and I got £20 for it.  Not bad for a 12-year-old computer, I thought.

From memory, it was an AMD K6 with 256MB RAM, and about 10GB HD.

Did something similar with my office computer after donating a new HD.  It's still in my office - used only for non-work purposes :)

---

### Post by stinger30au on 2008-11-12
i revived a celeron 400 with 256 meg of ram and 12 gig hdd with xubuntu 8.04

its goes well for what it is. takes 30 seconds to boot up.
still useable for surfing the web and playing youtube and open office

forget about games though

---

