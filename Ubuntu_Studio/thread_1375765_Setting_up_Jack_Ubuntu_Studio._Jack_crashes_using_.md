---
title: "Setting up Jack Ubuntu Studio. Jack crashes using hda intel sound card"
date: 2010-01-08
forum: Ubuntu Studio
---

### Post by parece06 on 2010-01-08
hey everyone, i've searched almost every thread regarding setting up jack and it's still not working. here is a list of my hardware.

description: Notebook
    product: HP Pavilion dv5000 (EZ415UA#ABA)
    vendor: Hewlett-Packard
    version: F.24
    serial: CND6241Q1P
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=0B19EF31-F818-11DA-A1B8-0016D40D23FE
  *-core
       description: Motherboard
       product: 30A8
       vendor: Hewlett-Packard
       physical id: 0
       version: 56.48
       serial: CND6241Q1P
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.24 (09/07/2007)
          size: 99KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U1
          size: 800MHz
          capacity: 1600MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm cpufreq
          configuration: id=0
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0200000-d027ffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:d0300000-d033ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0280000-d02fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d0340000-d0343fff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:44000000-440fffff
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wmaster0
                version: 02
                serial: 00:13:02:53:8c:37
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.108 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:28 memory:44000000-44000fff
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0544000-d05443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:2000(size=4096) memory:d0000000-d00fffff memory:40000000-43ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:08:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:d0004000-d0004fff ioport:2400(size=256) ioport:2800(size=256) memory:40000000-43ffffff(prefetchable) memory:48000000-4bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:08:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:d0007000-d00077ff memory:d0000000-d0003fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:08:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:22 memory:d0005000-d0005fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:08:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:20 memory:d0007800-d00078ff
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:08:08.0
                logical name: eth0
                version: 01
                serial: 00:16:d4:0d:23:fe
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:20 memory:d0006000-d0006fff ioport:2000(size=64)
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4084N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KQ09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:18d0(size=8) ioport:18c4(size=4) ioport:18c8(size=8) ioport:18c0(size=4) ioport:18b0(size=16) memory:d0544400-d05447ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK1246GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LB21
                serial: Y7ISF2ZSS
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c038c038
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: aaac80be-7730-4917-ac4a-46f29622d070
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-06 09:39:32 filesystem=ext4 lastmountpoint=/35&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;S&#65533;x&#1958;&#65533;IZ&#65533;*&#65533;&#65533;*&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533; modified=2010-01-07 11:13:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-07 11:13:08 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2910MiB
                   capacity: 2910MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2910MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)



