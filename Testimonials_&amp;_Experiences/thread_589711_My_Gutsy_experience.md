---
title: "My Gutsy experience"
date: 2007-10-24
forum: Testimonials &amp; Experiences
---

### Post by pepolez on 2007-10-24
Last weekend I decided it was about time that I did a dist-upgrade on my Ubuntu install. So, instinctively I tried to do a normal dist upgrade, but found that Fiesty had some graphics glitch when installing on my computer that caused it to fail (I'm not sure of the exact details).

So, I thought so myself, I want to upgrade, but Fiesty is a problem, and the Edgy installer always insists I have no root partition. At this point of course, the dist-upgrade has already broken my current install, so I might as well try reinstalling with Gutsy.

After downloading and burning a copy of the install CD (in Windows), I started the install. The installer CD seemed to be loading fine, until it got to the X server. At this point, my monitor switched itself in to standby mode suddenly, which, on my monitor, usually indicates the monitor doesn't support the mode it is being run at.

Sighing, I went to press Ctrl+Alt+F1 to get to a terminal, but simply pressing Ctrl-Alt seemed to have fixed the problem, although something has happened to my monitor  - the image was not fitting the screen properly. You know how when you get a new CRT you have spend ten minutes fiddling with things like H/V position, shape, tilt, etc? I had to do that.

Okay, so far, not an overall good impression. Unfortunately for me though, the install didn't get any easier. I started the install, which went fine until I came to partition my hard drive. The partitioner only showed one of my five hard drives - the one that was NOT on my PCI IDE controller card. My 'root' hard drive is on my PCI IDE controller.

Of course, at this point, I had to spend ten minutes shutting down, unplugging my PC, taking it apart, and struggling to shove cables in sockets covered by a big mess of power and data cables. My idea here was to plug my 'root' drive in to my onboard controller as well as a CDROM drive, and worry about all of my other drives later.

Success! This got me through the install successfully. Well okay, that's an achievement, but just to be sure, I allowed my system to boot in its temporary hardware setup in to the new install, just to make sure it worked. Yup, it did. Now I was getting somewhere.

I shut down my computer again and restored the original drive configuration, which, thanks to the by UUID identification of drives in the fstab, should work if the PCI IDE controller is detected. So, at this point I was relying on my PCI IDE controller that wasn't supported by the installer to be supported by the new system.

Some more luck! The system recognised the controller and booted successfully.

Next I logged in, and started setting up my other hard drives. Without thinking, I first tried to add the hard drives by device name in the fstab - bad idea. Unlike my previous install, the drives on my PCI IDE controller were now prefixed with sd, rather than hd so instead of having hda through hdh, I now had sda to sdd, and hda to hdd. After finding my other drives, I decided to add them to my fstab by UUID, just to be on the safe side.

 I also edited my network configuration in /etc/network/interfaces for my network setup and copied over my own home directory. Now, this restoration of my old home directory caused me a little problem with X. To make sure I had EVERYTHING from my old home directory, I also copied hidden files and directories, which included my .Xsession file. Of course, this caused problems for me - programs with a GUI would fail to start with some error about MIT-MAGIC-COOKIEs. So, I deleted the .Xsession file, and restarted the X server.

Now I was going well, I had my preferences back, my files back, my drives mounted, and my network (mostly) working. Okay, time to install. Unluckily for me, I happened to reinstall when the Automatix site was down the other day, so I ended up sitting around pawing through Synaptic and installing other stuff I needed.

By this point in time, it was getting fairly late, so I decided to go to bed. The next day, I returned to my computer, and was able to successfully download and run Automatix, which instead of replacing my sources list, was kind enough to add duplicates of entires I already had in it. After editing the sources file and running an apt-get update, I continued running Automatix, and was able to install all of the applications I wanted successfully.

So okay, now I have my shiny new install of Gutsy, with all the nice new versions of programs and pretty icons. Of course, it wasn't all perfect from then on, I still had some problems:
- Whenever I logged in, my network configuration for my second network interface would be broken, and I would manually have to take down the network interface and start it again.
- I had one occasion where the system froze entirely. And by entirely frozen, I mean it froze entirely, the display, the sound, any sort of hardware initialisation.
- When my multithreaded TCL apps crash, they will often be killed for 'stack smashing' before the error trace has finished printing - rather annoying when trying to fix the script.
- Suspend does not work (it did in previous install)
- Hibernate does not work (it did in previous install)

The conclusion I draw from this experience, is that Gutsy is great, provided you don't run in to any hardware or configuration problems.

I also submit the following suggestions:
- If possible, make nautilus support browsing of Windows shares by default
- Provide a way for users to change which channel a media key volume control controls on the fly (i.e. I can change one channel, and then press a key combo to change to control of another channel).
- Stop Automatix from duplicating existing entires in the sources.list.

And, to be a bit more helpful in reguards to my problems, here is my hardware configuration, first in human readable form, and then in lshw form:
**human**
AMD Semperon 2400+ CPU (1.6GHz)
nVidia 6600GT AGP graphics card
MSI KM4AM-L motherboard
Realtek 8139too PCI NIC
Silicon Image IDE RAID controller
Western Digital 120GB IDE HDD (x2)
Western Digital 200GB IDE HDD
Western Digital 250GB IDE HDD
Quantum Fireball 8GB HDD
LG HL-DT-ST DVD-ROM drive
LG HL-DT-ST DVDRAM drive
Thermaltake Hardcano 13 (cardreader device attached to USB)
Generic 4 port USB hub
Generic floppy drive

Auriga Colorpro 17CFmonitor (seems to support up to 1280x1024@60Hz)
Logitech G11 keyboard
Logitech MX400 mouse
Wacom 'Sapphire' graphics tablet


**lshw:**
> 
nibbler                   
    description: Desktop Computer
    product: KM400-8237
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-6734
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/28/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm)   2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1666MHz
          capacity: 2100MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga bus_master vga_palette cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-network:0
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: eth0
             version: 10
             serial: 00:30:bd:19:15:76
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.20.0.133 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-storage
             description: RAID bus controller
             product: PCI0680 Ultra ATA-133 Host Controller
             vendor: Silicon Image, Inc.
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=pata_sil680 latency=32 module=pata_sil680
           *-disk:0
                description: SCSI Disk
                product: ST3120022A
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.54
                serial: 5JS3GA1M
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 14GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 101MB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 509MB
                   capabilities: primary nofs
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 96GB
                   capacity: 96GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10001MB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 19GB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 67GB
           *-disk:1
                description: SCSI Disk
                product: WDC WD2000JB-00G
                vendor: ATA
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 08.0
                serial: WD-WCALL1040568
                size: 186GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 186GB
                   capabilities: primary
           *-disk:2
                description: SCSI Disk
                product: WDC WD1200BB-00D
                vendor: ATA
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/sdc
                version: 65.1
                serial: WD-WMACK1255227
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdc1
                   capacity: 111GB
                   capabilities: primary
           *-disk:3
                description: SCSI Disk
                product: WDC WD2500JB-55R
                vendor: ATA
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdd
                version: 20.0
                serial: WD-WCANKH911966
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdd1
                   capacity: 232GB
                   capabilities: primary
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: QUANTUM FIREBALL SE8.4A
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: API.0C00
                   serial: 338818265875
                   size: 8063MB
                   capacity: 8063MB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 8056MB
                      capabilities: primary
              *-cdrom
                   description: DVD reader
                   product: HL-DT-STDVD-ROM GDR8161B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 0100
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2 status=nodisc
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: A103
                   serial: K2653HC0948
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: 78
             serial: 00:11:09:2c:59:e6
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 1
          bus info: usb@4:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdf
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdf
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdg
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdg
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdh
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdh


