---
title: "Server 16.04.3 Monitor Flashing"
date: 2017-12-29
forum: Server Platforms
---

### Post by ghanson59 on 2017-12-29
Running on an old AMD Turion on a Gigabyte motherboard with 8GB RAM. Simple, headless server that has been running for 6 months. When I ssh into the server everything is fine. However, if I use a monitor and keyboard attached to the server itself the system boots properly but once at the Ubuntu login prompt, and from there on, the screen flashes. It simply blinks out for about one second then comes back up. It's intermittent, sometimes occurring every few seconds then not again for a minute or two. It's on the desk next to me and is doing it right now.
I edited grub and set GRUB_GFXMODE =1280X1024 which is the monitor's max resolution. Still the blinking continues.
If I go into UEFI the screen does not flash. It only happens once I reach the login prompt.

Any suggestions as to how to fix this?

Thanks,
Greg

---

### Post by mörgæs on 2017-12-30
First let's see the hardware details. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the command line, run it and post lshw.txt in code tags.

---

### Post by ghanson59 on 2017-12-31
Output from sudo lshw -sanitize
 ```

computer
    description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: F2A78M-HD2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: To be filled by O.E.M.
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F1
          date: 01/09/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             product: Dimm0_PartNum
             vendor: Dimm0_Manufacturer
             physical id: 0
             serial: [REMOVED]
             slot: Node0_Dimm0
        *-bank:1
             description: DIMM Synchronous [empty]
             product: Dimm1_PartNum
             vendor: Dimm1_Manufacturer
             physical id: 1
             serial: [REMOVED]
             slot: Node0_Dimm1
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Dimm2_PartNum
             vendor: Dimm2_Manufacturer
             physical id: 2
             serial: [REMOVED]
             slot: Node0_Dimm2
        *-bank:3
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: BLS8G3D1609DS
             vendor: Undefined
             physical id: 3
             serial: [REMOVED]
             slot: Node0_Dimm3
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cache:0
          description: L1 cache
          physical id: 2f
          slot: L1 CACHE
          size: 192KiB
          capacity: 192KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 30
          slot: L2 CACHE
          size: 4MiB
          capacity: 4MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: AMD A10-5800K APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 35
          bus info: cpu@0
          version: AMD A10-5800K APU with Radeon(tm) HD Graphics
          slot: P0
          size: 1400MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Family 15h (Models 10h-1fh) I/O Memory Management Unit
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Trinity [Radeon HD 7660D]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:38 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             product: Trinity HDMI Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:39 memory:feb44000-feb47fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:fea00000-feafffff ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 06
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:36 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0000000-d0003fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:feb4a000-feb4bfff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-62-generic xhci-hcd
                physical id: 0
                bus info: usb@7
                logical name: usb7
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-62-generic xhci-hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
        *-usb:1
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:feb48000-feb49fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-62-generic xhci-hcd
                physical id: 0
                bus info: usb@9
                logical name: usb9
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-62-generic xhci-hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:37 ioport:f190(size=8) ioport:f180(size=4) ioport:f170(size=8) ioport:f160(size=4) ioport:f150(size=16) memory:feb51000-feb517ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb50000-feb50fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-62-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb4f000-feb4f0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-62-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-usb:4
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4e000-feb4efff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-62-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: Dell USB Entry Keyboard
                   vendor: DELL
                   physical id: 5
                   bus info: usb@4:5
                   version: 1.78
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:5
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb4d000-feb4d0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-62-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 16
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: FCH IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f100(size=16)
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb40000-feb43fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:6
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4c000-feb4cfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-62-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EFRX-68F
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0A82
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=4389368a-b09f-43b1-b833-234492d2dd1b logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 923GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-07-29 14:56:32 filesystem=ext4 lastmountpoint=/ modified=2017-12-31 10:01:36 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-12-31 10:01:45 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 7363MiB
                capacity: 7364MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000DL003-9VT1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: CC3C
             serial: [REMOVED]
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=c4f57356-fe0f-bb44-b6fd-898dc3c37e96 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                serial: [REMOVED]
                capacity: 1863GiB
                configuration: name=zfs-adc148bbd78976c8
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@1:0.0.0,9
                logical name: /dev/sdb9
                serial: [REMOVED]
                capacity: 8191KiB
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000DL003-9VT1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: CC3C
             serial: [REMOVED]
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=b69912d3-733d-ab49-ba76-60558fa7b890 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                serial: [REMOVED]
                capacity: 1863GiB
                configuration: name=zfs-05f8ba369fd20eb2
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@2:0.0.0,9
                logical name: /dev/sdc9
                serial: [REMOVED]
                capacity: 8191KiB

```

Not only does the monitor blink but I let the server run all night and then today attempted to SSH into it with no luck. I had to shut down power to the server then restart to get it to post to a local monitor and keyboard. Would the system drop out video after a while? Again, this thing has been running 24x7 for six months without a hitch and now it is acting up. The cpu is an AMD A10 (not the Turion which is another server doing simple file storage tasks).

Thanks for the help.

---

### Post by mörgæs on 2018-01-01
I am not sure I understand your post. Is the problem a flashing display or a failing SSH connection?

---

### Post by ghanson59 on 2018-01-01
Please forgive me for the extraneous detail. This thread is about the flashing monitor. I'm using the onboard Radeon graphics in the AMD A10. I know that Ubuntu has had issues with graphics drivers so could that be a cause?

---

### Post by mörgæs on 2018-01-02
For your card the Radeon drivers are the only ones available so [AMDGPU]("https://help.ubuntu.com/community/AMDGPU-Driver") is not an option. I have never heard that Radeon should cause flashing, though.

I don't know if it's possible to tweak the Radeon drivers. Hoping another user has something to contribute.

---

