---
title: "zram?"
date: 2018-06-30
forum: Ubuntu Development Version
---

### Post by VMC on 2018-06-30
Lubuntu Cosmic 06/29/2018:
When did we start implementing "ramz"? I've never seen or used before. To my surprize its there even though I have a swap partition in place and working?! 
I'm looking into removing it. I see no purpose for it, for me.

EDIT: [BugReport]("https://bugs.launchpad.net/ubuntu/+source/calamares-settings-ubuntu/+bug/1780585")

---

### Post by sudodus on 2018-07-01
Lubuntu has used zram in the live sessions for several years in order to make it possible to 'Try Lubuntu' and install Lubuntu in computers with a low amount of RAM. But zram has not been installed in the installed Lubuntu systems.

What about your problem with Lubuntu Cosmic: is there zram also in the installed system?

---

### Post by VMC on 2018-07-01
Its installed with zram present.

---

### Post by sudodus on 2018-07-01
zram in the installed Lubuntu system is probablly a bug, but I am not sure.

I suggest that you create a bug report about it, and see what response you get from the Lubuntu developers. If you link to the bug report to a new post in this thread, I will make a test installation, and if I am also affected, I will confirm it.

[hr][/hr]
Edit:

My experience from when zram was introduced some years ago: it is not stable enough for an installed system, and for that reason it was only used in the live Lubuntu system.

---

### Post by VMC on 2018-07-01
This is so early on in the development, I'll wait. I just was confused as to what it was. Some google post indicated how to handle the zram.

---

### Post by flocculant on 2018-07-03
> **VMC said:**
> This is so early on in the development, I'll wait. I just was confused as to what it was. Some google post indicated how to handle the zram.

Up to you of course. but ... ;)

Report early - might get fixed, report late - less chance of it.

---

### Post by VMC on 2018-07-03
Yes, your right. I usually zsync each week around the weekend. If its still showing up, I'll file a report.

---

### Post by sudodus on 2018-07-08
@vmc,

I zsynced the current daily iso file, dated 2018-07-07,

cosmic-desktop-amd64.iso

Then I tried to install Lubuntu Cosmic from a cloned USB pendrive, but failed. I tried with with the new 'Lubuntu installer' from the 'System' menu, alias Calamares. I tried in BIOS mode.

[LIST]
[*]I tried with manual partitioning in a couple of ways and it failed in different ways.
[*]
[*]I tried the most basic way (to use the whole drive), 'Erase disk'.
[*]
[*]I tried in UEFI mode - and it wanted a DVD (failed to use the data in the pendrive).
[*]
[*]I burned a DVD and it booted, but the installer failed (in UEFI mode and in BIOS mode).
[*]
[/LIST]

How did you manage to install it?

[hr][/hr]
Edit: Finally I tried via the Ubuntu mini.iso (64-bit), and it worked.

There is no zram in this installed system. So I cannot confirm the bug.

---

