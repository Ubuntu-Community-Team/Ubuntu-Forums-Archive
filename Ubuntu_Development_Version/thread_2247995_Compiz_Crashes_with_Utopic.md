---
title: "Compiz Crashes with Utopic"
date: 2014-10-11
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2014-10-11
Updated 3.16.0-21 to -22, booted, Compiz crashed, recovered, reported launchpad Bug 1380177.  
There must be a flock of compiz bugs recently!

So far I've gotten compiz crashes on all four of my pc's, this 
Acer 5253 wide screen notebook, 
Lenovo M58p desktop, 
Acer Aspire 1 netbook. all with amd64 ubuntu utopic.  Even my 
Compaq Presario Pentium D 3.33 gHz 32 bit got a compiz failure a couple days ago.

BTW, also get failures with kernel 3.17.

Intrepid up thru July 31 no such trouble.  Grief of varying degrees since.

This is:

```
Linux Acer5253 3.16.0-22-generic #29-Ubuntu SMP Thu Oct 9 16:26:18 UTC 2014 
x86_64 x86_64 x86_64 GNU/Linux
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] 
Wrestler [Radeon HD 6310]
model name	: AMD E-350 Processor
model name	: AMD E-350 Processor

ProblemType: Crash
DistroRelease: Ubuntu 14.10
Package: compiz-core 1:0.9.12+14.10.20140918-0ubuntu1
ProcVersionSignature: Ubuntu 3.16.0-22.29-generic 3.16.4
Uname: Linux 3.16.0-22-generic x86_64
.tmp.unity.support.test.0:
 
ApportVersion: 2.14.7-0ubuntu5
Architecture: amd64
CompizPlugins: No value set for `/apps/compiz-1/general/screen0/options/active_plugins'
CompositorRunning: compiz
CompositorUnredirectDriverBlacklist: '(nouveau|Intel).*Mesa 8.0'
CompositorUnredirectFSW: true
CrashCounter: 1
CurrentDesktop: Unity
Date: Sat Oct 11 16:52:53 2014
Disassembly: => 0x0:	Cannot access memory at address 0x0
DistUpgraded: Fresh install
DistroCodename: utopic
DistroVariant: ubuntu
ExecutablePath: /usr/bin/compiz
GraphicsCard:
 Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310] [1002:9802] 
(prog-if 00 [VGA controller])
   Subsystem: Acer Incorporated [ALI] Device [1025:0520]
InstallationDate: Installed on 2014-10-06 (4 days ago)
InstallationMedia: Ubuntu 14.10 "Utopic Unicorn" - Alpha amd64 (20141006)
MachineType: Acer Aspire 5253
```

Anyone have a clue about why Compiz is trying to access 0x0?  Looks like a very peculiar location.

Thanks.

BTW, as expected, I've tried Intrepid Gnome 3.12, Mate, Lubuntu none of them had trouble the brief time I ran them.  I don't think they use Compiz.
Also tried Intrepid Ubuntu Next.  No crashes, but treats a wide screen monitor with mouse as a narrow touch screen phone. Not for me.

---

### Post by Doug S on 2014-10-11
Jerry: compiz has been O.K. for me on utopic. However I don't actually do much on the 14.10 desktop.

Also kernel 3.17 has been good for me, but I only run it on a 14.04 server computer.

---

### Post by jerrylamos on 2014-10-13
Well, Intel Core 2 Duo desktop just got a compiz crash after today's 13 October upbated.
5 hours ago my AMD/ATI wide screen notebook got the same crash.

Two pc's different manufacturer's hardware, same crash, and RC is coming up in a few days?

BTW, chromium browser also crashing, different problem.

---

### Post by jerrylamos on 2014-10-14
So far 67 people signed up as "affecting me"
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1366351](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1366351)

No significant comments from the launchpad debug crew yet.

---

### Post by ventrical on 2014-10-14
I'm not sure that this is related but what is happening here with Intel Graphics is that after an update or so the driver jockey will eventually choose a video graphic driver that is llvmpipe!! I did an experiment yesterday. I switched the harddrive  to an exact same machine and it came up with the correct driver . Then also used another hardrive from another machine and installed it on suspect machine and Unity driver came up. No llvmpipe. Very frustrating bug.

 I have two ATi (AMD) graphics still to be updated.

Regards..

---

### Post by ventrical on 2014-10-14
*I  zsynced the daily utopic-desktop-amd64 and installed it on my Acer Extensa 4420 with AMD64 Athlon2x and Radeon Xpress 1250 with Broadcomm Wirless. This lappy old by most standards. A miracle occured:)  It correctly installed the bcwmkernel from Other Software and also installed a non-llvmpipe graphics driver for the old radeon. Results. Unity 3D with compiz. A little slow to boot but looks like they got some radeon driver problems worked out. Thats good news for old broadcomm hardware and ATi Hardware.*

```


