---
title: "studio 11.10 and xruns"
date: 2011-12-07
forum: Ubuntu Studio
---

### Post by mjhouska on 2011-12-07
Hi, I have a new system i built with a Biostar A780L3G main board. And a fresh install with all packages selected and that audio priority option selected. my processor is a :
AMD Phenom II x2 560 and i have 4GB dual channel ram.

I also installed the nonfree codecs from mediubuntu(this after i tested jack.

Iran Jack in it's default config after completing install and updates 
and go frequent xruns

How do i stop this? please walk me through as a lot of the "how to
 sites give confusing(install synaptic in 11.4? why? it's there by
 default!) or conflicting information or perhaps outdated.

other than that it is a fresh install(64 bit) with the non-free codecs
and i am logged on with a smile on my face. :)  please help.

---

### Post by mjhouska on 2011-12-07
here is my lshw dump. i had to install emacs since the notes app cant import text files.

batcave
    description: Desktop Computer
    product: A780L3G (To Be Filled By O.E.M.)
    vendor: BIOSTAR Group
    serial: None
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A780L3G
       vendor: BIOSTAR Group
       physical id: 0
       serial: None
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014
          date: 04/21/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X2 560 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X2 560 Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 3300MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe900000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: 760G [Radeon 3000]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:feaf0000-feafffff memory:fe900000-fe9fffff
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:feae8000-feaebfff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 00:30:67:b4:bb:bb
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.167.1.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:41 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe8ff800-fe8ffbff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK2555GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: FG00
                serial: 798IS33JS
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003eb23
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 45e8518d-0a0c-44d4-bf9d-39aa8e9efac8
                   size: 229GiB
                   capacity: 229GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-04 15:02:44 filesystem=ext4 lastmountpoint=/ modified=2011-12-04 15:54:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-07 01:41:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 3837MiB
                   capacity: 3837MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3837MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-222AB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fe000-fe8fefff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fd000-fe8fdfff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe8ff000-fe8ff0ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fc000-fe8fcfff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8f7000-fe8f7fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe8f6800-fe8f68ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
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
             resources: irq:16 memory:fe8f0000-fe8f3fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
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
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8f5000-fe8f5fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by mjhouska on 2011-12-07
also how do i control frequency scaling in this xfce?

---

### Post by mjhouska on 2011-12-07
I'm thinking of going  to 10.04 but i like adventure and learning. and this hardware is a step up from my old laptop. and i am determined to get the most out of this hd audio chipset. right now i'm using standard stereo speakers and plan on getting a  Makie onyx Blackjack for mic an guitar input.

---

### Post by mjhouska on 2011-12-07
P.S. I went with an ATI gpu on the mainboard because an article i read about the X replacement(i forget it's name) that canonical is working on will get the best support from ATI.

---

### Post by Totalchaos on 2011-12-07
here is two quick suggestions:
1. Replace Jack2 with Jack1
2. Replace the 64bit system with a 32bit one. I really can't see any advantages of 64bit in audio production systems

try it and than share your observations ;)

ps: if you try studio 10.04 32bit you will hit both of my suggestions. Consider using a realtime kernel

---

### Post by mjhouska on 2011-12-07
I will do that tomorrow. thanks

---

### Post by mjhouska on 2011-12-08
I installed 11.10 32 bit and went into synaptic  and selected jackd1 which marked jackd2 for removal as well. sill gettin xruns in default config 
(qjackctl)

---

### Post by mjhouska on 2011-12-08
should i try rt kernel in this 11.04? and is that possible?

---

### Post by mjhouska on 2011-12-08
To be honest , I like the Gnome interface much much better. i think they are just being silly and retarded and should just settle for bugfixing gnome 2.

---

### Post by mjhouska on 2011-12-08
I understand the need for a tablet interface but they should fork that into a tablet distro.
[rant off].

---

### Post by mjhouska on 2011-12-08
Ok! I added the Borgani ppa and through synaptic i installed 3.0.0-13-lowlatency kernel.
i've run jack and... No XRuns! and it's been running 5 minutes now. :P

now i need help to tweak it as it is still at default config.

---

### Post by mjhouska on 2011-12-08
whoops now  i have one xrun so far

---

