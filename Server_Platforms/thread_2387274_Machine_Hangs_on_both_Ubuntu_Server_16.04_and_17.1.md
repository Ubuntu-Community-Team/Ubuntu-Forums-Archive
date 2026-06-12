---
title: "Machine Hangs on both Ubuntu Server 16.04 and 17.10"
date: 2018-03-17
forum: Server Platforms
---

### Post by twmarshall19 on 2018-03-17
The title pretty much says it all. The machine is pretty old, now 11 years old with a Core 2 Duo which I'm to lazy to check because it's so late and I'm posting this just before I go to bed, 2GB of DDR2 ram, and everything that should fit the spec of 17.10, if not, 16.04. After inputting the keyboard region, it just hangs, going blank on both HDD and DVD activity. Sorry if there's some very common issue and very easy to spot thing that I'm missing, but I'm an Ubuntu Server n00b.

---

### Post by mörgæs on 2018-03-17
Hi, welcome to the fora.

From a live boot (desktop ISO) please copy ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post the results in CODE tags. It will show us the hardware details.

---

### Post by twmarshall19 on 2018-03-17
Okay. It's quite a lot, but I got it. ```
computer
    description: Desktop Computer
    product: 6073AK1 (NONE)
    vendor: LENOVO
    version: ThinkCentre M57p
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=NONE keyboard_password=disabled power-on_password=disabled sku=NONE uuid=[REMOVED]
  *-core
       description: Motherboard
       product: LENOVO
       vendor: LENOVO
       physical id: 0
       version: NONE
       serial: [REMOVED]
       slot: INSIDE
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 2RKT38AUS
          date: 02/15/2008
          size: 125KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing escd cdboot edd acpi usb ls120boot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          slot: LGA 775
          size: 2180MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti retpoline tpr_shadow vnmi flexpriority dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 4MiB
             capacity: 6MiB
             capabilities: burst internal write-back
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 48594D503131325536344350382D59352020
             vendor: Hyundai Electronics
             physical id: 0
             serial: [REMOVED]
             slot: J6G1
             size: 1GiB
             width: 40968 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 34383030303032302D303100000000000000
             vendor: Southland Microsystems
             physical id: 1
             serial: [REMOVED]
             slot: J6G2
             size: 1GiB
             width: 41480 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns) [empty]
             product: 012345678901234567890123456789012345
             vendor: 48spaces
             physical id: 2
             serial: [REMOVED]
             slot: J6H1
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns) [empty]
             product: 012345678901234567890123456789012345
             vendor: 48spaces
             physical id: 3
             serial: [REMOVED]
             slot: J6H2
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: 82Q35 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82Q35 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0100000-d017ffff ioport:1c70(size=8) memory:c0000000-cfffffff memory:d0000000-d00fffff memory:c0000-dffff
        *-communication:0
             description: Communication controller
             product: 82Q35 Express MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:25 memory:d03a6000-d03a600f
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: 82Q35 Express PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi cap_list
             configuration: latency=0
             resources: ioport:1c88(size=8) ioport:1c7c(size=4) ioport:1c80(size=8) ioport:1c78(size=4) ioport:1c20(size=16)
        *-communication:1
             description: Serial controller
             product: 82Q35 Express Serial KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:1c90(size=8) memory:d01a4000-d01a4fff
        *-network
             description: Ethernet interface
             product: 82566DM-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 02
             serial: [REMOVED]
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=1.3-1 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:24 memory:d0180000-d019ffff memory:d01a5000-d01a5fff ioport:1820(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-36-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Laser Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@3:1
                   version: 56.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Generic
                   physical id: 2
                   bus info: usb@3:2
                   version: 2.05
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-36-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-36-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:d03a6800-d03a6bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:26 memory:d01a0000-d01a3fff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-36-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-36-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18e0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-36-generic uhci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d03a6c00-d03a6fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: USB 2.0 FD
                   vendor: PNY Technologies
                   physical id: 5
                   bus info: usb@2:5
                   logical name: scsi4
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=480mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdb
                      size: 3854MiB (4041MB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512 signature=f100956e
                    *-volume
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 1
                         bus info: scsi@4:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /media/ubuntu/SRVR_VOL
                         version: FAT32
                         serial: [REMOVED]
                         size: 3851MiB
                         capacity: 3853MiB
                         capabilities: primary fat initialized
                         configuration: FATs=2 filesystem=fat label=SRVR_VOL mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IO (ICH9DO) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:1
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c40(size=16) ioport:1c30(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d03a7000-d03a70ff ioport:1c00(size=32)
        *-ide:2
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1cc0(size=8) ioport:1cb4(size=4) ioport:1cb8(size=8) ioport:1cb0(size=4) ioport:1c60(size=16) ioport:1c50(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500418AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC38
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=31879055
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/ubuntu/NAS HDD
                version: 1.0
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2018-03-17 14:58:49 filesystem=ext4 label=NAS HDD modified=2018-03-17 15:00:31 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2018-03-17 15:00:31 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B1ST   i
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /cdrom
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,nojoliet,check=s,map=n,blocksize=2048 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime,nojoliet,check=s,map=n,blocksize=2048 signature=550f2a26 state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 2
                   version: FAT12
                   serial: [REMOVED]
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat 
```

---

### Post by mörgæs on 2018-03-18
It looks like fine hardware. The BIOS is somewhat old but I doubt an upgrade would change anything.

Are you able to install from the live boot?

---

### Post by twmarshall19 on 2018-03-18
Yeah, it will. I even ran memtest and verified the CD, and both came out positive.

---

### Post by twmarshall19 on 2018-03-18
I have some news: I ran the server setup (17.10) in Expert Mode and -v, and isolated the point at which it crashes. It crashes whenever you load the debconf preconfig file. This happens on both versions, and I have no idea why. I'll try to do the install without it.

---

### Post by twmarshall19 on 2018-03-18
New problem: It just decides to not install. After doing every step except for the debconf preconfig file, it sort crashes and says that I cannot install. The preconfig file to definitely the culprit, how do I bypass this?

---

### Post by mörgæs on 2018-03-19
How does the 18.04 server version behave?

---

### Post by twmarshall19 on 2018-03-31
Sorry that I haven't been able to test it as I haven't been home, but the same thing happens. It locks up on the debconf preconfig file.

---

### Post by mörgæs on 2018-04-01
Here is a post describing a possible solution:
[https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-preseed-not-found-669215/](https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-preseed-not-found-669215/)

I'm aware that it's old but nevertheless worth trying.

---

