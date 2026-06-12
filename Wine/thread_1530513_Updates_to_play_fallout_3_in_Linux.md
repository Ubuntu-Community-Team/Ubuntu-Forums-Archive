---
title: "Updates to play fallout 3 in Linux?"
date: 2010-07-13
forum: Wine
---

### Post by Nick_Jinn on 2010-07-13
Is there some driver or graphics update that will allow me to play Fallout 3 on Linux?

Once upon a time I got a walk through but I lost it. 

Nvidia Geforce 6800, 768mb video ram
4GB DDR2 RAM
Phenom Quad 3.4 ghrz

---

### Post by cogadh on 2010-07-13
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

---

### Post by Nick_Jinn on 2010-07-13
Thanks. Ill let you know if it works. DOnt mark as solved yet.

---

### Post by cogadh on 2010-07-14
You and the admins/mods are the only ones who can mark it as solved anyway.

---

### Post by Nick_Jinn on 2010-07-14
I am having problems. I cant even install desktop effects, probably because I have 2 video cards.....one in my motherboard and the other is a mid/higher end Nvidia Geforce.

I am using an Asus AM2+, 4gb DDR2 Ram, and Phenom Quad 3.4 ghrz.

I should be able to run some effects, but its not happening. I think somebody else had this bug.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/573557](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/573557)


But I am only starting to become a geek, and I feel like I am a little stuck.

---

### Post by cogadh on 2010-07-14
Just disable the on board video chipset in your computer's BIOS and the problem should go away.

---

### Post by Nick_Jinn on 2010-07-15
> **cogadh said:**
> Just disable the on board video chipset in your computer's BIOS and the problem should go away.


Awesome. Only problem is that I am just barely a step above noob still and dont know how to do this properly outside of some methods that require me to log in and type in some stuff outside of graphics mode, which is something I really dont feel confident enough to do by memory without cutting and pasting the command line.

---

