---
title: "Borked Ubuntu GNOME Vivid images?"
date: 2015-02-12
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-02-12
For a few days I've been trying Ubuntu GNOME, both amd64 and i386, to no avail. If I create a live USB with UnetBootin or create a live DVD it just boots to various kinds of borkage - like what appears to be a partial desktop, but really just gray with a top panel and nothing else - or sometimes the "spalash" dots just stop moving and never resume.

So last night and today I decided to try dd same as have many times before ................ sudo dd if=path/to/image.iso of=/dev/sd#

So (check highlighted parts):

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  116GB  116GB   primary   ext4            boot
 2      116GB   232GB  116GB   primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   375GB  20.4GB  logical   ext4
13      375GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.4GB  logical   ext4
15      415GB   436GB  20.4GB  logical   ext4
16      436GB   456GB  20.4GB  logical   ext4
17      456GB   477GB  20.4GB  logical   ext4
18      477GB   498GB  21.0GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: SMI USB DISK (scsi)
**[COLOR="#FF0000"]Disk /dev/sdb: 3995MB[/COLOR]**
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  3995MB  3994MB  primary  fat32        boot


lance@lance-desktop:~$ **[COLOR="#FF0000"]ls Downloads/Ubuntu_GNOME[/COLOR]**
trusty-desktop-amd64.iso                ubuntu-gnome-14.04.1-desktop-i386.iso
trusty-desktop-amd64.iso.zs-old         vivid-desktop-amd64.iso
trusty-desktop-i386.iso                 vivid-desktop-amd64.iso.zs-old
trusty-desktop-i386.iso.zs-old          vivid-desktop-i386.iso
ubuntu-gnome-14.04.1-desktop-amd64.iso  vivid-desktop-i386.iso.zs-old
lance@lance-desktop:~$ **[COLOR="#FF0000"]sudo dd if=Downloads/Ubuntu_GNOME/vivid-desktop-amd64.iso of=/dev/sdb[/COLOR]**
```

But it takes a long time, several minutes at least to complete and then Parted shows this error:

```
Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                  
```

Have I lost my mind??????????????????

---

### Post by ventrical on 2015-02-13
I got the gnome 'foot' and three dots, then , lockup. No terminal .. nothing.

Regards..

---

### Post by ventrical on 2015-02-13
Tried different USB stick .. still the same. Lock up.

---

### Post by ventrical on 2015-02-13
> 
But it takes a long time, several minutes at least to complete and then Parted shows this error:

```
Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                  
```

Have I lost my mind??????????????????

  I got this same error when I tired to make a partition on <free space> using gparted back a awhile ago.

[http://ubuntuforums.org/showthread.php?t=2259055&page=11&p=13223265#post13223265](http://ubuntuforums.org/showthread.php?t=2259055&page=11&p=13223265#post13223265)

---

### Post by kansasnoob on 2015-02-13
Thanks ventrical. I'll try the actual Ubuntu images sometime today, then Ubuntu GNOME one more time, and if they're still borked I'll try to figure out how to file a bug report.

---

### Post by ventrical on 2015-02-13
> **kansasnoob said:**
> Thanks ventrical. I'll try the actual Ubuntu images sometime today, then Ubuntu GNOME one more time, and if they're still borked I'll try to figure out how to file a bug report.

I was able to get to terminal on my Intel Video graphics box but on nVidia card boxes .. nope.

I'll be looking in.

Regards..

---

### Post by sammiev on 2015-02-13
On my intel I can get into terminal and add systemd-sysv. After that it boots normal as I'm running it in VM and do not have the choice of advance on my grub, until then I could not even log in.

---

### Post by kansasnoob on 2015-02-13
Todays images are working OK - both Ubuntu and Ubuntu GNOME - so maybe it was just temporary borkage :confused:

---

### Post by kansasnoob on 2015-02-13
> **ventrical said:**
> I was able to get to terminal on my Intel Video graphics box but on nVidia card boxes .. nope.

I'll be looking in.

Regards..

Could this be the nVidia problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602)

You could find out by using this boot parameter:

nouveau.config=NvMSI=0

That was actually the reason I wanted to grab a new Vivid iso, to follow up there testing this kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.5-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.5-vivid/)

**EDIT**: I spoke too soon - Ubuntu GNOME Vivid is still borked on this hardware:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Guess I'll revert to installing from the Alpha 2 to perform the aforementioned kernel test - then on to prepping for a grueling two weeks of iso-testing; 14.04.2 next week and Vivid Beta 1 the week after.

---

### Post by ventrical on 2015-02-14
I am hoping to do some added testing but it appears the Polar Vortex could be keeping me really busy:)

Regards..

---

### Post by kansasnoob on 2015-02-15
The Ubuntu GNOME 20150215 amd64 image worked OK on these two boxes:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

---

### Post by ventrical on 2015-02-16
Did one test that was positive so far. Others : mouse was not found.

today's daily:

```

