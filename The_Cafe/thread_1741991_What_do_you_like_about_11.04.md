---
title: "What do you like about 11.04?"
date: 2011-04-28
forum: The Cafe
---

### Post by josephmills on 2011-04-28
I was just wondering what you like or don't like about natty 11.04 thanks

---

### Post by BrokenKingpin on 2011-04-28
Xfce 4.8 is in the repos.

---

### Post by wojox on 2011-04-28
I never liked docks before. Now I do. Also the way the windows integrate into the panel.

---

### Post by sikander3786 on 2011-04-28
Unity itself :-D

Something new to learn and tease my brain :-)

Windows don't minimize when I click the icon in dock :-( Tease...

---

### Post by josephmills on 2011-04-28
very cool! I am just thinking about doing the upgrade but would like to here more thanks for you time here is what I am working with ```
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
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 1733MHz
          capacity: 1733MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
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
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dff00000-dff7ffff ioport:ec38(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:dff80000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:dfd00000-dfdfffff ioport:44000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:15:c5:01:8e:ec
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5751-v3.29a latency=0 multicast=yes
                resources: irq:16 memory:dfdf0000-dfdfffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:dfc00000-dfcfffff ioport:40000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCI6515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:dfc00000-dfc00fff ioport:1400(size=256) ioport:1800(size=256) memory:40000000-43ffffff memory:48000000-4bffffff
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6515 SmartCard Controller
                vendor: Texas Instruments
                physical id: 1.5
                bus info: pci@0000:03:01.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:dfcfc000-dfcfcfff memory:dfcfd000-dfcfdfff
           *-network
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:17 memory:dfcfe000-dfcfffff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dfebfe00-dfebffff memory:dfebfd00-dfebfdff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:ee00(size=256) ioport:ec80(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:8c:00:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A ip=192.168.*>* multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```
```


free
             total       used       free     shared    buffers     cached
Mem:       1017412     907936     109476          0      62296     348796
-/+ buffers/cache:     496844     520568
Swap:      1648636      10452    1638184

```
what do you think ?

---

### Post by arzali on 2011-04-28
What  I like:
Fullscreen flash performance is much much better than on 10.10
the Launcher and integrated title bar into the panel.

What i don't like:
No netspeed monitor for the unity panel
some compiz actions don't work.

All in all its a nice release but still needs some work

---

### Post by josephmills on 2011-04-28
I really like cairo dock to have tux walk around my dock. Any one tried it yet?

---

### Post by murderslastcrow on 2011-04-28
Being able to scrub through all of the indicators and menu items on the panel without unclicking and reclicking. Oh yeah, and everything else.

---

### Post by Version Dependency on 2011-04-28
I love the idea of lenses...and the fact that companies can create custom lenses for Unity.  I have the Gwibber lens and the Askubuntu lens installed.  Very nice stuff.  I think we will see many more large websites creating custom lenses.

---

### Post by cgroza on 2011-04-28
So far, I love it all.

---

### Post by cosine352 on 2011-04-28
I have black screen after upgrade from 10.10. I am missing out all the fun.](*,)](*,)

---

### Post by MooPi on 2011-04-28
So far I'm drawing a blank screen. Can't seem to get it to load on a good system. Granted it is the lowest spec machine I own , it should still work. Integrated Nvidia graphics maybe the issue ? Was hoping to test it out but the alternate install wouldn't work either.

---

### Post by kaldor on 2011-04-28
Quite fond of Unity, but it needs a lot of work. It feels buggy and incomplete, but it's definitely a great DE.

---

### Post by cosine352 on 2011-04-30
ubuntu is becoming a crap. Now the focus is on eye candy rather than stability. disappointed.

---

### Post by Frogs Hair on 2011-04-30
11.04 is very fast on my hardware and I am pleasantly surprised by Unity now that I am getting used to it . 

I hated the idea of unity when I first heard it was to be used and I actually referred to it as the Purbal Place desktop .

Finding a theme I like helps , but that was trial and error due to the fact that some GTK themes work and others don't.

---

### Post by TeoBigusGeekus on 2011-04-30
Unity will eventually mature and become a great DE, thanks to all us beta testers.

Canonical on the other hand should try to fix Ubuntu's large number of bugs before concentrating on making it look like a Fisher Price toy for the sake of newcomers' comfort.

---

### Post by SoFl W on 2011-04-30
> **cosine352 said:**
> ubuntu is becoming a crap. Now the focus is on eye candy rather than stability. disappointed.

+1  But I am not sure it is Ubuntu, but rather Gnome?

> **TeoBigusGeekus said:**
> Canonical on the other hand should try to fix Ubuntu's large number of  bugs before concentrating on making it look like a Fisher Price toy for  the sake of newcomers' comfort.

The problem is the more eye candy it becomes I think it will drive away new comers.  After looking at the latest, I no longer feel confident to tell people about Ubuntu or Linux.

---

### Post by disabledaccount on 2011-04-30
Ubuntu as a distribution i great - I don't have to waste the time to get things working - everything (almost) works OOTB. Besides, every new version is generally faster and do not need HW upgrades - unlike "other" desktop system(s) :)

I don't like unity - I know, I know - recursive discussions is full of topics about this.
But I've just realised that there can be reason for crating this new GUI (at first I just though that someone made terrible mistake). I think that Canonical plans to attack mobile market and Unity has to be heavily tested first. Secondary, it's easier to mantain one GUI for desktops and mobiles...

---

### Post by Perosteck on 2011-04-30
Can't see much eye candy. The launcher bar is more functional than eye candy.

---

### Post by trollger on 2011-04-30
Firefox 4
Libreoffice

and GNOME 3

---

### Post by m_duck on 2011-04-30
What a refreshing thread - some positive remarks about Unity! Unfortunately I don't have the time to test it at the moment but I will be interested to try it come summer.

---

### Post by cap10Ibraim on 2011-04-30
> **sikander3786 said:**
> 
Windows don't minimize when I click the icon in dock :-( Tease...
did you report this missing feature , i just realized that it's missing :P

---

### Post by cap10Ibraim on 2011-04-30
> **cosine352 said:**
> ubuntu is becoming a crap. Now the focus is on eye candy rather than stability. disappointed.
ABOUT HIGH PERFORMANCE COMPUTING 
[http://arstechnica.com/science/news/2011/04/high-performance-computing-on-gamer-pcs-part-2-the-software-choices.ars](http://arstechnica.com/science/news/2011/04/high-performance-computing-on-gamer-pcs-part-2-the-software-choices.ars) 
> The master and all workers run Ubuntu server edition 

---

### Post by oldos2er on 2011-04-30
> **josephmills said:**
> I was just wondering what you like or don't like about natty 11.04 thanks
 
I like the fact that I can run most any DE I wish on it.

---