### Post by cogadh on 2010-07-15
You can't modify the BIOS ([Basic Input/Output System]("http://computer.howstuffworks.com/bios.htm")) settings from within Linux, you have to access the BIOS by pressing a particular key while your machine is booting (before the OS actually boots). Which key to press depends on your machine, but there is usually some kind of prompt when you initially boot a machine that will tell you which key to press ("Press <something> to enter Setup"). If there isn't any prompt, you will have to check the documentation for your machine to find out what to do. Once in the BIOS settings, you will have to explore around a bit to find the appropriate setting to change (I can't be more specific, there is no real standard for what your BIOS configuration will look like). If you can find out the make/model of the motherboard your machine has, I can be a bit more specific.

---

### Post by Nick_Jinn on 2010-07-15
This is a custom Build. 

Asus M4A770 motherboard.

---

### Post by cogadh on 2010-07-15
Are you sure about that model number? The only available model numbers in that series seem to be:

M4A77
M4A77D
M4A77T
M4A77T/USB3
M4A77TD
M4A77TD PRO

Whichever one it actually is could make a difference on what settings are available and what needs to be changed.

---

### Post by Nick_Jinn on 2010-07-15
It could be a D. It looks totally symmetrically square, not round like an O but even less like a D.

D would make sense though.

---

### Post by gradinaruvasile on 2010-07-15
Get in the BIOS  ans see if you have something related to initializing the display (init display first or something). That should be set to PCIE (or VGA) (MGPU is the onboard card ususlly in the ASUS BIOS).

---

### Post by Nick_Jinn on 2010-07-15
I got into the bios, or something called "Bios Flash" or something, and I dont understand most of what I was looking at.

---

### Post by cascade9 on 2010-07-15
You might have go into the BIOS flash utility (alt + F2 during boot). 

> **Nick_Jinn said:**
> This is a custom Build. 

Asus M4A770 motherboard.

If you've got onbaord video, its not a 770 chipset. They have no onboard video.

Can you please post the output from (in 'code' tags)- 

sudo lshw

---

### Post by Nick_Jinn on 2010-07-15
>    physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:c000(size=4096) memory:fa000000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9600 GSO]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:cc00(size=128) memory:fe9e0000-fe9fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:fea00000-feafffff ioport:f8f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 90:e6:ba:c8:1d:48
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:27 ioport:d800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8ff8000-f8ffbfff(prefetchable) memory:feaf0000-feafffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:f9fffc00-f9ffffff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXE209UK6189
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4b76fad2
              *-volume
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10GiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f9ffe000-f9ffefff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f9ffd000-f9ffdfff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f9fff800-f9fff8ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffc000-f9ffcfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffb000-f9ffbfff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f9fff400-f9fff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r
                configuration: status=nodisc
           *-disk
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 0.1.0
                bus info: scsi@5:0.1.0
                logical name: /dev/sdb
                version: 1AJ1
                serial: S246J1LZ305159
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b00fb00f
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 2c673749-2fe0-4e49-8099-4f3acb6396c6
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-06-04 07:56:43 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.1.0,2
                   logical name: /dev/sdb2
                   size: 819GiB
                   capacity: 819GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 9546MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: W95 FAT32 partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 37GiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sdb7
                      logical name: /
                      capacity: 32GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sdb8
                      logical name: /home
                      capacity: 591GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f9ff4000-f9ff7fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=4096) memory:feb00000-febfffff
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 5
                bus info: pci@0000:03:05.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=uhci_hcd latency=64
                resources: irq:20 ioport:ec00(size=32)
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 5.1
                bus info: pci@0000:03:05.1
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=uhci_hcd latency=64
                resources: irq:21 ioport:e880(size=32)
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: 5.2
                bus info: pci@0000:03:05.2
                version: 63
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ehci_hcd latency=64
                resources: irq:22 memory:febffc00-febffcff
           *-firewire:0
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 5.3
                bus info: pci@0000:03:05.3
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: irq:20 memory:febff000-febff7ff ioport:e800(size=128)
           *-multimedia
                description: Multimedia audio controller
                product: CA0106 Soundblaster
                vendor: Creative Labs
                physical id: 7
                bus info: pci@0000:03:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2
                resources: irq:22 ioport:e480(size=32)
           *-firewire:1
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:03:08.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: irq:23 memory:febfe800-febfefff ioport:e400(size=128)
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffa000-f9ffafff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          bus info: usb@2:3
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
        *-disk:4
             description: SCSI Disk
             physical id: 0.0.4
             bus info: scsi@6:0.0.4
             logical name: /dev/sdg
     *-scsi:1
          physical id: 2
          bus info: usb@2:5
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdh
             size: 7648MiB (8019MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=00060e57
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdh1
                logical name: /media/04A2-9013
                version: FAT32
                serial: 04a2-9013
                size: 7641MiB
                capacity: 7642MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:22:6b:a3:4e:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bg



I guess my video card is only selling for half of what I bought it for....its still good though.


I dont seem to be having problems anymore (miraculously) using desktop effects with the default drivers.....I dont know if that means I can play Ubuntu or not.


It seems like 'playonlinux' hasnt been updating when I do the general update.

---

### Post by cascade9 on 2010-07-15
I'm hoping from "I dont seem to be having problems anymore" that things have fixed themselves. 

I only asked for the output from lshw to see what motherboard you had, but you cut off the beginning of the output (where the motherboard info appears). BTW, dont use the 'quote' tags for lshw output, 'code' tags work much better- not as much scrolling to get though the page its posted on.

---

### Post by Nick_Jinn on 2010-08-06
Finally got it working in Ubuntu Ultimate after upgrading Wine and not using PlayonLinux or Winedoors....just regular wine, marked the dll and other files as native as per the instructions and bobs my uncle. :p

I am getting extremely good frame rates in Linux. I doubt I would notice any quality improve if I was playing in Windows.


The real question though is using mods. Anyone help me out? Is it possible to use Script extender? What about Geck?

How do I mod files manually? I always did it the lazy way with the mod manager before, but I think Im feeling more confident now and am up to doing it manually.

---

### Post by cogadh on 2010-08-06
Using mods is essentially the same in Linux through Wine as it is on Windows; the only real difference is file locations and even that is not all that different once you get into the .wine directory. You should check [Wine's Application Database]("http://appdb.winehq.org/") to see if any of the modding applications you might need will work, but otherwise, whatever you already did to use mods is what you would still do. 

If by "mod files manually" you are asking how to create your own mods, this is not the right place to be asking. You would be much better off asking that somewhere like the Fallout 3 forums.

---

### Post by Nick_Jinn on 2010-08-07
> **cogadh said:**
> If by "mod files manually" you are asking how to create your own mods, this is not the right place to be asking. You would be much better off asking that somewhere like the Fallout 3 forums.

Mod Manager crashed. I need to narrow my search to find info on setting up mod manger with wine. I keep getting results for the game itself and snippets of commentary from people who dont know if mod manager works. A few other people have documented mod manager crashing at startup....kind of like Fallout was before I followed instructions better after a clean install.


As for 'manual modding', I dont mean creating mods. I mean just dragging and dropping data folders into the right place. That was the 'harder' way of doing it, but it seems like a sure bet to work if the mod manager keeps crashing.

---

### Post by ElSlunko on 2010-08-07
Glad to hear you got the base game running. I did as well on my system without much problem except the latest patch borked my install. Not really sure why but playing it without the patch at the moment.

Not sure about mods but there is a ton of helpful info on the wine page as I'm sure you've noted.

---

