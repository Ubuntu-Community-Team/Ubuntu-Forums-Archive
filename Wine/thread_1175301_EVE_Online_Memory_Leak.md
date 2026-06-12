---
title: "EVE Online Memory Leak?"
date: 2009-06-01
forum: Wine
---

### Post by napalm brain on 2009-06-01
Since the CCP has stopped developing a Linux client, I've started to use Wine. Everything has run without a hitch aside from a few basic issues with the Arial font not showing up in the EULA which was easily resolved. 

The main issue has been a memory leak in the client. I start the game, it runs for around 45 minutes and suddenly my system completely locks up. I can't move the mouse or log out of the session. I end up having to Alt+SysRq+REISUB.

Any ideas as to what I could do to resolve this issue?

Also--I realize I did not post any information but I'm not entirely sure how to paste the input with my system freezing. If someone could give me a hand so I could provide more information as to what's failing--it would be greatly appreciated. My system exceeds the system requirements too. So that isn't an issue.

---

### Post by nolliecrooked on 2009-06-01
> **napalm brain said:**
> Since the CCP has stopped developing a Linux client, I've started to use Wine. Everything has run without a hitch aside from a few basic issues with the Arial font not showing up in the EULA which was easily resolved. 
 
The main issue has been a memory leak in the client. I start the game, it runs for around 45 minutes and suddenly my system completely locks up. I can't move the mouse or log out of the session. I end up having to Alt+SysRq+REISUB.
 
Any ideas as to what I could do to resolve this issue?
 
Also--I realize I did not post any information but I'm not entirely sure how to paste the input with my system freezing. If someone could give me a hand so I could provide more information as to what's failing--it would be greatly appreciated. My system exceeds the system requirements too. So that isn't an issue.
 
are you sure its a memory leak?

---

### Post by napalm brain on 2009-06-01
It's sort of my assumption.

I try to monitor the memory usage and it continues to go up as I play. It goes from around 75% to 80% and so on. The last time I was able to check before everything went haywire (mind you, it's locked while playing, so I don't think it's an issue of me switching from the game while it's in use) it was around 95%. At that point, everything began to lag.

If it doesn't sound like a memory leak, any insight as to what it might be?

---

### Post by nolliecrooked on 2009-06-01
> **napalm brain said:**
> It's sort of my assumption.
 
I try to monitor the memory usage and it continues to go up as I play. It goes from around 75% to 80% and so on. The last time I was able to check before everything went haywire (mind you, it's locked while playing, so I don't think it's an issue of me switching from the game while it's in use) it was around 95%. At that point, everything began to lag.
 
If it doesn't sound like a memory leak, any insight as to what it might be?
 
ok before anything, what are your PC specs?

---

### Post by napalm brain on 2009-06-01
Input from lshw:

```
    description: Notebook
    product: VGN-FZ190N
    vendor: Sony Corporation
    version: R5312032
    serial: 28399139-3000418
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=7FECC3E0-35EA-11DC-87C0-0013A9C09186
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0050J7 (04/18/2007)
          size: 103KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          slot: N/A
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
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
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM
             physical id: 0
             slot: SODIMM1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM [empty]
             physical id: 1
             slot: SODIMM2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          size: 100MHz
          capabilities: vmx ht
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
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G86M [GeForce 8400M GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:6c:f3:91
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 16
                serial: 00:13:a9:c0:91:86
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:09:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@0000:09:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:09:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW  DVR-K17
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB2DB1EVG81RBE
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ad3533a7
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ce1c3b0b-eb35-4f53-a8f3-ce58ead957f6
                   size: 76GiB
                   capacity: 76GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2008-10-09 17:40:21 filesystem=ext3 modified=2009-05-30 22:51:25 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-30 22:51:25 state=mounted
              *-volume:1
                   description: Extended partition
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: 0e91928c-e068-11dd-b671-8fbd31388181
                   size: 32GiB
                   capacity: 35GiB
                   capabilities: primary extended partitioned partitioned:extended extended_attributes large_files ext2 initialized
                   configuration: filesystem=ext2 modified=2009-01-25 21:39:21 mounted=2009-01-25 21:39:21 state=clean
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2957MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 32GiB
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:8b:8e:89:07:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by nolliecrooked on 2009-06-01
ok your laptop only has 1GIGb of RAM, and your GeForce 8400M has to share out of that RAM space(128MEGb or 256MEGb).
 
EVE Online **REQUIRES** at least 1GIGb of RAM and at the mo your kinda like this;
 
1GIGb of RAM -(Minus) 128MEGb GeForce 8400M RAM take = 896MEGb of RAM
 
thats **BELOW** what EVE requires, so my basic suggeston is **UPGRADE** your RAM to 2GIGb, that should help!
 
BTW, what version of WINE are you using?

---

### Post by napalm brain on 2009-06-01
Ah, that makes enough sense. I figured it just wouldn't run if it didn't have enough RAM. Shows you how much I know. 

I am using Wine 1.1.22. I'm guessing that takes up some RAM too?

Thank you for your help.

---

### Post by nolliecrooked on 2009-06-01
> **napalm brain said:**
> Ah, that makes enough sense. I figured it just wouldn't run if it didn't have enough RAM. Shows you how much I know. 
 
I am using Wine 1.1.22. I'm guessing that takes up some RAM too?
 
Thank you for your help.
 
ummmmm yea as a backround process but it dosent really matter. I havent played Eve in like FOREVER, but yeah the RAM thing looks like it could be the issue.
 
good luck anyway.

---

### Post by asdfoo on 2009-06-01
Also make sure you're using a nvidia driver 180.51 or newer, earlier drivers had leaks when running some games.

---

### Post by napalm brain on 2009-06-01
Yes, it is the latest driver. I'm usually on-top of updates. 

I'm just not sure if it's worth getting more RAM for a laptop. Someone told me that it was never worth upgrading drivers on a laptop.

---

### Post by nolliecrooked on 2009-06-02
> **napalm brain said:**
> Yes, it is the latest driver. I'm usually on-top of updates. 
 
I'm just not sure if it's worth getting more RAM for a laptop. Someone told me that it was never worth upgrading drivers on a laptop.
 
they were wrong, upgrading a laptops RAM can make a **LOT** of difference.

---

