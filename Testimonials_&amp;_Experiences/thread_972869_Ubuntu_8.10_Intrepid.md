---
title: "Ubuntu 8.10 Intrepid"
date: 2008-11-06
forum: Testimonials &amp; Experiences
---

### Post by starcannon on 2008-11-06
Easiest install yet. I keep /home on its own partition allowing me the power of a clean install. The nvidia 177.80 driver on this 6600gt runs perfectly. I will note that some devices are being reported incorrectly(for instance the network is not disabled, indeed i'm using it to create this post right now); how ever, while I see a lot of fuss around the forums, for me it was a point and click dream. I'm fussy about graphics drivers so I manually installed the driver, I should try it at some point with the hardware drivers utility, my guess is its flawless though.
Great job Canonical and the entire Ubuntu team.
Thanks,
Rob

Heres my hardware list:
```

starcannon-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1009MiB
     *-cpu
          product: AMD Athlon(tm) XP 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 2100MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:50:8d:f9:35:e4
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.107 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=12 mingnt=1
        *-multimedia:1
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-storage
                description: RAID bus controller
                product: SiI 3112 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage bus_master cap_list
                configuration: driver=sata_sil latency=32 module=sata_sil
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:c8:22:92:f2:a8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by zengrits on 2008-11-06
Installed Intrepid on Sony Vaio S-260P (Intel Centrino). Works flawlessly and the installation progressed without a hitch. Dual booting with Windows XP.

My first install of Intrepid on an old Sotec 3120 (Celeron 1.2 processor) was also a breeze with everything working.

I'm able to watch movies and TV shows on Hulu on both laptops - something I was unable to do with other distros.

Installed Skype (not a part of the distro but available) on both computers. Audio has been a problem using some distros, but sound is great on the Sotec, a computer I had always considered Linux unfriendly. Haven't had time to test Skype on the Sony.

---

