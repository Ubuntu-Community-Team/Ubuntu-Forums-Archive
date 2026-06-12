---
title: "Anyone else experiencing high swap usage?"
date: 2013-02-14
forum: Ubuntu Development Version
---

### Post by nismoryco on 2013-02-14
I use two different machines during the week.  They both have 8gb of ram and both still have swap space turned on.  I have been noticing some serious problems with Unity.  First off, the dash home button is sluggish and using alt-tab is so slow that it is completely useless.  Clicking on the launcher to change applications is normal.  I also have found that using alt-tab puts something in a terrible condition.  Out of the blue, my swap usage will start climbing uncontrollably.  My memory usage typically hovers around 1-1.2 gb even during this condition.  When the system runs out of swap space, it become completely unresponsive.  I believe the use of alt-tab is causing the condition.  Has anyone else noticed this?  This is happening on both machines running Raring.

---

### Post by QIII on 2013-02-14
Hmmmm...

Haven't seen that on my Unity machine.  I'll have to check this evening.

---

### Post by ventrical on 2013-02-14
alt+tab is the Unity application switcher. (I actually do not have ccsm installed on this one machine). I was having some problems like you described about a week ago , until I zsynced the raring-desltop-i386.iso. This was on an Ati based graphics machine.

```

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AP [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AP [Radeon 9600] (Secondary)

```


This machine only has 1.2GB of ddr with 1.2 Gb of swap sapce (currently runnng at zero bytes)

 I *do* have the  anomolous Unity black-space with this newer install (meaning that when I click the unity dash icon I get a black-space behind all the icons). But otherwise it is working well but not as fast as Quantal and Precise predecessors .

---

### Post by nismoryco on 2013-02-14
I'm running Intel graphics on both machines.  Graphics performance, in general, seems normal with exceptions that I noted above.

---

### Post by grahammechanical on 2013-02-14
No. I find the memory usage is about 20% less than in 12.04/12.10. At the moment System Monitor is showing 71% out of 1GB RAM and swap at 10% of 2GB.

But I have 3 Libre office windows open, Chromium with 2 tabs (this site and the BBC streaming a radio program), + system monitor and the terminal running top.

There are 2 CPUs running between 5 - 8%. which is an improvement over switching from one CPU to the other.

Have you tried running top or htop (needs to be installed)?

Regards.

P.S. I was trying to find in the back issues of the Ubuntu Weekly Newsletter a link to someone's blog about testing for memory leaks. The best I came up with is this:

[https://wiki.ubuntu.com/Nexus7/MeasuringMemoryUsage]("https://wiki.ubuntu.com/Nexus7/MeasuringMemoryUsage")

It is Nexus 7 related because that is where the development effort is going but the principles can be applied on desktop Ubuntu.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-reduced-power-ram]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-reduced-power-ram")

---

### Post by ventrical on 2013-02-14
I just basically did what grahamechanical was doing with the exception that I inadvertently loaded Libre Office, Libre Calc and Libre Impress (plus a bunch of other programs) and yet another phenomenon occured!!! After I loaded Libre Impress Unity went  *hyper* space , meaning that it seem to be freed up from some sort of bottleneck. The Unity application switched went so fast before my eyes it was like a Walt Disney cartoon...

This is a rather older machine; specs:

