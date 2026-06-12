---
title: "Gedit - erratic and mouse disappears"
date: 2015-01-17
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-01-17
Gedit in Vivid is unmanageable at the present time. I've tried using it and my mouse will just disapear while over it. Then I cannot tell where the cursor/mouse is and so it is not functional to use it.
I've been using leafpad as a replacement. I don't want a replacement because nothing can replace gedit. You can save a file without changing it for example. It remembers where it was the last time you used it.
The preferences and addons are fantastic. The good features are too numerous as you know to mention. I know Ubuntu is leaning more heavily on Unity than Gnome but nothing can replace gedit - maybe a uedit. :p

I was wondering if it is being developed and will we see a workable version of gedit in Vivid?

[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

---

### Post by mc4man on 2015-01-17
I would suspect that gedit 3.14 may show at some point if they can & are motivated to fix for an ubuntu session.
Here the current 3.10 works ok now that a newer gtksourceview-3.0-1 was put up. (- libgtksourceview-3.0-1 3.14.1-1 ect.

Though somewhat unrelated I dislike the removal of 'text previews' in text file icons though that's likely a  nautilus/gtk 'issue' or redhat change

---

### Post by ventrical on 2015-01-17
Works just fine here in gnome-flashback with compiz bells and whistles..

---

### Post by Cavsfan on 2015-01-17
> **mc4man said:**
> I would suspect that gedit 3.14 may show at some point if they can & are motivated to fix for an ubuntu session.
Here the current 3.10 works ok now that a newer gtksourceview-3.0-1 was put up. (- libgtksourceview-3.0-1 3.14.1-1 ect.

Though somewhat unrelated I dislike the removal of 'text previews' in text file icons though that's likely a  nautilus/gtk 'issue' or redhat change

I hope they drop version 3.14 in here. I guess libgtksourceview isn't helping much here. I've got the same version.

> **ventrical said:**
> Works just fine here in gnome-flashback with compiz bells and whistles..

It's been finicky here. It'll work for a while then the mouse will disappear. Maybe I'll try it some more.
But a newer version sure would be nice.

[https://wiki.gnome.org/Apps/Gedit](https://wiki.gnome.org/Apps/Gedit) - This shows it was edited on February 12, 2014. So, I guess that means there is hope. Maybe I'll have another look there when I have more time.

---

### Post by ventrical on 2015-01-17
It could be an HPET problem in BIOS. Also .. sounds like a video driver problem , not gedit. What is your hardware? What graphics driver are you using? I ran it both in gnome-flashback and unity and no problems.

Thanks..

---

### Post by philhughes on 2015-01-18
This is not just a problem with Vivid. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219)

---

### Post by ventrical on 2015-01-18
Those scenarios did not happen on my Desktop Tower with SandyBridge graphics.

```

ventrical@ventrical-MS-7798:~$ lshw
WARNING: you should run this program as super-user.
ventrical-ms-7798         
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: Intel(R) Pentium(R) CPU G630 @ 2.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2699MHz
          capacity: 2700MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave lahf_lm arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=snb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:24 memory:f7d00000-f7d0ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:27 memory:f7d1a000-f7d1a00f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7d17000-f7d173ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:f7d10000-f7d13fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:e000(size=4096) memory:f7c00000-f7cfffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: d4:3d:7e:99:b8:a7
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.2.29 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:25 ioport:e000(size=256) memory:f7c04000-f7c04fff memory:f7c00000-f7c03fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7d16000-f7d163ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: B75 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7d15000-f7d157ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d14000-f7d140ff ioport:f040(size=32)
     *-scsi
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NS95
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: RN00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by Cavsfan on 2015-01-18
> **philhughes said:**
> This is not just a problem with Vivid. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219)

That I'm pretty sure describes my exact problem. I me tooed the bug.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                           331.113-0ubuntu2                           amd64        NVIDIA binary driver - version 331.113
ii  nvidia-331-uvm                                       331.113-0ubuntu2                           amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-331                                331.113-0ubuntu2                           amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                         0.6.7                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      331.20-0ubuntu8                            amd64        Tool for configuring the NVIDIA graphics driver

```


```
cavsfan@cavsfan-MS-7529:~$ lshw
WARNING: you should run this program as super-user.
cavsfan-ms-7529           
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3952MiB
     *-cpu
          product: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fa000000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9800 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:29 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:feae0000-feafffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:28 memory:f9ffc000-f9ffffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:f0000000-f01fffff ioport:f0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff ioport:f0400000(size=2097152)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:24:21:51:21:3a
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:27 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff
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
             resources: irq:23 ioport:cc00(size=32)
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
             resources: irq:19 ioport:c880(size=32)
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
             resources: irq:18 ioport:c800(size=32)
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
             resources: irq:16 ioport:c480(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f9ffbc00-f9ffbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
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
             resources: ioport:400(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S202J
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SB02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---

### Post by ventrical on 2015-01-18
I have an extra near exact same system with that nVidia card.. and it has been questionable. My assumption is the frivers. I'll try to dupe it and I bet I can.

```

ventrical@ventrical-MS-7798:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)
02:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
ventrical@ventrical-MS-7798:~$ lshw
WARNING: you should run this program as super-user.
ventrical-ms-7798         
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2001MiB
     *-cpu
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2403MHz
          capacity: 2403MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fa000000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS Rev. 2]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:44 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:feae0000-feafffff
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c800(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c880(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:cc00(size=32)
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f9fffc00-f9ffffff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f9ff8000-f9ffbfff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:80000000-803fffff ioport:f8f00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:80400000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: b0
                serial: 00:24:8c:1f:87:da
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.2.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:febc0000-febfffff ioport:ec00(size=128)
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c080(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c400(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c480(size=32)
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f9fff800-f9fffbff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff90(size=16) ioport:ffa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9fff400-f9fff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=16) ioport:b400(size=16)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by mc4man on 2015-01-18
> **philhughes said:**
> This is not just a problem with Vivid. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219)
Definetly seems to be some ibus nonsense. Only happens here when ctrl+c is used, cut from the menu is ok.
Also disappears once focus is taken off of gedit & then returned.

Here rather than add more ibus packages I just disable ibus in system settings (Keyboard Input method system: none) as it's of no use to me anyway.

---

### Post by ventrical on 2015-01-18
Yes.. it does in on this video card in nouveau also:

```

01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)
02:00.0

```

but not others..

---

### Post by ventrical on 2015-01-19
Works fine on this nVidia series.

```

03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

must be drivers or card is deprecated.

---

### Post by Cavsfan on 2015-01-19
> **mc4man said:**
> Definetly seems to be some ibus nonsense. Only happens here when ctrl+c is used, cut from the menu is ok.
Also disappears once focus is taken off of gedit & then returned.

Here rather than add more ibus packages I just disable ibus in system settings (Keyboard Input method system: none) as it's of no use to me anyway.

I switched back to using gedit vs leafpad as default and love gedit! It has too many positives to mention.
It is rare that the cursor disappears but it happens occasionally. Haven't been paying attention to exactly what causes it.

I must be dense but I cannot find that. 
Is it in here?

[ATTACH=CONFIG]259361[/ATTACH]

---

### Post by Cavsfan on 2015-01-19
In the bug it states that if you long press Alt the cursor will disappear.
I just tried that and it did disappear. It did not come back and nothing I tried would bring it back.

---

### Post by ventrical on 2015-01-19
Nope .. not here on:

```

03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

---

### Post by Cavsfan on 2015-01-19
> **ventrical said:**
> Nope .. not here on:

```

03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

Odd. I fail to see how it could be driver related though. I no longer have Utopic on my computer but this does not happen with Precise, Trusty or Mint 17 Rebecca.
On Vivid I have the 331.113 driver.

---

### Post by mc4man on 2015-01-19
> **Cavsfan said:**
> I switched back to using gedit vs leafpad as default and love gedit! It has too many positives to mention.
It is rare that the cursor disappears but it happens occasionally. Haven't been paying attention to exactly what causes it.

I must be dense but I cannot find that. 
Is it in here?

[ATTACH=CONFIG]259361[/ATTACH]
No,  look in System Settings > Language Support > Keyboard Input ..., set to "None", then log out in & the issue should go away

The easiest way to see the bug would be to highlight some text in gedit > ctrl+c, at that point the cursor would start disappearing while in gedit window.

---

### Post by ventrical on 2015-01-19
> **Cavsfan said:**
> Odd. I fail to see how it could be driver related though. I no longer have Utopic on my computer but this does not happen with Precise, Trusty or Mint 17 Rebecca.
On Vivid I have the 331.113 driver.

I'm using nouveau.
 
 Just tried  your test again on upgraded gnome session with this graphics card:

```

01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)

```

 Odd that the same card would work in gnome-session and not Ubuntu-unity.

  Looks like mac4man has the quick workaround though.

Regards..

---

### Post by Cavsfan on 2015-01-19
Thanks          mc4man! That fixed it! Pressing Alt had the same effect as selecting some text and then pressing Cntl+v: both made the cursor go invisible. 
I finally found it and it was actually under Applications > System Tools, while most things are under Applications > Other.

Thanks ventrical for you input as well. :D

Glad that the Applications Menu applet in Cairo Dock has a search. Although you need to know fairly closely what you are looking for. It's not as intuitive as the Unity Dash.

Do you think they will straighten out the menu at some point in FB?

---

### Post by mc4man on 2015-01-19
Ot - 
screen shows gedit 3.14 in an ubuntu session, ambiance theme. Clearly needs fixing..

---

### Post by Cavsfan on 2015-01-19
I love gedit! :) It is undeniably the best text editor in Linux. It remembers where it was from the last time, it highlights certain text, 
you can save files such as conky files without making any changes to the file. 

I was using leafpad all this time and to save a conky file you have to first add a space and then delete it just to be able to save the file.

Like I said the benefits are too numerous to mention. :D

And when I see **gksu gedit <filename>** or **gksudo gedit <filename>** give off errors, then and only then will I worry about anything.

---

### Post by Cavsfan on 2015-01-19
> **mc4man said:**
> Ot - 
screen shows gedit 3.14 in an ubuntu session, ambiance theme. Clearly needs fixing..

Was this in proposed? I don't see any difference between this and gedit 3.10.4.
But I failed to figure out ambiance theme even though gnome tweak tool shows ambiance theme already.

[ATTACH=CONFIG]259370[/ATTACH]

Don't know what's up with the lack of borders in this, nautilus, pretty much everything except Firefox and terminal.
At least there is the minimize, close and maximize buttons.
Although I cheated after I first installed and put emerald window decorator on Vivid.

But, with that open on a white background you cannot see the borders.

---

### Post by syntaxerror74 on 2015-01-20
Got 3.14 running for quite some time now (gnome3-staging PPA makes it possible, whenever the Ubuntu retirees are too slow to reach for their crutches :D But seriously people, 3.10 is really TOO OLD now.)

BUT ...

There is a strange problem which I do not only have in Gedit but also in other related applications: the "window-slow-mo'-resizing" issue.

That is, whenever I try to resize the Gedit main window, it takes several SECONDS until the resizing is finished. Resizing is performed as if a slow-motion camera was filming it.
Has anybody else ever gotten to witness this phenomenon too?

---

### Post by ventrical on 2015-01-20
> **syntaxerror74 said:**
> Got 3.14 running for quite some time now (gnome3-staging PPA makes it possible, whenever the Ubuntu retirees are too slow to reach for their crutches :D But seriously people, 3.10 is really TOO OLD now.)

BUT ...

There is a strange problem which I do not only have in Gedit but also in other related applications: the "window-slow-mo'-resizing" issue.

That is, whenever I try to resize the Gedit main window, it takes several SECONDS until the resizing is finished. Resizing is performed as if a slow-motion camera was filming it.
Has anybody else ever gotten to witness this phenomenon too?


Sounds like llvmpipe..

---

### Post by Cavsfan on 2015-01-20
> **syntaxerror74 said:**
> Got 3.14 running for quite some time now (gnome3-staging PPA makes it possible, whenever the Ubuntu retirees are too slow to reach for their crutches :D But seriously people, 3.10 is really TOO OLD now.)

BUT ...

There is a strange problem which I do not only have in Gedit but also in other related applications: the "window-slow-mo'-resizing" issue.

That is, whenever I try to resize the Gedit main window, it takes several SECONDS until the resizing is finished. Resizing is performed as if a slow-motion camera was filming it.
Has anybody else ever gotten to witness this phenomenon too?

Careful many of us are older than you I would guess. :p

No I haven't experienced anything involving resizing gedit or any other windows myself.

@ventrical I do not have that file:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy llvmpipe
N: Unable to locate package llvmpipe

```

---

### Post by ventrical on 2015-01-20
> **Cavsfan said:**
> Careful many of us are older than you I would guess. :p

No I haven't experienced anything involving resizing gedit or any other windows myself.

@ventrical I do not have that file:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy llvmpipe
N: Unable to locate package llvmpipe

```

But you don't have slowing moving resizing windows either , do you?

 I don't know .. i have it working here just fine on several differnt machine with nVidia cards but one nVidia card produces the results with nouveau installed .. all other cases  I have tried on different machines do no show any symptoms as described in bug report.  I hold down LONG <alt>. and my mouse does not disappear.  Also .. I believe you had installed Cario-dock ... and I mentioned earlier on in another thread about how cario-doc will break gnome-flashback-compizDE and unityDE to some extent.. at least it did for me. Same thing with gnome -session . Ifi I start installing alternate DEs in there from the USC it is bound to break. At first it is novelty , but then will break unless you have larger , faster system and get the depends settled right.

---

### Post by Cavsfan on 2015-01-20
> **Cavsfan said:**
> Careful many of us are older than you I would guess. :p

No I haven't experienced anything involving resizing gedit or any other windows myself.

@ventrical I do not have that file:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy llvmpipe
N: Unable to locate package llvmpipe

```

> **ventrical said:**
> But you don't have slowing moving resizing windows either , do you?

 I don't know .. i have it working here just fine on several differnt machine with nVidia cards but one nVidia card produces the results with nouveau installed .. all other cases  I have tried on different machines do no show any symptoms as described in bug report.  I hold down LONG <alt>. and my mouse does not disappear.  Also .. I believe you had installed Cario-dock ... and I mentioned earlier on in another thread about how cario-doc will break gnome-flashback-compizDE and unityDE to some extent.. at least it did for me. Same thing with gnome -session . Ifi I start installing alternate DEs in there from the USC it is bound to break. At first it is novelty , but then will break unless you have larger , faster system and get the depends settled right.

No resizing problems here. I mentioned that already. There is an odd black border that is around the window 
(gedit or any window) when I resize a window but it goes away when I release the button on my mouse.
But I do not have any problem whatsoever with gedit since I disabled that ibus option 
as mc4man said. It fixed my problems with gedit. Nothing compares to gedit.

It's odd that I'm in Mint 17.1 Rebecca (Trusty) right now and the gedit version is 2.30.4. It works without any problems.

[ATTACH=CONFIG]259389[/ATTACH]

I'm with mc4man I believe it is ibus related and not Nvidia. Cairo Dock has not given me any problems but, I know between that 
and CCSM you can really screw your system up. Been there and done that. I've never really had Cairo Dock take my system down.
But CCSM I've checked or unchecked something and the whole system goes unresponsive. It takes the reset button to get it back.

That can happen when I log into Unity and go back to FB. Most of the time it still looks like Unity and I have to uncheck the Unity related 
stuff in CCSM then it converts to a FB session.

---

### Post by Elfy on 2015-01-21
thread title changed as per request

---

### Post by mc4man on 2015-01-21
> **Elfy said:**
> thread title changed as per request
Cavsfan - You can do such stuff yourself in threads you create..
Just go to 1st. post of thread > Edit > Advanced & do as you please.

---

### Post by Cavsfan on 2015-01-22
> **Elfy said:**
> thread title changed as per request

Much appreciated as always. :)

> **mc4man said:**
> Cavsfan - You can do such stuff yourself in threads you create..
Just go to 1st. post of thread > Edit > Advanced & do as you please.

Oh, D'oh I thought only an admin could do it. Thanks I'll remember that from now on.

OK, based on mc4man's post #10 and post #17 (explaining to my slow mind) a workaround by (in FB) going to
Applications > System Tools > Systems Settings > Language Support and changing Keyboard input method system from ibus to none solved this whole problem. 

Solved!  Thanks for your valuable input ventrical, mc4man and philhughes and any others I may have missed. :)

