---
title: "Maxed out!!!!!!"
date: 2008-10-10
forum: The Cafe
---

### Post by thepizzaman on 2008-10-10
who has the most maxed out computer? and what did you spend on it?
for it to be maxed out... it has to be at least a dual core with at least 2 gigs of ram and at least a 512 graphics card :)
ok may the anti-force be with you :P

---

### Post by aeiah on 2008-10-10
i bought a nice server rack at work if that counts? 4 machines with 2 opterons each with 4gb ram per cpu. 4x 1TB hdds per machine.

they run fedora xen hypervizors and load balance and mirror with eachother so they act like one machine. they're pretty beefy.

anyway, 2GB ram isnt maxed out. i didnt pay loads and loads for my computer a few years ago and that had 2GB of ram (it now has 1GB, one of the sticks broke :( )

---

### Post by paul101 on 2008-10-10
erm


16 core server with 32 gb ram and... erm, no graphics card :(


wait... thats still to be delivered to my dads work... the server we have atm cant handle virtualising 10 pc's at the same time


on the side note... i have a totaly maxed out celeron 1.5ghz with 256mb ram and a huge 16mb dedicated graphics. running xubuntu 8.04

---

### Post by aeiah on 2008-10-10
we dont really need graphics cards for lamp servers and email. its pretty rare that you need a meaty graphics card on a server unless you're using it for crypto numbercrunching stuff like folding at home utilises.

---

### Post by thepizzaman on 2008-10-11
sure servers can count
any extreme gaming computers out there?

---

### Post by MaxIBoy on 2008-10-11
Gigabyte S-Series motherboard (microATX)
Compaq branded case (from my old prefab)
Quad-core Phenom, overclocked from 2.2 to 2.6 Ghz (planning to overclock even more after I get a new fan for it.)
4 GB G.Skill DDR2 RAM
250 GB 7400 RPM SATA HDD
160 GB 7400 RPM IDE HDD (from my old prefab)
ASUS EAH4850 (Fried :(. Will replace with this model: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127370](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127370))
500 Watt HEC Raptor500 power supply
80 mm CPU fan being used as a case fan (from my old prefab)
[img]http://img363.imageshack.us/img363/4903/rigfanya2qb8.jpg[/img]


Not the best rig under the sun, but I'm proud of it.

---

### Post by thepizzaman on 2008-10-12
hey are those amd quads? anything worth buyin?

---

### Post by Martje_001 on 2008-10-13
> **thepizzaman said:**
> hey are those amd quads? anything worth buyin?
Yes they are worth buying ;). My config:

```
mekkie
    description: Desktop Computer
    product: GA-MA790GP-DS4H
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=30303146-4430-4132-3333-4146FFFFFFFF
  *-core
       description: Motherboard
       product: GA-MA790GP-DS4H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F1 (07/18/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) 9550 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) 9550 Quad-Core Processor
          slot: Socket M2
          size: 2200MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache:0
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-cache:1 DISABLED
          description: L2 cache
          physical id: d
          slot: External Cache
          capacity: 1MiB
          capabilities: synchronous internal write-through
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns) [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon HD 3300 Graphics
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:d0:a2:33:af
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.66 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32 module=ahci
           *-disk
                description: ATA Disk
                product: ST380215AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 4.AA
                serial: 5QZ7KGRP
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005cdb4
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 21f807db-9f4e-4d3f-85ae-efe9705b707d
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-01 21:40:01 filesystem=ext3 modified=2008-10-12 22:20:11 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-10-12 14:45:35 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: ae733ebb-ff6d-4fe4-88ce-7f6f7b8bc1c5
                   size: 502MiB
                   capacity: 502MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB700/SB800 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=32 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRW 20X20X12X
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 6A31
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
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
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:03:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
     *-pci:1
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
```
Not maxed out, but still pretty damn fast :P

---

### Post by I-75 on 2008-10-13
My high end computer is a Gateway Media Center Dual Core Pentium D 940 Processor with 3.2 Ghz speed and 2048 Ram.

---

### Post by thepizzaman on 2008-10-13
nice quad :)

---

### Post by Ms_Angel_D on 2008-10-13
Best comp I ever bought...[CLICK HERE]("http://www.thedallemagnes.info/index.php?option=com_content&task=view&id=189&Itemid=38") I'm not into making them but hey it's a great computer none the less :D

---

### Post by thepizzaman on 2008-10-14
awesome :) i want a quad.........

---

### Post by derekr44 on 2008-10-14
Code2 Quad Extreme @ 3.2
8GB DDR3 1066
GeForce 280GTX (x3)
80GB SSD (Raid 0)
1TB Data
Dual 30"
4TB External Storage
















Ok, I can dream can't I?

---

### Post by thepizzaman on 2008-10-14
ok then if we can dream...... :)
AMD Phenom X4 9950 Quad Core Processor
Sapphire Radeon HD 4870 X2 Video Card (x4)
(x2) Patriot EP 4096MB PC8500 DDR2 1066MHz (2X2048MB)
MSI K9A2 Platinum Motherboard - AMD790FX, Socket AM2+, ATX, Audio, PCI Express 2.0, Gigabit LAN, S/PDIF, USB 2.0, Firewire, eSATA, RAID
4TB hard drives
2 blue ray burners
(4) NEC MultiSync LCD4620-BK-AV 46" Widescreen LCD Monitor - 1920x1080@60 Hz(Compressed), 16ms, 1200:1, DVI-D, D-sub, HDMI, Composite RCA, Black
thats my dream :D

---

