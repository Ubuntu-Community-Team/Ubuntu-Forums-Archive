---
title: "Yay! I got a new Nvidia 9500GT gfx card, and a new power supply......"
date: 2010-04-10
forum: The Cafe
---

### Post by dragos240 on 2010-04-10
So what now? 1gb of vram is a lot. Do I need to reconfigure X? Anyone fond on upgrading your graphics card? Gentoo user.

---

### Post by dragos240 on 2010-04-10
:(

---

### Post by -grubby on 2010-04-10
What was your old one?

---

### Post by dragos240 on 2010-04-10
> **-grubby said:**
> What was your old one?

A GPU. A 6150se nforce 430. It's only recognizing the GPU T_T.

---

### Post by chris4585 on 2010-04-10
What do you know, your old card is the same as my onboard gpu.  I don't know how to go about it on gentoo, but I usually just download the proprietary drivers from nvidia's website, should work on any distro.

---

### Post by -grubby on 2010-04-10
> **dragos240 said:**
> A GPU. A 6150se nforce 430. It's only recognizing the GPU T_T.

Your dedicated card is also a GPU, y'know. Make sure you've got the right card selected in your BiOS, also.

---

### Post by dragos240 on 2010-04-10
> **-grubby said:**
> Your dedicated card is also a GPU, y'know. Make sure you've got the right card selected in your BiOS, also.

In my BIOS? Where can I configure that? What setting in the bios?

---

### Post by -grubby on 2010-04-10
> **dragos240 said:**
> In my BIOS? Where can I configure that? What setting in the bios?

It really depends on your BIOS. I'm assuming there's an option on there to do with the onboard card... sometimes you can set the video to PCI-E instead of onboard or just disable the onboard video. I don't even have a BIOS (mac), so I can't provide a specific example.

---

### Post by dragos240 on 2010-04-10
> **-grubby said:**
> It really depends on your BIOS. I'm assuming there's an option on there to do with the onboard card... sometimes you can set the video to PCI-E instead of onboard or just disable the onboard video. I don't even have a BIOS (mac), so I can't provide a specific example.

Sadly, I don't think that my bios has that option. I inserted the card, and it boots up much slower than it used to, I think it's looking for what the graphics card is. It doesn't know what it is.

---

### Post by cariboo on 2010-04-10
In some bioses, you have to set the priority, usually it will give you a choice of onboard or PCIe. You may have to search around a bit, but on the mb's I use, the setting is in the onboard peripheral settings section.

---

### Post by dragos240 on 2010-04-10
> **cariboo907 said:**
> In some bioses, you have to set the priority, usually it will give you a choice of onboard or PCIe. You may have to search around a bit, but on the mb's I use, the setting is in the onboard peripheral settings section.

I think I saw that!

I think I'll dig for a while. :popcorn:

---

### Post by dragos240 on 2010-04-10
Hmm... I have "Integrated Peripherals". When I go into it, there are 3 sections:
> IDE Function Setup
> Onboard Device
> Onboard I/O Chip Setup

I'm not sure what one to pick. I went into each. There is nothing about video in the main menu. However there is something about "RAID configuration" in the first one, and in the last there is this:
Onboard Serial Port 1        [3F8/IRQ4]
Onboard Parallel Port         [378/IRQ7]
Parallel Port Mode              [SPP]

I'm pretty confused.

---

### Post by -grubby on 2010-04-10
> **dragos240 said:**
> 
> Onboard Device
I'm pretty confused.

Try this and tell me what happens

---

### Post by dragos240 on 2010-04-10
> **-grubby said:**
> Try this and tell me what happens

I think It's useless, but:

OnChip USB                                  [V1.1+V2.0]
USB Keyboard Support                [Enabled]
USB Mouse Support                     [Enabled]
USB Storage Support                   [Enabled]
HD Audio                                      [Auto]
Onboard LAN                               [Enabled]
Onboard LAN Boot ROM              [Enabled]

nothing else.........

---

### Post by sisco311 on 2010-04-10
Well, I know this sounds like rtfm, but still, consult the motherboard's manual. Then post back if you have any further questions.

---

### Post by dragos240 on 2010-04-10
> **sisco311 said:**
> Well, I know this sound like rtfm, but still, consult the motherboard's manual. Then post back if you have any further questions.

I have a prebuilt, store bought, computer. I did not buy the motherboard separately, no can do.

---

### Post by sisco311 on 2010-04-10
> **dragos240 said:**
> I have a prebuilt, store bought, computer. I did not buy the motherboard separately, no can do.

That's a good start. first you have to find your motherboard type. 

In Ubuntu you can run:
```
sudo lshw
```

in other distros **cat /proc/<google search>** (sorry, it's 3:17am here) :)

---

### Post by dragos240 on 2010-04-10
> **sisco311 said:**
> That's a good start. first you have to find your motherboard type. 

In Ubuntu you can run:
```
sudo lshw
```in other distros **cat /proc/<google search>** (sorry, it's 3:17am here) :)

```

harley-desktop
    description: Desktop Computer
    product: T5234
    vendor: Gateway
    version: 300
    serial: GC47B30000359
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MCP61PM-AM
       vendor: ELITEGROUP
       physical id: 0
       version: 1.0A
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/11/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          slot: Socket AM2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache:0
          description: L1 cache
          physical id: 6
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: f
          slot: External Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 1GiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:b000(size=4096) memory:fdf00000-fdffffff memory:fd800000-fd8fffff(prefetchable)
        *-network
             description: Wireless interface
             product: RT2561/RT61 802.11g PCI
             vendor: RaLink
             physical id: 5
             bus info: pci@0000:01:05.0
             logical name: wlan0
             version: 00
             serial: 00:1d:7e:05:b8:bc
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci ip=192.168.1.103 latency=64 multicast=yes wireless=IEEE 802.11bg
             resources: irq:16 memory:fdff8000-fdffffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fdfe0000-fdfeffff ioport:bc00(size=8)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe028000-fe02bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-H652D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/JAPANESE 1 & 2
             version: GA01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/JAPANESE 1 & 2
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fe02d000-fe02dfff
        *-disk:0
             description: ATA Disk
             product: WDC WD3200AAJS-0
             vendor: Western Digital
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 12.0
             serial: WD-WCARW1142790
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0a7d030c
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 2de8fee9-511b-4146-83a3-d625cebe2a09
                size: 39MiB
                capacity: 39MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 modified=2010-04-10 19:47:18 mounted=2010-04-10 19:33:53 state=clean
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: a1118d74-46dc-47fe-ac91-ea5eac9e0bff
                size: 1035MiB
                capacity: 1035MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: 2787bf46-ef35-4d45-b0d0-8788e1344d3c
                size: 297GiB
                capacity: 297GiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2009-12-28 21:16:35 filesystem=ext3 modified=2010-04-10 16:35:01 mounted=2010-04-10 19:33:53 state=clean
        *-disk:1
             description: ATA Disk
             product: ST3500320AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: SD15
             serial: 9QM6K4ME
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000bc843
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: 17b69031-4e14-4b23-acbf-ba3a93514d58
                size: 460GiB
                capacity: 460GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-04-10 16:30:19 filesystem=ext4 lastmountpoint=/8&#65533;&#65533;d&#65533;&#65533;&#65533;?&#65533;(&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;@N&#65533;7&#65533;&#65533;&#65533;FAu&#65533;&#65533;&#65533; k&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Gu&#65533; modified=2010-04-10 16:38:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-04-10 20:16:45 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                size: 5507MiB
                capacity: 5507MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 5507MiB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c800(size=16) memory:fe02c000-fe02cfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:9000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
        *-network
             description: Ethernet interface
             product: 88E8039 PCI-E Fast Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: eth0
             version: 14
             serial: 00:1b:b9:e3:17:10
             capacity: 100MB/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
             resources: irq:27 memory:fdcfc000-fdcfffff ioport:9c00(size=256)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26 ioport:8000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:23 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: e
          bus info: usb@1:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C4400
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdc
     *-scsi:1
          physical id: 10
          bus info: usb@1:5
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdd
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@7:0.0.1
             logical name: /dev/sde
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@7:0.0.2
             logical name: /dev/sdf
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@7:0.0.3
             logical name: /dev/sdg
     *-scsi:2
          physical id: 11
          bus info: usb@2:2
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdh

```

---

### Post by sisco311 on 2010-04-10
The relevant part is:
```

  *-core
       description: Motherboard
       product: **MCP61PM-AM**
       vendor: **ELITEGROUP**
       physical id: 0
       version: 1.0A

```

seek out & download the manual...


(why don't you start a thread in one of the appropriate support forum?)

---

### Post by chris4585 on 2010-04-10
There might have been a wire that connects the video card to the motherboard, maybe if there was one, you didn't attach it?

---

### Post by dragos240 on 2010-04-10
> **chris4585 said:**
> There might have been a wire that connects the video card to the motherboard, maybe if there was one, you didn't attach it?

I let my dad do it, since he's assembled computers before. He also stayed grounded the entire time with a cord that went from the bottom wall socket to the table, which he touched every once in a while. I checked inside and the fan on the gfx card is running, so I assume it's working.

---

### Post by cariboo on 2010-04-10
The setting you want is under the PCI/PnP Setup menu. 

What chris4585 is saying is that there may be a 4-6 pin power connector on the video card, I don't think the 9500GT has one though.

---

### Post by steveneddy on 2010-04-10
Is the video onboard video and you bought an extra card for video?

I see this in your list:

 > *-display
          description: VGA compatible controller
          product: C61 [**GeForce 6150SE nForce 430**]
          vendor: nVidia Corporation
          physical id: d

Looks like the video in onboard or you haven't actually installed the video card?

do you have TWO video cards installed?

didn't you purchase a 9500 GT?

If you have onboard video, you will have to blacklist the onboard video so the OS doesn't see it or disable the onboard video in the BIOS, which after reading, you don't have control over that area through the BIOS.

---

### Post by swoll1980 on 2010-04-10
> **chris4585 said:**
> What do you know, your old card is the same as my onboard gpu.  I don't know how to go about it on gentoo, but I usually just download the proprietary drivers from nvidia's website, should work on any distro.

I just click on the little icon that appears in the task bar. I love Ubuntu.

---

### Post by chris4585 on 2010-04-10
> **swoll1980 said:**
> I just click on the little icon that appears in the task bar. I love Ubuntu.

Ha, yeah 10.04 has been the only time since 7.10 that, that process has worked for me.

---

### Post by swoll1980 on 2010-04-10
> **chris4585 said:**
> Ha, yeah 10.04 has been the only time since 7.10 that, that process has worked for me.

I haven't had a problem with it since it was introduced. Maybe I've been lucky.

---

### Post by cchhrriiss121212 on 2010-04-11
> I haven't had a problem with it since it was introduced. Maybe I've been lucky.
It has failed on me numerous times, so I'm reluctant to use it now.

Regarding the new card, make sure you have the monitor connected to the port on the new card and not where it was before.

---

### Post by dragos240 on 2010-04-11
> **cariboo907 said:**
> **The setting you want is under the PCI/PnP Setup menu. **

What chris4585 is saying is that there may be a 4-6 pin power connector on the video card, I don't think the 9500GT has one though.

There are a few options:

Init Display First [PCIEx]
Reset Configuration Data [Disabled]

Resources Controlled By [Auto(ESCD)]
IRQ Resources Press Enter

PCI/VGA Palette Snoop [Disabled]

** PCI Express relative items **
Maximum Payload Size [4096]

I think the last one may be useful.

---

### Post by dragos240 on 2010-04-11
> **cchhrriiss121212 said:**
> It has failed on me numerous times, so I'm reluctant to use it now.

Regarding the new card, make sure you have the monitor connected to the port on the new card and not where it was before.

I tried that as well. No output.

---

### Post by cascade9 on 2010-04-11
> **sisco311 said:**
> The relevant part is:
 ```

   *-core
        description: Motherboard
        product: **MCP61PM-AM**
        vendor: **ELITEGROUP**
        physical id: 0
        version: 1.0A
 
```seek out & download the manual...
 
 (why don't you start a thread in one of the appropriate support forum?)
 
 
 Agreed on 'appropriate support forum' and the idea of getting the manual, but from what I could see at the ECS site, they dont even list that motherboard (probably because its not for general use, its meant to be sold only to corporate builders like gateway, packarbell, etc). Someone else can have a look if they want- 
 
 [http://www.ecs.com.tw/](http://www.ecs.com.tw/) 

> **cariboo907 said:**
> The setting you want is under the PCI/PnP Setup menu. 

What chris4585 is saying is that there may be a 4-6 pin power connector on the video card, I don't think the 9500GT has one though.

They dont. ;) 

> **steveneddy said:**
> Is the video onboard video and you bought an extra card for video?

I see this in your list:

Looks like the video in onboard or you haven't actually installed the video card?

do you have TWO video cards installed?

didn't you purchase a 9500 GT?

If you have onboard video, you will have to blacklist the onboard video so the OS doesn't see it or disable the onboard video in the BIOS, which after reading, you don't have control over that area through the BIOS.

Blacklisting is the last resort. Better to disable it in the BIOS. 

@ dragos240-  I'm guessing from the other manual I got from ECS that this is where you onboard video disable is- 

Advanced Chipset Features-> Onboard GPU- set this to 'disable' 

BTW, remove the current drivers before you enable the new video card. Then reboot, go into BIOS, enable the video card, save settings, change the cable over, boot into the OS, an reinstall the nvidia drivers.

---

### Post by dragos240 on 2010-04-11
> **cascade9 said:**
> Agreed on 'appropriate support forum' and the idea of getting the manual, but from what I could see at the ECS site, they dont even list that motherboard (probably because its not for general use, its meant to be sold only to corporate builders like gateway, packarbell, etc). Someone else can have a look if they want- 
 
 [http://www.ecs.com.tw/](http://www.ecs.com.tw/) 



They dont. ;) 



Blacklisting is the last resort. Better to disable it in the BIOS. 

@ dragos240-  I'm guessing from the other manual I got from ECS that this is where you onboard video disable is- 

Advanced Chipset Features-> **Onboard GPU**- set this to 'disable' 

BTW, remove the current drivers before you enable the new video card. Then reboot, go into BIOS, enable the video card, save settings, change the cable over, boot into the OS, an reinstall the nvidia drivers.

Unfortunately, that option doesn't exist.

---

### Post by cascade9 on 2010-04-11
It migth be hiding somewhere else in the BIOS, but that is unlikely. Still, worth a look, check every page. ;) 

This is why I really dislike 'corporate' computers- locked down BIOSes with less options than they should have.

---

### Post by dragos240 on 2010-04-11
I want to know if this is set up right:
[ATTACH]152930[/ATTACH]

Sorry for the low quality, best quality my netbook cam could take. Anything drastically wrong here?

---

### Post by cascade9 on 2010-04-11
Thats fine. 

The only issue your having is the &$^&!@#$!@ corporate BIOS.

*edit- its pretty hard to see if the card is fully inserted into the slot from that angle, but I would assume that it is.

---

### Post by dragos240 on 2010-04-11
Anyone know how I can upgrade my bios? It's a phoenix bios. Apparently it's award winning :p.

---

### Post by cascade9 on 2010-04-11
> **dragos240 said:**
> Anyone know how I can upgrade my bios? It's a phoenix bios. Apparently it's award winning :p.

Depends. The safe way? Go to the manufcturers site, put in your model number, etc etc, get the newest BIOS, then flash it whatever way they suggest (warning- a lot of them now do BIOS updates from windows, but its still possible to do them the old fashioned way with floppy drives). 

That probably wont give you the 'disable onboard video' option though. To do that you would need to start playing with BIOSes, and either hack the BIOS or try crossfalshing.. If you've never flashed a BIOS before I dont think that hacking or crossflashing is a good idea...

BTW, 'crossflashing' is using a BIOS from a different motherboard. I would guess that the BIOS from the ECS 6100SM-M@ *may* work, but there is no way of knowing without trying it.

---

### Post by swoll1980 on 2010-04-11
If you have a windows install you can run a exe from their site. If not you will have to flash it the old fashioned way.

---

### Post by dragos240 on 2010-04-11
It wants me to PAY for a new BIOS. Fat chance.

---

### Post by cascade9 on 2010-04-11
What on earth? Pay for a BIOS? What evil company does that? :|

---

### Post by swoll1980 on 2010-04-11
> **dragos240 said:**
> It wants me to PAY for a new BIOS. Fat chance.

> **cascade9 said:**
> What on earth? Pay for a BIOS? What evil company does that? :|

Get it from your mobo or computer manufacturer's site.

---

### Post by spoons on 2010-04-11
Have you plugged the monitor into the new graphics card? Sounds daft, but I've seen people not do that.

---

### Post by dragos240 on 2010-04-11
> **spoons said:**
> Have you plugged the monitor into the new graphics card? Sounds daft, but I've seen people not do that.

I tried. Nothing happened.

---

### Post by dragos240 on 2010-04-11
> **swoll1980 said:**
> Get it from your mobo or computer manufacturer's site.

My manufacturer wants me to pay.

---

### Post by cascade9 on 2010-04-12
> **swoll1980 said:**
> Get it from your mobo or computer manufacturer's site.

The motherboard manufacturers site has no BIOS for that system (its an OEM model, so no support by ECS). 

dragos240- seems like this is a known problem, I found a page somewhere with the same issue you are having on vista, and this - 

> MCP61PM-AM Motherboard BIOS Release Notes[IMG]http://static.packardbell.com/sup/tpl/img/dot.gif[/IMG]
Here you will find the BIOS revision history for the MCP61PM-AM motherboard. Please note that not all BIOS versions may be available as download. [Click here]("http://support.packardbell.com/global/item/index.php?i=cnt_motherboard_MCP61PM-AM&PibLinkType=2006") to see the list of available BIOS downloads. 

  V011  
[LIST]
[*]Fixed a no video issue on add-on video card.
[/LIST]


[http://support.packardbell.com/global/item/index.php?i=instr_releasenotes_bios_mcp61pm-am&pi=platform_amadeus_istart](http://support.packardbell.com/global/item/index.php?i=instr_releasenotes_bios_mcp61pm-am&pi=platform_amadeus_istart)

So if you want to get your video working, you are going to have to pay your manufacturer for your BIOS update, find the offical BIOS 'somwewhere else' or take the risk of flashing a diffeernt BIOS onto your computer (BTW, Acer, eMachines, Gateway, HP and PackardBell all have systems with this motherboard) 

how much do they want for the BIOS?

---

### Post by dragos240 on 2010-04-12
$30 or something. That's about the money I would need to buy CS:S.

---

### Post by cascade9 on 2010-04-12
$30? Rip-off. You could get a motherboard for your current parts for not much more than that. (as to if it would fit in your case, thats a different question)

---

### Post by dragos240 on 2010-04-12
> **cascade9 said:**
> $30? Rip-off. You could get a motherboard for your current parts for not much more than that. (as to if it would fit in your case, thats a different question)

A new motherboard would be a good idea anyway. My current board can only support 2gb of ram and my 2 64 bit CPUs are the max I can have. So buying a new motherboard is a pretty good idea.

---

### Post by swoll1980 on 2010-04-12
> **dragos240 said:**
> A new motherboard would be a good idea anyway. My current board can only support 2gb of ram and my 2 64 bit CPUs are the max I can have. So buying a new motherboard is a pretty good idea.

$30 is a rip off. I've never heard of people being charged for a BIOS update before.

---

### Post by cascade9 on 2010-04-12
> **dragos240 said:**
> A new motherboard would be a good idea anyway. My current board can only support 2gb of ram and my 2 64 bit CPUs are the max I can have. So buying a new motherboard is a pretty good idea.

Probably not  a bad idea, but be careful- some corporate computers have non-standard motherboard mounting holes and switches that can mean you have to replace the case as well.

---

