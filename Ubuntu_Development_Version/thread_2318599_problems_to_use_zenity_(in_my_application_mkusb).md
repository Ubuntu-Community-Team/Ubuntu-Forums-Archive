---
title: "problems to use zenity (in my application mkusb)"
date: 2016-03-27
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-03-27
I was testing/using my application program mkusb in Lubuntu Xenial i386, when I started to get problems.

After today's update/dist-upgrade ***zenity windows are flaky***. Sometimes they are empty, and the next attempt they work again. Finally I rebooted, and then I was prompted to write this bug report: [Bug #1562607, 'problems to use zenity (in my application mkusb) - after update/dist-upgrade'](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/1562607)

I made a second update/dist-upgrade before trying to run mkusb again - but the bug is still alive.

Please check if the bug affects you too in a current version of Xenial i386 daily (for example when you try to run mkusb). and mark 'affects me too' if it does!

**Edit:** It seems to be a problem with **webkit2gtk-4.0**

---

### Post by sudodus on 2016-03-27
I installed mkusb into a clean current Lubuntu Xenial i386 live system. It seems to work well - also the zenity windows. The differences compared my installed system are

**- live versus installed**
- free versus nvidia proprietary driver (version 304.131)
- clean versus contains several packages and settings (also from older daily files)

I suspect that webkit and the nvidia proprietary driver have problems to cooperate, but I am far from sure.

---

### Post by sudodus on 2016-03-27
I removed the nvidia 304.131 driver from my installed system. After rebooting I'm prompted for a new bug directly at log in. It seems to affect xorg-server, but the free desktop graphics driver (nouveau) seems to work with my nvidia Geforce GT 430 card.

I tried mkusb twice (making persistent live drives) and ***the zenity windows worked*** without any glitch. It is too early to be sure, but it indicates that there are problems with the nvidia graphics. I hope it will be fixed before 16.04 LTS will be released.

---

### Post by sudodus on 2016-03-28
Yesterday I added a feature to [mkusb: to select either GPT or MSDOS partition table for persistent live drives](http://ubuntuforums.org/showthread.php?t=1958073&page=18&p=13461879#post13461879). The reason is that several HP computers seem to need an MSDOS partition table to boot from a USB drive.

If you have an HP computer, please test if you can boot it from a persistent live drive made with mkusb 10.6 :-)

-o-

Today I have tested a lot using zenity via mkusb in Xenial. It seems to work well with the free driver and my nvidia card.

---

### Post by ventrical on 2016-03-28
> **sudodus said:**
> I installed mkusb into a clean current Lubuntu Xenial i386 live system. 

whoops :) ok.. I didn't see the otherpart (installed) right away ;)

regards..

---

### Post by sudodus on 2016-03-29
> **ventrical said:**
> whoops :) ok.. I didn't see the otherpart (installed) right away ;)

regards..

There are two issues:

1 - my problem with the graphics: I think I know what is happening now, the current versions of the nvidia proprietary driver does not play well with webkit (which is used by zenity).

2 - the added feature of mkusb 10.6: persistent live drives can be created with a partition table, that can be managed by some HP computers, that fail to boot from USB with GPT). It was when developing mkusb 10.6 in an installed Xenial system, that I discovered the problem with the graphics.

If you have an HP computer and time enough for testing, please try if your HP computer can boot from such a persistent live drive, and tell me if it works :-P

It is also worthwhile to test mkusb again in Xenial - test how it copes with the new versions of the program packages related to graphics. I found this problem with nvidia, but I have no system with AMD/ATI/Radeon graphics and a proprietary driver. That might also create problems.

---

### Post by ventrical on 2016-03-29
> **sudodus said:**
>  I found this problem with nvidia, but I have no system with AMD/ATI/Radeon graphics and a proprietary driver. That might also create problems.

The AMD/ATI HD 5450 Silent that I have is useless in Unity on 16.04 and a few other flavours. My HP dual core has nVidia onboard graphics. I'll have to look see.

regards.

---

### Post by ventrical on 2016-03-29
> **sudodus said:**
> There are two issues:


If you have an HP computer and time enough for testing, please try if your HP computer can boot from such a persistent live drive, and tell me if it works :-P


I was able to boot from two different usb drives on the machine specs detailed below.

I used one of the persistent drives I built with mkusb (trusty-mythubuntu) which worked well (not able to download from SC - reports no conection - but *is* connected). Will not deal with this bug here.

