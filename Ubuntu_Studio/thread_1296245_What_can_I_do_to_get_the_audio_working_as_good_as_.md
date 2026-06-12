---
title: "What can I do to get the audio working as good as in winXP???"
date: 2009-10-20
forum: Ubuntu Studio
---

### Post by eeter on 2009-10-20
For long time I have been attempting to switch from WinXP to Ubuntu, but for my frustration there has been one big obstacle which I'm unable to defeat. 
I'm producing electronic music on a not very high-end machine and I need the system to be fast. To be honest I'd really be happy if Ubuntu cold be as fast as WindowsXP on my machine. I have done all of those common audio-workstation setup procedures I found in forums and HowTo's, but it still feels like something major is missing or Ubuntu isn't made for being fast. 
One example: running one of my tracks in Ubuntu loads the CPU over 90% at the point where in WinXP it's around 30%. In XP the highest CPU peak was around 50%.

I really hope someone could explain me how to get Ubuntu working on my side if it's possible at all.

---

### Post by sgosnell on 2009-10-20
What app are you using for the editing?  It's probably not an OS problem, but an application problem.  There are several audio editors available.

---

### Post by eeter on 2009-10-20
I'm using Renoise 2.1.0 for linux platform.

---

### Post by sgosnell on 2009-10-20
I'm not familiar with that one.  Have you tried other packages?  Audacity is an excellent audio editor, but I don't know exactly what you're trying to do, so I don't know if it does what you want.

---

### Post by eeter on 2009-10-20
Yes, I have tried other packages also, but what I want is not just an audio editor as I'm more oriented to sound design and modular processing side of music production. Sorry but Audacity is really like a very simple program for recording, but nothing much more... And I think it runs without any problems.
I don't really believe that it's a application problem, because Renoise have been serving me well under Windows. 
But for curiosity I will make a little comparison experiment with some other software also.

---

### Post by sgosnell on 2009-10-20
It's not unusual for apps ported between OSs to run differently on one or the other.  Normally, though, things run faster under Linux than Windows.  Good luck in your search, I don't use the software so I can't be of much more help, I'm afraid.

---

### Post by sgx on 2009-10-20
Hi, for multi-track recording using windows vst plugins, your best alternatives are to use wine and wineasio, with Reaper, EnergyXT, or Cantabile as DAW/vst host, and soundcards/graphics that work.
 There are sporadic reports from people using other software, versions of FL Studio, Usine, Bidule, etc but I cannot confirm those to be usable for basic multi-track recording/editing, nor have I seen credible evidence in google to support further searches.
Reaper is fast and stable in my linux setup.

I use audacity and the ladspa fx, for basic audio editing and format conversions. Ardour has packaging issues in many linux settings, to be
expected, as it is under constant developement, so
compiled versions of ardour and all its dependancies might help.

LMMS package crashes too much, but like ardour, using compiled versions of everything involved likely would help stability.

Hydrogen, Rakarrack, linuxsampler, and zynaddsubfx make a powerful
linux-only core for creating new music of professional quality. (The GSCW drumkits for Hydrogen are worth the large size) Using these  apps with the
Rosegarden sequencer might be an excellent choice if they are all stable
when used at the same time. Qtractor is a new sequencer I have not yet used, though I have it installed, and started it.

The good news is that Reaper output can be routed to linux destinations using qjackctl, so a powerful vst setup can be used as a massive rompler, feeding amazing sound to whatever you have in linux that can eat it :)

I would suggest starting with a linux stripped of everything but the media apps you use, and use one realtime kernel, more than one kernel installed will lead to problems down the road, because of the large number
of beta software you will be using, and beta is not meant as a negative slurr, just a reality check for new users to note!

The linux I use most often is a full KDE environment that is
a hair over 300 meg in size before adding the wine/Reaper setup.
Opera is installed, to see the outside world a bit. No games or office
apps are permitted in the studio.

There are no doubt many other linux audio success scenarios out there, but until they are posted repeatedly, and in detail, no-one will know. The results with what we can have today, are limited only by skill and imagination.
Cheers

