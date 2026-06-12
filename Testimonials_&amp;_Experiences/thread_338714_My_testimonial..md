---
title: "My testimonial."
date: 2007-01-14
forum: Testimonials &amp; Experiences
---

### Post by DarkN00b on 2007-01-14
A user called Koori23 made a post earlier in the Cafe basically saying [quote="Koori23"]Honestly, having read for many hours, some of the posts in this forum.. I'm beginning to think I've missed something. Maybe I am the only one who *hasn't* had incrediby horrible experiences with Ubuntu..[/quote]

That got me to thinking that I should post here about my own great experience with Ubuntu.

Back in August I installed Dapper and went whole hog because I wasn't paying attention, overwriting my Windows partition. I have never looked back. I installed edgy about a month after it came out, and all I had to do was install my wireless firmware to be on my way.

Ubuntu is great! It meets all my requirements for and OS: audio/video editing, watching movies, listening to music and more -- in short everything I need from an OS. Thank you Canonical and the entire Ubuntu family for giving me the opportunity to use such an awesome operating system.

For completeness' sake I include the output of the 'lshw' command below. One last comment after that.

```
laptop                    
    description: Notebook
    product: HP Pavilion ze2000 (PM341AV#ABA)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF5080324
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=600EE008-8971-D911-9E40-00C09F7EC604
  *-core
       description: Motherboard
       product: 09EC
       vendor: Quanta
       physical id: 0
       version: 34.20
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.14 (01/28/2005)
          size: 102KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: U1
          size: 1300MHz
          capacity: 1300MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 256MB
          capacity: 2GB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: J5G3
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: J5G2
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-system:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
        *-system:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:e8000000-efffffff iomemory:e0000000-e007ffff ioport:1800-1807 irq:193
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:f0000000-f7ffffff iomemory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: USB WLAN
                   vendor: ZyXEL Communications Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   capabilities: usb-1.10
                   configuration: driver=zd1201 maxpower=500mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:201
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e0100000-e01003ff irq:209
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network DISABLED
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 10
                serial: 00:c0:9f:7e:c6:04
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
                resources: ioport:3000-30ff iomemory:e0206800-e02068ff irq:193
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@02:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:e0204000-e0204fff irq:169
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@02:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:e0206000-e02067ff iomemory:e0200000-e0203fff irq:217
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1810-181f iomemory:22000000-220003ff irq:185
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK4025GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: KA101A
                   serial: 15SL0077S
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 36GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 635MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: Toshiba DVD-ROM SD-C2612
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1A25
                   serial: 254G610125
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:1880-189f irq:5
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:e0100c00-e0100dff iomemory:e0100800-e01008ff irq:177
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:177
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:a0:c5:c1:41:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.34 multicast=yes wireless=IEEE 802.11b

```

So if you have had a good experience with Ubuntu, go ahead and post it here. So often we hear about people's problems with Ubuntu, but we don't hear nearly as much about the good.

---

### Post by MontanaMax on 2007-01-14
I think my experience with Ubuntu started at the same time yours did. I was writing a paper on FOSS for a college class, and decided I should try some of this Linux stuff out for myself. After installing Mandrake, CentOS, and attempting Suse, I got a Kubuntu CD from a friend. It was the first distribution that recognized and worked smoothly with my HP TC1100 Tablet without a fuss, and I've been loving it ever since. I upgraded to Kubuntu Edgy about 3 weeks after it was released. The upgrade was successfull, but my machie ran slower than it did on Dapper. So I did a fresh data backup to an external drive and performed a fresh clean Kubuntu Edgy install. Welcome back speed!

I really love that with a little digging I can always find quality software, and near seamless support for any peripheral I've tried (iPod / printer / USB drives / wireless / etc.) I'm not quite on the bleeding edge  - I haven't installed Beryl or Feisty yet, and I keep most of my real experimenting on a VMware virtual machine, but I have eye candy galore, a stable system.  great performance - and new releases and features to look forward to every month or so!

Thanks "Ubuntu People"!  :)