Peace be amongst us. :)

---

### Post by syntaxerror74 on 2015-01-23
> **ventrical said:**
> But you don't have slowing moving resizing windows either , do you?

 I don't know .. i have it working here just fine on several differnt machine with nVidia cards but one nVidia card produces the results with nouveau installed .. 

BINGO!!
I *am* on a NVidia card (older one) and yes, I have the nouveau drivers.
You really know your stuff, my deepest respect.

Finally I know where to look for that nuisant "slow-mo' window resizing" problem.
THANK YOU!

---

### Post by startas on 2015-01-23
Actually, dissappearing mouse cursor in gedit in general ubuntu / linux keyboard input bug, it doesnt matter which ubuntu version you will use, just move mouse over opened gedit, press ctrl or shift button (at least these 2 enables this bug 100% as far as i tried) and then mouse cursor will dissappear. The solution is to go to keyboard options in ubuntu and change input method from ibus or whatever to none.

---

### Post by ventrical on 2015-01-23
Not 'general'. Does not happen with exception on one machine with specific nVidia adapter card. I respectfully disagree with generalized fix. This is a nVidia driver problem imo.

Regards..

---

### Post by startas on 2015-01-23
Well, not so much nvidia problem, when you are using only intel graphics, and same "stuff" happens.

---