2nd. Did an install of Ubuntu Mate from a standard USB drive created with mkusb on this machine:

```

ventrical@ventrical-RK574AA-ABA-a1730n:~$ inxi -b
System:    Host: ventrical-RK574AA-ABA-a1730n Kernel: 4.2.0-19-generic i686 (32 bit)
           Desktop: MATE 1.10.2  Distro: Ubuntu 16.04 xenial
Machine:   System: HP-Pavilion product: RK574AA-ABA a1730n
           Mobo: ASUSTek model: NODUSM3 v: 1.05
           Bios: Phoenix v: 5.04 date: 12/15/2006
CPU:       Dual core AMD Athlon 64 X2 5000+ (-MCP-) speed/max: 2000/2600 MHz
Graphics:  Card: NVIDIA C51 [GeForce 6150 LE]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NV4E GLX Version: 2.1 Mesa 11.0.5
Network:   Card: NVIDIA MCP51 Ethernet Controller driver: forcedeth
Drives:    HDD Total Size: 320.1GB (2.0% used)
Info:      Processes: 154 Uptime: 9 min Memory: 401.5/1885.5MB
           Client: Shell (bash) inxi: 2.2.28 
ventrical@ventrical-RK574AA-ABA-a1730n:~$ 



```

I am very surprised that compiz works  on this older nVidia.

regards..

---

### Post by sudodus on 2016-03-29
Looks good :-)

'2nd. Did an install of Ubuntu Mate from a standard USB drive created with mkusb on this machine'

*Does it mean a cloned 'live-only' system or is there a persistent-live system on that USB drive?*

I think the problem would be with a persistent-live system - that many HP computers do not want to boot them via grub and mkusb makes persistent-live systems that boot via grub. If you select an MSDOS partition table it is more likely to boot (at least in BIOS mode).

---

### Post by ventrical on 2016-03-29
> **sudodus said:**
> Looks good :-)

'2nd. Did an install of Ubuntu Mate from a standard USB drive created with mkusb on this machine'

*Does it mean a cloned 'live-only' system or is there a persistent-live system on that USB drive?*

I think the problem would be with a persistent-live system - that many HP computers do not want to boot them via grub and mkusb makes persistent-live systems that boot via grub. If you select an MSDOS partition table it is more likely to boot (at least in BIOS mode).

As I said , it worked ok with persistence on another usb created with mkusb.

2nd. Yes.. that was a 'live only' usb stick made with mkusb.

I am about to make a usb with Lubuntu 16.04 amd64 daily.iso with updated mkusb persietnce and live only and then try an install on HP box.

regards..

---

### Post by ventrical on 2016-03-29
1st result:

Lubuntu 16.04 daily created with mkusb  "live usb" booted no problem. There was some verbose script but nothing to do with mkusb.

Next; Building persistent drive with mkusb.

---

### Post by ventrical on 2016-03-29
2nd.  Now persistent drive test.  Just unbelievable! You did it !!  Some of the new options in mkusb  are foreign at first .. but they do work. This is persistent mode in ISO mode on HP 64bit system which is a little older.

```

lubuntu@lubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
lubuntu@lubuntu:~$ uname -a
Linux lubuntu 4.4.0-15-generic #31-Ubuntu SMP Fri Mar 18 19:08:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
lubuntu@lubuntu:~$ lshw
WARNING: you should run this program as super-user.
lubuntu                   
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 1873MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: NVIDIA Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: NVIDIA Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: NVIDIA Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: NVIDIA Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: NVIDIA Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:b000(size=4096) memory:fde00000-fdefffff ioport:fdb00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff memory:fb000000-fbffffff memory:80000000-8001ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: NVIDIA Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:23 ioport:4c00(size=64) ioport:4c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323 [TrueFire] 1394a Controller
             vendor: LSI Corporation
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fddff000-fddfffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:03:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:fdde0000-fddeffff ioport:ac00(size=8)
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: enp0s20
          version: a3
          serial: 00:1a:92:25:45:b1
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.11 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:21 memory:fe02b000-fe02bfff ioport:c800(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
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
  *-scsi:0
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
lubuntu@lubuntu:~$ 

```

---

### Post by sudodus on 2016-03-29
Thanks a lot for testing :-)

It is very important to get mkusb tested by new people and with new hardware.

---

