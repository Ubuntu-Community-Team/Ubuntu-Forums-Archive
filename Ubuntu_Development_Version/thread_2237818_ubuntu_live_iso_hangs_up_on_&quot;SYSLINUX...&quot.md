---
title: "ubuntu live iso hangs up on &quot;SYSLINUX...&quot; message"
date: 2014-08-04
forum: Ubuntu Development Version
---

### Post by startas on 2014-08-04
So, looks like 14.10 dev series are the worst of all time, it doesnt even boot. There was some iso files long time ago that booted, but all other amd64 isos arent even booting, it just hangs up on message "SYSLINUX 3.86 2010-04-01 CBIO Copyright (C) 1994-2010 H. Peter Anvin et al".

---

### Post by Elfy on 2014-08-04
not getting that - but I get no usable desktop on tty7 until I've startx'd

new image should be up shortly - will check again later if I remember

Edit - jenkins shows them failing too - someone will look I would suspect

---

### Post by Elfy on 2014-08-04
current build boots fine for me

---

### Post by startas on 2014-08-04
I found similiar problems with stable ubuntu versions also, but they got BOOT prompt after syslinux message, so they can write something and then cd boots, but i dont even get boot prompt, everything stops at syslinux message... There was some good booting isos at the very beginning, when 14.10 dev just started, but after that there even wasnt new daily iso files, as they all failed testing, now i noticed, that there is newer amd64 iso file, but it fails too, probably got through testing via alpha 2 release. And of course, now there is no new daily build isos for a few days, cause they all fail testing too... It is strange that you got to boot this broken iso.

---

### Post by ventrical on 2014-08-04
It's booting fine here .  Just hit TAB and then enter your choice .... 'live' , live install .. etc..

  I am typing this message from the live USB.

Regards..

```

ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1983MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2394MHz
          capacity: 2394MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82Q963/Q965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:92000000-930fffff ioport:80000000(size=301989888)
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
                resources: irq:47 memory:92000000-92ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:2000(size=128) memory:93080000-930fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:93000000-93003fff
        *-communication
             description: Communication controller
             product: 82Q963/Q965 HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:48 memory:93325900-9332590f
        *-network
             description: Ethernet interface
             product: 82566DM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:19:d1:75:5b:c8
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.1-0 ip=192.168.2.36 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:46 memory:93300000-9331ffff memory:93324000-93324fff ioport:30c0(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:30a0(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:3080(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:93325400-933257ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:93320000-93323fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:93400000-934fffff ioport:100000000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:93200000-932fffff ioport:100200000(size=2097152)
           *-ide
                description: IDE interface
                product: 88SE6101/6102 single-port PATA133 interface
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:17 ioport:1018(size=8) ioport:1024(size=4) ioport:1010(size=8) ioport:1020(size=4) ioport:1000(size=16) memory:93200000-932001ff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:93500000-935fffff ioport:100400000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:6000(size=4096) memory:93600000-936fffff ioport:100600000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:7000(size=4096) memory:93700000-937fffff ioport:100800000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3060(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3040(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3020(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:93325000-933253ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:93100000-931fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:07:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:19 memory:93104000-931047ff memory:93100000-93103fff
        *-isa
             description: ISA bridge
             product: 82801HO (ICH8DO) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3138(size=8) ioport:314c(size=4) ioport:3130(size=8) ioport:3148(size=4) ioport:3110(size=16) ioport:3100(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:93325800-933258ff ioport:3000(size=32)
        *-ide:1
             description: IDE interface
             product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3128(size=8) ioport:3144(size=4) ioport:3120(size=8) ioport:3140(size=4) ioport:30f0(size=16) ioport:30e0(size=16)
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ubuntu@ubuntu:~$ 

```

---

### Post by startas on 2014-08-05
Nope, nothing works. This is the first message, that appears just after i select to boot from ubuntu usb, so cant do anything else.

---

### Post by Elfy on 2014-08-05
and you get the same with updated image?

---

### Post by ventrical on 2014-08-05
> **startas said:**
> Nope, nothing works. This is the first message, that appears just after i select to boot from ubuntu usb, so cant do anything else.


Are you booting from UEFI?

What is hardware you are using?

---

### Post by startas on 2014-08-05
No uefi, simple, a few years old laptop with core i3, intel hd graphics, 4gb ram. I have been trying all ubuntu dev versions since 13.04, and it never happened, this error showed up only with 14.10. Also, with older ubuntu versions, daily isos were released almost daily, and with 14.10, there was very few daily iso releases, only a few at the very beginning, and one like 2 months later, most of the time there was no daily iso releases.

---

### Post by Elfy on 2014-08-05
> **startas said:**
> No uefi, simple, a few years old laptop with core i3, intel hd graphics, 4gb ram. I have been trying all ubuntu dev versions since 13.04, and it never happened, this error showed up only with 14.10. Also, with older ubuntu versions, daily isos were released almost daily, and with 14.10, there was very few daily iso releases, only a few at the very beginning, and one like 2 months later, most of the time there was no daily iso releases.

Is this *just* Ubuntu images or any of the flavours available images?

---

### Post by startas on 2014-08-05
I tried only ubuntu, as i have no interest in other desktops.

---

### Post by Elfy on 2014-08-05
well I've no particular interest in anything but Xubuntu tbh - but if I find something that's possibly going to/or has affected other flavours that IS affecting Xubuntu I'll check quickly, that is what this sub-forum is for

unsubscribing now that this is an Ubuntu only issue

---

