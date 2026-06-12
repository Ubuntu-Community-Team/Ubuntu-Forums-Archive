---
title: "help setting up a Compro Videomate C100 video capture card"
date: 2012-08-03
forum: Ubuntu Studio
---

### Post by abduljones on 2012-08-03
Been having real trouble getting this card to work. It totally screwed up my Windows os, to the point that a re install was the easiest option. So there I was, with a clean, empty hard drive and I thought- it can wait. Let's try Ubuntu. Three days I've been at it. I couldn't get a workable 12.04 onto the machine until yesterday and then I got so confused with what I had or hadn't loaded, I decided to start again- this time with studio. This is what I've got per lshw
 tracey@tracey-desktop:~$ lshw
WARNING: you should run this program as super-user.
tracey-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1508MiB
     *-cpu
          product: AMD Sempron(tm) Processor 3000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: 15.12.2
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KiB
     *-pci:0
          description: Host bridge
          product: 755 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:a0000000-bfffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:d4000000-d6ffffff memory:c0000000-cfffffff
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:5 memory:d4000000-d4ffffff memory:c0000000-cfffffff memory:d5000000-d5ffffff memory:d6000000-d601ffff
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRAM GSA-H42N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: RL01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD writer
                product: CD/DVDW TS-H552B
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr1
                version: TS04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:5 memory:d7222000-d7222fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:10 memory:d7223000-d7223fff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:11 memory:d7224000-d7224fff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:9 memory:d7220000-d7220fff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:14:2a:ff:56:76
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
             resources: irq:10 ioport:e000(size=256) memory:d7221000-d7221fff memory:60000000-6001ffff
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=32
             resources: irq:11 ioport:e100(size=8) ioport:e200(size=4) ioport:e300(size=8) ioport:e400(size=4) ioport:e500(size=16)
        *-multimedia:0
             description: Multimedia audio controller
             product: SB X-Fi
             vendor: Creative Labs
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_ctxfi latency=32 maxlatency=5 mingnt=4
             resources: irq:3 ioport:e600(size=32) memory:d7000000-d71fffff memory:d0000000-d3ffffff
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth1
             version: 10
             serial: 00:40:f4:17:28:03
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=32 maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:11 ioport:e700(size=256) memory:d7225000-d72250ff
        *-multimedia:1
             description: Multimedia controller
             product: SAA7134/SAA7135HL Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84
             resources: irq:5 memory:d7226000-d72263ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3


          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
tracey@tracey-desktop:~$ 


 Then v4l2-ctl -I

Video input : 0 (Television: no hsync lock., no sync lock)

Then v4l2-ctl -n


Video input : 0 (Television: no hsync lock., no sync lock)
tracey@tracey-desktop:~$ v4l2-ctl -n
ioctl: VIDIOC_ENUMINPUT
	Input       : 0
	Name        : Television
	Type        : 0x00000001
	Audioset    : 0x00000001
	Tuner       : 0x00000000
	Standard    : 0x0000000000FFBFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
	Status      : 0x00010100 (no hsync lock., no sync lock)
	Capabilities: 0x00000004 (SD presets)

	Input       : 1
	Name        : Composite1
	Type        : 0x00000002
	Audioset    : 0x00000001
	Tuner       : 0x00000000
	Standard    : 0x0000000000FFBFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
	Status      : 0x00000000 (ok)
	Capabilities: 0x00000004 (SD presets)

	Input       : 2
	Name        : S-Video
	Type        : 0x00000002
	Audioset    : 0x00000001
	Tuner       : 0x00000000
	Standard    : 0x0000000000FFBFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
	Status      : 0x00000000 (ok)
	Capabilities: 0x00000004 (SD presets)
tracey@tracey-desktop:~$ 

  
  All I've done otherwise is:
                            downloaded and installed Opera
                                    ditto           VLC
                                    ditto           v4l2 utilities

  I also tried
 
 tracey@tracey-desktop:~$ mplayer -vf pp=lb /dev/video
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video.
File not found: '/dev/video'
Failed to open /dev/video.


Exiting... (End of file)

   I downloaded VLC because I needed something to capture video, but all the combinations of options it gives me play nothing. It doesn't crash, however, which is a big improvement onthe previous Unbuntu.
  I would greatly appreciate your help in getting the card working as it's the only thing I can't do that i used to do on Windows (different VCD). Also, apologies for all the info, but I'm not sure what's important

---

### Post by abduljones on 2012-09-27
Right guys, a belated update. Sorry to be so long, but I haven't had the time to throw at this.
  I loaded windows xp on to the computer (so it is now dual boot) mainly to use the provided windows drivers and check that the card was actually working. it took a little fiddling, but I got it working in windows. I then went back to ubuntu, and I did get it working there, albeit briefly, but the settings weren't saved when I shut down, and now I can't replicate what I did. So it looks like it might work in Ubuntu- it's a matter of getting the settings right. I will have another go when I get a decent block of time to throw at it and report back

---