### Post by Cavsfan on 2015-01-23
> **startas said:**
> Well, not so much nvidia problem, when you are using only intel graphics, and same "stuff" happens.

@mc4man, what do you think? Is this an ibus problem or an Nvidia driver problem? It seems that if you have intel graphics and are still getting this problem that it would be more likely an ibus problem.

Any how, on this Nvidia Geforce 9800 GT 1GB changing the ibus setting to none fixed my problem **100%**. I cannot attest to any other cards as I only have one system and one card.

---

### Post by ventrical on 2015-01-23
Basically (at this stage of the game) any adapter card that is  'aging' or getting rolled to  llvmpipe is going to present anomalous bugs.  If the iBus fix works , then use it.  I am just stating my own opinion .. I am not challenging macs' bugfix.  I clearly stated  my opinion . I did not declare an assumption.

Regards..

---

### Post by ventrical on 2015-01-23
Here is example with 14.04.1 tester.iso that *was* non llvmpipe and that , as of yesterday install, became llvmpipe (and mouse pointer disappears in gedit when pressing spacebar).

```

*-display:0
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0

```

So it tells me that I have i915 driver yet ...

---

### Post by startas on 2015-01-23
Yet again, my pc is hot new - intel haswell + nvidia maxwell, so it is not about the age of hardware. And this is linux, so i cant be sure which of millions of bugs is causing this thing, but what i know is that i googled about it, and i found a solution for it.