### Post by cariboo on 2014-08-05
I just booted from the current build iso, and didn't encounter any problems. How did you create your boot device? Was it a DVD or a USB drive of some sort?

---

### Post by startas on 2014-08-06
Usb flash drive, burned iso to usb with linux live usb, using this method for more than 2 years for many linux distros, worked all the time.

---

### Post by sudodus on 2014-08-06
During development, there might be problems with the USB making tools, that pick files from the iso image and write them into a FAT32 file system. Cloning has a higher success rate. I suggest that you try ***mkusb*** according to these links

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by ventrical on 2014-08-06
I use SDC on a locked down version of Maveric Meercat  (ubuntu 10.10) of my 1.5 TB hdd. Never fails development releases.

Regards..

---

### Post by sudodus on 2014-08-06
Interesting :-)

It seems that many tools in Ubuntu 10.10 had a high quality.
If I remember correctly, also its installer, ubiquity, is still going strong.

---

### Post by ventrical on 2014-08-06
It detects all those partitions (that Windows8 UEFI) has where 14.04.1 will not.

---

### Post by ventrical on 2014-08-06
> **startas said:**
> I tried only ubuntu, as i have no interest in other desktops.

I could only suggest to try an download the .iso again and try to burn it once more.

---

### Post by startas on 2014-08-06
No no no, linux live usb is windows program, i burn linux to usb with it, it always works.

---

### Post by ventrical on 2014-08-06
> **startas said:**
> No no no, linux live usb is windows program, i burn linux to usb with it, it always works.


Apparently it is not working now. Thanks for the explanation . I did not know you were using Windows to burn isos to USB. This happened to me once where for some strange reason I had to format the USB to FAT32 using Windows XP and then , after that, I had my USB back working again to burn isos again.

 Have you tried different USBs?

Has perhaps USB stick seen it's day?

Just thinking out loud..

---

### Post by startas on 2014-08-06
Nope, program works fine, usb flash also works fine, other distros iso are burning fine. I really think it has to do something will ubuntu daily isos failing even simple testing.

---

### Post by startas on 2014-08-08
I just tried xubuntu daily iso, and it doesnt boot too, so i guess this bug affects all *buntus.

---

### Post by cariboo on 2014-08-08
> **startas said:**
> I just tried xubuntu daily iso, and it doesnt boot too, so i guess this bug affects all *buntus.

All that proves, is that the tool you are using is broken. Have you tried unetbootin?

---

### Post by startas on 2014-08-09
Well, this tool works with many other distros, it also works with ubuntu <=14.04, so not exactly the definition of "broken". Sounds like the oposite - works everything, except ubuntu 14.10.

---

### Post by ventrical on 2014-08-09
> **startas said:**
> Well, this tool works with many other distros, it also works with ubuntu <=14.04, so not exactly the definition of "broken". Sounds like the oposite - works everything, except ubuntu 14.10.

  Well how come mutliple persons have replied that it *is* working and your's is not?

Regards..

---

### Post by startas on 2014-08-09
And i will tell the 100th time - ubuntu 14.10 daily isos are broken, you can count on 1 hand how many of them got through testing into daily isos folder on ubuntu site...

---

### Post by ventrical on 2014-08-09
This same situation happened during saucy/raring testing of daily isos.  There were some who had no problems and others who could not get it to boot or work at all (and that went for Intel graphics adapters as well).

  When I first read this thread I downloaded the full daily ubuntu-desktop-amd64.iso (utopic) in an attempt to duplicate your problem and it booted just fine into live.

  The only difference in those cases was that  some of the ones that were not working were in the U.K. .. and other that were working were in North America. What this mean (if anything) I don't know. If your's isn't working .. then it isn't. Mine is. :)

---

### Post by ventrical on 2014-08-09
I'm downloading the daily xubuntu 14.10 now. I'm busy atm .. but will get back on this.

Regards..

---

### Post by ventrical on 2014-08-09
> **startas said:**
> I just tried xubuntu daily iso, and it doesnt boot too, so i guess this bug affects all *buntus.

Works excellently here.

Perhaps if you zsynced an older file .. it may have corrupted.

Regards

---

### Post by ventrical on 2014-08-09
Ubuntu .isos not busted.

Declare my assumptions.

Document my work.

[https://www.youtube.com/watch?v=hojB2c4CSmU&feature=youtu.be](https://www.youtube.com/watch?v=hojB2c4CSmU&feature=youtu.be)

---

### Post by grahammechanical on 2014-08-09
My hardware is ordinary. There is nothing exotic about it and I never had to use an F6 option to run the live session like some people did until the development cycle of about a year ago when the only way I could the daily image to load was to tick all the F6 options. Things improved a week or so later. Stuff like this happens.

In the past it was quiet common to see F6 options being recommended. I do not see it so much now. Not even nomodeset. With newer hardware coming out all the time I think that F6 options are still necessary.

Regards.

---

### Post by startas on 2014-08-09
> **ventrical said:**
> This same situation happened during saucy/raring testing of daily isos.

Actually that was exactly the oposite - there was released almost all daily isos of saucy/raring, whereas with utopic there is only very few releases, most daily builds fails.

---

### Post by ventrical on 2014-08-09
> **startas said:**
> Actually that was exactly the oposite - there was released almost all daily isos of saucy/raring, whereas with utopic there is only very few releases, most daily builds fails.

In the early stages , no it was not.  And it carried on to near the end of those cycles with nVida and ATi graphics cards.

Grahamechanical can tell you about it. (I think he did above about trusty)  but saucy had those probs too.

---

