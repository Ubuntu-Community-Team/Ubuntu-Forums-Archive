---
title: "Seagate ST31500341AS abysmal performance"
date: 2010-03-05
forum: Server Platforms
---

### Post by noeffred on 2010-03-05
Hello

I'm running the 9.04 server edition and I'm experiencing massive performance problems with the ST31500341AS disks.

I'm running them connected to the onboard ICH7 controller in a software raid5 configuration.

At the moment the raid is growing, but this is what I'm getting from the disks:

```

#sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   1878 MB in  2.00 seconds = 939.01 MB/sec
 Timing buffered disk reads:   36 MB in  3.22 seconds =  11.19 MB/sec

```
the raid is growing at the moment, is this the source of the problem?

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdd1[3] sdc1[1] sde1[0] sdb1[2]
      2930271744 blocks super 0.91 level 5, 128k chunk, algorithm 2 [4/4] [UUUU]
      [============>........]  reshape = 63.8% (936187392/1465135872) finish=916.2min speed=9620K/sec

unused devices: <none>

```
here's the lshw output
```

nas
    description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=D60195CE-B576-11DC-8733-0011D8A408ED
  *-core
       description: Motherboard
       product: DG31PR
       vendor: Intel Corporation
       physical id: 0
       version: AAD97573-205
       serial: BTPR75200GPL
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: PRG3110H.86A.0059.2008.1024.1834 (10/24/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU          430  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU          430  @ 1.80GHz
          slot: J3E1
          size: 1800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx x86-64 constant_tsc up arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: Unknown
             vendor: Unknown
             physical id: 0
             serial: Unknown
             slot: J6H1
             size: 512MiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: Unknown
             vendor: Unknown
             physical id: 1
             serial: Unknown
             slot: J6H2
             size: 512MiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-generic UNCLAIMED
          physical id: 904
          bus info: parisc@0904
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
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
        *-pci:1
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
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:1c:c0:3a:88:27
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.90 latency=0 link=yes module=r8169 multicast=yes port=MII speed=1GB/s
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
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: SanDisk SDCFJ-51
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: HDX
                serial: 020802K2805S5826
                size: 488MiB (512MB)
                capabilities: removable
                configuration: ansiversion=5
              *-medium
                   physical id: 0
                   logical name: /dev/sda
                   size: 488MiB (512MB)
                   capabilities: partitioned partitioned:dos
                   configuration: signature=00012e08
                 *-volume
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      logical name: /dev/sda1
                      logical name: /boot
                      version: 1.0
                      serial: 9872128c-a823-4548-b568-31ae279f58f7
                      size: 488MiB
                      capacity: 488MiB
                      capabilities: primary bootable journaled extended_attributes recover ext3 ext2 initialized
                      configuration: created=2008-12-09 18:03:50 filesystem=ext3 modified=2010-03-04 21:34:05 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2010-03-04 21:34:05 state=mounted
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: CC1H
                serial: 9VS3GH3D
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d8f47083
              *-volume
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 1397GiB
                   capabilities: primary multi
           *-disk:1
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@2:0.1.0
                logical name: /dev/sdc
                version: CC1H
                serial: 9VS3HPH7
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c9f5f778
              *-volume UNCLAIMED
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   capacity: 1397GiB
                   capabilities: primary multi
           *-disk:2
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 2
                bus info: scsi@3:0.0.0
                logical name: /dev/sdd
                version: CC1H
                serial: 9VS3J7DY
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ab6c5117
              *-volume UNCLAIMED
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   capacity: 1397GiB
                   capabilities: primary multi
           *-disk:3
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 3
                bus info: scsi@3:0.1.0
                logical name: /dev/sde
                version: CC1H
                serial: 9VS3J86P
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9f7a393d
              *-volume UNCLAIMED
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@3:0.1.0,1
                   capacity: 1397GiB
                   capabilities: primary multi
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

```

I used some Samsung drives before which gave me around 60MB/s without any problems. It's totally the same setup (files got copied over from one RAID to the other). Is there some sort of hardware issue I'm not aware of? The server has all updates applied and all other hardware (not much of it actually) is working perfectly... I'm kind of stuck to be honest. This is so slow that there must be something wrong... I was under the impression that this drive is supposed to be rather fast, but this is unusable... I've seen CF cards that are faster than that...

finally, my kernel version
```

Linux nas 2.6.28-18-server #59-Ubuntu SMP Thu Jan 28 02:25:03 UTC 2010 x86_64 GNU/Linux

```

and the infos on the raid
```

$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.91
  Creation Time : Wed Mar  3 08:37:36 2010
     Raid Level : raid5
     Array Size : 2930271744 (2794.52 GiB 3000.60 GB)
  Used Dev Size : 1465135872 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Mar  5 21:43:58 2010
          State : active, recovering
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

 Reshape Status : 63% complete
  Delta Devices : 1, (3->4)

           UUID : c4acc76c:d3443a80:c7780c0e:bc15422d (local to host nas)
         Events : 0.610063

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       2       8       17        2      active sync   /dev/sdb1
       3       8       49        3      active sync   /dev/sdd1

```

At the moment I can write with some 25MB/s via Samba, but I can only read at ~4-5MB/s! :? can someone enlighten me to the source of all this? dmesg is clean and there are no other problems, it's just unusably slow...

---

### Post by richardjh on 2010-03-05
I am not able to remember if this is the same disk I had when I had this problem. 
cat /proc/mdstat was showing estimated 10 hours to synchronise a 250GB software RAID 1.

I fixed it by passing all-generic-ide as a kernel parameter at boot time. 
It runs like a dream now.

Like I say I can't remember if it was this disk, but it is worth a go if you are able to reboot the server.

---

### Post by noeffred on 2010-03-05
Ha! You sir are worth your weight in gold! Just added the all-generic-ide parameter and lo and behold:

```
/dev/sde:
 Timing cached reads:   1678 MB in  2.00 seconds = 839.10 MB/sec
 Timing buffered disk reads:  322 MB in  3.01 seconds = 107.15 MB/sec

```

Cheers mate, you really helped me out there!

---

### Post by richardjh on 2010-03-05
Don't forget to add the parameter to your /etc/grub.conf to make it persist across reboots.
Also you may need to add it when new kernels are installed. Something to bear in mind.

I was debating if it was worth posting such a vague shot in the dark, so really glad it helped out.

---