---

### Post by ventrical on 2015-01-23
> **startas said:**
> Yet again, my pc is hot new - intel haswell + nvidia maxwell, so it is not about the age of hardware. And this is linux, so i cant be sure which of millions of bugs is causing this thing, but what i know is that i googled about it, and i found a solution for it.

Have both old and new ..  10 working machines on KVMs. After a while I get to see behaviour of things. I have seen "too new" bugs and "too old" bugs :)

Yes.. millions of bugs :)

Glad you have found fix.

Regards..

---

### Post by Cavsfan on 2015-01-23
Ventrical, I don't even know what llvmpipe is lol! And I'm not denying that it may be an nvidia driver problem. Just saying it is not on my system.

The workaround for the problem is here in this thread. [http://ubuntuforums.org/showthread.php?t=2261278&page=2&p=13211065#post13211065](http://ubuntuforums.org/showthread.php?t=2261278&page=2&p=13211065#post13211065)

Which may have been what you found googling for the solution.

---

### Post by ventrical on 2015-01-23
> **syntaxerror74 said:**
> BINGO!!
I *am* on a NVidia card (older one) and yes, I have the nouveau drivers.
You really know your stuff, my deepest respect.

Finally I know where to look for that nuisant "slow-mo' window resizing" problem.
THANK YOU!

Thanks you .. I wish I had time to actually track the bug down or where the code is.  And now yet another IntelGraphics machine convorted to llvmpipe :)