from what i gather, i'm using an hda intel sound card with i believe a conexant codec. here is the message i get from jack control after hitting the start button.

 p, li { white-space: pre-wrap; }  [COLOR=#999999]09:18:05.839 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]09:18:05.845 Statistics reset.[/COLOR]
 [COLOR=#999999]09:18:05.935 Startup script...[/COLOR]
 [COLOR=#990099]09:18:05.936 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]09:18:05.941 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]09:18:06.338 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]09:18:06.339 JACK is starting...[/COLOR]
 [COLOR=#990099]09:18:06.339 /usr/bin/jackd -R -P70 -t5000 -dalsa -dhw:0 -r48000 -p512 -n3 -i8 -o8[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... hw:0|hw:0|512|3|48000|8|8|nomon|swmeter|-|32bit
 control device hw:0
 [COLOR=#999999]09:18:06.397 JACK was started with PID=28607.[/COLOR]
 [COLOR=#cccc99]09:18:06.542 ALSA connection change.[/COLOR]
 [COLOR=#999999]09:18:07.605 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]09:18:07.606 Post-shutdown script...[/COLOR]
 [COLOR=#990099]09:18:07.607 killall jackd[/COLOR]
 [COLOR=#cc3366]09:18:07.607 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]09:18:08.079 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]09:18:08.646 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


i've tried many different combinations regarding the buffer rate/period, sample rate, etc. so i do not think that would be the problem. i would love to get ubuntu studio working, particularly ardour and audacity but it seems i have to set up jack which has been a real pain. if anyone out there can attempt to help me, any information would be appreciated. i'm new to linux so i do not know all the commands to find out the specs of my machine but if any more info is needed from my end, just let me know how to get it and i will be as quick as i can in responding. thanks

---

### Post by AutoStatic on 2010-01-08
Hello parece06, could you post the output in a terminal of **aplay -l** and **cat /proc/asound/card*/codec* | grep -i codec** ? And did you try different interfaces in QjackCtl?

---

### Post by thorgal on 2010-01-08
are you sure about the number of channels (-i8 and -o8 ) you passed to the jack ALSA backend ?? Try without setting them.

---

### Post by parece06 on 2010-01-09
thanks for the quick replies everyone...autostatic, here is my **-aplay terminal**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and my codec terminal is :

Codec: Conexant CX20551 (Waikiki)

and your question as far as trying different interfaces, i'm assuming you mean using different options like hw, 0, hw, 0,0 , etc. then yes i've tried many different combinations along with many different driver combinations.

thorgal, i tried putting the input and outputs at 0 (comes up as default) to no avail.

just let me know what else i need to do and/or what else you need to know. i will try and log on here at least twice a day. thanks again everyone

---

### Post by AutoStatic on 2010-01-09
Hello parece06, thanks for the output! Is it possible to post a screenshot of **gnome-alsamixer**? It might not be installed yet, if so, you can install it with Synaptic, just search for **gnome-alsamixer**.
And you could try entering *hw:Intel* as the Interface in QjackCtl (just remove *(default)* or *hw:0*), then you're sure you got the right device.

---

### Post by parece06 on 2010-01-10
thanks for the help autostatic. after downloading the gnome alsa mixer, here is a screenshot of it. also, i changed the interface and i'm not sure what exactly it did, however jackcontrol is still failing. i attached a screenshot of my jackcontrol setup as well. sorry for my late response, my birthday was yesterday so i didn't have the chance to get to the computer. again, i appreciate you helping me.

---

### Post by AutoStatic on 2010-01-11
Happy belated birthday :)
Your settings look good, JACK is still crashing? Could you post the outcome of **cat /proc/interrupts** ? And does your soundcard need the 'Force 16bit' option? And did you try setting Periods/Buffer to 2, from my personal experience onboard soundcards work best with this setting. My USB soundcard on the other hand works better with a Periods/Buffer setting of 3. And your mic is muted, maybe unmuting helps? And did you try playing around with the 'Audio' setting in QjackCtl, maybe your soundcard doesn't like Duplex and needs to be set Playback or Capture only. And what if you tick 'Verbose messages' in QjackCtl, could you post the output?

---

### Post by parece06 on 2010-01-11
CPU0       CPU1       
  0:    4271149          0   IO-APIC-edge      timer
  1:       1255          0   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:      18878          0   IO-APIC-fasteoi   acpi
 12:     887002          0   IO-APIC-edge      i8042
 14:     249689          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:      37984          0   IO-APIC-fasteoi   uhci_hcd:usb5, i915
 18:          1          0   IO-APIC-fasteoi   uhci_hcd:usb4, yenta
 19:          3          0   IO-APIC-fasteoi   uhci_hcd:usb3, ohci1394
 20:       8601          0   IO-APIC-fasteoi   eth0, mmc0
 22:      78697          0   IO-APIC-fasteoi   HDA Intel, tifm_7xx1
 23:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 27:      33420          0   PCI-MSI-edge      ahci
 28:     728460          0   PCI-MSI-edge      iwl3945
NMI:          0          0   Non-maskable interrupts
LOC:     701511    2625247   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:     730401     787323   Rescheduling interrupts
CAL:         34         76   Function call interrupts
TLB:       1088       2267   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         58         58   Machine check polls
ERR:          0
MIS:          0




----this is the outcome of the command you had told me to do. also, when i unmuted the alsa mic mixer, jackcontrol started. upon reboot, it doesn't start anymore, even though the alsa mixer still says that my mic is unmuted. I've unticked the force 16 bit option and ticked the verbose message. i've also tried changing the audio mode to duplex, capture, and playback. numerous combinations of ticks and unticks have been tried. can it be that something running in the background is taking priority over alsa or jackcontrol, etc.

---

### Post by AutoStatic on 2010-01-12
Your soundcard shares an IRQ with your cardreader. As long as you don't use the cardreader when working with audio it should be no problem. To completely eliminate the possibility that the cardreader is the bottleneck you could do a **sudo modprobe -r tifm_7xx1** (that will unload the cardreader kernel module) and then start JACK again.
And could you also post the outcome of **uname -a** just to verify the kernel you're using?

---

### Post by parece06 on 2010-01-13
hey audiostatic, just want to thank you for your posts. i gave up and think i might've tweaked the settings too much so i just reinstalled ubuntu and download the ubuntu studio audio packages and now jack is running!! i am not using the real time kernel, i was just wondering if it really is worth the possibility of messing up jack and having to install ubuntu again. also, i've got a wireless usb midi keyboard and i'm having a difficult time getting it to work. i've connected the midi port to my zynadd synth and it just doesnt recognize it. ideally, what i would like to do is use hydrogen and the synth to accept my midi keyboard. i then want those to programs to be connected to either rosegarden or ardour. idk if you are familiar with the software part of ubustudio or not. I seem to have gone through every tutorial to connect my midi through jack and have been unsuccessful.

---