---

### Post by rahimveron on 2007-10-24
Kust one question: SO many Hard Drives :)

---

### Post by ukripper on 2007-10-24
How much SWAP space you have assigned?

Can you post output of:
sudo fdisk -l

---

### Post by pepolez on 2007-10-24
> **ukripper said:**
> How much SWAP space you have assigned?

Can you post output of:
sudo fdisk -l

> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c7d36e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        1925      104422+  83  Linux
/dev/sda3            1926        1990      522112+  82  Linux swap / Solaris
/dev/sda4            1991       14593   101233597+   5  Extended
/dev/sda5            1991        3265    10241406   83  Linux
/dev/sda6            3266        5814    20474811   83  Linux
/dev/sda7            5815       14593    70517286   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00070c9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc8e5b21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241   83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd719

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001   83  Linux

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe475210d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1027     8249346   83  Linux


Oh, I think I've managed to fix my little network issue now. I'd somehow managed to misspell 'eth1' on the 'auto' line, doh!

As for the hard drives, only five of those are actually physical hard drives. Another four of them are my Hardcano 13 thermal monitor  - it has a cardreader built in with four different slots.

---

### Post by pepolez on 2007-11-19
Oops, double post. See below

---

### Post by pepolez on 2007-11-19
Okay, I've now upgraded the core parts of my computer (motherboard, CPU, graphics card, ram). This upgrade was fairly painless, except for a few minor things:

-My mouse doesn't work unless I unplug it and plug it back in again (strangely though, my tablet is unaffected)  <-- EDIT: This seems to be a hardware problem, it affects Windows too
-I can't utilise the auto sensing features of my sound jacks
-My network interfaces skip a number
-When telling a window to move to a certain workspace, it will (more often then not) move to a random workspace (I'm using compiz-fusion)

For diagnostics, I again provide a human readable and lshw description of my hardware setup:
**human**
AMD Athlon64 4000+ dual core CPU
2gb Kingston DDR2 667MHz RAM
Inno3D GeForce 8600GT PCI-E graphics card
Gigabyte GA-MA69GM-S2H motherboard

**lshw**
> 
nibbler
    description: Desktop Computer
    product: GA-MA69GM-S2H
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=20D3972C-2653-DC11-A208-001D7D919390
  *-core
       description: Motherboard
       product: GA-MA69GM-S2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2 (07/27/2007)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.1
          slot: Socket M2
          size: 1GHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          product: Athlon
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: 15.11.1
          slot: Socket M2
          size: 1GHz
          capacity: 3200MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KB
             capacity: 1MB
             capabilities: synchronous internal write-through
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 2GB
          capacity: 2GB
        *-bank:0
             description: DIMM 32 MHz (31.2 ns) [empty]
             physical id: 0
             slot: A0
             width: 64 bits
             clock: 32MHz (31.2ns)
        *-bank:1
             description: DIMM 32 MHz (31.2 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 32MHz (31.2ns)
        *-bank:2
             description: DIMM 32 MHz (31.2 ns)
             physical id: 2
             slot: A2
             size: 1GB
             width: 64 bits
             clock: 32MHz (31.2ns)
        *-bank:3
             description: DIMM 32 MHz (31.2 ns)
             physical id: 3
             slot: A3
             size: 1GB
             width: 64 bits
             clock: 32MHz (31.2ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
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
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=32 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom:0
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: A103
                   serial: K2653HC0948
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 status=nodisc
              *-cdrom:1
                   description: DVD reader
                   product: HL-DT-STDVD-ROM GDR8161B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 0100
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2 status=nodisc
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
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:02:06.0
                logical name: eth0
                version: 10
                serial: 00:30:bd:19:15:76
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-storage
                description: RAID bus controller
                product: PCI0680 Ultra ATA-133 Host Controller
                vendor: Silicon Image, Inc.
                physical id: 7
                bus info: pci@0000:02:07.0
                logical name: scsi0
                logical name: scsi1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list emulated
                configuration: driver=pata_sil680 latency=32 module=pata_sil680
              *-disk:0
                   description: SCSI Disk
                   product: ST3120022A
                   vendor: ATA
                   physical id: 0
                   bus info: scsi@0:0.0.0
                   logical name: /dev/sda
                   version: 8.54
                   serial: 5JS3GA1M
                   size: 111GB
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: scsi@0:0.0.0,1
                      logical name: /dev/sda1
                      capacity: 14GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: scsi@0:0.0.0,2
                      logical name: /dev/sda2
                      capacity: 101MB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: scsi@0:0.0.0,3
                      logical name: /dev/sda3
                      capacity: 509MB
                      capabilities: primary nofs
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: scsi@0:0.0.0,4
                      logical name: /dev/sda4
                      size: 96GB
                      capacity: 96GB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux filesystem partition
                         physical id: 5
                         logical name: /dev/sda5
                         capacity: 10001MB
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/sda6
                         capacity: 19GB
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/sda7
                         capacity: 67GB
              *-disk:1
                   description: SCSI Disk
                   product: WDC WD2000JB-00G
                   vendor: ATA
                   physical id: 1
                   bus info: scsi@0:0.1.0
                   logical name: /dev/sdb
                   version: 08.0
                   serial: WD-WCALL1040568
                   size: 186GB
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: scsi@0:0.1.0,1
                      logical name: /dev/sdb1
                      capacity: 186GB
                      capabilities: primary
              *-disk:2
                   description: SCSI Disk
                   product: WDC WD1200BB-00D
                   vendor: ATA
                   physical id: 2
                   bus info: scsi@1:0.0.0
                   logical name: /dev/sdc
                   version: 65.1
                   serial: WD-WMACK1255227
                   size: 111GB
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: scsi@1:0.0.0,1
                      logical name: /dev/sdc1
                      capacity: 111GB
                      capabilities: primary
              *-disk:3
                   description: SCSI Disk
                   product: WDC WD2500JB-55R
                   vendor: ATA
                   physical id: 3
                   bus info: scsi@1:0.1.0
                   logical name: /dev/sdd
                   version: 20.0
                   serial: WD-WCANKH911966
                   size: 232GB
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: scsi@1:0.1.0,1
                      logical name: /dev/sdd1
                      capacity: 232GB
                      capabilities: primary
           *-network:1
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: f
                bus info: pci@0000:02:0f.0
                logical name: eth2
                version: 10
                serial: 00:1d:7d:91:93:90
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=172.20.0.132 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 1
          bus info: usb@2:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdf
             version: 9144
             capabilities: removable
            *-disc
                physical id: 0
                logical name: /dev/sdf
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdg
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdg
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdh
             version: 9144
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdh



---