Regards..

---

### Post by ventrical on 2015-01-23
> **Cavsfan said:**
> Ventrical, I don't even know what llvmpipe is lol! And I'm not denying that it may be an nvidia driver problem. Just saying it is not on my system.

The workaround for the problem is here in this thread. [http://ubuntuforums.org/showthread.php?t=2261278&page=2&p=13211065#post13211065](http://ubuntuforums.org/showthread.php?t=2261278&page=2&p=13211065#post13211065)

Which may have been what you found googling for the solution.


 Thanks .. but my reply was off topical to your thread here.  Not the same bug. I am not looking for solution to gedit problem but I thank mac4man  for his suggested fix. (probably will have to use it). :)

Regards..

---

### Post by syntaxerror74 on 2015-01-23
Let's say, off-topic *by one half.*
As this is a thread specific to Gedit, it was not that OT ;)

Ventrical, the major problem that I can't report "my" issue anywhere is that 3.14 is *NOT* officially ready for any 'Buntus yet! As they'd commonly give you the response "you're using a version beyond the scope of the latest 'Buntu packages, you're on your own".

This is also the reason why I want 3.14 to appear in Ubuntu eventually, so that I might find more people to witness this (rare?) issue.

---

### Post by ventrical on 2015-01-23
> **syntaxerror74 said:**
> Let's say, off-topic *by one half.*
As this is a thread specific to Gedit, it was not that OT ;)

Ventrical, the major problem that I can't report "my" issue anywhere is that 3.14 is *NOT* officially ready for any 'Buntus yet! As they'd commonly give you the response "you're using a version beyond the scope of the latest 'Buntu packages, you're on your own".

This is also the reason why I want 3.14 to appear in Ubuntu eventually, so that I might find more people to witness this (rare?) issue.

Ok .. thanks for clarifiying that.:)

Regards..

---

### Post by Cavsfan on 2015-01-24
I just downloaded and installed the daily ISO which is I guess the alpha2. Before I installed any nvidia drivers or anything I used gedit and it exhibited the same exact disappearsing mouse behavior as before.
I changed that setting from ibus to none and all is fine.

---

