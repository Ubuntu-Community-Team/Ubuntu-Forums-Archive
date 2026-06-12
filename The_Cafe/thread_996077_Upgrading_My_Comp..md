---
title: "Upgrading My Comp."
date: 2008-11-28
forum: The Cafe
---

### Post by AnLGP on 2008-11-28
Hello,

I've got this computer:

[http://support.gateway.com/s/PC/R/GTModels/5454/5454sp2.shtml](http://support.gateway.com/s/PC/R/GTModels/5454/5454sp2.shtml)

And was wondering what should I upgrade?  I don't really game much so my video card isn't a huge necessity for me.  I've got about 400 gigs of HD space (not all on board, though, and I have really been looking forward to buying a TB HD).

I could also see me putting in RAM.  I run Ubuntu with the awesome WM but I like to do a lot of graphics work and listen to music and surf at the same time and eventually it can start bogging down.

I am looking for gift ideas to tell people what I want and it would probably come in the form of a gift card to newegg.com ;)

Also, I could see getting a decent flash drive and just sticking an OS on there and wiping the 250 g drive I have in my computer clean and using it for storage..  thoughts on that?

Thanks!

---

### Post by nick09 on 2008-11-28
Here is a graphics card and from what I have read, it runs good in Linux:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150247](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150247)

RAM:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820141241](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141241)

1TB HDD:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152102](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152102)

You can go cheaper on the graphics card if you want to.

---

### Post by AnLGP on 2008-11-28
Thanks!

---

### Post by nick09 on 2008-11-28
I found out your computer even supports core 2 duo so here a comparison of the ones that are compatible with your system:
[http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=2010340343%201050722265%201051107411&bop=And&CompareItemList=N82E16819115032%2CN82E16819115045](http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=2010340343%201050722265%201051107411&bop=And&CompareItemList=N82E16819115032%2CN82E16819115045)

EDIT: Never mind. Though you could look up Pentium D processors. Though it will be useful if you provide what model the motherboard is. Your manual could tell you what motherboard it uses.

---

