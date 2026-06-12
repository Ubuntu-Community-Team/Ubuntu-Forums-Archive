---
title: "Graphics card that fits Ubuntu"
date: 2009-01-27
forum: The Cafe
---

### Post by fredscripts on 2009-01-27
Hi!

I'm in a Pentium IV machine, with a graphics card GeForce2 MX/MX 400 (64MB).

A few months ago, for my surprise, Ubuntu told me that there were drivers available and if I wanted to install them. Of course I proceeded.

I'm very glad that compiz effects are currently working. Of course, with such an old graphics card it works so laggy.

I'm planning to buy a new graphics card to run compiz confortable (also the graphics in general, because to my surprise, even with drivers, Windows graphics are more clean and faster).

I'm a newbie in hardware stuff but I think that the type of connection that is needed for this graphics card ( VGA compatible controller ) is now deprecated. I wonder which is the best graphics card that fits this connection and is perfectly supported by Ubuntu (also Debian), so Ubuntu gets the maximum of the device.

Thanks so much!!



PS: I don't know if this is the best place to ask but I've seen several times this kind of questions in this sub forum.

---

### Post by mips on 2009-01-27
1. What is your budget?
2. Do you use your PC for graphics intensive tasks?
3. Do you game and what games do you play?
4. PCI, AGP or PCIe bus? Tell us your computer/motherboard make&model if not sure.

I would recommend nVidia.

---

### Post by Johnsie on 2009-01-27
Intel onboard works great.

---

### Post by kaldor on 2009-01-27
Nvidia have Linux drivers, go with them.

I use a GeForce 8400, and my girlfriend uses an 8600. 

Though, I hear the 9000 series geforce cards are poorly supported with openGL.

---

### Post by MikeTheC on 2009-01-27
I bought an XFX nVidia 9600 GSO a month or so ago, and it works flawlessly. Of course, you're going to have to go with an AGP-interfaced card for that system (at best) and so, while not zero, your choices are going to be fewer and, quite possibly, a touch more expensive. Good luck!

---

### Post by zachtib on 2009-01-27
> **MikeTheC said:**
> I bought an XFX nVidia 9600 GSO a month or so ago, and it works flawlessly. Of course, you're going to have to go with an AGP-interfaced card for that system (at best) and so, while not zero, your choices are going to be fewer and, quite possibly, a touch more expensive. Good luck!

I'm guessing he'll need a PCI card...

And it shouldn't take much... my work computer has a Geforce 5200, and it runs Compiz fine (and at 1600x1200)

---

### Post by Frak on 2009-01-27
Nvidia 6800 GT is the best you can get for that. (AGP wise, you can get a PCI for anything, just the bus is a bit slower and narrower) Nonetheless, it's still a good card.

---

### Post by forrestcupp on 2009-01-27
> **zachtib said:**
> I'm guessing he'll need a PCI card...


Right, and the *old* PCI cards, not the newer PCI express.  They're pretty hard to find nowadays.

---

### Post by Frak on 2009-01-27
> **forrestcupp said:**
> Right, and the *old* PCI cards, not the newer PCI express.  They're pretty hard to find nowadays.
My local staples sells a 7500 PCI card. They still sell for them.

---