---

### Post by eeter on 2009-10-20
Maybe you can... 
there is a fully functional Renoise demo version for Linux with the exception that rendering the master output to disk is disabled. You can get it from here [http://www.renoise.com/download/renoise/](http://www.renoise.com/download/renoise/) and just try the demo songs (some of them are quite light-weight but I get CPU overload with those also)...

---

### Post by eeter on 2009-10-20
> **sgx said:**
> Hi, for multi-track recording using windows vst plugins, your best alternatives are to use wine and wineasio, with Reaper, EnergyXT, or Cantabile as DAW/vst host, and soundcards/graphics that work.
 There are sporadic reports from people using other software, versions of FL Studio, Usine, Bidule, etc but I cannot confirm those to be usable for basic multi-track recording/editing, nor have I seen credible evidence in google to support further searches.
Reaper is fast and stable in my linux setup.

I use audacity and the ladspa fx, for basic audio editing and format conversions. Ardour has packaging issues in many linux settings, to be
expected, as it is under constant developement, so
compiled versions of ardour and all its dependancies might help.

LMMS package crashes too much, but like ardour, using compiled versions of everything involved likely would help stability.

Hydrogen, Rakarrack, linuxsampler, and zynaddsubfx make a powerful
linux-only core for creating new music of professional quality. (The GSCW drumkits for Hydrogen are worth the large size) Using these  apps with the
Rosegarden sequencer might be an excellent choice if they are all stable
when used at the same time. Qtractor is a new sequencer I have not yet used, though I have it installed, and started it.

The good news is that Reaper output can be routed to linux destinations using qjackctl, so a powerful vst setup can be used as a massive rompler, feeding amazing sound to whatever you have in linux that can eat it :)

I would suggest starting with a linux stripped of everything but the media apps you use, and use one realtime kernel, more than one kernel installed will lead to problems down the road, because of the large number
of beta software you will be using, and beta is not meant as a negative slurr, just a reality check for new users to note!

The linux I use most often is a full KDE environment that is
a hair over 300 meg in size before adding the wine/Reaper setup.
Opera is installed, to see the outside world a bit. No games or office
apps are permitted in the studio.

There are no doubt many other linux audio success scenarios out there, but until they are posted repeatedly, and in detail, no-one will know. The results with what we can have today, are limited only by skill and imagination.
Cheers

Yes, I have checked and tested most of those apps mentioned above. I quite liked QTractor and some synth-apps, but it's still not quite what I prefer to use...

Sorry that I might sound rude but I'm really not very interested in those other apps. During years I have worked with different kind of audio software and I have finally found out that for me the tracker interface suits the best... And since Renoise is the most professional and stable music tracker available I will stick to it. Of coarse if there is any job to apply to other audio applications they will become handy and I will use them, but since I feel myself most comfortable working with Renoise it will remain the main application in my production process.

---

### Post by AutoStatic on 2009-10-21
Hello eeter,

Which Desktop Environment are you using? Maybe you could try switching to a lighter one like XFCE or Fluxbox. What could also help is to disable as much services running in the background as possible. Did you already take a look into that? And what are the specs of your machine?

---

### Post by kayosiii on 2009-10-21
This would be my current list of things to try...

1) Open up a process monitor and figure out which application is using the CPU. Something could be conflicting
2) get rid of pulse audio. It's not that it is bad - but if it starts fighting with other audio systems 
3) get jack up and running properly this is what asio + rewire is to windows. - this is currently a pita on Ubuntu but in my opinion linux professional audio is pretty pointless without it.

Good luck

---

### Post by AutoStatic on 2009-10-21
> **kayosiii said:**
> This would be my current list of things to try...
2) get rid of pulse audio. It's not that it is bad - but if it starts fighting with other audio systems Not if you configure PulseAudio a bit better, ie. make it work together with JACK. You could also prevent it from starting up altogether.