```

root@ventrical-P4M266A-8237:~# lshw
ventrical-p4m266a-8237    
    description: Desktop Computer
    product: P4M266A-8237
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00000000-0000-0000-00E0-00004CE17DC1
  *-core
       description: Motherboard
       product: P4M266A-8237
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 07/05/2005
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 2800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 478
          size: 2800MHz
          clock: 133MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
     *-pci
          description: Host bridge
          product: P4M266 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:e4000000-e5ffffff memory:c0000000-dfffffff
           *-display:0
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:c0000000-cfffffff ioport:9000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff memory:e5010000-e501ffff
        *-network:0
             description: Ethernet interface
             product: SMC2-1211TX
             vendor: Accton Technology Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth0
             version: 10
             serial: 00:10:b5:7d:33:14
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.23 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:17 ioport:a000(size=256) memory:e6000000-e60000ff
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a400(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:a800(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:ac00(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:b000(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:b400(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:e6001000-e60010ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:b800(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: 78
             serial: 00:e0:4c:e1:7d:c1
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:c000(size=256) memory:e6002000-e60020ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 53073H6
             vendor: Maxtor
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sda
             version: DAC1
             serial: K60N9NLC
             size: 28GiB (30GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ded6b
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f54f8e0d-7fcc-4fe0-82d9-92ce19f830e4
                size: 27GiB
                capacity: 27GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-02-12 14:40:38 filesystem=ext4 lastmountpoint=/ modified=2013-02-14 10:07:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-02-14 10:07:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sda2
                size: 1278MiB
                capacity: 1278MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1278MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: CD-R/CD-RW writer
             product: CRW-4832AX
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/sr0
             version: 0.50
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc
root@ventrical-P4M266A-8237:~# 

```I guess I am unofficially calling it the *zoom* factor. :) 

The logical explantion for this phenomenon is that sometimes the extra load on the processor and bus will incite the power supply to produce more voltage (where at a more or less idle pace it is regulated in a power-saving mode. So the extra load produces more wattage (and some continuous extra voltage) to boost system performance.

 It never ceases to amaze  me the things we discover with Ubuntu! :)

Oh yeah .. and btw .. all on a single core!!

---

### Post by Gyokuro on 2013-02-15
> **grahammechanical said:**
> No. I find the memory usage is about 20% less than in 12.04/12.10. At the moment System Monitor is showing 71% out of 1GB RAM and swap at 10% of 2GB.

But I have 3 Libre office windows open, Chromium with 2 tabs (this site and the BBC streaming a radio program), + system monitor and the terminal running top.

There are 2 CPUs running between 5 - 8%. which is an improvement over switching from one CPU to the other.

Have you tried running top or htop (needs to be installed)?

Regards.

P.S. I was trying to find in the back issues of the Ubuntu Weekly Newsletter a link to someone's blog about testing for memory leaks. The best I came up with is this:

[https://wiki.ubuntu.com/Nexus7/MeasuringMemoryUsage](https://wiki.ubuntu.com/Nexus7/MeasuringMemoryUsage)

It is Nexus 7 related because that is where the development effort is going but the principles can be applied on desktop Ubuntu.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-reduced-power-ram](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-reduced-power-ram)

Thank you as I found out I have the same problem on Precise 12.04.2 with the new LTS stack. Since yesterday the machine is constantly swapping (6GB RAM) and now already at 600 MB swap space - have to find out what's going on.

---

### Post by nismoryco on 2013-02-15
It's compiz. And, it's has something to do with Intel graphics.  I'm not seeing this on my desktop with nvidia graphics. The unity switcher is working completely normal on that machine, too.

The screen shot shows the problem. I killed compiz and everything went back to normal.

---

### Post by Gyokuro on 2013-02-15
> **nismoryco said:**
> It's compiz. And, it's has something to do with Intel graphics.  I'm not seeing this on my desktop with nvidia graphics. The unity switcher is working completely normal on that machine, too.

The screen shot shows the problem. I killed compiz and everything went back to normal.

+1 Confirmed - killing compiz helps but as soon it get restarted it is memleaking again. So I have to wait that compiz memory leaking get fixed. Is there someone who has already send a bug report??

---

### Post by nismoryco on 2013-02-15
@Gyokuro:

Are you using the xorg-edgers ppa?

---

### Post by Gyokuro on 2013-02-15
> **nismoryco said:**
> @Gyokuro:

Are you using the xorg-edgers ppa?

No - released 12.04.2 (ubuntu-12.04.2-alternate-amd64.iso) and I have an identical machine which I have only updated - there is no memleaking! Only on the test machine which I have installed from scratch via previous mentioned iso.

---

### Post by nismoryco on 2013-02-15
I re-installed Raring without using the xorg-edgers PPA this time. I am no longer having the issue. If I upgrade from xorg-edgers, the problem returns.

---

### Post by Gyokuro on 2013-02-17
Bug got reported: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1127959](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1127959)

---