### Post by VMC on 2018-07-08
I 'dd' to a usb flash. Odd, but it fails using loop-back method. Never failed before. [COLOR=#000000]Calamares is also new this time. No more ubiquity. Thanks for trying.[/COLOR]

---

### Post by sudodus on 2018-07-09
I was trying with a Toshiba laptop with a third generation Intel i5 processor. I have used this computer since 2013 to test Lubuntu and other Ubuntu flavours, and I know very well what to expect with it both in UEFI mode and BIOS mode (alias CSM alias legacy mode).

Like you, I cloned from the iso file to a USB pendrive, and it booted nicely. But Calamares failed for me. I tried many ways, and it failed in different ways. (I checked anyway to boot from what was created, but the installed system could not boot.)

Did you start from a 64-bit or 32-bit iso file?

Did you install with Calamares? In that case, please specify what you selected at each step, and I can try according to your steps.

---

### Post by VMC on 2018-07-09
loop-back install failed most likely at same spot as yours did using Calamares.

 **dd** to **usb**, booted usb, installed lubuntu from usb using Calamares, **zram** present on installed system.

The loop-back method that has stood the test of time, failed as Calamares was unsquashing the filesystem. I was going to copy the screenshot, but it installed using usb.

---

### Post by sudodus on 2018-07-09
Please describe *how* you used Calamares (with details).

[LIST]
[*]Does it work if the USB drive is cloned from the *current* daily iso file?
[*]
[*]Please describe the computer, brand name and model (or virtual machine, whatever it is).
[*]
[*]Please describe with details, how to select options in the different steps, and tell me if there are other things to consider, for example about the computer (hardware components and settings).
[/LIST]

---

### Post by VMC on 2018-07-09
```
CPU~Dual core AMD Athlon II X2 250 (-MCP-) speed/max~1800/3000 MHz Kernel~4.15.0-24-generic x86_64 Up~16 min Mem~559.4/3693.2MB HDD~1000.2GB(0.6% used) Procs~159 Client~Shell inxi~2.3.56
```

OK, I see. Many people use vbox. I don't. I install into real partition.

Here's a step by step guide showing both Ubiquity & Calamares:
[https://www.zdnet.com/article/hands-on-with-ubiquity-and-calamares-two-linux-installers-side-by-side/](https://www.zdnet.com/article/hands-on-with-ubiquity-and-calamares-two-linux-installers-side-by-side/)

Manjaro is using Calamares in the link.

edit2: Another Calamares guide, showing Manjaro instlling using Calamares:
[http://linuxbsdos.com/2015/09/29/calamares-a-distribution-independent-system-installer/](http://linuxbsdos.com/2015/09/29/calamares-a-distribution-independent-system-installer/)

---

### Post by VMC on 2018-07-09
Maybe Lubuntu.org wants **zram** installed. Look at the bottom of filesystem.manifest:

**xubuntu**:
> ...
xxd    2:8.0.1766-1ubuntu1
xz-utils    5.2.2-1.3
yelp    3.28.1-1ubuntu2
yelp-xsl    3.28.0-1
yudit-common    2.9.6-7
zenity    3.28.1-1
zenity-common    3.28.1-1
zip    3.0-11build1
zlib1g:amd64    1:1.2.11.dfsg-0ubuntu2
**lubuntu**:> ...xxd    2:8.0.1766-1ubuntu1xz-utils    5.2.2-1.3
yelp    3.28.1-1ubuntu2
yelp-xsl    3.28.0-1
youtube-dl    2018.06.18-1.1
yudit-common    2.9.6-7
zenity    3.28.1-1
zenity-common    3.28.1-1
zip    3.0-11build1
zlib1g:amd64    1:1.2.11.dfsg-0ubuntu2
zlib1g-dev:amd64    1:1.2.11.dfsg-0ubuntu2
[COLOR=#ff0000]**zram-config    0.5**[/COLOR]

---

### Post by sudodus on 2018-07-09
I think the following two items might contain the solution:

1. I have an old Dual core AMD Athlon II X2, not the same as yours, but I hope close enough.

> **VMC said:**
> ```
CPU~Dual core AMD Athlon II X2 250 (-MCP-) speed/max~1800/3000 MHz Kernel~4.15.0-24-generic x86_64 Up~16 min Mem~559.4/3693.2MB HDD~1000.2GB(0.6% used) Procs~159 Client~Shell inxi~2.3.56
```


2. I will use manual partitioning and install into a real partition (in BIOS mode, which is the only option with my old computer with the old Athlon CPU).

> 
OK, I see. Many people use vbox. I don't. I install into real partition.


---

### Post by sudodus on 2018-07-09
Sorry, I get one of the failures again, that I got before when trying in my Toshiba, that can manage both UEFI and BIOS, when trying (this time with the 64-bit daily iso file dated July 8).

I am trying in an **old computer from 2008** with an

[LIST]
[*]ASUS M2N-VM DVI motherboard
[*]AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
[*]and 2 GB RAM
[/LIST]

This computer has no UEFI features, but the error indicates that the installer checks for UEFI, fails and quits.

"Command [ -d /sys/firmware/efi ] && ehroot /tmp/..."

A **screendump of the error window** is attached.

[hr][/hr]

Output of **lshw**:
```

lubuntu
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=60BEBF7C-8DFE-D511-AD2F-001D60A176D7
  *-core
       description: Motherboard
       product: M2N-VM DVI
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev x.xx
       serial: MS6C79B21908156
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0603
          date: 03/26/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 2300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow rep_good nopl cpuid extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory:0
          description: System Memory
          physical id: 30
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP67 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:dc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-usb:0
          description: USB controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:dfeff000-dfefffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 4.15.0-23-generic ohci_hcd
             physical id: 1
             bus info: usb@3
             logical name: usb3
             version: 4.15
             capabilities: usb-1.10
             configuration: driver=hub slots=6 speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dfefec00-dfefecff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 4.15.0-23-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 4.15
             capabilities: usb-2.00
             configuration: driver=hub slots=6 speed=480Mbit/s
           *-usb
                description: Mass storage device
                product: Mass Storage Device
                vendor: Generic
                physical id: 4
                bus info: usb@1:4
                logical name: scsi2
                version: 1.00
                serial: 058F312D81B1
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=250mA speed=480Mbit/s
              *-disk:0
                   description: SCSI Disk
                   product: USB SD Reader
                   vendor: Generic
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sdb
                   version: 1.00
                   capabilities: removable
                   configuration: logicalsectorsize=512 sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sdb
              *-disk:1
                   description: SCSI Disk
                   product: USB CF Reader
                   vendor: Generic
                   physical id: 0.0.1
                   bus info: scsi@2:0.0.1
                   logical name: /dev/sdc
                   version: 1.01
                   capabilities: removable
                   configuration: logicalsectorsize=512 sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sdc
              *-disk:2
                   description: SCSI Disk
                   product: USB SM Reader
                   vendor: Generic
                   physical id: 0.0.2
                   bus info: scsi@2:0.0.2
                   logical name: /dev/sdd
                   version: 1.02
                   capabilities: removable
                   configuration: logicalsectorsize=512 sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sdd
              *-disk:3
                   description: SCSI Disk
                   product: USB MS Reader
                   vendor: Generic
                   physical id: 0.0.3
                   bus info: scsi@2:0.0.3
                   logical name: /dev/sde
                   version: 1.03
                   capabilities: removable
                   configuration: logicalsectorsize=512 sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sde
     *-usb:2
          description: USB controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:dfefd000-dfefdfff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 4.15.0-23-generic ohci_hcd
             physical id: 1
             bus info: usb@4
             logical name: usb4
             version: 4.15
             capabilities: usb-1.10
             configuration: driver=hub slots=6 speed=12Mbit/s
     *-usb:3
          description: USB controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:dfefe800-dfefe8ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 4.15.0-23-generic ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 4.15
             capabilities: usb-2.00
             configuration: driver=hub slots=6 speed=480Mbit/s
           *-usb
                description: Mass storage device
                product: Mass Storage Device
                vendor: JetFlash
                physical id: 2
                bus info: usb@2:2
                logical name: scsi3
                version: 1.00
                serial: 6SY1D0AP
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
              *-disk
                   description: SCSI Disk
                   product: Transcend 16GB
                   vendor: JetFlash
                   physical id: 0.0.0
                   bus info: scsi@3:0.0.0
                   logical name: /dev/sdf
                   logical name: /cdrom
                   version: 8.01
                   size: 14GiB (16GB)
                   capabilities: removable
                   configuration: ansiversion=2 logicalsectorsize=512 mount.fstype=iso9660 mount.options=ro,noatime,nojoliet,check=s,map=n,blocksize=2048 sectorsize=512 state=mounted
                 *-medium
                      physical id: 0
                      logical name: /dev/sdf
                      logical name: /cdrom
                      size: 14GiB (16GB)
                      capabilities: partitioned partitioned:dos
                      configuration: mount.fstype=iso9660 mount.options=ro,noatime,nojoliet,check=s,map=n,blocksize=2048 signature=30ab8989 state=mounted
                    *-volume
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 2
                         logical name: /dev/sdf2
                         version: FAT12
                         serial: 811b-9d07
                         size: 15EiB
                         capabilities: primary boot fat initialized
                         configuration: FATs=2 filesystem=fat
              *-cdrom
                   description: SCSI CD-ROM
                   product: AutoRun Disk
                   vendor: Generic
                   physical id: 0.0.1
                   bus info: scsi@3:0.0.1
                   logical name: /dev/sr1
                   version: 8.00
                   capabilities: removable audio
                   configuration: ansiversion=2 status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/sr1
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:dfef8000-dfefbfff
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:e000(size=4096) memory:dff00000-dfffffff
        *-network
             description: Ethernet interface
             product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 7
             bus info: pci@0000:01:07.0
             logical name: enp1s7
             version: 10
             serial: 00:19:e0:0d:00:95
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.23 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:e800(size=256) memory:dffffc00-dffffcff memory:dffc0000-dffdffff
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d480(size=8) ioport:d400(size=4) ioport:d080(size=8) ioport:d000(size=4) ioport:cc00(size=16) memory:dfef6000-dfef7fff
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: enp0s10
          version: a2
          serial: 00:1d:60:a1:76:d7
          capacity: 1Gbit/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:24 memory:dfefc000-dfefcfff ioport:c880(size=8) memory:dfefe400-dfefe4ff memory:dfefe000-dfefe00f
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-pci:3
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-pci:4
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-pci:5
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-pci:6
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-pci:7
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 11
          bus info: pci@0000:00:11.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0
     *-display
          description: VGA compatible controller
          product: C68 [GeForce 7050 PV / nForce 630a]
          vendor: NVIDIA Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:21 memory:de000000-deffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:c0000-dffff
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 13
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S203P
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 14
          logical name: scsi6
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250620AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sda
             version: L
             serial: 9QE3BH4F
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=1b2412db
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sda1
                logical name: /tmp/calamares-root-f3pp1nqk
                version: 1.0
                serial: d870cd18-8438-42b8-a6d4-622e547d749f
                size: 232GiB
                capacity: 232GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2018-07-09 18:04:53 filesystem=ext4 lastmountpoint=/tmp/calamares-root-f3pp1nqk modified=2018-07-09 18:05:57 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2018-07-09 18:05:57 state=mounted

```

---

### Post by VMC on 2018-07-09
I found four **zram**  files under an unsquashed folder:
```
./squashfs-root/lib/modules/4.15.0-23-generic/kernel/drivers/block/zram
./squashfs-root/usr/src/linux-headers-4.15.0-23-generic/include/config/zram
./squashfs-root/usr/src/linux-headers-4.15.0-23/drivers/block/zram
./squashfs-root/usr/src/linux-headers-4.15.0-23/tools/testing/selftests/zram
```

It looks like this in not an accident or error.

---

### Post by sudodus on 2018-07-09
I can't even use Calamares, and you complain about zram :-P

---

### Post by VMC on 2018-07-09
@sudodus- Read the bug report, hopefully it will be resolved soon. Its confirmed.

---

### Post by VMC on 2018-07-09
> **sudodus said:**
> I can't even use Calamares, and you complain about zram :-P
If you want to test Calamares, try installing with one of the other OS's (manjaro). Just a thought.
I'm going to look at my error report from loop-back and compare it to yours.

---

### Post by VMC on 2018-07-09
Here's the slide show. Just unzip to folder and follow the slide:

---

### Post by sudodus on 2018-07-10
> **VMC said:**
> @sudodus- Read the bug report, hopefully it will be resolved soon. Its confirmed.

Yes, the new Lubuntu developer, Simon Quigley, made a bug-fix :-)

---

### Post by sudodus on 2018-07-10
> **VMC said:**
> Here's the slide show. Just unzip to folder and follow the slide:

Thank you :-)

I *think* this slideshow indicates, that I am doing things the right way in the Calamares windows. Something else is wrong for me, maybe some hardware in the computers, that I have tested, maybe my European timezone, even though I have also tried the default timezone and locale (New York). Maybe something else.

Anyway, I have created a bug report at Launchpad, [#1780875](https://bugs.launchpad.net/ubuntu/+source/calamares-settings-ubuntu/+bug/1780875).

---

### Post by VMC on 2018-07-10
> **sudodus said:**
> Thank you :-)

I *think* this slideshow indicates, that I am doing things the right way in the Calamares windows. Something else is wrong for me, maybe some hardware in the computers, that I have tested, maybe my European timezone, even though I have also tried the default timezone and locale (New York). Maybe something else.

Anyway, I have created a bug report at Launchpad, [#1780875]("https://bugs.launchpad.net/ubuntu/+source/calamares-settings-ubuntu/+bug/1780875").
Did you see the fix release on that bug report?

---

### Post by sudodus on 2018-07-10
Yes, and I have found more bugs along the road,

[1780977](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1780977)

[1780984](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1780984)

[1781015](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1781015)

---

### Post by tsimonq2 on 2018-07-11
Please, keep the bug reports coming. :)

I really do appreciate the testing work here.

---

### Post by sudodus on 2018-07-11
For the first time I am able to install Lubuntu Cosmic with Calamares!

The bugfixes in the current daily iso file **cosmic-desktop-amd64.iso** dated July 11 2018 has made it possible to install Lubuntu Cosmic in my old computer from 2008,

[LIST]
[*]    ASUS M2N-VM DVI motherboard
[*]    AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
[*]    and 2 GB RAM
[/LIST]
[hr][/hr]
And there is [no longer] any problem with zram in the installed system. So I suggest the you mark this thread as SOLVED :-)

---