```
pingu
    description: Sub Notebook
    product: HP Tablet PC TX1100
    vendor: Hewlett-Packard
    version: 0F0F
    serial: KRD3460703
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific chassis=sub-notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=0008A38F-AC63-0010-908F-6F7FF7AE0FCF
  *-core
       description: Motherboard
       product: 08B0
       vendor: Hewlett-Packard
       physical id: 0
       version: 31.0A
       serial: KRD3460703
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: FirstBIOS Pro 2002 Q3 (06/06/2005)
          size: 106KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1000MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: U49
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: J6A
             size: 512MB
             width: 64 bits
             clock: 333MHz (3.003ns)
        *-bank:1
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: J7A
             size: 512MB
             width: 64 bits
             clock: 333MHz (3.003ns)
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: e2000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e2000000-e3ffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 420 Go 32M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:d8000000-d8ffffff iomemory:f0000000-f3ffffff iomemory:e8000000-e807ffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: USB K/B+Mouse
                   vendor: Jing-Mold
                   physical id: 2
                   bus info: usb@1:2
                   version: 4.20
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:15
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:12
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Bluetooth wireless interface
                   product: Bluetooth by hp
                   vendor: ACTIONTEC
                   physical id: 2
                   bus info: usb@3:2
                   version: 8.02
                   capabilities: bluetooth usb-1.10
                   configuration: driver=hci_usb maxpower=90mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d0000000-d00003ff irq:10
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb:0 UNCLAIMED
                   description: Mass storage device
                   product: USB Multibay IDE
                   vendor: Compaq
                   physical id: 3
                   bus info: usb@4:3
                   version: 11.00
                   serial: 0B00015A042E4D79
                   capabilities: usb-2.00 scsi
                   configuration: maxpower=98mA speed=480.0MB/s
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub Controller
                   vendor: NEC Corporation
                   physical id: 4
                   bus info: usb@4:4
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                 *-usb
                      description: Keyboard
                      product: Compaq Wireless HID Receiver
                      vendor: Chicony
                      physical id: 4
                      bus info: usb@4:4.4
                      version: 2.10
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@02:05.0
                logical name: eth1
                version: 04
                serial: 00:04:23:7e:3e:4c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.46 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:e0002000-e0002fff irq:15
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@02:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:e0003000-e0003fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@02:06.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:e0004000-e0004fff irq:10
           *-system UNCLAIMED
                description: System peripheral
                product: PCI1620 Firmware Loading Function
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@02:06.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: ioport:4000-403f
           *-network:1
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 7
                bus info: pci@02:07.0
                logical name: eth0
                version: 01
                serial: 00:11:0a:42:a3:e2
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.36 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:e0000000-e0001fff irq:12
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1860-186f iomemory:55000000-550003ff irq:12
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC25N040ATMR04-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MO2OAD0A
                   serial: MRG226K2HS7BJH
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 35GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 1584MB
                      capabilities: extended partitioned partitioned:extended
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:1880-189f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:d0000c00-d0000dff iomemory:d0000800-d00008ff irq:10
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:10

```

---

### Post by francisco_athens on 2007-06-11
> **MontanaMax said:**
> 
I really love that with a little digging I can always find quality software, and near seamless support for any peripheral I've tried (iPod / printer / USB drives / wireless / etc.) I'm not quite on the bleeding edge  - I haven't installed Beryl or Feisty yet,
Indeed!  I've had a good experience installing fresh Feisty on my TC1100.  Though, I'm still waiting for the automatic wacom rotation patch to be included in the driver!  Beryl window managers don't seem to like the nvidia chipset in 16-bit mode, only 24-bit, go figure! Otherwise I'm happy!

---

### Post by Bluecircle on 2007-06-11
I've also had a close to perfect experience. A few broken things that were fun to fix and help me learn, but nothing that couldn't be fixed without 10 minutes of research and a quick tutorial! :)

lshw:

```

brian-laptop              
    description: Notebook
    product: VGN-TX770P
    vendor: Sony Corporation
    version: J001K019
    serial: 28240832-3007502
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=CD5CB6A0-DF2D-11D4-8C62-0013A92ADF71
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0051V1 (12/01/2005)
          size: 113KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.30GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.13.8
          slot: N/A
          size: 1300MHz
          capacity: 1300MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst internal write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 6
             slot: L3 Cache
             capabilities: burst data
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: SODIMM DDR 100 MHz (10.0 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM1
             size: 512MB
             width: 32 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: SODIMM DDR 100 MHz (10.0 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM2
             size: 512MB
             width: 32 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-6-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: /dev/usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-6-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: /dev/usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-6-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: /dev/usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Bluetooth wireless interface
                   product: UGX
                   vendor: ALPS
                   physical id: 1
                   bus info: usb@3:1
                   version: 19.15
                   capabilities: bluetooth usb-2.00
                   configuration: driver=hci_usb maxpower=100mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-6-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: /dev/usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.22-6-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: /dev/usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: NECEL
                   physical id: 2
                   bus info: usb@5:2
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: maxpower=100mA slots=3 speed=480.0MB/s
                 *-usb:0 UNCLAIMED
                      description: Generic USB device
                      product: HP LaserJet 1020
                      vendor: Hewlett-Packard
                      physical id: 1
                      bus info: usb@5:2.1
                      version: 1.00
                      serial: FN0W91J
                      capabilities: usb-2.00
                      configuration: maxpower=98mA speed=480.0MB/s
                 *-usb:1
                      description: Generic USB device
                      product: OneTouch III
                      vendor: Maxtor
                      physical id: 2
                      bus info: usb@5:2.2
                      logical name: scsi2
                      version: 3.03
                      serial: GC202Q4U
                      capabilities: usb-2.00 emulated scsi-host
                      configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s
                    *-disk
                         description: SCSI Disk
                         product: OneTouch IIIm
                         vendor: Maxtor
                         physical id: 0.0.0
                         bus info: scsi@2:0.0.0
                         logical name: /dev/sdb
                         version: 0337
                         serial: GC202Q4U
                         size: 465GB
                         capabilities: partitioned partitioned:dos
                         configuration: ansiversion=4
                       *-volume
                            description: HPFS/NTFS partition
                            physical id: 1
                            bus info: scsi@2:0.0.0,1
                            logical name: /dev/sdb1
                            capacity: 465GB
                            capabilities: primary
                 *-usb:2 UNCLAIMED
                      description: Generic USB device
                      product: PS2 to USB Converter
                      vendor: CHESEN
                      physical id: 3
                      bus info: usb@5:2.3
                      version: 0.10
                      capabilities: usb-1.10
                      configuration: maxpower=100mA speed=1.5MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:06:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 5.2
                bus info: pci@0000:06:05.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 5.3
                bus info: pci@0000:06:05.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-network:0
                description: Ethernet interface
                product: 82562EM/EX/GX - PRO/100 VM (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth0
                version: 03
                serial: 00:13:a9:2a:df:71
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.106 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: b
                bus info: pci@0000:06:0b.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:7e:f3:58
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK8007GA
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BG01
                serial: 36SF4463S
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 71GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MB
                   capacity: 2933MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: UJ-832D
                vendor: MATSHITA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.61
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

---

### Post by neorou on 2007-06-12
I started out with Breezy Badger Kubuntu less than 2 years ago. I liked it right away. 

At the time, my knowledge of linux was not as full as I wanted it to be. As I worked with various hard ware, including building my own linux boxes, I gradually started warming up to better methods of installation and configuration. The most specific example being getting drivers for my PCMCIA card and having to write one of my own. If it weren't for NDISwrapper, I would have to buy a new PCMCIA card.

Most of my linux-using-colleagues used KDE and I was influenced by Linus Thorvalds own criticisms of GNOME. 
[http://mail.gnome.org/archives/usability/2005-December/msg00021.html](http://mail.gnome.org/archives/usability/2005-December/msg00021.html)
After comparing the two, I decided that since most people seem to use GNOME vs. KDE on Ubuntu, I would use Ubuntu/GNOME. Not that it matters, it's excellent that I could use KDE software on GNOME. I installed Kivio from KOffice today, and it rocks!!

I do some development with Python and PHP and started to think I should use what other people are using. So, late last year I made the switch to Ubuntu. 
I briefly tried Xubuntu, but despite my love for its simplicity, I had to rely on the terminal a lot. Learning how to configure Thunar just was not as easy and quick as I would like it to be. 
Most of the people I would be supporting at my job would not ever use the terminal. So, I thought, it would be best for me to have both. Thus, I ditched Xubuntu and went full Ubuntu.

So far, I must admit, I felt like I made the right choice. I upgraded to Edgy, then I didn't stay with Edgy for too long, as Feisty Beta came out, and I always thought of trying out the latest. Feisty worked great, although I felt like I was forced to use Apache2 for LAMP development. It did not take too long for me to get to know it and work with it. There were some growing pains and in the end, I had to backup my data and start with a clean install. 

In the interest of keeping in mind to help people, I also worked with installing applications using Aptitude's GUI instead of from the command line. 
There were a few problems with some packages which I ended up sorting out by reading people's posts on this forum and others. Most of the folks I would be supporting would not know where to look. In that sense, I felt like a better way of managing aptitude, or at least, an alternative for it should be available. As to how that should be done, maybe there should be a dedicated post for that. Software search, installation and configuration management for beginners is a must, I think.

I work in a very tightly controlled research institution. Access to the internet is also tightly controlled. All internet requests are filtered and scanned. This severely slows down managing mutiple boxes for updates. If there is a way to download nightly or even weekly multiverse repository update and setting up I would do that. I haven't gotten around to doing it. Is there such a thing? If there isn't there should be one.

Overall though, of all the LINUX distros I've tried, Ubuntu is at the very top. It's the easiest to install and configure, and it seems to be the one that gets updated the quickest. Also, the community is the largest and I get my support information the fastest. Between the wikis and this forum, within a span of 2 years, I've learned quite a lot about linux from using Ubuntu.

I would recommend Ubuntu Feisty Fawn to my colleagues to try out without reservations and to further suggest to them to make it their main operating system.
Ubuntu guys: keep up the most excellent work!!!!!

---