### Post by Sunflower1970 on 2009-01-27
I have an nVidia 7600 GT AGP card I got from Newegg.com a couple of years ago. I love it. Don't know if it's even available, anymore though :(

---

### Post by fredscripts on 2009-01-27
> **mips said:**
> 1. What is your budget?
2. Do you use your PC for graphics intensive tasks?
3. Do you game and what games do you play?
4. PCI, AGP or PCIe bus? Tell us your computer/motherboard make&model if not sure.

I would recommend nVidia.

Thanks for answering,

As I said I don't know too much about hardware , so I can only answer that mainly I want that compiz effects and some openGL projects that I'm working get optimized by the graphics card (so Ubuntu got the right drivers to do that work).

I can show you the output of lshw for details (sorry long paste):

```
fredlab
    description: Desktop Computer
    product: MS-6547
    vendor: MSI
    version: 2.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-6547
       vendor: MSI
       physical id: 0
       version: 2.00
       serial: 00000000
       slot: PCI2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (12/20/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: PGA478
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 511MiB
     *-pci
          description: Host bridge
          product: SiS645 Host & Memory & AGP Controller
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: SiS961 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JVKPHLK
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0a240a23
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7acb84dd-0311-234c-a3de-70cb9a334856
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-09 20:12:34 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 10236MiB
                   capacity: 10236MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10236MiB
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 4c36ded5-97b1-41e0-af4d-e9f5e91c186b
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-09 21:16:08 filesystem=ext3 modified=2009-01-27 16:01:46 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-01-27 16:01:46 state=mounted
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 31a489dc-8d90-4d0a-8189-6ac93aab4033
                   size: 956MiB
                   capacity: 956MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-M1612
                vendor: TOSHIBA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1004
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 10
             serial: 00:a0:c5:b3:5e:48
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 2
          bus info: usb@2:1.1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=454c4fc9
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/LaCie
                version: 3.1
                serial: 2e22dcba-646e-8e4b-8efd-f9a82cbf00d1
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-09-01 19:19:38 filesystem=ntfs label=LaCie modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:92:0e:ba:5a:43
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


Thanks you all for the help, so I guess I should ask in the store for some nVidia cards that has AGP connection and compare MB and other parameters (7600 GT is a good choice).

---

### Post by fredscripts on 2009-01-27
Oh by the way, the main point was that Ubuntu gets the maximum of the graphics card, so is there any way to get a list of graphics card that fits my specification and also are suported by Ubuntu (good drivers)?

---

### Post by igknighted on 2009-01-27
> **fredscripts said:**
> ...


Thanks you all for the help, so I guess I should ask in the store for some nVidia cards that has AGP connection and compare MB and other parameters (7600 GT is a good choice).

You are correct, AGP is the way to go.  However if you walk into any big box store, expect to pay twice (or more) as much as the same card online.  There are some things I would buy locally, but new hardware (especially graphics cards) isn't one.

You might also try your local craigslist.  I bet a lot of people are upgrading cards of that type, so you might be able to pick up a used one cheap.

Try this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814150107](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150107)

or this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121273](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121273)

The ATI is much more capable (dx10, hd video) and is supported by good open source and binary drivers, but nvidia has always been the fallback for linux.  If you plan on keeping the card a few years, be aware that the 6 series is the oldest supported nvidia chipset, and support could be pulled any time (see the 5 series earlier this year).

---

### Post by jrusso2 on 2009-01-27
I don't doubt ATI makes a more current card for AGP but Nvidia works so much easier with Linux.  And if you don't believe me get ATI.

I have a similar PC here that runs a Nvidia 7600 GS that runs fine and is AGP.

---

### Post by overdrank on 2009-01-27
> **fredscripts said:**
> Thanks for answering,

As I said I don't know too much about hardware , so I can only answer that mainly I want that compiz effects and some openGL projects that I'm working get optimized by the graphics card (so Ubuntu got the right drivers to do that work).

I can show you the output of lshw for details (sorry long paste):

Thanks you all for the help, so I guess I should ask in the store for some nVidia cards that has AGP connection and compare MB and other parameters (7600 GT is a good choice).

Your motherboard [MS-6547]("http://www.msicomputer.com/product/p_spec.asp?model=645_Ultra") can handle > One AGP 4X/2X universal slot. 
If you can wait a week or so I might have a 6600 to cut you a deal. :)

---

### Post by forrestcupp on 2009-01-27
I'm pretty sure the geforce 7900 is the best AGP card you can get.  But you would be happy with the much cheaper 7600.

---

### Post by Zero Prime on 2009-01-27
> **jrusso2 said:**
> I don't doubt ATI makes a more current card for AGP but Nvidia works so much easier with Linux.  And if you don't believe me get ATI.

I have a similar PC here that runs a Nvidia 7600 GS that runs fine and is AGP.

How can Nvidia be easier with ATI?  Go to the ATI website, download the driver, make it executable and launch it as sudo.  All done.

---

### Post by collinp on 2009-01-27
I can prove very easily that my Geforce 6200 handles Compiz well, and they have versions for AGP and PCI (not PCIe); any computer should have PCI. Mine was made by EVGA.

---

### Post by Frak on 2009-01-27
> **Zero Prime said:**
> How can Nvidia be easier with ATI?  Go to the ATI website, download the driver, make it executable and launch it as sudo.  All done.
There are compatibility issues with ATi in Linux. One such can be multiple monitors, another is fullscreen applications, etc.

---

### Post by Zero Prime on 2009-01-28
Luckily, the latest drivers have rectified these problems.  You can even use hybrid-crossfire in Linux with ATI now.  The only problem I have found is clipping during video play back when compositing (such as Compiz) is on.

---

### Post by Johnsie on 2009-01-28
I hate to say it but in Windows you wouldn't need to worry which one you buy.

+1 for windows

-1 for the hardware companies who still aren't releasing decent fully working, easy to install Linux drivers.

---

### Post by mips on 2009-01-28
> **Johnsie said:**
> I hate to say it but in Windows you wouldn't need to worry which one you buy.

+1 for windows

-1 for the hardware companies who still aren't releasing decent fully working, easy to install Linux drivers.

The current 180.x nvidia drivers are the dogs nads.

---

### Post by forrestcupp on 2009-01-28
> **Zero Prime said:**
> The only problem I have found is clipping during video play back when compositing (such as Compiz) is on.And also clipping while playing any opengl game or running any opengl app, including screen savers.  Until that gets fixed, nvidia is for me because they already fixed that long ago.  Unfortunately, ATI isn't ever going to do anything about this problem; they're waiting on xorg to fix it.

> **mips said:**
> The current 180.x nvidia drivers are the dogs nads.This is true.  You can't really beat nvidia with 180.x in Linux.

---

### Post by Zero Prime on 2009-01-28
> **forrestcupp said:**
> And also clipping while playing any opengl game or running any opengl app, including screen savers.  Until that gets fixed, nvidia is for me because they already fixed that long ago.  Unfortunately, ATI isn't ever going to do anything about this problem; they're waiting on xorg to fix it.

This is true.  You can't really beat nvidia with 180.x in Linux.

Not true.  I play Urbanterror with no clipping issues with metacity composite running and still get 92 FPS (that's with the FPS limiter set at 92 FPS and integrated ATI 3200HD graphichs).  ATI has made great strides with their drivers.  I'm not debating which is better, just that ATI has come a long way.  I don't use screen savers so I can't comment on that.  Never could get them to work right with my old Nvidia card so I never tried again.

---

### Post by cb951303 on 2009-01-28
You can buy an Ati X850XT AGP if you can find it. They are very well supported by open source ATI drivers.

NVIDIA has currently no plan for KMS compatbility. Buying an ATI may help you in the future. But, proprietary ATI drivers are troublesome, so I were you, I would get the best supported card by open source ATI drivers, which also happens to have an AGP version (Ati X850)

---

### Post by Frak on 2009-01-28
> **Zero Prime said:**
> Not true.  I play Urbanterror with no clipping issues with metacity composite running and still get 92 FPS (that's with the FPS limiter set at 92 FPS and integrated ATI 3200HD graphichs).  ATI has made great strides with their drivers.  I'm not debating which is better, just that ATI has come a long way.  I don't use screen savers so I can't comment on that.  Never could get them to work right with my old Nvidia card so I never tried again.
I can play Urban Terror on Linux with the Nvidia 181 drivers at 110 fps on an integrated GeForce 6150 SE (NForce 430). My chipset is originally around 3 years old (IIRC).

---

