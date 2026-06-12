---
title: "Morrowind, works great then dies :("
date: 2009-06-07
forum: Wine
---

### Post by man_bash on 2009-06-07
Hi

I tried to launch Morrowind from the windows partition (I know it is not the greatest idea, but I'm tight on HDD space), and it ran fantastic for a few minutes, even better than in Windows!!! The FPS counter usually stayed up high in 100's, not lower than 70 anywhere in-game, at least in the vicinity of Uvirith's Grave, and there was a fog, (the screen only supports 75 Hz at 1600x1200 though, I should use a frame limiter in .ini, but this was a test run). The loading times were amazing, loading exterior (Uvirith's Grave cell) was so fast I didn't even notice it load, it was just there when I went outside, which usually it takes a few seconds on Windows. I even went inside and out 3 times just to double-check, and that went without a hitch. Then, 5 minutes later, the sound died. 2 minutes after that the game froze altogether (although this was during a fight). I have the upside-down paper doll error (which doesn't bother me all that much really, if it were the only problem).

I am using Wine from repository, 1.0.1, this is on Ubuntu Jaunty, 64-bit

I did the adjustments in wine's regedit from Oblivion's guide prior to that.

What do you suggest I should do?

Hardware:
Motherboard: DFI Infinity NF4X
CPU: Turion ML-30 (OC)
VC: GeForce 8600 GTS (factory OC), 256 MB GDDR3
RAM: 2 GB DDR

Note: Jaunty was the 1-st distro that worked with the graphics card in full 3D mode. Previous versions have all failed, giving 2D only. 3D works great, I run Compiz without problems; Counter-Strike through Wine (3 hours without a hitch!); Warsow, Nexuiz both play fine

Here's the lshw output
```
description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.2 dmi-2.2 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: NF4X-INF
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (10/19/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-30
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Turion(tm) 64 Mobile Technology ML-30
          slot: Socket 754
          size: 2560MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi4
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
        *-disk
             description: ATA Disk
             product: Maxtor 6L250R0
             vendor: Maxtor
             physical id: 0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: BAJ4
             serial: L514MN7G
             size: 233GiB (251GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=001de4a8
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/disk-3
                version: 3.1
                serial: 6c99077c-74fe-4747-8cf7-6ff915e858ab
                size: 21GiB
                capacity: 21GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-07-20 08:07:20 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                size: 211GiB
                capacity: 211GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 25GiB
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sdb6
                   capacity: 95GiB
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sdb7
                   logical name: /media/disk-2
                   capacity: 90GiB
                   configuration: mount.fstype=reiserfs mount.options=rw,nosuid,nodev state=mounted
        *-cdrom
             description: DVD writer
             product: 16X16X
             vendor: DVDRW
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: YTS1
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: WDC WD3200KS-00P
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 21.0
             serial: WD-WCAPD2858915
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=b93505e9
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 74faa940-1dfe-fc41-91ca-1fd49ac2b656
                size: 29GiB
                capacity: 29GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-05-26 11:19:19 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 144fe781-26cb-fe47-89d9-735163126932
                size: 44GiB
                capacity: 44GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-05-27 23:24:00 filesystem=ntfs state=clean
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 7d9a3753-defb-48cd-b16e-432d4d089ef1
                size: 1929MiB
                capacity: 1929MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 221GiB
                capacity: 221GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /media/disk
                   capacity: 74GiB
                   configuration: mount.fstype=reiserfs mount.options=rw,nosuid,nodev state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /media/disk-1
                   capacity: 74GiB
                   configuration: mount.fstype=ext3 mount.options=rw,nosuid,nodev,errors=continue,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 72GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:01:29:d3:a0:e5
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: GeForce 8600 GTS
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi:0
          physical id: f
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
     *-scsi:1
          physical id: 10
          logical name: scsi7
        *-cdrom:0
             description: DVD reader
             product: Virt. CD/DVD-ROM
             vendor: CDEmu
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 1.10
             capabilities: removable audio dvd
             configuration: status=nodisc
        *-cdrom:1
             description: DVD reader
             product: Virt. CD/DVD-ROM
             vendor: CDEmu
             physical id: 0.1.0
             bus info: scsi@7:0.1.0
             logical name: /dev/cdrom2
             logical name: /dev/dvd2
             logical name: /dev/scd2
             logical name: /dev/sr2
             version: 1.10
             capabilities: removable audio dvd
             configuration: status=nodisc
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:62:26:c7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:ae:c7:1a:fc:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by Progressive on 2009-06-08
I'm thinking this is a sound issue. WINE has problems with sound, especially lots of sounds at once.

In the INI file, try turning off battle sounds and footsteps, and see if that makes a difference. Or try disabling all sounds totally, and work backwards to find which particular sound is the problem.

---