### Post by AnLGP on 2008-11-28
ah, sudo lshw my friend : )

     
    description: Computer
    product: GT5018E
    serial: CCT5A 810 01697
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=0E2E1921-1EEB-11DA-A6B6-000EA68F733F
  *-core
      [B] description: Motherboard
       product: D945GCZ
       vendor: Intel Corporation
       physical id: 0
       version: AAC99321-501
       serial: AZCZ53715743
       slot: Base Board Chassis Location[/B]
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
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
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: NT94510J.15A.0045.2005.0802.2004 (08/02/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x36345436343030304855332E374120202020
             vendor: 0xC100000000000000
             physical id: 0
             serial: 0x03214815
             slot: J6H1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x36345436343030304855332E374120202020
             vendor: 0xC100000000000000
             physical id: 2
             serial: 0x03214613
             slot: J6J1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: Theater 550 PRO PCI [ATI TV Wonder 550]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=4 mingnt=2
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:03:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-network
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 01
                serial: 00:13:20:9a:86:77
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
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
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: CD/DVDW TS-H552B
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GA04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: Maxtor 6Y060L0
                vendor: Maxtor
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sda
                version: YAR4
                serial: Y202WABE
                size: 57GiB (61GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=52df0fb1
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 3d1868fe-11bf-4ed8-b67c-b6f2f55c3d50
                   size: 57GiB
                   capacity: 57GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-26 15:55:37 filesystem=ext3 modified=2008-11-28 02:40:19 mounted=2008-11-27 00:26:04 state=clean
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD2500JS-22M
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 02.0
                serial: WD-WCANK1233880
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3647784d
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: a5c173b4-8bc1-49bd-a6ed-c3845ebd07ec
                   size: 230GiB
                   capacity: 230GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-26 16:53:27 filesystem=ext3 modified=2008-11-28 02:40:19 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-26 19:36:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 2925MiB
                   capacity: 2925MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 2925MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@5:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@5:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@5:0.0.3
             logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:d2:89:34:26:96
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Th3Professor on 2008-11-28
> **AnLGP said:**
> Hello,

I've got this computer:

[http://support.gateway.com/s/PC/R/GTModels/5454/5454sp2.shtml](http://support.gateway.com/s/PC/R/GTModels/5454/5454sp2.shtml)

And was wondering what should I upgrade?  I don't really game much so my video card isn't a huge necessity for me.  I've got about 400 gigs of HD space (not all on board, though, and I have really been looking forward to buying a TB HD).

I could also see me putting in RAM.  I run Ubuntu with the awesome WM but I like to do a lot of graphics work and listen to music and surf at the same time and eventually it can start bogging down.

I am looking for gift ideas to tell people what I want and it would probably come in the form of a gift card to newegg.com ;)

Also, I could see getting a decent flash drive and just sticking an OS on there and wiping the 250 g drive I have in my computer clean and using it for storage..  thoughts on that?

Thanks!

I'd say go for:
4GB RAM
1TB HDD
new GPU
7.1 speakers
2nd LCD monitor

...AND last but not least:

[CENTER][IMG]http://ecx.images-amazon.com/images/I/31Sy3r1dssL._SS500_.jpg[/IMG]

[IMG]http://g-ecx.images-amazon.com/images/G/01/ciu/c3/1d/84ff225b9da005036c502110.L.jpg[/IMG]
[/CENTER]

---

### Post by AnLGP on 2008-11-28
Thanks.

I have a nice monitor but don't really see the need for a second one.  I've never understood the advantage?  If someone could put a nice concise list up I'd be appreciative.

My speakers are decent.  They're not 7.1, though..  hmm.

---

### Post by nick09 on 2008-11-28
You can only use Pentium D, Pentium 4, and Celeron D processors.

Here is information about your motherboard:
[http://www.intel.com/products/motherboard/D945GCZ/index.htm](http://www.intel.com/products/motherboard/D945GCZ/index.htm)

Also forget my suggestion on the ram, get one of these:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820178164](http://www.newegg.com/Product/Product.aspx?Item=N82E16820178164)

You don't need a second screen or a 7.1 audio system as you are not gonna do any real gaming and for the fact that you mostly do graphic work.

@Th3Professor: That does not really help him. Did you do any research on his hardware? It helps to to do such research to minimize the possible problems in the future.

---

### Post by Th3Professor on 2008-11-28
You can get this 1TB hard drive for $95 with promo code:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136151](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136151)

[IMG]http://c1.neweggimages.com/NeweggImage/productimage/22-136-151-01.jpg[/IMG]

---

### Post by AnLGP on 2008-11-28
Thanks this has given me a lot to look into :)

---

### Post by nick09 on 2008-11-28
According to this page:
[http://www.intel.com/support/motherboards/desktop/d945gcz/sb/CS-026632.htm](http://www.intel.com/support/motherboards/desktop/d945gcz/sb/CS-026632.htm)

You can use a Pentium D 940 @3.2GHz with your kind of system. You can get it for $80 off of ebay:
[http://cgi.ebay.com/Intel-Pentium-D-Processor-940-HH80553PG0884M-SL95W_W0QQitemZ110295065115QQcmdZViewItem](http://cgi.ebay.com/Intel-Pentium-D-Processor-940-HH80553PG0884M-SL95W_W0QQitemZ110295065115QQcmdZViewItem)

Your old heatsink will work with it since it is the same socket. Also use isopropyl alcohol if you see any thermal paste on it. Use this thermal paste when adding in the new processor:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835100009](http://www.newegg.com/Product/Product.aspx?Item=N82E16835100009)

Remember you only need a small dot of the stuff(about the size of a grain of rice). If there is too much then it will just act as a insulator.

---

### Post by Th3Professor on 2008-11-28
You can also remove paste with:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835100010](http://www.newegg.com/Product/Product.aspx?Item=N82E16835100010)

An alternative to the dot is spreading, there are threads on that in these forums and other websites.

---

### Post by nick09 on 2008-11-28
Uh... You are have to spread the dot of thermal paste.

---

### Post by Th3Professor on 2008-11-28
negative

---

