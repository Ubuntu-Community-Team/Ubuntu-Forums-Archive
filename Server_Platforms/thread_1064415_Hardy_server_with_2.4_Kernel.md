---
title: "Hardy server with 2.4 Kernel"
date: 2009-02-08
forum: Server Platforms
---

### Post by tommynz1975 on 2009-02-08
I've tried to install ubuntu 8.04 server cd that I got from shipit, this worked fine until reboot. but the CPU isn't upto the job.
this kernel requires the following features not present on your cpu
0.6

I found the cd was setup for !686 so I downloaded the !386 iso, same isssue.
From googling I have only been able to gleem that I need to use a 2.4 Kernel

Can I please be pointed to a download link for a complete iso

The System is a 
via chipset  1GHz 256 ram 

your help appreciated.

---

### Post by bettlebrox on 2009-02-08
What CPU do you have?
>but the CPU isn't upto the job
What do you mean?

2.4 kernel's are quite old at this point, and you'd probably have to compile your own as I don't think there was ever a Ubuntu version that used a 2.4 kernel. 

What makes you think you need a 2.4 kernel?

---

### Post by PilotJLR on 2009-02-08
If you really do need a 2.4 kernel, then try this first:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

As bettlebrox says, though, I'd also be interested in why a 2.4 kernel is neccessary. Posting the model of your CPU would help.

---

### Post by tommynz1975 on 2009-02-10
Sorry for  the delay. family stuff.

Let me clear things up...  Miss information has suggested that I wanted to have a 2.4 Kernel

The error message was

This kernel require the following features not present on the CPU: 0:6
unable to boot, please use a kernel apprppriate for your CPU 

this error occured using the shipit cd and d/l a i386.iso

-----------
this is my print out of lshw

```
description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: GA-PCV2-CSI/DSI
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2 ID (03/13/2006)
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: VIA Nehemiah
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: PC1500
          slot: Socket 370
          size: 532MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr cx8 sep mtrr pge cmov pat mmx fxsr sse up rng rng_en ace ace_en cpufreq
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: External Cache
             size: 64KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 256MiB
          capacity: 256MiB
        *-bank
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 256MiB
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: VT8623 [Apollo CLE266]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8623 [Apollo CLE266] integrated CastleRock graphics
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: driver=vt8623fb latency=32 mingnt=2 module=vt8623fb
        *-network:0
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: eth0
             version: 00
             serial: 00:00:b4:b5:ad:95
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 module=ne2k_pci multicast=yes
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth1
             version: 10
             serial: 00:0f:ea:45:55:e4
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.6 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
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
             version: 80
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
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0842N
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BH10
                serial: S0DWJ1TL608468
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=97899789
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: b67ad370-40ac-47be-8eea-d011079f1d2d
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-09 15:13:04 filesystem=ext3 modified=2009-02-11 09:24:41 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-02-11 09:24:41 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 635MiB
                   capacity: 635MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 635MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: COM5232/AAH SL
                vendor: AOPEN
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                serial: )AOPEN   COM5232/AAH SL  1.02050705AOpen0701611
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
                                               
```     

Thank-you for your time.
the eth0 card is in the one and only expantion slot on the motherboard.

---

### Post by bettlebrox on 2009-02-11
U have a VIA Nehemiah processor, a quick google turned up problems with earlier 2.6.2* kernels booting on this processor. Have U tried Ubuntu 8.10? Is there a reason U need to use 8.04?

---

### Post by Thirtysixway on 2009-02-12
> **bettlebrox said:**
> U have a VIA Nehemiah processor, a quick google turned up problems with earlier 2.6.2* kernels booting on this processor. Have U tried Ubuntu 8.10? Is there a reason U need to use 8.04?

Most likely because it's an LTS.  I prefer to use LTS on my server so that I'm not worrying about upgrading every 6 months.

---

### Post by bettlebrox on 2009-02-12
I'd suggest opening a bug report:
[http://www.ubuntu.com/community/reportproblem](http://www.ubuntu.com/community/reportproblem)

---

