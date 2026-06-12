---
title: "First Crash On Karmic Released Version"
date: 2009-10-29
forum: The Cafe
---

### Post by Johnsie on 2009-10-29
Amsn crashed in under two minutes of me trying Karmic when I sent a voice message. Bug reported. Looks like there are some stability issues...

---

### Post by Cam42 on 2009-10-29
Would that be the Amsn devs fault?

---

### Post by Icehuck on 2009-10-29
> **Johnsie said:**
> Amsn crashed in under two minutes of me trying Karmic when I sent a voice message. Bug reported, not impressed.

Blasphemy! Ubuntu is perfect!  :popcorn:

Thank you for reporting bugs it really does help make a difference.

---

### Post by Johnsie on 2009-10-29
Second crash... went to start a 'quick race' in Torcs and the window disappeared. Will attempt to start another race and see what happens.




> 

john@johns-laptop:~$ torcs
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
WARNING: ssgLoadTexture: Cannot determine file type for './(null)'
linuxModLoad: ...  /usr/lib/torcs/drivers/cylos1/cylos1.so: cannot open shared object file: No such file or directory
Pb with loading /usr/lib/torcs/drivers/cylos1/cylos1.so driver
No driver for that race...



With regard to who's fault the amsn crash was... That could be anyone... The people who packaged the application, the people who developed the sound drivers, the developer of amsn. I'd need to replicate the bug to try and find out what caused it. It's not about placing blame, it's about getting to the root of the problem  and getting it fixed. If I was a first time user those bugs would've been a bad first impression, especially since Windows 7 is now so stable.

---

### Post by Johnsie on 2009-10-29
I'm not sure if this is a glitch or not, but the first time I ran empathy it immediately asked me if I wanted to import my settings from Pidgin... I clicked 'yes' because I didn't really fancy typing in all my IM details. Unfortunately it seems to have imported all the accounts twice. So I have two records for each account.

I was unable to replicate the problem with AMSN, but the responsiveness of clicking 'send' button on a voice message is pretty bad. If it's doing something then it should indicate that it is doing something.

---

### Post by pwnst*r on 2009-10-29
your box is possessed.  -> exorcism.

---

### Post by Johnsie on 2009-10-29
New problem

telepathy-butterfly closed unexpectedly.

[Screenshot]("http://i564.photobucket.com/albums/ss83/steekyjim/Screenshot.png")

---

### Post by NoaHall on 2009-10-29
Hm. Try running "sudo ldconfig" - it might help with the file missing thing.

---

### Post by Johnsie on 2009-10-29
nope, it still happens. What does that command actually do? There was no output.

---

### Post by NoaHall on 2009-10-29
See here -> [http://linux.die.net/man/8/ldconfig](http://linux.die.net/man/8/ldconfig)

It explains it better than me.

Anyway, it was just a suggestion - not a true fix.

What hardware do you have? (mainly, graphics card and amount of RAM/CPU clock)

---

### Post by Johnsie on 2009-10-29
telepathy-butterfly just crashed again. I might just switch back to pidgin.

My hardware is just a run of the mill atom netbook with Intel graphics:

> 
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 994MiB
     *-cpu
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
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
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fe980000-fe9fffff ioport:cc80(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe940000-fe97ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fe880000-fe8fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fe938000-fe93bfff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:d000(size=4096) memory:fea00000-feafffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:03:0d:ad:a9:37
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.100 latency=0 multicast=yes
                resources: irq:26 ioport:dc00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:feae0000-feafffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: RTL8187SE Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 22
                serial: 00:21:85:7a:86:e0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
                resources: irq:17 ioport:ec00(size=256) memory:febfc000-febfffff
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:cc00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c480(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe937c00-fe937fff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage



---

### Post by NoaHall on 2009-10-29
And this is a fresh install?

If not, try uninstalling the apps, and reinstalling.

---

### Post by Johnsie on 2009-10-29
Nope, it's an standard upgrade from a perfectly working Jaunty. The upgrade process was actually very smooth.

---

### Post by NCLI on 2009-10-29
Since you're experiencing problems, I'd recommend a fresh install, without formatting your /home of course.

---

### Post by Johnsie on 2009-10-29
I'm not going to reinstall the whole operating system just because three programs don't work properly. I could spend several hours setting it all up again and still have the same issues.

I've found out that the telepathy-butterfly bug is quite common:

[https://bugs.edge.launchpad.net/ubuntu/+source/pymsn/+bug/391912](https://bugs.edge.launchpad.net/ubuntu/+source/pymsn/+bug/391912)

Hopefully it will be resolved quickly, but in the meantime I will go back to pidgin for my msn purposes.

I can survive without torcs... and well, amsn has never been the most stable of programs for me. I'll just not use the voice messaging when I'm on Linux.

---

### Post by negotiation on 2009-10-30
Same story here: smooth upgrade from Jaunty - empathy looks to be causing it. Ditching empathy, back to pidgin.

---