### Post by mjhouska on 2011-12-08
p, li { white-space: pre-wrap; }  jackd 0.121.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]14:30:20.887 JACK was started with PID=1914.[/COLOR]
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#9999cc]14:30:22.924 JACK connection change.[/COLOR]
 [COLOR=#999933]14:30:22.945 Server configuration saved to "/home/michael/.jackdrc".[/COLOR]
 [COLOR=#999999]14:30:22.947 Statistics reset.[/COLOR]
 [COLOR=#999999]14:30:23.312 Client activated.[/COLOR]
 [COLOR=#996633]14:30:23.319 Buffer size change (1024).[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.037 msecs[/COLOR]
 [COLOR=#cc66cc]14:38:29.924 XRUN callback (1).[/COLOR]
 [COLOR=#cc66cc]14:42:49.323 XRUN callback (2).[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.039 msecs[/COLOR]

---

### Post by sgx on 2011-12-08
> **mjhouska said:**
> whoops now  i have one xrun so far
Is it audible?
During recording or playback, or during idle?

Glad things are working out so far!

I ignore inaudible xruns, as long as there are no other major problems
at the same time, that may be inducing them. I have made some recordings
nearly maxing out the system, with occasional audible pops,
which never were on the recorded music, when I went to edit them out.

---

### Post by mjhouska on 2011-12-08
i havent tried recording anything. i'll try a mic

---

### Post by mjhouska on 2011-12-08
no pops yet after recording in Ardour. looks like i get to play now! thanks:)

---

### Post by noisemaker? on 2011-12-09
> **mjhouska said:**
> whoops now  i have one xrun so far


you will always get Xruns.. you will need to get used to it... it is normal to get some Xrun if you open another application for example or if you change routing with jackd... 

if you use firewire, have a look here

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

forget that stuff with 128 Samples and so on.. i have been using jackd for many years with diffrent interface diffrent pc and all kinds of distrubutions... use 1024 Samples it has higher latency but less xruns.. i use also 1024 Samples buffer under Windows. low latency is a fake.. everybody is talking about it, but nobody has it... the only way to get low latency is to use a pci interface RME.. this is the truth, everybody who says something different is lying... i have used soooo many diffrent systems and they all have the same problem...

So don't worry to much about Xrun and don't worry about using higher latency with 1024 Samples buffer.. I get mostly bout 3 to 5 Xruns a day... I have payed 60 &#8364; for Firewirecard with the best Texas Instruments you can get...

I just start renoise which uses jackd in background... so i dont see the xruns anymore.. if you open jackd you tend to look at Xruns. Most of Xruns you don't even hear, they just ppear if you open an other programs or even tough if the screen saver comes on. disable ny power managment stuff nd also disable the network connection, this also prevents from some xruns with harsh noise

---

### Post by jejeman on 2011-12-09
> **noisemaker? said:**
> 
forget that stuff with 128 Samples and so on.. i have been using jackd for many years with diffrent interface diffrent pc and all kinds of distrubutions... use 1024 Samples it has higher latency but less xruns.. i use also 1024 Samples buffer under Windows. low latency is a fake.. everybody is talking about it, but nobody has it... the only way to get low latency is to use a pci interface RME.. this is the truth, everybody who says something different is lying... i have used soooo many diffrent systems and they all have the same problem...
I use regullary 128 samples, and it gives ~5ms latency, with no xruns. (when I say no, I don't count the ones when applications starts etc.)
Also, here you can see my settings for firewire device [http://ubuntuforums.org/showpost.php?p=10649025&postcount=18](http://ubuntuforums.org/showpost.php?p=10649025&postcount=18)
Songs I make are simple, so mybe thats why I don't have trouble with so low samples. Personally I think, all latencys up to 10ms are okay. If one can't achive them, one should use the lowest one can get.

---

### Post by noisemaker? on 2011-12-12
> **jejeman said:**
> I use regullary 128 samples, and it gives ~5ms latency, with no xruns. 


muaaaaaaaaaahahaha you joker

as mentioned i got the modt expensive firewirecard i could find... it says on the box especially recommended for professional studio ussage and recommended by rme and some other companies... texas instruments of courese.. wel i have that crapy focusrite saffire pro.. but i git it because ffado device supportlist says, this one has full support...

when i put 128 buffer, it drops xruns like i cant even count so fast...

and i have tried this with diffrent systems, desktop as well as laptop and diffrent interface and diffrent firewirecards allways exacty the same behaiver.. 1024 is good, maybe 512 ot most if you like 2 o3 xruns, but dont even try 128.. This is not even a matter of windows or linux, the only way you can get realy low latency is to use RME HDSP 9652 or the old 9652. Those RME PCI Cards where the only Cards which i have seen, which trully run at low latency without crackles in audio

---

### Post by jejeman on 2011-12-12
> **noisemaker? said:**
> muaaaaaaaaaahahaha you jokerWell, if qjakctl and jack lies to me, then I'm lieing to you.

I can confirm that on 3 machines I use <=128 samples without any trouble. ubuntu studio 10.04.

---

### Post by trulan on 2011-12-14
While it is true that you will get the occasional xrun while opening or closing applications, a properly configured system with a good soundcard (this includes supported firewire devices) should be able to run at 128 or even 64 frames/period.  On my hardware, (PreSonus Firepod, onboard Ricoh firewire chip), buffering settings of 64x3, 44.1kHz gives a round trip latency of just under 10ms.   (measured using jack_iodelay)  I can't do a lot of effects processing at these settings, but it works great for overdubbing and for simple live signal processing.

That being said, in actual real-world use there are very few situations where latency that low is any advantage at all.  Most times, the effort people put into system configuration to get super-low latency would be better spent just making music.  But it is fun to see just how far the system can be pushed. ;)

---

### Post by sgx on 2011-12-15
> **noisemaker? said:**
> 
Those RME PCI Cards where the only Cards which i have seen, which trully run at low latency without crackles in audio
maudio pci cards share those abilities. :D

---

### Post by marbangnes on 2011-12-18
Thank you for the this information it helped me to. :-)

---

