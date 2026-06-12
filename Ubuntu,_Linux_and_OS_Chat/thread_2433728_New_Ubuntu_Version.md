---
title: "New Ubuntu Version?"
date: 2019-12-24
forum: Ubuntu, Linux and OS Chat
---

### Post by uzzo23 on 2019-12-24
Hello all, I am considering a newer version of ubuntu or some other distro since I've been running 14.04 for a good while now. I'm getting several error messages on startup so I'm thinking that it may be time to upgrade. I'll try and post my computer specs here so maybe it'll help make things a little easier. Thanks in advance for any help/suggestions.

```
phillip@phillip-OptiPlex-360:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Model name:            Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
Stepping:              10
CPU MHz:               2925.617
BogoMIPS:              5851.23
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
NUMA node0 CPU(s):     0,1
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm kaiser tpr_shadow vnmi flexpriority dtherm

```

```
phillip-optiplex-360
    description: Mini Tower Computer
    product: OptiPlex 360
    vendor: Dell Inc.
    serial: BX3PFK1
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=mini-tower power-on_password=enabled uuid=44454C4C-5800-1033-8050-C2C04F464B31
  *-core
       description: Motherboard
       product: 0T656F
       vendor: Dell Inc.
       physical id: 0
       version: A02
       serial: ..CN1374099Q00BR.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A02
          date: 07/02/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: CPU
          size: 2933MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm kaiser tpr_shadow vnmi flexpriority dtherm
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 3MiB
             capacity: 3MiB
             capabilities: internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125U64CP8-S6
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: 3D119C40
             slot: DIMM_1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125U64CP8-S6
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: 3D219C40
             slot: DIMM_2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0a
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:dfc00000-dfcfffff
        *-display:0
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:26 memory:dfe00000-dfe7ffff ioport:ecd8(size=8) memory:c0000000-cfffffff memory:dff00000-dfffffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dfe80000-dfefffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:27 memory:dfdfc000-dfdfffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:dfb00000-dfbfffff ioport:d0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 10
                serial: 00:25:64:a0:7d:42
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:dfbf0000-dfbfffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-165-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-165-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-165-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Keyboard
                   product: Dell USB Keyboard
                   vendor: Dell
                   physical id: 1
                   bus info: usb@4:1
                   version: 3.06
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
              *-usb:1
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-165-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:ff980800-ff980bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-165-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:df900000-dfafffff
           *-network
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 10
                serial: 04:8d:39:40:0f:61
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
                resources: irq:16 ioport:dc00(size=256) memory:df9fff00-df9fffff memory:dfa00000-dfa1ffff
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
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm pci_native_mode_controller__supports_both_channels_switched_to_isa_compatibility_mode__supports_bus_mastering bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ece0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72105
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: A3EA
             serial: JPB530HA1L0WEB
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=ce93aa3a
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 29923bb4-83e6-4ffc-b0a9-705a4fafb852
                size: 461GiB
                capacity: 461GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-10-01 22:59:05 filesystem=ext4 lastmountpoint=/ modified=2019-12-24 08:01:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2019-12-24 08:01:48 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 4019MiB
                capacity: 4019MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4019MiB
                   capabilities: nofs
        *-cdrom
             description: DVD writer
             product: DVD-RW DVR-221D
             vendor: PIODATA
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 1.DE
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GH50N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/dvdrw
             logical name: /dev/sr1
             version: B101
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by crip720 on 2019-12-24
The new supported versions now are 18.04 and 19.10, with 16.04 supported till 2021.  Might be easier to do a clean install now than an upgrade.  You will need to check if your errors are OS based or hardware based which an upgrade/install won't fix.  Your specs might have an easier time with Lubuntu or Xubuntu or similar light desktop.  Ubuntu has gone to gnome desktop with 18.04, which is heavier.

---

### Post by yetimon_64 on 2019-12-24
> **crip720 said:**
> ...Your specs might have an easier time with Lubuntu or Xubuntu or similar light desktop.  Ubuntu has gone to gnome desktop with 18.04, which is heavier.

With 4GiB of RAM I was thinking Xubuntu 18.04 would go nicely there. The processor is and older Core(TM)2 Duo CPU.

I had an old Acer Laptop using about these specs in the late 2000's about ten or eleven years ago. I definitely would NOT put a full Ubuntu installation with a Gnome DE there, it could be a bit slow or "painful" to use. I think Xubuntu at the most, Lubuntu would probably fly along on this. My preference would be for Xubuntu here though with that much RAM. 

Regards, yeti

---

### Post by poorguy on 2019-12-24
I have several **Dell Optiplex 380 desktops** with **e7500 processor** and **4.0 GB DDR3 memory** and these desktops will run **Ubuntu 18.04** with those specs although I'd recommend a light weight **Ubuntu flavour.**

I'm not trying discourage using the **Ubuntu flavours **however most of the lightweight **Ubuntu flavours** reach[B] EOL 2021.
[/B]

Since you mentioned and I quote **"some other distro"** here's a suggestion.

I'm using **Peppermint 9** and **Peppermint 10** on mine and it runs great on them and it's **Ubuntu 18.04 LTS** under the hood and **supported until 2023.**
Here's a link so have a look.

[https://peppermintos.com/2019/12/peppermint-10-respin-released/](https://peppermintos.com/2019/12/peppermint-10-respin-released/)

[https://peppermintos.com/](https://peppermintos.com/)

[https://forum.peppermintos.com/](https://forum.peppermintos.com/)

---

### Post by mörgæs on 2019-12-25
After you reinstall a new distro (many good options mentioned above) you should change all passwords which have been entered while running 14.04.

---

### Post by uzzo23 on 2019-12-25
Thanks guys, I wound up installing a fresh version of Xubuntu 18.04 on it. I haven't gotten a chance to play with it much yet though. Right now I have to figure out how to put my home folder that I backed up before the install back on it.

---

### Post by mörgæs on 2019-12-25
Don't.

Copy the needed user files one by one but not the configuration. What made sense in 14.04 can cause problems for 18.04.

---

### Post by uzzo23 on 2019-12-25
> **mörgæs said:**
> Don't.

Copy the needed user files one by one but not the configuration. What made sense in 14.04 can cause problems for 18.04.

I don't have any idea where to start my friend. It all looks like a foreign language to me.



[ATTACH=CONFIG]284673[/ATTACH]

---

### Post by mörgæs on 2019-12-25
Your new install contains by default a number of directories called

/home/patrick/Documents
/home/patrick/Desktop
/home/patrick/Downloads

and so on.

Create a new directory, say

/home/patrick/Documents/SavedFromOldInstall

and unpack the duplicity archive here. The unpacking is free to create directories like
/home/patrick/Documents/SavedFromOldInstall/Documents

but for now don't put anything into
/home/patrick/Documents

When that is done write again so we can take a look at next step.

---

### Post by uzzo23 on 2019-12-25
> **mörgæs said:**
> Your new install contains by default a number of directories called

/home/patrick/Documents
/home/patrick/Desktop
/home/patrick/Downloads

and so on.

Create a new directory, say

/home/patrick/Documents/SavedFromOldInstall

and unpack the duplicity archive here. The unpacking is free to create directories like
/home/patrick/Documents/SavedFromOldInstall/Documents

but for now don't put anything into
/home/patrick/Documents

When that is done write again so we can take a look at next step.

Okay my friend, I did what you said. I basically just copied and pasted it in the new folder you told me to create.



[ATTACH=CONFIG]284674[/ATTACH]

---

### Post by mörgæs on 2019-12-25
No, you copied the files into the new directory.
You need to unpack them here.

---

### Post by uzzo23 on 2019-12-25
> **mörgæs said:**
> No, you copied the files into the new directory.
You need to unpack them here.

You'll have to excuse my ignorance. I can put one together but as far as programming and technical stuff I'm just not good on. This is the first time in several months that I've actually turned my Linux machine on. It was giving problems and I just didn't have time to deal with it so I've just been using my windows 7 machine. It's made me lazy because I really enjoy Linux and learning new things about it. Is there an easy way to extract all of the files from the SD card and put them in the new file I created?

---

### Post by mörgæs on 2019-12-26
I can see that you are posting the same question in another thread so I am signing out here.

---

### Post by uzzo23 on 2019-12-26
> **mörgæs said:**
> I can see that you are posting the same question in another thread so I am signing out here.

Yes,my apologies, I started that thread as soon as I got done installing the new xubuntu version. I'll go ahead and shut this one down and put the link to that thread here. I still haven't figured out what I need to do to get those files onto the new version yet. Maybe someone will be able to help me finish it up on that thread. Thanks for all the suggestions here, I appreciate it.

[https://ubuntuforums.org/showthread.php?t=2433741](https://ubuntuforums.org/showthread.php?t=2433741)

---

### Post by Skaperen on 2019-12-26
how is your fresh new Xubuntu 18.04 LTS  doing?  how is your backup folder doing?  got your SD card switched to read-only?

---

### Post by uzzo23 on 2019-12-29
> **Skaperen said:**
> how is your fresh new Xubuntu 18.04 LTS  doing?  how is your backup folder doing?  got your SD card switched to read-only?

Sorry for the delay, it's been kind of crazy around here the last couple of days. I like xubuntu so far although I haven't had a whole lot of time to play with it. I'm still having the issue with the restoration of my backed up files. I posted that on another thread because this is not the appropriate sub-forum for support. I think it's just for chat only.

---

### Post by bernard010 on 2020-01-19
I would use 18.04 Ubuntu or any one of the other flavors. It's standard support is until April 2023.
How is your new OS doing? I hope well..

---

### Post by uzzo23 on 2020-01-19
> **bernard010 said:**
> I would use 18.04 Ubuntu or any one of the other flavors. It's standard support is until April 2023.
How is your new OS doing? I hope well..

It's doing fine, I actually like it quite well. I was never able to restore any of my home folder back so I lost everything and am starting over again. I'm not real happy about that but it's not the first time it's happened.

---

### Post by mastablasta on 2020-01-21
data is still in compressed files.

you should unpack the files (e.g. right click and select "extract" to get the unpacked files). if duplicity has an option where it would guide you, you can do it through there.

this pic should explain it better: [https://docs.xfce.org/xfce/thunar/archive](https://docs.xfce.org/xfce/thunar/archive)

btw have you ever looked at duplicati ? same back end as duplicity i believe, but a much nicer front end for the user.

---