daily live success:


ubuntu-gnome              
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 992MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy vmmcall
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:dc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:deeff000-deefffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:deefec00-deefecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:deef8000-deefbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1d:60:1c:d4:6e
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.46 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:28 memory:deefd000-deefdfff ioport:d480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) memory:deefc000-deefcfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:e000(size=4096) memory:def00000-dfffffff ioport:c0000000(size=503316480)
        *-display
             description: VGA compatible controller
             product: GT218 [GeForce 210]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:27 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ec00(size=128) memory:def80000-deffffff
        *-multimedia
             description: Audio device
             product: High Definition Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:18 memory:def7c000-def7ffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ubuntu-gnome@ubuntu-gnome:~$ 
ubuntu-gnome              
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 992MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy vmmcall
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:dc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:deeff000-deefffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:deefec00-deefecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:deef8000-deefbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1d:60:1c:d4:6e
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.46 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:28 memory:deefd000-deefdfff ioport:d480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) memory:deefc000-deefcfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:e000(size=4096) memory:def00000-dfffffff ioport:c0000000(size=503316480)
        *-display
             description: VGA compatible controller
             product: GT218 [GeForce 210]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:27 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ec00(size=128) memory:def80000-deffffff
        *-multimedia
             description: Audio device
             product: High Definition Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:18 memory:def7c000-def7ffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ubuntu-gnome@ubuntu-gnome:~$ 

```

---

### Post by sudodus on 2015-02-16
It seems the current Vivid daily ISOs are working again. I tested Lubuntu desktop i386, and it works too :-)

---

### Post by sgage on 2015-03-17
> **sudodus said:**
> It seems the current Vivid daily ISOs are working again. I tested Lubuntu desktop i386, and it works too :-)

As of this past Saturday (14 March) I have been unable to boot a daily build of Ubuntu Gnome from USB (or DVD). Symptoms are similar to those reported in the OP. I end up with what looks like a Gnome Shell desktop, but the 'try or install' screen isn't there. The instant I move the mouse, it all goes away to a black screen.

I tried the nouveau.config parameter as had been suggested. I've tried several different USB burning utilities, and even sacrificed a DVD - no joy.

Anyone else having this problem currently? Any workaround (some other boot parameter or such)? I'd like to check out the current state of play...

---

### Post by ventrical on 2015-03-17
About to smoke daily-live....

---

### Post by ventrical on 2015-03-17
it's working fine here on:

```



ubuntu-gnome@ubuntu-gnome:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation B75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
ubuntu-gnome@ubuntu-gnome:~$ 

```

I used this method to burn:

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

---

### Post by sgage on 2015-03-17
Thanks, ventrical, for checking it out.

What flavor of graphics do you have? I'm beginning to think this might be an nvidia issue...

BTW, I tried your burn method, and here's what I got when I booted the stick:

```
isolinux.bin missing or corrupt.
DISK BOOT FAILURE
```

Oh well!

---

### Post by ventrical on 2015-03-17
> **sgage said:**
> Thanks, ventrical, for checking it out.

What flavor of graphics do you have? I'm beginning to think this might be an nvidia issue...

BTW, I tried your burn method, and here's what I got when I booted the stick:

```
isolinux.bin missing or corrupt.
DISK BOOT FAILURE
```

Oh well!

I'm using SandyBridge (intel)

```

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

```


  I'll try nVidia box.

Regards..

---

### Post by ventrical on 2015-03-17
Serious nVidia failure.

ACPI Probe failed:

Although I do have  some working desktop I am getting broken relics and some screen distortion.

```

 *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0

```

Look at ff text titles very closely.

---

### Post by ventrical on 2015-03-17
I tired to file a bug against nouveau-firmware but it cannot find the installed package - so I am assuming it is nouveau/ mabey gnome-desktop, that has bug. I don't know .. but nViida graphics card is  not working normal.

Could be fcitx foo foo keyboard input thingy that is buggy because some of the characters look chinese.

---

### Post by sgage on 2015-03-17
> **ventrical said:**
> Serious nVidia failure.

ACPI Probe failed:

Although I do have  some working desktop I am getting broken relics and some screen distortion.



I figured it was nVidia related. In my case (GeForce 8500 GT) I end up with what looks like a plain Gnome Shell desktop - top panel and the wallpaper - but the instant I move the mouse or touch a key, it all goes away. Last successful build for me was Wednesday, 11 March...

---