ventrical-extensa-4420    
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 2755MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
          vendor: Advanced Micro Devices [AMD]
          physical id: 2
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:f0000000-f01fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon Xpress 1200/1250/1270]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:43 memory:d0000000-dfffffff memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:1f:e1:36:a1:a4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.2.10 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:f0200000-f0203fff
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:c4000000-c41fffff ioport:c4200000(size=2097152)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f0609000-f06093ff
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:f0404000-f0404fff
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:f0405000-f0405fff
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f0406000-f0406fff
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:f0407000-f0407fff
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f0408000-f0408fff
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:f0609400-f06094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f0400000-f0403fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:3000(size=4096) memory:f0300000-f03fffff memory:c0000000-c3ffffff
           *-pcmcia
                description: CardBus bridge
                product: OZ711SP1 Memory CardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 6
                bus info: pci@0000:0b:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:20 memory:f0300000-f0300fff ioport:3000(size=256) ioport:3400(size=256) memory:c0000000-c3ffffff memory:c8000000-cbffffff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.2
                bus info: pci@0000:0b:06.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:20 memory:f0303800-f03038ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.3
                bus info: pci@0000:0b:06.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage cap_list
                configuration: latency=64
                resources: memory:f0301000-f0301fff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 6.4
                bus info: pci@0000:0b:06.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:20 memory:f0302000-f0302fff memory:f0303000-f03037ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-network
          description: Ethernet interface
          product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 0
          bus info: pci@0000:0c:00.0
          logical name: eth0
          version: 10
          serial: 00:40:b9:df:e7:00
          size: 100Mbit/s
          capacity: 100Mbit/s
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.30 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
          resources: irq:20 ioport:3000(size=256) memory:c8000000-c80001ff
     *-scsi
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM GD-S200
             vendor: HITACHI
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 0020
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ventrical@ventrical-Extensa-4420:~$ 

```

however, there is always the chance during an update that it could get bumped back to llvmpipe .. but so far , so good.

Regards..

---

### Post by Cavsfan on 2014-10-14
Not encountering any such issues with compiz on an older Nvidia GeForce 9800GT card.
It hasn't crashed even once.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                            331.89-0ubuntu5                            amd64        NVIDIA binary driver - version 331.89
ii  nvidia-331-uvm                                        331.89-0ubuntu5                            amd64        NVIDIA Unified Memory kernel module
ii  nvidia-libopencl1-331                                 331.89-0ubuntu5                            amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.89-0ubuntu5                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.7                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                            amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by jerrylamos on 2014-10-15
Indications in launchpad there could be a bug in unity settings.

> Martin Pitt (pitti) wrote on 2014-10-14: 	#62

I'm being haunted by this for two days now, since I use my laptop's internal display (conference). This never happens at home with the external monitor. It crashes every few minutes and is unbearable; I found that disabling multiple workspaces helps a lot to calm it down.
My current experience:
>  Whoopsie, got another crash after the update in comment #14 in bug # 1380278 which on the surface looks like comment #12 in Bug # 1380278 ......

So whatever may be in:

"This bug was fixed in the package unity-settings-daemon - 14.04.0+14.10.20141014-0ubuntu1"

after shutdown, boot I still got another crash....
I'm up to date as of 15 October with the unity-settings-daemon update but still getting crashes.

---

### Post by mc4man on 2014-10-15
There is a proposed fix (needs to get by jenkins) so no real use for any more comments in bug report(s) 
Better to just wait & see what it brings when it shows up..

---

### Post by jerrylamos on 2014-10-15
O.K., I'll keep quiet.  
As usual ubuntu practice, we are not told when a fix is available in daily build.
Therefore we won't know if the failures we get are after the fix is applied.

---

### Post by mc4man on 2014-10-15
> **jerrylamos said:**
> O.K., I'll keep quiet.  
As usual ubuntu practice, we are not told when a fix is available in daily build.
Therefore we won't know if the failures we get are after the fix is applied.

The 'fix' is not yet available, when the bug says fix-released then it will.
You can also glance at the top of many reports & look for a "Related branches" section. If there it can provide some add. info as to current state - screen

---

### Post by zika on 2014-10-16
> **jerrylamos said:**
> As usual ubuntu practice, we are not told when a fix is available in daily build.
Therefore we won't know if the failures we get are after the fix is applied.You are told if You ask to be told.

---

