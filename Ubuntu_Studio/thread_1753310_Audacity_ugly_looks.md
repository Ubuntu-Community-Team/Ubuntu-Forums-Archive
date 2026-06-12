---
title: "Audacity ugly looks"
date: 2011-05-08
forum: Ubuntu Studio
---

### Post by esantidp on 2011-05-08
Hi people!

Im looking to record some samples through my line in and have heard of Audacity as a good choice. 

However [[IMG]http://img197.imageshack.us/img197/3123/audacitylooksbad.png[/IMG]](http://img197.imageshack.us/i/audacitylooksbad.png/)

Uploaded with [ImageShack.us](http://imageshack.us) <--- Audacity looks like this in my Ubuntu Box!

Is this a problem with qt4? Are there any other choices? I can't get Jack and Ardour to record either and have checked my alsamixer for mic and line-in already. 

I would consider CLI programs if necesary!

Thanks in advance

---

### Post by jejeman on 2011-05-09
What is your cpu, ram, graphic card (which driver), sound card and ubuntu version?

---

### Post by esantidp on 2011-05-09
Output for my lshw

WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 2600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:fc400000-fc47ffff ioport:24b0(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:2440(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:2460(size=32)
        *-usb:2 UNCLAIMED
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:fc480000-fc4803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:1000(size=4096) memory:fc500000-fc7fffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5782 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: eth0
                version: 03
                serial: 00:13:21:5e:db:69
                width: 64 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5782-v3.13 latency=64 mingnt=64 multicast=yes
                resources: irq:20 memory:fc500000-fc50ffff
           *-multimedia
                description: Multimedia audio controller
                product: CM8738
                vendor: C-Media Electronics Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=C-Media PCI latency=66 maxlatency=24 mingnt=2
                resources: irq:16 ioport:1000(size=256)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:24a0(size=16) memory:40000000-400003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:fc00(size=32)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:df:e1:6b:f8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.65 multicast=yes wireless=IEEE 802.11bg

I'm using Ubuntustudio10.04 with the KXstudio PPAS

---

### Post by satanselbow on 2011-05-09
Audacity is an excellent audio editor - it is however hideously ugly as the dev team have good ears but bad eyes :popcorn: 

That really is as pretty as it gets - excellent software but ugly as hell :(

[IMG]http://i56.tinypic.com/fwixsg.jpg[/IMG]

... my pretty...

---

### Post by jejeman on 2011-05-09
So you have:
Intel(R) Celeron(R) CPU 2.60GHz
Intel 82865G Integrated Graphics Controller
audio card CM8738
Ubuntustudio10.04 with the KXstudio PPAS

on the screen shot of audacity you are only missing the menu bar. Rest looks ok. Try to change the desktop theme.

Can you start jack, is it running stable?

---

### Post by esantidp on 2011-05-09
Jack Works fine, though i needed to make some tweaking to make it work. 


Will try and change the theme

---

### Post by esantidp on 2011-05-09
Changed the desktop theme, no good either.

---

### Post by mikeymo1741 on 2011-05-09
Are you using Unity, or Gnome?  I've read that the Unity desktop can cause Audacity's GUI to break.  

In any case, Audacity is an [ugly joint]("http://4.bp.blogspot.com/_PZ6CW7H68p0/SwVjyrxqjYI/AAAAAAAAAqk/ats7au5jgkE/s1600/SS1.png")...

---

### Post by Renegade Electron on 2011-05-10
What about Ardour as an alternative to Ubuntu Studio or Audacity? Any opinions on the comparison of quality and dependability between these programs?

---

### Post by jejeman on 2011-05-10
How can Ardour be alternative to Ubuntu Studio? One is application, the other gnu/linux distribution?

---

### Post by esantidp on 2011-05-10
Not using Unity IIRC, I'll check out. 

Ardour runs fine. 

I read in another post that Audacity runs on GTK1, Im definetly running Gnome on GTK2, can this be the problem?

---

### Post by cchhrriiss121212 on 2011-05-10
This is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/660314](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/660314)

---

### Post by esantidp on 2011-05-11
The menu is there, the thing is that everything in it is just like a line _________. The trick mentioned in the bug did not work for me :(

---

