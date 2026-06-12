---
title: "Newb Installing 10.04 on Proliant 3000 Server"
date: 2010-06-26
forum: Server Platforms
---

### Post by einstein on 2010-06-26
I got my hands on my first real server hardware yesterday - a PIII 600 MHz COMPAQ Proliant 3000 with 1.8 GB RAM, Smart Array 3200 controller and 4x18.2GB SCSI ULTRA 3 hard drives.  RAM is upgraded from original and USB card added - otherwise hardware arrangement appears to be original.

Minimal 10.04 installed (35 minutes boot to boot) as Server 10.04 could not detect CD drive.

My problem?  Everything works but it does not look right. Probably my bigger problem??  I know almost nothing about RAID and the more I read the more ethereal my understanding seems to become.

When installing, I chose to install with LVM on c0d0.  Grub written to MBR.

I have posted df -l, fdisk -l and lshw output below.  Would someone tell me if this looks correct and, possibly, offer some pointers if it does not.

df -l:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/server-root
                       7450552    752184   6319900  11% /
none                    864548       228    864320   1% /dev
none                    869148         0    869148   0% /dev/shm
none                    869148        36    869112   1% /var/run
none                    869148         0    869148   0% /var/lock
none                    869148         0    869148   0% /lib/init/rw
/dev/ida/c0d0p1         233191     16286    204464   8% /boot
```

fdisk -l:
```
Disk /dev/ida/c0d0: 8414 MB, 8414461440 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000ce69

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d0p1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/ida/c0d0p2              32        1023     7965697    5  Extended
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(1022, 233, 43)
/dev/ida/c0d0p5              32        1023     7965696   8e  Linux LVM

Disk /dev/ida/c0d1: 8414 MB, 8414461440 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaafcab00

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d1p1   *           1        1022     8209183+   7  HPFS/NTFS

Disk /dev/ida/c0d2: 8414 MB, 8414461440 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaafcaaff

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d2p1   *           1        1022     8209183+   7  HPFS/NTFS

Disk /dev/ida/c0d3: 8414 MB, 8414461440 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaafcaafe

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d3p1   *           1        1022     8209183+   7  HPFS/NTFS

Disk /dev/ida/c0d4: 8414 MB, 8414461440 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaafcaafd

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d4p1   *           1        1022     8209183+   7  HPFS/NTFS

Disk /dev/ida/c0d5: 8414 MB, 8414461440 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaafcaafc

         Device Boot      Start         End      Blocks   Id  System
/dev/ida/c0d5p1   *           1        1022     8209183+   7  HPFS/NTFS

Disk /dev/ida/c0d6: 4139 MB, 4139397120 bytes
21 heads, 30 sectors/track, 12832 cylinders
Units = cylinders of 630 * 512 = 322560 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6c6c6c6c
```

lshw```

server
    description: Computer
    product: PROLIANT
    vendor: COMPAQ
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: cpus=1
  *-core
       description: Motherboard
       physical id: 0
     *-cpu
          product: Pentium III (Katmai)
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.7.3
          size: 600MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory
          description: System memory
          physical id: 1
          size: 1697MiB
     *-pci:0
          description: Host bridge
          product: CNB20-LE Host Bridge
          vendor: Broadcom
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
          resources: memory:0-fff
        *-generic UNCLAIMED
             description: System peripheral
             product: Advanced System Management Controller
             vendor: Compaq Computer Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1800(size=256) memory:c6dfff00-c6dfffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 3D Rage IIC 215IIC [Mach64 GT IIC]
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 7a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64 mingnt=8
             resources: memory:c5000000-c5ffffff(prefetchable) ioport:2000(size=256) memory:c6dfe000-c6dfefff memory:6c100000-6c11ffff(prefetchable)
        *-pci
             description: PCI bridge
             product: PCI to PCI Bridge (IBM27-82351)
             vendor: IBM
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:c6e00000-c6efffff memory:6c000000-6c0fffff(prefetchable)
           *-storage
                description: Mass storage controller
                product: Smart-2/P RAID Controller
                vendor: Compaq Computer Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master rom
                configuration: driver=cpqarray latency=0
                resources: irq:31 ioport:3000(size=256) memory:c6efff00-c6efffff memory:6c000000-6c003fff(prefetchable)
        *-network
             description: Ethernet interface
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth0
             version: 08
             serial: 00:02:b3:0a:14:7d
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.181 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
             resources: irq:29 memory:c6dfd000-c6dfdfff ioport:2400(size=64) memory:c6c00000-c6cfffff
        *-isa
             description: ISA bridge
             product: OSB4 South Bridge
             vendor: Broadcom
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 4d
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: CNB20-LE Host Bridge
          vendor: Broadcom
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
     *-pci:2
          description: Host bridge
          product: CNB20-LE Host Bridge
          vendor: Broadcom
          physical id: 102
          bus info: pci@0000:00:11.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
     *-pci:3
          description: Host bridge
          product: CNB20-LE Host Bridge
          vendor: Broadcom
          physical id: 103
          bus info: pci@0000:00:11.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi:0
          description: SCSI storage controller
          product: 53c875
          vendor: LSI Logic / Symbios Logic
          physical id: 4
          bus info: pci@0000:02:04.0
          logical name: scsi0
          version: 14
          width: 32 bits
          clock: 33MHz
          capabilities: scsi bus_master scsi-host
          configuration: driver=sym53c8xx latency=255 maxlatency=64 mingnt=17
          resources: irq:22 ioport:4000(size=256) memory:c6ffff00-c6ffffff memory:c6ffe000-c6ffefff
     *-scsi:1
          description: SCSI storage controller
          product: 53c875
          vendor: LSI Logic / Symbios Logic
          physical id: 4.1
          bus info: pci@0000:02:04.1
          logical name: scsi1
          version: 14
          width: 32 bits
          clock: 33MHz
          capabilities: scsi bus_master scsi-host
          configuration: driver=sym53c8xx latency=255 maxlatency=64 mingnt=17
          resources: irq:21 ioport:4400(size=256) memory:c6ffdf00-c6ffdfff memory:c6ffc000-c6ffcfff
        *-tape
             description: SCSI Tape
             product: SDT-10000
             vendor: COMPAQ
             physical id: 0.6.0
             bus info: scsi@1:0.6.0
             logical name: /dev/nst0
             logical name: /dev/st0
             version: 1.05
             serial: 0004912759
             capabilities: removable
             configuration: ansiversion=2
     *-usb:0
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 8
          bus info: pci@0000:02:08.0
          version: 61
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=uhci_hcd latency=64
          resources: irq:25 ioport:4800(size=32)
     *-usb:1
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 8.1
          bus info: pci@0000:02:08.1
          version: 61
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=uhci_hcd latency=64
          resources: irq:25 ioport:4820(size=32)
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: VIA Technologies, Inc.
          physical id: 8.2
          bus info: pci@0000:02:08.2
          version: 63
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ehci_hcd latency=64
          resources: irq:25 memory:c6ffbf00-c6ffbfff
```

---

### Post by einstein on 2010-06-26
As usual, seem to have solved it myself.  The info in my original post is wrong.  I did install incorrectly.

Booted the SmartStart CD and did a System Erase and then followed the CD cues.  This included configuring the system as RAID5.  Then I pretended to wish to install SCO LinuxWare 7.1 but did not have the CD for it.  So, I popped in the Ubuntu Server 10.04 Minimal CD and .... life is good.  df -l and fdisk -l now return results that look correct.

---