> **kayosiii said:**
> 3) get jack up and running properly this is what asio + rewire is to windows. - this is currently a pita on Ubuntu but in my opinion linux professional audio is pretty pointless without it.I have no problems whatsoever setting up JACK with 9.04. I do admit that it can take a while before you find out the optimal settings for your specific soundcard(s) but when you found them JACK is easy to set up whenever you install a new machine.

---

### Post by andied on 2009-10-21
I am not using advanced apps (just rhythmbox, audacious, vlc, etc.) but I have been disappointed with the higher cpu usage, compared to XP,  particulary as I am using 32 bit XP and 64 bit linux. 

I recently installed karmic beta and find it significantly lighter on the system resources, still a bit heavier than XP, but not much.

---

### Post by sgx on 2009-10-21
32 bit linux only uses half the cpu power of 64 bit linux :)

---

### Post by Stochastic on 2009-10-22
> **sgx said:**
> 32 bit linux only uses half the cpu power of 64 bit linux :)

This is simply not true, its only difference is in bit size, not cycles per second - which is how most gauge CPU power/usage.  Though this is now WAYYY off topic.


Back to why Renoize isn't performing as nice as you'd like: probably you're not using Jack as it's audio server.  The default audio chain in Ubuntu is not very well co-ordinated for professional audio - though it tries.  Jack audio server (once setup to work best with your sound card) will give much better performance.  You may also want to try the realtime kernel (particularly if you're running Ubuntu 8.04 or 9.10) to give audio even lower latencies without dropouts.  Use the package [qjackctl]("apt:qjackctl") to control the Jack audio server.

---

### Post by eeter on 2009-10-22
the funny thing is that I know quite well these standard procedures to get audio working properly in Ubuntu. I installed realtime kernel, I use JACK, I configured JACK to be lighter on my machine... Plus several alternative suggestions I have found here and there like using a lighter window manager, tuning off unnecessary processes etc.
But it still seems like it's not affecting the preformance. With the same project I was testing I get still CPU overload and it's really not normal. Even with a lighter project CPu is around 30% and the GUI starts lagging already so awfully that I cannot work like this.
As I found out the best workaround at the moment is to use Renoise in Wine. Which has also some disadvantages, but at least it's not torturing my machine like hell.

---

### Post by AutoStatic on 2009-10-22
Which version of Ubuntu and which kernel are you using? What are the specs of your machine? Do you know which application is the resource hog?

---

### Post by eeter on 2009-10-22
The linux distro I was testing with Renoise was Ubuntu 9.10 Karmic Beta. Today I'll give RC a try.
Kernel version. 2.6.31-9-rt

Anyway here are the specs when I ran *sudo lshw*:
```

    description: Desktop Computer
    product: AMD690VM-FMH
    vendor: FUJITSU SIEMENS
    version: V5.09
    serial: YSIC027268
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: AMD690VM-FMH
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: V5.09
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: V5.09 (02/20/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 4000+
          slot: Socket AM2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 1639 MHz (0.6 ns) [empty]
             product: None
             physical id: 0
             slot: A0
             width: 64 bits
             clock: 1639MHz (0.6ns)
        *-bank:1
             description: DIMM DDR2 1639 MHz (0.6 ns) [empty]
             product: None
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 1639MHz (0.6ns)
        *-bank:2
             description: DIMM DDR2 1639 MHz (0.6 ns)
             product: None
             physical id: 2
             slot: A2
             size: 512MiB
             width: 64 bits
             clock: 1639MHz (0.6ns)
        *-bank:3
             description: DIMM DDR2 1639 MHz (0.6 ns)
             product: None
             physical id: 3
             slot: A3
             size: 512MiB
             width: 64 bits
             clock: 1639MHz (0.6ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:d000(size=4096) memory:fda00000-fdbfffff ioport:d8000000(size=134217728)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690 [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=64
                resources: memory:d8000000-dfffffff(prefetchable) memory:fdbf0000-fdbfffff ioport:de00(size=256) memory:fda00000-fdafffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:e000(size=4096) memory:fdf00000-fdffffff ioport:fdc00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:1e:90:15:92:bd
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:25 ioport:ee00(size=256) memory:fdfff000-fdffffff memory:fdc00000-fdc1ffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:16 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
           *-disk:0
                description: ATA Disk
                product: ST3160815AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 6RX1YME8
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6dc51263
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/3A2418D42418954B
                   version: 3.1
                   serial: 7c4c2b2d-3d2b-524c-8154-c5238cb0b6ca
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-10 23:30:51 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount. options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_
other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H60N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CV02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD160JJ
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: ZM10
                serial: S08HJ1RLC04454
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=19df19de
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 89fe5eff-a369-42fa-9fde-09a1fd3f9196
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-16 15:51:35 filesystem=ext4 lastmountpoint=/8]&#65533;4&#65533;&#65533;&#65533;m&#476;&#65533;h]&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;&#65533;&#65533;&#65533;)&#65533;&#65533;&#65533; &#65533;$3&#65533;&#65533;&#65533;&#65533;.&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;{%3&#65533; modified=2009-10-16 16:09:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-10-22 11:15:40 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 2549MiB
                   capacity: 2549MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 2549MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe02e000-fe02efff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:fe02d000-fe02dfff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe02c000-fe02cfff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:fe02b000-fe02bfff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe02a000-fe02afff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe029000-fe0290ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:fa00(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
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
             resources: irq:16 memory:fe020000-fe023fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
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
             capabilities: pci bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fde00000-fdefffff memory:fdd00000-fddfffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 10
                serial: 00:40:f4:cc:00:29
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=88.196.110.32 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:20 ioport:cc00(size=256) memory:fdeff000-fdeff0ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:03:08.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: irq:23 memory:fdefe000-fdefe7ff ioport:cf00(size=128)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             size: 995MiB (1043MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=8f52ef50
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/UMMIOMA
                version: FAT32
                serial: b444-2f4f
                size: 992MiB
                capacity: 995MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount. options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepag
e=cp437,iocharset=iso8859-1,utf8,flush,errors=remount-ro state=mounted
```

And:
```
urmok6iv@urmok6iv-desktop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe020000 irq 16
urmok6iv@urmok6iv-desktop:~$ 
```

Wasn't there some kind of problem with HDA-Intel chipsets, that there are no good drivers for them? :sad:
Oh dear...
Or maybe there is some kind of conflict with that my machine is 64bit but some of the apps are 32bit? But unfortunately I don't understand this architecture subject fully yet. :(

---

### Post by AutoStatic on 2009-10-22
> **eeter said:**
> The linux distro I was testing with Renoise was Ubuntu 9.10 Karmic Beta. Today I'll give RC a try.
Kernel version. 2.6.31-9-rt

Anyway here are the specs when I ran *sudo lshw*:

Wasn't there some kind of problem with HDA-Intel chipsets, that there are no good drivers for them? :sad:
Oh dear...
Or maybe there is some kind of conflict with that my machine is 64bit but some of the apps are 32bit? But unfortunately I don't understand this architecture subject fully yet. :(Your system is up to par. But you're using a beta version of Ubuntu which makes it hard to troubleshoot, for me at least since I don't use beta versions myself. I do use the same kernel and haven't had any problems with it yet. The only program that nags on my systems is LMMS. The onboard soundchip is not the issue I think, neither are the 32bits apps on your 64bits system. Did you check how many resources are in use by which program with the System Monitor (System - Administration - System Monitor) or with Htop (Applications - System Tools - Htop)?

---

### Post by eeter on 2009-10-22
From System Monitor I can see that the biggest resource user is System Monitor by itself. I also checked it when running Renoise. Yeah. Renoise just uses unreasonably too much of CPU (2-3 times more than it's usual) when there is no need for that.
Hmm.. And if Renoise runs fine in wine then I must conclude that my hardware and drivers are working fine...

---

### Post by AutoStatic on 2009-10-22
Probably Renoise is not fully optimized for your specific setup. I'll try to give it a go too on different systems, even though I'm not using 9.10 (yet).
Here you stumble on the very essence why I like open source software so much. No pun towards Renoise, but with no source code available it's impossible to compile an optimized version and your stuck with a generic Linux binary that reacts differently on each system. It's not even clear if the binary is 64 or 32 bits.

---

### Post by Stochastic on 2009-10-22
> **eeter said:**
> As I found out the best workaround at the moment is to use Renoise in Wine. Which has also some disadvantages, but at least it's not torturing my machine like hell.

Well this is the most interesting and revealing info.  If the software works better with a translation layer added in, on the same system, with the same audio setup, then the culprit MUST lie in the difference between the Windows code version and the Linux code version.  It looks like this is a thread that should be linked to/started on the Renoise forums, it'd be interesting to hear what the Renoise team has to say on the matter.

I'd certainly think that because of the relative infancy of the Linux version, that these reports would be of great value to their development.  I can't imagine their relatively new port to this operating system would be as efficient as it could be.  I am rooting for it though, it's great software and it's even nicer to see a commercial software distributor taking this platform seriously.

So go nag the Renoise devs about this and please post their response, I'd love to read it.

---

### Post by sgosnell on 2009-10-22
I agree.  If it runs faster in wine, then there is a definite problem with the port to Linux.  The code is very inefficient, and my first guess would be that it's mostly because they coded the program originally in the Microsoft Windows development environment, and then just recompiled it for Linux without even trying to optimize it.  It's optimized for Windows, as much as possible, and that's a far different environment than Linux.  If you paid for the program, you're entitled to better support than that, IMO, but you may not get it.  Bug the renoise developers daily, and hope it helps.  That's the only way you're going to get results.

---

### Post by nelio2k on 2009-10-22
Just a thought... but is your CPU scaled down? I think by default ubuntu's "ondemand" profile will try to use the least amount of CPU power and only scale up when you reach 95% threshold.

---

### Post by AutoStatic on 2009-10-23
@nelio2k, good thinking. A **cat proc/cpuinfo** should reveal if the CPU is running at full speed or not. You could try bum (Boot-Up manager) or sysv-rc-conf to check if the ondemand service is running and disable it.

@henrythomas, Audio Editor is a Windows program, we're talking Ubuntu here ;) Besides, it's an editor, not a tracker.

---

### Post by sgx on 2009-10-23
> **Stochastic said:**
> Well this is the most interesting and revealing info.  If the software works better with a translation layer added in, on the same system, with the same audio setup, then the culprit MUST lie in the difference between the Windows code version and the Linux code version.  It looks like this is a thread that should be linked to/started on the Renoise forums, it'd be interesting to hear what the Renoise team has to say on the matter.

I'd certainly think that because of the relative infancy of the Linux version, that these reports would be of great value to their development.  I can't imagine their relatively new port to this operating system would be as efficient as it could be.  I am rooting for it though, it's great software and it's even nicer to see a commercial software distributor taking this platform seriously.

So go nag the Renoise devs about this and please post their response, I'd love to read it.

In similar fashion, The linux Energy XT2 is a bit limited when compared to the windows version used with wineasio. But I don't think EXT2 has a big team of coders, so the author(s) can get stretched thin trying to have productive functionality on both platforms, with users from each one insisting that theirs is the version that needs xxx feature first or the most. :)

---

### Post by tomsa on 2009-11-17
I just started working with Renoise last night- and at first I was having playback problems as well.  I found one *very* useful tidbit of information on their website that solved my playback problems entirely!  I copied these instructions for you from the Renoise website, and like I said, they worked for me.  I hope they work for you too!

> Ho do I configure Linux to enable Realtime Threads for ALSA or JACK?
To allow Renoise to create realtime threads, which are required for low latencies with ALSA or JACK, you have to edit the /etc/security/limits.conf file. A realtime kernel does NOT help here, does not set the required options automatically!

To enable RT thread creation via PAM open the /etc/security/limits.conf file as root (or via sudo).

Then somewhere at the end of the file add:

    * YOURUSERNAME - rtprio 99
      YOURUSERNAME - nice &#8722;10

Alternatively you could also create a group “Audio”, add your user to that group, and use “@Audio” instead of “YOURUSERNAME”.

Save. Log Out. Login. Then it should work. To make sure that it works, launch Renoise, select ALSA and make sure the “Realtime threads” option is on. You will get a friendly warning if RT creation failed.

You can find a more detailed explanation about PAM and low latencies in Linux here [http://tapas.affenbande.org/wordpress/?page_id=73](http://tapas.affenbande.org/wordpress/?page_id=73).

This was taken from: [http://tutorials.renoise.com/Renoise/SettingUpLinux](http://tutorials.renoise.com/Renoise/SettingUpLinux)

Cheers!

---

### Post by VertexPusher on 2009-11-18
> **tomsa said:**
> I just started working with Renoise last night- and at first I was having playback problems as well.  I found one *very* useful tidbit of information on their website that solved my playback problems entirely!  I copied these instructions for you from the Renoise website, and like I said, they worked for me.  I hope they work for you too!
If missing RT priority was the issue here, WINE would be affected too, but apparently performance under WINE is much better. So the issue here is that the Linux version of the program performs worse than the Windows version, probably due to badly optimized code.

Also note that RT priority does not reduce CPU load. In fact CPU load will increase the more you reduce latency, because smaller audio buffers require more buffer refill cycles per second, and each refill cycle has a constant overhead that quickly adds up. If the overhead becomes too large (e.g. because of badly optimized code or too many plugins in the audio path), the only solution is to increase latency.

---

### Post by tomsa on 2009-11-18
> If missing RT priority was the issue here, WINE would be affected too, but apparently performance under WINE is much better. So the issue here is that the Linux version of the program performs worse than the Windows version, probably due to badly optimized code.


Well, that is most likely true.  I hadn't really thought about that.  Of course, that is what you get when you find a musician offering help on a tech forum.  Still, I suppose it's worth a try anyway- as it is both easy to do, and undo.  

One thing that remains true for all linux distros, however, is that serious pro audio usage remains either infuriating, or next to impossible (yes, I know about ubuntu studio, ardour, jack, rosegarden, hydrogen, 64studio, etc..... I've been over it).  If I was doing electronic music for my main source of income, rather than my own entertainment/ education it would definitely not be in linux.  It's really a shame, and I'd love to see that change- but I don't know that I have the time or knowledge to contribute much to the open source music world.  My personal acoustic cash cow takes too much of my time.

Linux is superior on so many things- audio is not one of them.

I will, however, keep plugging away and encourage others to do the same in the effort to try and continue to push the means of music production and performance away from the limiters that still hold most of the controlling influence on the music recording, production, and distribution systems that are in place today.

Sorry for the off topic rant at the end there.

---

### Post by VertexPusher on 2009-11-18
> **tomsa said:**
> Linux is superior on so many things- audio is not one of them.
I disagree. Audio is in fact one of the things where Linux really shines. ALSA is on par with ASIO but much easier to configure, and it works with any mainstream soundcard, not only the "professional" ones. Try to run onboard soundcards at less than 4ms latency to see what I mean. It's impossible on Windows. And there is no such thing as a realtime Windows kernel.

The problem is with the applications. Jack is awesome, but not easy to configure for non-techies. PulseAudio just sucks.

---

### Post by thorgal on 2009-11-18
ach so, it's more a question of polishing the different technologies. The underlying capabilities in linux are quite outstanding. The user side of things leaves a taste of unfinished / unpolished that can sometimes feel bitter. That's what the audio centric distros are trying to improve:
- keep the excellent fleshy stuff
- sweeten it to some extent

We've seen that it is not always a success, just like baking an excellent home made bread can take more than one try :)

Just be patient. I think that we should first get the kernel right (the flesh) in all circumstances. The glazing will come along once the kneading has been perfected. We are currently probably mixing too many different flavors (jack, pulse, ALSA, oss, etc).

---

