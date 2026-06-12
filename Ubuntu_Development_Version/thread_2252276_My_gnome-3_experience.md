---
title: "My gnome-3 experience"
date: 2014-11-10
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-11-10
Well... I thought I would post this here. I downloaded the daily-live current ubuntu-gnome iso and proceeded to  use SDC to install it to USB 2.0.  A phenomenon occured (again). It took only 3 seconds to load the .iso!!! I thought something was busted, but , nope .. here I am in ubuntu-gnome "live" and I must conceed it is as awesome as ever.

  Thanks to Canath for the recommend. I never thought they were this far with it.

Congrads to devs.

  Regards...

edit:

I'll explore around a bit  and get back and report in the other threads already opened.

---

### Post by ventrical on 2014-11-10
Ok... what I am seeing now is a little bit of unity8, ubuntu-desktop, unity 2D !! and other kewl  graphicals. with a gnome3 twist. So it leads me to ask the question ;  Why unity8??

---

### Post by grahammechanical on 2014-11-10
With respect, wrong question. Why Unity at all? But lets us not go into that. It is the past.

What you are seeing is evidence of Unity using existing APIs in Gnome 3 DE. At least I think so. You are looking at an alternative reality. I wonder about those many people who hate Unity. Would they like Gnome 3 shell? With a little bit of cooperation from Gnome devs and Unity would have been an alternative login session to Gnome 3 shell and not a replacement.

Freedom of choice is good, Even if it is not to our taste.

---

### Post by Hazzabin on 2014-11-10
G'day Ventrical

this little app into Gnome I quite like

[http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard](http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard)

it is oldish but still working on my 15.04 install

---

### Post by ventrical on 2014-11-10
Thanks for input.  Gnome3 worked great on my Sandy Bridge Intel graphics. When I booted live on two seperate machines with nVidia adapters the gnome-3 desktop was persona non gratais (terminal only.)  So I can use gnome3 on my sandy bridge . Looks like others will have to wait. Haven't tried my AMD ATI HD yet.

---

### Post by ventrical on 2014-11-10
> **grahammechanical said:**
> With respect, wrong question. Why Unity at all? But lets us not go into that. It is the past.

  You are looking at an alternative reality. 

:)

  I think for tonight I will take the cookie that the Oracle has baked, go to sleep and try again in the morning. :)

Regards..

---

### Post by ventrical on 2014-11-10
> **Hazzabin said:**
> G'day Ventrical

this little app into Gnome I quite like

[http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard](http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard)

it is oldish but still working on my 15.04 install


I am going to try and see if I can get a nVidia install working first.

Thanks..

---

### Post by Hazzabin on 2014-11-10
Thought you be way gone asleep by now.

I have to change that idea/link as mine came across from an 'UPGRADE' not a iso latest install, latest install it's not working or listed in dconf to be able to change/modify

Sorry    least ways it's not my latest November 10th ISO :mad: :P

---

### Post by Chanath on 2014-11-11
> **ventrical said:**
> Ok... what I am seeing now is a little bit of unity8, ubuntu-desktop, unity 2D !! and other kewl  graphicals. with a gnome3 twist. So it leads me to ask the question ;  Why unity8??

I wrote a little bit about why Unity in Ubuntu-Gnome here; [http://ubuntuforums.org/showthread.php?t=2251751](http://ubuntuforums.org/showthread.php?t=2251751)

If I try to uninstall libunity9, Ubuntu-Gnome would break, i.e, Brasero, Empathy, Nautilus, Shotwell, Ubuntu-Gnome-desktop would alos be uninstalled. I wonder what would happen, if I uninstall it and other unity libraries and then, install Gnome 3.14 through GNOME 3 Staging PPA. Would that ppa too have all these unity connected libraries?  

The "Gnome-classic" session Ubuntu-Gnome has quite unresponsive panels, and if we'd like to have responsive panels and install Gnome-flashback, then again unity libraries are needed.

---

### Post by Chanath on 2014-11-11
> **Hazzabin said:**
> G'day Ventrical

this little app into Gnome I quite like

[http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard](http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard)

it is oldish but still working on my 15.04 install

The app-folder-categories is no more there in dconf>org>gnome>shell.
Some info about categories is here; [http://blogs.gnome.org/mclasen/2014/03/17/app-folder-configuration/](http://blogs.gnome.org/mclasen/2014/03/17/app-folder-configuration/)
I am still trying to find out how to implement it.

Edit: I can't find gnome-software, so the only way to get the "categories," at least for me, is by using an extension Gno-menu.

---

### Post by ventrical on 2014-11-11
> **Chanath said:**
> I wrote a little bit about why Unity in Ubuntu-Gnome here; [http://ubuntuforums.org/showthread.php?t=2251751](http://ubuntuforums.org/showthread.php?t=2251751)

If I try to uninstall libunity9, Ubuntu-Gnome would break, i.e, Brasero, Empathy, Nautilus, Shotwell, Ubuntu-Gnome-desktop would alos be uninstalled. I wonder what would happen, if I uninstall it and other unity libraries and then, install Gnome 3.14 through GNOME 3 Staging PPA. Would that ppa too have all these unity connected libraries?  

The "Gnome-classic" session Ubuntu-Gnome has quite unresponsive panels, and if we'd like to have responsive panels and install Gnome-flashback, then again unity libraries are needed.

At current I am just curious as to why nVidia adapters roll right to terminal in the 'live' session. I am going to try a hard install later today ... but work calls once again :)  btw .. It's been a while since I have tested gnome-3... thats my problem .. not anyone else .. so I am a little rusty and it may take me a bit to get acclimatized once again.

Regards..

---

### Post by grahammechanical on 2014-11-11
Is there such a thing as a Gnome distribution? I do not think so. Ubuntu Gnome is not a Gnome distribution. It is a Ubuntu distribution which in turn is a Debian distribution. Take Debian, add Gnome 3 DE and then add Gnome 3 shell and you may have a distribution with next to no bits of Unity in there. But it would not be a flavour of Ubuntu.

---

### Post by ventrical on 2014-11-11
Started it  up just now .. live session.. works like a charm.

```

    *-display
                description: VGA compatible controller
                product: G71GL [Quadro FX 3500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:44 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fc000000-fcffffff ioport:9c00(size=128) memory:fe7e0000-fe7fffff
        

```

edit:

Not sure why it works now. I did not change the iso at all. 

I'll try my other machines with nVidia graphics..

Regards.

---

### Post by ventrical on 2014-11-11
Ok... I got the boot to terminal again and so I tried:

```

sudo service gdm start

```

and then in a few seconds .. boom! 'live' gnome3 desktop running on USB.

```

 *-display
             description: VGA compatible controller
             product: GT218 [GeForce 210]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:43 memory:fb000000-fbffffff memory:b0000000-bfffffff memory:ce000000-cfffffff ioport:bc00(size=128) memory:fcf00000-fcf7ffff

```

---

### Post by ventrical on 2014-11-11
Other Graphical Notes:

  I like the way the control panel works on shutdown. It is very graphically sophisticated yet easy to use. Nice eye candy for sure. It's like the whole DE is a convergence from all 4 sides of the screen that pull in to center view and then dash back out again.  Not so buggy or unstable.  Much more workable as a rolling desktop that the other one there .. errrmm.. unity8 that is :)

Regards.

---

### Post by ventrical on 2014-11-11
I did a hard install  <choose alongside> and it was quite a rather effervescent experience. Ubiquity ran smoothly and the whole process was refreshing. There are no nVidia/nouveau problems here - but then again this install came off the Nov. 10th daily-live/current , so I haven't update/upgraded yet. :)

It is currently running normally cool on this 45nm lithography Core 2 Duo with Speed Step enabled. (this is one of my overclocking machines)  

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.26 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.26 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.02 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +11.98 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      4066 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +37.5°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +39.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +38.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +31.0°C  (high = +80.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +41.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +130.0°C, hyst =  +2.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping    : 6
microcode    : 0x60b
cpu MHz        : 1998.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6295.92
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping    : 6
microcode    : 0x60b
cpu MHz        : 1998.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6295.92
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

ventrical@ventrical-System-Product-Name:~$ 

```

on this hardware profile.

```


ventrical@ventrical-System-Product-Name:~$ lshw
WARNING: you should run this program as super-user.
ventrical-system-product-name
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2000MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2997MHz
          capacity: 2997MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:9000(size=4096) memory:fa700000-fe7fffff ioport:bfe00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: G71GL [Quadro FX 3500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:45 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fc000000-fcffffff ioport:9c00(size=128) memory:fe7e0000-fe7fffff
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
             resources: irq:16 ioport:dc00(size=32)
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
             resources: irq:17 ioport:e000(size=32)
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
             resources: irq:18 memory:febffc00-febfffff
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
             resources: irq:44 memory:febf8000-febfbfff
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
             resources: irq:41 ioport:1000(size=4096) memory:80000000-803fffff ioport:dfe00000(size=1048576)
        *-pci:2
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
             resources: irq:42 ioport:2000(size=4096) memory:fe900000-fe9fffff ioport:80400000(size=2097152)
           *-network
                description: Ethernet interface
                product: Attansic L1 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:18:f3:70:0f:9e
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=192.168.2.38 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:46 memory:fe9c0000-fe9fffff memory:fe9a0000-fe9bffff
        *-pci:3
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
             resources: irq:43 ioport:a000(size=4096) memory:fe800000-fe8fffff ioport:80600000(size=2097152)
           *-storage
                description: SATA controller
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:16 memory:fe8fe000-fe8fffff memory:fe8e0000-fe8effff
           *-ide
                description: IDE interface
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=8) ioport:a480(size=4) ioport:a400(size=16)
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
             resources: irq:23 ioport:d480(size=32)
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
             resources: irq:19 ioport:d800(size=32)
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
             resources: irq:18 ioport:d880(size=32)
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
             resources: irq:23 memory:febff800-febffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:fea00000-feafffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:21 memory:feaff800-feafffff ioport:bc00(size=128)
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
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
             resources: irq:19 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) ioport:e080(size=16)
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
             resources: memory:80800000-808000ff ioport:400(size=32)
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
             resources: irq:19 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) ioport:c800(size=16)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ventrical@ventrical-System-Product-Name:~$ 

```

So, as I am navigating around on this polished gem , rolling release desktop, I find it hard to make a negative comment about the developers not putting any special care into this project because IMHO .. it's another masterpiece of coordinated and dedicated effort by Ubuntu, Canonical and partners and U+1 testers.

Regards..

---

### Post by sammiev on 2014-11-11
> **ventrical said:**
> I did a hard install  <choose alongside> and it was quite a rather effervescent experience. Ubiquity ran smoothly and the whole process was refreshing. There are no nVidia/nouveau problems here - but then again this install came off the Nov. 10th daily-live/current , so I haven't update/upgraded yet. :)

It is currently running normally cool on this 45nm lithography Core 2 Duo with Speed Step enabled. (this is one of my overclocking machines)  

So, as I am navigating around on this polished gem , rolling release desktop, I find it hard to make a negative comment about the developers not putting any special care into this project because IMHO .. it's another masterpiece of coordinated and dedicated effort by Ubuntu, Canonical and partners and U+1 testers.

Regards..

WoWser! what a write up.

---

### Post by Chanath on 2014-11-11
> **ventrical said:**
> I did a hard install  <choose alongside> and it was quite a rather effervescent experience. Ubiquity ran smoothly and the whole process was refreshing. There are no nVidia/nouveau problems here - but then again this install came off the Nov. 10th daily-live/current , so I haven't update/upgraded yet. :)

It is currently running normally cool on this 45nm lithography Core 2 Duo with Speed Step enabled. (this is one of my overclocking machines)  

So, as I am navigating around on this polished gem , rolling release desktop, I find it hard to make a negative comment about the developers not putting any special care into this project because IMHO .. it's another masterpiece of coordinated and dedicated effort by Ubuntu, Canonical and partners and U+1 testers.

Regards..

Install some extensions and check whether these extensions get disabled after a reboot. Also see whether you can create categories.

---

### Post by ventrical on 2014-11-11
> **sammiev said:**
> WoWser! what a write up.

It is what it is. :)   I'll have to strike some of my earlier critiques from an instructional develpment point of veiw as Ubuntu-Gnome may be easier to teach than that which I previously stated.  Here , in testing, I think we have to take the good, the bad and the ugly and work with that.. and when we see the good ,, we should report that also. IMO.

Regards..

---

### Post by ventrical on 2014-11-11
> **Chanath said:**
> Install some extensions and check whether these extensions get disabled after a reboot. Also see whether you can create categories.

Extensions where ?? In firefox?

How to create categories?  I told you guys I'm a little rusty :)

Regards..

---

### Post by Hazzabin on 2014-11-11
Extensions for Gnome get from inside Tweak, once Tweak is open down left side you should see a box with 'Extensions' click that and another list opens with different extentions you can either enable or not

quite a few still do not work, can get more from here too

[https://extensions.gnome.org/#page=1](https://extensions.gnome.org/#page=1)

---

### Post by ventrical on 2014-11-11
> **Hazzabin said:**
> Extensions for Gnome get from inside Tweak, once Tweak is open down left side you should see a box with 'Extensions' click that and another list opens with different extentions you can either enable or not

quite a few still do not work, can get more from here too

[https://extensions.gnome.org/#page=1](https://extensions.gnome.org/#page=1)

Ok..  when I enabled a few extension it locked the mouse , reported a problem .. but hey .. we are in early development here.  Does not seem to be a big issue. Just control of eye candy. But extensions did not reset after reboot.. only error report from apport.

honestly ..  it's getting better by the minute :)

---

### Post by Hazzabin on 2014-11-11
Great mate, slightly off topic how the heck are you getting thumbnails/images up, I tried b4 so you could 'SEE' the Tweak thing 

and yup old age don't help either :)

---

### Post by ventrical on 2014-11-11
Anyone care to add to this bug? or is there already report under different file?

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1391690](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1391690)

thnks

---

### Post by ventrical on 2014-11-11
> **Hazzabin said:**
> Great mate, slightly off topic how the heck are you getting thumbnails/images up, I tried b4 so you could 'SEE' the Tweak thing 

and yup old age don't help either :)

I just randomly chose the below extensions. Now the desktop acts like a suped-up gnome-classic pulldown menu when you click <applications> and the windows switcher pops  when you slam the mouse up top-left. So basically you have a souped up version of olde gnome slipping and sliding on gnome-shell!:) It's just awesome.! :) lol

Remember .. for me it's been a while .. so I more or less just got me toe in the water right now :)

Regards

---

### Post by ventrical on 2014-11-11
Thing is that this ubuntu-gnome is running on xorg and it's putting the other servers to shame. I can't believe .. but it's happening.

---

### Post by sammiev on 2014-11-11
I wish they would give us 3.14 to play with. I do not want to add any ppa, I want to test it as is.

---

### Post by Chanath on 2014-11-12
I installed Gnome 3.14.1 through the ppa, to check whether the extensions would stay enabled after a reboot, it didn't. By the way, I suppose it is the ppa that finally moves into Ubuntu repos as gnome 3.14.1. In the tweak-tool, everything gets disabled after rebooting, except window, gtk+, icons and cursor themes.

the Tweak-tool was already installed in ubuntu-gnome vivid, so if there is a bug in it, it came from compiling it in the DE. I have a Debian Gnome 3.14.1 install in my laptop, and the gnome 3.14.1 came from the Debian testing repo, just like Vivid is a testing repo, and there I installed the Tweak-tool manually. In the Debian Testing (now frozen) all extensions stay enabled after rebooting.  There it is deb packages, and here too it is deb packages, but something goes wrong, when reinventing the wheel in compiling Ubuntu deb packages. 

Also, try if you can make folder categories in folder-children and how to populate them.

---

### Post by Hazzabin on 2014-11-12
[COLOR=#000000]"Also, try if you can make folder categories in folder-children and how to populate them."

hey Canath, there was no way I could make that happen but I'm sure I'm doing something wrong 

I've not tried the debian install, maybe time I learn't :)

And thanks for your input,ideas too[/COLOR]

---

### Post by ventrical on 2014-11-12
> **Chanath said:**
> Install some extensions and check whether these extensions get disabled after a reboot. Also see whether you can create categories.

Yep .. thismornings startup .. those extension settings gone. Looks to be a random bug because it did not do it yesterday from reboot. They may only appear after hard boot.

Definitely a bug.

---

### Post by Chanath on 2014-11-12
> **Hazzabin said:**
> [COLOR=#000000]"Also, try if you can make folder categories in folder-children and how to populate them."

hey Canath, there was no way I could make that happen but I'm sure I'm doing something wrong 

I've not tried the debian install, maybe time I learn't :)

And thanks for your input,ideas too[/COLOR]

I cannot do this in the Debian install too, but at least two category folders (Sundry and Utilities) are there in the Fedora21 beta2. I downloaded it and checked that too. I read this, [http://blogs.gnome.org/mclasen/2014/03/17/app-folder-configuration/](http://blogs.gnome.org/mclasen/2014/03/17/app-folder-configuration/) and thinking how to go about it. There is a app called Software in it, but that doesn't have an "Add to folder" in it. Here is a screenshot of Software app. I can add a folder using Dconf-editor, but it doesn't show up in the Dash. I don't know how to use Dconf to populate them. By the way, Clasen has interesting thoughts on Gnome 3.

---

### Post by Chanath on 2014-11-12
> **ventrical said:**
> Yep .. thismornings startup .. those extension settings gone. Looks to be a random bug because it did not do it yesterday from reboot. They may only appear after hard boot.

Definitely a bug.

It is not a big deal right now, as Vivid is still in testing, but if people are testing the Ubuntu-gnome Vivid, it might stop them from continuing, as there are already distros with Gnome 3.14.1 without this problem. By the way, I find the U+1 has very little comments/posts, not like those days when Trusty was in testing, that is, not much traffic.

---

### Post by ventrical on 2014-11-12
> **Chanath said:**
> I cannot do this in the Debian install too, but at least two category folders (Sundry and Utilities) are there in the Fedora21 beta2. I downloaded it and checked that too. I read this, [http://blogs.gnome.org/mclasen/2014/03/17/app-folder-configuration/](http://blogs.gnome.org/mclasen/2014/03/17/app-folder-configuration/) and thinking how to go about it. There is a app called Software in it, but that doesn't have an "Add to folder" in it. Here is a screenshot of Software app. I can add a folder using Dconf-editor, but it doesn't show up in the Dash. I don't know how to use Dconf to populate them. By the way, Clasen has interesting thoughts on Gnome 3.

Yes .. unity7 is that popular. It's hard to give up once acclimatized to it.

Regards..

---

### Post by Chanath on 2014-11-12
> **ventrical said:**
> Yes .. unity7 is that popular. It's hard to give up once acclimatized to it.

Regards..

If I can autohide the top panel of Unity, I'd still use it. Gnome 3 comes up with many new stuff and there are lot of people, who keep on making extensions to it, so Gnome 3 is getting more and more interesting. Have you used the "old" Slingshot launcher? Its actions are much like the Unity Dash, and much easier to use too. If you install Gnome-flashback in vanilla Ubuntu, then autohide both panels, (or even delete one panel), install Plank dock, tweak it a bit, install the "old" Slingshot launcher and with Ubuntu's Compiz still there, you can have the effects, you can have a very nice working distro. Even though, you still have the Unity session (otherwise named Ubuntu session), you looking in there would be less and less. Zorin had done that quite nicely, and he had deleted both Gnome panels, and put in place the old AWN dock with some tweaking. I'd keep the top panel on, but auto hide it, and use the Plank dock and the old Slingshot. This is still true in Vivid vanilla Ubuntu. This can be done with Vivid Ubuntu-Gnome too. This can be done with Vivid Xubuntu, but with one Xfce autohiding panel, Plank dock and the old Slingshot and Kwin for eyecandy. You can use the "new" slingshot, but who needs the eOS extra libraries?

---

### Post by ventrical on 2014-11-12
> **Chanath said:**
> If I can autohide the top panel of Unity, I'd still use it. Gnome 3 comes up with many new stuff and there are lot of people, who keep on making extensions to it, so Gnome 3 is getting more and more interesting. Have you used the "old" Slingshot launcher? Its actions are much like the Unity Dash, and much easier to use too. If you install Gnome-flashback in vanilla Ubuntu, then autohide both panels, (or even delete one panel), install Plank dock, tweak it a bit, install the "old" Slingshot launcher and with Ubuntu's Compiz still there, you can have the effects, you can have a very nice working distro. Even though, you still have the Unity session (otherwise named Ubuntu session), you looking in there would be less and less. Zorin had done that quite nicely, and he had deleted both Gnome panels, and put in place the old AWN dock with some tweaking. I'd keep the top panel on, but auto hide it, and use the Plank dock and the old Slingshot. This is still true in Vivid vanilla Ubuntu. This can be done with Vivid Ubuntu-Gnome too. This can be done with Vivid Xubuntu, but with one Xfce autohiding panel, Plank dock and the old Slingshot and Kwin for eyecandy. You can use the "new" slingshot, but who needs the eOS extra libraries?


 I appreciate all that you are saying and  *I* will certainly give some of those suggestions a whirl but I deal with customers who are basically computer illiterate. <I do not want to get to far off topic here>. Even before Unity came out with the introduction of Natty Narwahl it was difficult to teach people to use Gnome (which is now gnome-classic) but I have had some success teaching people to use ubuntu-desktop (currently unity7). For what most people use their PCs for , browsing , entertaiment, e-mail it is fairly easy to  help people make the migrartion from Windows XP. etc  to ubuntu-linux. I have tried to teach L,X and K buntus but people seem to meander instantly, loose interest and go back to Windows.  Unity captures their attention and imagination and it is fundementally easier to use and easier to teach.

 But in all fairness to gnome3 and it's current state, I can teach it to younger persons, programmers and enthusiasts and those that already have a level of computer expertise but not to general noobs or persons that are challanged in other ways. Those end_users that I have helped migrate from Windows to Unity rarely ever place service or help calls to me and they catch on really fast.  It's not that gnome3 has a teachability problem, it's just me , the teacher, that knows about the downtime it takes to go through all the fiddle sticks and I don't have much patience in that arena :)

Regards..

---

### Post by Chanath on 2014-11-12
> **ventrical said:**
> I appreciate all that you are saying and  *I* will certainly give some of those suggestions a whirl but I deal with customers who are basically computer illiterate. <I do not want to get to far off topic here>. Even before Unity came out with the introduction of Natty Narwahl it was difficult to teach people to use Gnome (which is now gnome-classic) but I have had some success teaching people to use ubuntu-desktop (currently unity7). For what most people use their PCs for , browsing , entertaiment, e-mail it is fairly easy to  help people make the migrartion from Windows XP. etc  to ubuntu-linux. I have tried to teach L,X and K buntus but people seem to meander instantly, loose interest and go back to Windows.  Unity captures their attention and imagination and it is fundementally easier to use and easier to teach.

 But in all fairness to gnome3 and it's current state, I can teach it to younger persons, programmers and enthusiasts and those that already have a level of computer expertise but not to general noobs or persons that are challanged in other ways. Those end_users that I have helped migrate from Windows to Unity rarely ever place service or help calls to me and they catch on really fast.  It's not that gnome3 has a teachability problem, it's just me , the teacher, that knows about the downtime it takes to go through all the fiddle sticks and I don't have much patience in that arena :)

Regards..

OK. 
We are here at U+1 to discuss things about the development release. I understand you are a teacher, and Unity appears to be good enough for people coming from Windows. But, once Unity moves to 8 or Next, it would be quite hard to teach them, even though it might be in the mobiles and tablets. Jumping in the bangwagon against Android won't give much susccess or any success at all, as Android would go much further. Anyway, I wish Ubuntu luck in this.

I have gone through Zorin quite a lot, and have seen so called non-Windows laptops with Zorin in shops in ceratin countries, as it looks so like Win7. And, Zorin is quite easy to teach, but also Zorin is quite easy to break, i.e, if certain apps would die, or made to die, they won't come back. Now, Leaving aside Zorin, what I suggest to you is to install Gnome-flashback in your Vanilla Ubuntu and check that out. You'd have two panels, and one of them can be deleted, and the window-list could be brought into the remaining panel. This remaining panel, the one on the top could be brought down and then made thicker, say 36-40 pixels. If you make it 41, then it looks just like the Win7 panel. It can be autohidden. You'd need a Win7 lookalike menu (app-finder), and that could be Gno-menu. People from windows like to type to find the app, and that is there in Gno-menu. 

If instead of Vanilla Ubuntu, you use Xubuntu, the Win7 like menu is already there, the Whisker menu. The Xfce4 file manager Thunar is real gem, much better than Nautilus. For guys like us, who'd love to look in everywhere, Thunar is quite helpful, for example, if you want to open in the text editor any .desktop in /usr/share/applications, all you have to do in Thunar is right click. Anyway, Xubuntu has only one panel now, and all you have to do is bring it down and thicken it to 40 pixels, and autohide it. You can even color it to look just like the Win7 panel. If you add Kwin, you can have quite nice eye-candy with cube and all, which of course Windows doesn't have. By the way, I've downloaded Xubuntu Vivid and writing from the live session. 
Regards!

---

### Post by Chanath on 2014-11-12
Ventrical, I am attaching a Xubuntu Trusty screenshot, the panel is not colored in blue, but has a changed theme. See whether it looks like a Win7 panel with lookalike menu.

---

### Post by ventrical on 2014-11-12
Nice pic indeed.

Back to case in point.

  I just came back from field trip consultation.  I was advising a client to migrate from Windows XP to Unity desktop but I decided to bring gnome3 15.04 live iso. It worked perfectly  but the client would have none of it. There was no way of convincing to use gnome3 but client was interested in Unity concept. So next visit will be an ubuntu-desktop trusty install. There are literally millions of millions of end_users who will not let go of XP.  When you tell them that the security updates have reached their EOL they look at you like you are a martian and then proceed to tell you how they want you to fix Windows XP. So I did.

 Unity8 and convergence-

Mark Shuttleworth has captained the ubuntu ship quite dilligently. He knows what he is doing. We'll have to wait and see. In my country , Canada, all the elementary schools are using slates .. even in grade1..so unity8 may find a place there and I have to realize that nothing that I say can stop the convergence ball from continuing to roll :)lol

Regards..

---

### Post by Chanath on 2014-11-12
> **ventrical said:**
> Mark Shuttleworth has captained the ubuntu ship quite dilligently. He knows what he is doing. We'll have to wait and see. In my country , Canada, all the elementary schools are using *slates* .. even in grade1..so unity8 may find a place there and I have to realize that nothing that I say can stop the convergence ball from continuing to roll :)lol

Regards..

Slates, you say? Are you living in BC?
As you might have noticed in Canada, most of the rich guys live in a vacuum, don't really know how it is on the street. I have few friends, who are on the top of their companies, and they are really lonely up there on that top. Mark is also on the very top.
By the way that picture is an original Win7 wallpaper. 
I think I should make a distro off Xubuntu and upload it to Sourceforge. I've never uploaded one there yet. I'll learn to do that, I hope in time.

Oh, nearly forgot, in my Debian install, I saw there is a session Gnome with Wayland, and I could boot into it, only I don't know yet, how this Wayland works. The top panel was invisible, but when I came near and right-clicked, it opened the Dash. I'd play with it to see what's happening. I don't know what to expect either. 
Regards!

---

### Post by ventrical on 2014-11-12
Any pad, pod or tablet I use the generalization  as slate.

:)

---

### Post by DogMatix on 2014-11-12
Not intending to stray any further off topic but isn't the basic argument usability. Gnome 3 isn't currently used in our household. But Ubuntu, Lubuntu, Mac OSX, Android and Windows are. My wife and seven year old son use a combination of all of those platforms, I don't even know if they know which is which and I don't even think they particularly care as long as they can access the apps they need (i.e. Facebook, YouTube, Email, Internet browser, Holiday photos, etc.) and they are pretty much identifiable by icons.

My son particularly is intriguing to watch as by trial and error he will accomplish the task he has intended on different desktop environments and user interfaces in relatively quick time.

I might just install a Gnome 3 desktop and watch him figure it out.

---

### Post by grahammechanical on 2014-11-12
So, what has been your experience of Ubuntu Gnome?

<sarcasm>That is the topic of this thread. Or have I got it wrong?</sarcasm>

This thread has gone from the Ubuntu Gnome experience on to questioning the ease of learning of Unity 8 and now it has moved on to implying that Mark Shuttleworth is isolated from the ordinary computer user. It is wrong.

We need reminding that this section of the "forum is for discussion of Vivid Vervet and Trusty Tahr point release testing only." I am quoting the message the moderators give to me every time I open this section.

I do not see that statement as giving us liberty to question the direction of Ubuntu development. 

I would not object to there being a thread on testing the Gnome Wayland compositor. The Ubuntu Gnome developers might one day like to offer users the option of running on Ubuntu Mir or Gnome Wayland (or whatever the compositor ends up being called).

@DogMatix

> [COLOR=#000000]My son particularly is intriguing to watch as by trial and error he will accomplish the task he has intended on different desktop environments and user interfaces in relatively quick time.[/COLOR]


Treasure those moments. The ability of children to learn new things and new ways brings joy to the heart.

Regards.

---

### Post by ventrical on 2014-11-12
> **grahammechanical said:**
> So, what has been your experience of Ubuntu Gnome?

<sarcasm>That is the topic of this thread. Or have I got it wrong?</sarcasm>

This thread has gone from the Ubuntu Gnome experience on to questioning the ease of learning of Unity 8 and now it has moved on to implying that Mark Shuttleworth is isolated from the ordinary computer user. It is wrong.


  I never implied that .. but I agree generally with your premise.

@Elfy,

Could you please move this thread to re-occuring discussions? 

Thank you.

Regards..

---

### Post by Chanath on 2014-11-13
> **ventrical said:**
> I never implied that .. but I agree generally with your premise.

@Elfy,

Could you please move this thread to re-occuring discussions? 

Thank you.

Regards..

Ventrical, I hope you won't move this thread somewhere else. If it moves, there is nothing much in U+1, other than your comment in another post, and that was 16 hours ago. There are two posts, commented more than 24 hours ago and two posts commented more than 48 hours ago. It is not like the Trusty U+1 days, no traffic at all. 

By the way, my Xubuntu Vivid refused to install, so I'd download it again sometime later in the evening. If I would be able to install it, I'd let you guys know what I do with it, of course, in another post. Hope some else would also try Xubuntu Vivid. I am still using Ubuntu-Gnome Vivid and test it against Debian Testing.
Regards!

---

### Post by ventrical on 2014-11-13
I also have an xubuntu vivid install that i am working .. but let's try a little to stay on topic:) I know I am probably the greatest offender with being off topic. Having said that , I certainly am not trying to make this thread a typical recurring discussion ... ie; unity vs this or that... or 

> 
As you might have noticed in Canada, most of the rich guys live in a  vacuum, don't really know how it is on the street. I have few friends,  who are on the top of their companies, and they are really lonely up  there on that top. Mark is also on the very top.

Although we all have a right to our opinion I think that a comment like this is inflammatory because it is simply not true. Without Mark's benevolence there would be no ubuntu experience at all. So , certainly .. if we can move past this and stick to gnome-desktop experience I will withdraw my request to move this thread.

@Elfy

Please belay my last.

Regards..

---

### Post by Chanath on 2014-11-13
> **ventrical said:**
> I also have an xubuntu vivid install that i am working .. but let's try a little to stay on topic:) I know I am probably the greatest offender with being off topic. Having said that , I certainly am not trying to make this thread a typical recurring discussion ... ie; unity vs this or that... or 



Although we all have a right to our opinion I think that a comment like this is inflammatory because it is simply not true. Without Mark's benevolence there would be no ubuntu experience at all. So , certainly .. if we can move past this and stick to gnome-desktop experience I will withdraw my request to move this thread.

@Elfy

Please belay my last.

Regards..

I agree and I am sorry about that comment. I didn't think about it that way, meaning inflammatory, so can I delete that part?

About Ubuntu-Gnome, I updated and dist-upgraded it, but still the extensions get disabled after rebooting. Other than that there are no problems.

---

### Post by ventrical on 2014-11-13
> **Chanath said:**
> 
About Ubuntu-Gnome, I updated and dist-upgraded it, but still the extensions get disabled after rebooting. Other than that there are no problems.


I get the same here. I filed a bug on  gnome-shell but I am not sure if this is the correct bug designation ie; what is causing the bug .. gnome-shell or gnome-tweak-tool?

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1391690](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1391690)

 Nobody mee tooed it so it looks like it is not that important or it is still to very early in the cycle or I got the wrong packet.

Regards..

---

### Post by Elfy on 2014-11-13
> Hope some else would also try Xubuntu Vivid. 

I do nothing BUT run Xubuntu dev versions, have very little interest in any other *buntu. Only time I'll boot an install is to check a bug to see if it's common. But any other discussion of that should take place in a different thread.

---

### Post by sgage on 2014-11-15
I just me-tooed your bug report re: extensions being turned off.

Other than that, Vivid/Gnome seems quite solid...

---

### Post by ventrical on 2014-11-15
Hey,

Thanks ..

:)

---

### Post by Cavsfan on 2014-11-15
I think I'll download the iso and install ubuntu gnome over my old devel utopic Mate install since that's my kind of thing. :)

---

### Post by ventrical on 2014-11-15
> **Cavsfan said:**
> I think I'll download the iso and install ubuntu gnome over my old devel utopic Mate install since that's my kind of thing. :)

I actually created a persisitive USB install on USB ver 3.0 (8GB) and it works awesomely. One caveat.. I used trusty tahr LTS SDC and it took a little while, longer that usual, but is working fine. SO I just keep update/upgrade until it breaks . (or not).

Regards..

---

### Post by Cavsfan on 2014-11-15
> **ventrical said:**
> I actually created a persisitive USB install on USB ver 3.0 (8GB) and it works awesomely. One caveat.. I used trusty tahr LTS SDC and it took a little while, longer that usual, but is working fine. SO I just keep update/upgrade until it breaks . (or not).

Regards..

I'm wondering when the breakage will occur or not. I remember the first kernel on utopic... Although we are very early in this cycle. I see the timetable for this release is up now and we are no where near alpha 1 yet.

Guess I could just use a live session and zync the ISO on a regular basis. I've never tried that but it doesn't look too hard to do.
I've just got USB 2.0 - a 1TB drive I back up stuff on and a 8GB USB stick. I don't think I could stand the speed of USB 2.0 though - it's sooo slow moving stuff to and from the drives.

But, then again I will probably just install it to the devel partiton I have.

I'll chime in when I get that done - should take me a couple of days maybe.

Regards...

---

### Post by Cavsfan on 2014-11-16
Well, yesterday I downloaded Gnome 15.04 and put it on a DVD-RW then I slept on it.

Today I booted into it and tried the live session for a while and it looked pretty sweet. So then I installed it. Here I am trying to figure out what to do next. :p

I do like having other partitions with Ubuntu on them to copy stuff from and thanks to cariboo907 for showing me how to just drop my browser and email folders into my home directory thus preserving the favorites, passwords and all.

Guess I'll just play around in here but it does look nice. :)

---

### Post by sgage on 2014-11-16
Ubuntu Gnome 15.04 is looking pretty solid already. Two buglets persist that have been around for the last couple of releases or more:

If 'Files' (Nautilus) is open, clicking on its launcher will not bring it up - it just goes back to the desktop.

The printer installation routine from the setup app has trouble installing my Epson Printer. As before, though, 'system-config-printer' continues to work perfectly.

I have not noticed any other problems. It just seems like a good solid Gnome Shell experience. All my 'necessary' extensions work. They ought to - it's still GS 3.12. Does anyone know if 3.14 is going to be coming along bye and bye?

I've been using GS since it first became stable, back in the day. It is my daily workhorse, and I'm all moved in and doing everything in Vivid (staying well backed-up, of course), so I'll be testing it constantly in all dimensions. Anyway, I will report if anything comes up.

---

### Post by Cavsfan on 2014-11-16
Lesson #1 - do not set a startup application containing [SIZE=2]**compiz --replace **[/SIZE]or you will lose the ability to login to gui.
I installed conky and set that up but it had a black background to the conky so I tried to get compiz going - bad idea. :)

Had to hunt around for a way to delete that via cli and finally found it in [SIZE=2]**~/.config/autostart/compiz.desktop**[/SIZE]. I deleted that file from that directory then was able to press Cntl+Alt+F7 and login as normal.

Then I noticed that the sessions were default (which I don't know what is yet), gnome and gnome flashback. It had been set to gnome sine I installed it.
 I tried flashback and of course it went to a black screen and I had to press reset to reboot.

I just installed all of the gnome-flashback files and am getting ready to reboot. I'm not a big fan of gnome shell myself, but I am of gnome flashback.

Lemme see...

---

### Post by Cavsfan on 2014-11-16
Gnome Flashback booted just fine and compiz was loaded (it added gnome classic, flashback (with metacity) and flashback (with compiz) as available sessions.

I selected gnome classic and it went no where. I had to reboot and gnome flashback had no mouse. It loaded compiz and the cube would rotate but no mouse. 

So I guess it's gnome shell for the time being... Many things do not work. I guess it can only get better eh? :p

---

### Post by Hazzabin on 2014-11-16
Hey Cavsfan

had the same issues and the below post with code worked to get mouse back
[http://ubuntuforums.org/showthread.php?t=2252957](http://ubuntuforums.org/showthread.php?t=2252957)

---

### Post by Cavsfan on 2014-11-17
> **Hazzabin said:**
> Hey Cavsfan

had the same issues and the below post with code worked to get mouse back
[http://ubuntuforums.org/showthread.php?t=2252957](http://ubuntuforums.org/showthread.php?t=2252957)

Wow! Thanks for that! I just navigated to that spot in dconf editor which comes pre-installed *nice* and logged out, changed the session to Flashback (with Compiz) and it worked!
I also noticed while setting up Cairo Dock that the Fire deco is back. :D.

I've still got Precise on this box as my main *buntu and it was the last to have fire. I think I'm loving it!

---

### Post by Cavsfan on 2014-11-17
I installed the nvidia drivers and thought that was what was possibly causing the mouse problem.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                  331.89-0ubuntu6                       amd64        NVIDIA binary driver - version 331.89
ii  nvidia-331-uvm                              331.89-0ubuntu6                       amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-331                       331.89-0ubuntu6                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.7                                 amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                       amd64        Tool for configuring the NVIDIA graphics driver

```

But it's working pretty sweet now! 
Thanks for that tip          Hazzabin!

Off to find a window decorator possibly emerald. :) I also need to manage the theme - the default is not quite right.

---

### Post by Cavsfan on 2014-11-19
I'm using Vivid Gnome exclusively now and installed Cairo Dock but neither logout via Cairo Dock or the logout via the upper right hand option works.

Not sure how long this has been happening but restart and suspend both work just fine.

---

### Post by cariboo on 2014-11-19
I started out doing an install from the mini.iso, and after having quite a few problems getting wireless to work, I also installed gnome-shell, then updated to Vivid. Although this seems to be the long way around, to get a fully functioning desktop, I'm extremely happy with the way it works on my under powered Compaq netbook with 1GiB ram and an Atom CPU. Shutdown seems to work intermittently for me, in gnome-shell, it works as it should, but in LXDE I have to open a terminal in order to get it to shutdown, reboot and suspend work as the should.

---

### Post by ventrical on 2014-11-19
> **Cavsfan said:**
> I'm using Vivid Gnome exclusively now and installed Cairo Dock but neither logout via Cairo Dock or the logout via the upper right hand option works.

Not sure how long this has been happening but restart and suspend both work just fine.

I have  had problems in the past with gnome-shell and adding gnome-flashback and cario-dock. There is almost invariably depend problems and breakage .. if not sooner .. then later.

Regards..

---

### Post by ventrical on 2014-11-19
> **cariboo907 said:**
> I started out doing an install from the mini.iso, and after having quite a few problems getting wireless to work, I also installed gnome-shell, then updated to Vivid. Although this seems to be the long way around, to get a fully functioning desktop, I'm extremely happy with the way it works on my under powered Compaq netbook with 1GiB ram and an Atom CPU. Shutdown seems to work intermittently for me, in gnome-shell, it works as it should, but in LXDE I have to open a terminal in order to get it to shutdown, reboot and suspend work as the should.

Thanks for bringing this up. I have a clients HP lappy which is not big on resources and I was preparing to try and do somthing .. uh .. minimal on it, but have been procrastinating because of :

 > 
Although this seems to be the long way around, to get a fully functioning desktop,


:)lol

regards..

---

### Post by Cavsfan on 2014-11-19
In addition to the problems previously mentioned. I cannot open a deb file with Ubuntu Software Center. It just opens and then nothing.

Gnome-session-flashback has also regressed to requiring gnome-screensaver like it did before. Gnome-screensaver is not maintained, is not a screensaver but a lock and I cannot for the life of me understand why it would go backwards like this. They had changed it to "suggests" to fix this problem.

I want a working screensaver - xscreensaver, which is maintained has been good and now mate-screensaver is available and it can use a folder with pictures to rotate through which is pretty sweet.
Guess I'll have to add that script that kills gnome-screeensaver before the new screensaver starts up. *sheesh* Such fun! :p

---

### Post by Cavsfan on 2014-11-20
After successfully booting into gnome flashback with compiz once and then rebooting it will not load the session for me. All I can get to is tty.
I'm in gnome shell or whatever default is for the time being. LoL Not even a kernel yet and it's broke. Such fun. :p

---

### Post by Cavsfan on 2014-11-21
While Cairo Dock will not logout, I did notice a little down arrow at the extreme top right in Gnome that if you click on it and then click on the right arrow to the right of your userid that will bring up an option to logoff and it works. :)

---

### Post by xc3RnbFO8P on 2014-11-21
> **Cavsfan said:**
> While Cairo Dock will not logout, I did notice a little down arrow at the extreme top right in Gnome that if you click on it and then click on the right arrow to the right of your userid that will bring up an option to logoff and it works. :)

I was wondering if it is a theme problem?

---

### Post by ventrical on 2014-11-21
> **Cavsfan said:**
> While Cairo Dock will not logout, I did notice a little down arrow at the extreme top right in Gnome that if you click on it and then click on the right arrow to the right of your userid that will bring up an option to logoff and it works. :)

Why they did this is beyond me. It makes no sense.
  But ... thanks in the meantime :)


btw .. no bullet biting here. Learned my lesson about gnome3 and incorporating other DEs with it.

---

### Post by Cavsfan on 2014-11-22
> **Ringi said:**
> I was wondering if it is a theme problem?

It may very well be theme related but Cairo Dock has never ever failed me in logging out. I got used to nothing working in indicator-applet-complete and have always relied on Cairo Dock.

> **ventrical said:**
> Why they did this is beyond me. It makes no sense.
  But ... thanks in the meantime :)


btw .. no bullet biting here. Learned my lesson about gnome3 and incorporating other DEs with it.

:lol: I don't mind breakage. The next update of indicator-applet-complete will fix this issue of not being able to login to different sessions. 

[http://ubuntuforums.org/showthread.php?t=2253658&page=2&p=13171943#post13171943](http://ubuntuforums.org/showthread.php?t=2253658&page=2&p=13171943#post13171943)

---

### Post by Cavsfan on 2014-11-22
Not long after I posted that I was able to log out with Cairo Dock. I could not before...

Then yesterday I tried editing a file **gksudo gedit /etc/fstab** for example and the password box came up but after I entered my password nothing happened.
But **gksudo leafpad /etc/fstab** did work so I used that.

Today both gedit and leafpad both work. #-o

---

### Post by ventrical on 2014-11-22
We are supposed to be using pkexec or sudo -H  .

---

### Post by Cavsfan on 2014-11-22
> **ventrical said:**
> We are supposed to be using pkexec or sudo -H  .

I remember something about that. :)
Like this?:
```
cavsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/fstab
[sudo] password for cavsfan: 

(gedit:21828): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:21828): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files 
```

It got the 1st error when I changed a space and the 2nd when I saved the file.

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/fstab

(gedit:23991): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

That just gave one error when I saved it - none when I made a change.

Guess I'll have to find those policies and load them up for pkexec. It seems that gave the same errors though. We'll see...

BTW I got my flashback back back back... :lol: with what zika posted on the "bit it" thread.

---

### Post by zika on 2014-11-23
> **Cavsfan said:**
> BTW I got my flashback back back back... :lol: with what zika posted on the "bit it" thread.All credits go to albertsmuktupavels.

---

### Post by Cavsfan on 2014-11-23
> **zika said:**
> All credits go to albertsmuktupavels.

You are right. Alberts is the programmer and he got us running but you helped me and for that I thank you too. I am still learning this stuff. :)

---

### Post by ventrical on 2014-11-23
> **Cavsfan said:**
> I remember something about that. :)
Like this?:
```
cavsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/fstab
[sudo] password for cavsfan: 

(gedit:21828): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:21828): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files 
```

It got the 1st error when I changed a space and the 2nd when I saved the file.

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/fstab

(gedit:23991): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

That just gave one error when I saved it - none when I made a change.

Guess I'll have to find those policies and load them up for pkexec. It seems that gave the same errors though. We'll see...

BTW I got my flashback back back back... :lol: with what zika posted on the "bit it" thread.


Good news ... but I am trying to keep this thread topical to gnome3 experience. The gnome3 install I have is running just fine. I do not plan to add any other DEs to it (this *1* in particular) but I do have it  (flashback) installed in other  installs  of other variant ubuntus. ( is why I suggest  the flagging of prefixes).

btw .. I get the same as you with gksu and pkexec....  I am not dispensing to anyone how to make alignments and adjustments to their previous practices.. just pointing out status quo .. (so as not to get chaos) :) lol

---

### Post by Cavsfan on 2014-11-25
Several things are random on Gnome. Sometimes I can logout and sometimes I can only restart. Sometimes gksudo gedit <file-name> will bring up gedit and others nothing happens. 
I installed leafpad and it gives no errors some times and like gedit sometimes it does not show up and others it does.

Also Ubuntu Software Center is not working very well I've tried to use it a few times and it comes up blank.

I opened Software Center with a .deb file and nothing really displayed. If I didn't know what .deb file I had I could not tell by looking at Software Center what it was.
But it did install OK.
I tried to search for mp3gain on Software Center and this is what it showed.

[ATTACH=CONFIG]258201[/ATTACH]

I installed the top one which is what I wanted but it does not work. It says error at the bottom:

[ATTACH=CONFIG]258202[/ATTACH]

---

### Post by ventrical on 2014-11-25
I did not get that fail here.

---

### Post by ventrical on 2014-11-25
As I said before .. my past experience with gnome3 and adding other DEs on top of it will only eventually bring chaos unless you are willing to  work the extra downtime. Other seem to slide by and more power to them :) lol

Regards..

---

### Post by Cavsfan on 2014-11-27
> **ventrical said:**
> As I said before .. my past experience with gnome3 and adding other DEs on top of it will only eventually bring chaos unless you are willing to  work the extra downtime. Other seem to slide by and more power to them :) lol

Regards..

Maybe I made a mistake by installing this. I might just install the vanilla Ubuntu desktop version. I'm will to tolerate some breakage but I do not actively seek it.

---

### Post by ventrical on 2014-11-27
Nope !  You made no mistake. it's just the nature of the depends invloved. Cario-dock *is* suppossed to work and as are all of the other DEs like xubuntu-desktop , lubuntu-desktop .. etc... but try installing them on an *U*buntu virgin install with Unity7 and watch how it will regress over time.  I have been doing Ubuntu since 2007 (actively posting at ubuntuforums since 2010) and working with Linux since 1995 or 96  (the time when Linus was trying to build a boot floppy disk and it wouldn't work- I beta tested that just to validate that it was a fail ). So I have lots of experience with fails when adding other DEs to Ubuntu, especially since the adoption of Unity DE as default.

Anyways ... I can't say for certain which depends are involved but I believe mac4man may know something about this. And breakage will come without warning .. so it is trail and error. Thats part of what we are doing here :) lol

 Great stuff Cavsfan... keep up the good work.

---

### Post by Cavsfan on 2014-11-28
> **ventrical said:**
> Nope !  You made no mistake. it's just the nature of the depends invloved. Cario-dock *is* suppossed to work and as are all of the other DEs like xubuntu-desktop , lubuntu-desktop .. etc... but try installing them on an *U*buntu virgin install with Unity7 and watch how it will regress over time.  I have been doing Ubuntu since 2007 (actively posting at ubuntuforums since 2010) and working with Linux since 1995 or 96  (the time when Linus was trying to build a boot floppy disk and it wouldn't work- I beta tested that just to validate that it was a fail ). So I have lots of experience with fails when adding other DEs to Ubuntu, especially since the adoption of Unity DE as default.

Anyways ... I can't say for certain which depends are involved but I believe mac4man may know something about this. And breakage will come without warning .. so it is trail and error. Thats part of what we are doing here :) lol

 Great stuff Cavsfan... keep up the good work.

I guess I'll try to hang in there a while longer. Just got some nice updates I believe. 

I started out in computer electronics repairing computers in the Air Force when computers were not near as sophisticated as my cell phone. Then branched into programming mainframes. I had some experience with linux as we had a fax server that had a linux OS and we passed data back and forth. I had to learn a bit to be able to check things out properly. I never made the jump into object oriented programming. That would have been the next logical step but a neurological disorder stopped me and I could no longer work. So, I pretend to be doing something worthwhile in Ubuntu and playing around with this and windows. I have been though my share of breakage, no where near what others on here have been through. I think I started on Jaunty Jackalope 9.04 and starting helping with the developmental cycle of Karmic Koala 9.10. Not absolutely sure but I think that's correct.

I struggle a little more than others but I can usually find a way to get things accomplished.

Now to check on what was updated and see what else I can break on here. :)

---

### Post by Hazzabin on 2014-11-28
My Three-pence worth :)

Gnome 15.04 (bare-bones) nothing else added except for Cairo-dock and some screenlets I like, apart from having to reset the extensions each time I've had no other issues

and yup cairo-dock works as it should. As we know some extensions currently work some do not.

I do note the different behavior when booting into my other gnome with compiz/flashback, even cairo-dock plays up, sometime soon that will be fixed, whatever it is that's causing
the difference. 

regards

---

### Post by Cavsfan on 2014-11-28
> **Hazzabin said:**
> My Three-pence worth :)

Gnome 15.04 (bare-bones) nothing else added except for Cairo-dock and some screenlets I like, apart from having to reset the extensions each time I've had no other issues

and yup cairo-dock works as it should. As we know some extensions currently work some do not.

I do note the different behavior when booting into my other gnome with compiz/flashback, even cairo-dock plays up, sometime soon that will be fixed, whatever it is that's causing
the difference. 

regards

Did you get the fire effect working on Cairo Dock? It's pretty sweet! I can move my mouse across the dock and everything looks as if it's on fire.
I'll try to make a movie if I can figure out how. Here's a screenie of it - no motion but you can see what I'm talking about. That effect dissipated after Precise I thought.

 [[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-11-28182454.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-11-28182454.php")

---

### Post by Hazzabin on 2014-11-28
Hey ya Cavsfan

Yeah I do remember it from way back, it doesn't seem to be 'listed' either in my gnome 14.04 or more importantly in 15.04, least it not showing where I expect it to be
that is in Icons-Animation-Pulse......or whotever 'Fire is not there

ps I use Vokoscreen for webcam and screen-videos

[[img]http://en.zimagez.com/miniature/screenshotfrom2014-11-29094703.png[/img]](http://en.zimagez.com/zimage/screenshotfrom2014-11-29094703.php)

---

### Post by Hazzabin on 2014-11-28
Cairo-dock configure in Gnome 15.04

[[IMG]http://en.zimagez.com/miniature/cairo-dockconfiguration013.png[/IMG]]("http://en.zimagez.com/zimage/cairo-dockconfiguration013.php")

---

### Post by Cavsfan on 2014-11-29
I'm in Mint Qiana 17 (Ubuntu 14.04) right now and I just turned on fire on mouse over. I never knew to look to see if it was there. It was set to blank and when I set it to fire and clicked apply it worked.
Although it is not as clearly visible as in the last picture. I have fire! :)

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-11-29094101.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-11-29094101.php")

Let me go over to 15.04 and see. It was not letting me logout a while ago. I had to press reset.

---

### Post by Cavsfan on 2014-11-29
Here is my cairo dock settings on Vivid 15.04 with fire.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-11-29094943.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-11-29094943.php")

---

### Post by Cavsfan on 2014-11-29
I also got fire going in 14.10 as well. Just didn't know where to look. 

My gnome system in flashback will not logout or restart with systemd and it won't logout with upstart but it will restart. Seems like that changes day to day.

---

### Post by Hazzabin on 2014-11-29
Well after lots of searching. there was a fault in my Cairo-dock install, got it sorted

My install of Gnome with flashback doing the same, I've been tending to get Gnome alone working better

---

### Post by Cavsfan on 2014-11-30
> **Hazzabin said:**
> Well after lots of searching. there was a fault in my Cairo-dock install, got it sorted

My install of Gnome with flashback doing the same, I've been tending to get Gnome alone working better

That's good. It was odd that your cairo dock settings looked different from mine. I guess that explains it.

I just booted into default Gnome and I'm not real fond of it as when I click on applications every xscreensaver option is included in them. I've got about 10 dots on the right side when I click on applications.

Since I removed gnome-screensaver and installed xscreensaver. I'm just used to the way flashback works I guess.

I was able to logout of that and change the session to flashback and login ok.

---

### Post by Cavsfan on 2014-11-30
I'm wondering if I am missing some fonts which might explain why Ubuntu Software Center looks so bad and why I couldn't read or see anything when I entered mp3gain before.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-11-30154457.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-11-30154457.php")

These fonts installed without issue:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy ttf-mscorefonts-installer
ttf-mscorefonts-installer:
  Installed: 3.4+nmu1ubuntu2
  Candidate: 3.4+nmu1ubuntu2
  Version table:
 *** 3.4+nmu1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/multiverse amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Hazzabin on 2014-11-30
My Cairo-dock uses a theme called 'Clear' 

As for 'Software Centre' I've serious issue with it until I figured that it may and sometimes is caused by whatever theme I'm using.....this also applies to 'Applications' pop-up from Cairo-dock totally unreadable

once swtich to a different theme often fixes

---

### Post by ventrical on 2014-12-01
> **Cavsfan said:**
> I'm wondering if I am missing some fonts which might explain why Ubuntu Software Center looks so bad and why I couldn't read or see anything when I entered mp3gain before.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-11-30154457.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-11-30154457.php")

These fonts installed without issue:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy ttf-mscorefonts-installer
ttf-mscorefonts-installer:
  Installed: 3.4+nmu1ubuntu2
  Candidate: 3.4+nmu1ubuntu2
  Version table:
 *** 3.4+nmu1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/multiverse amd64 Packages
        100 /var/lib/dpkg/status
```

I had a bug on one of my gnome3 installs (no flashback installed). I used Software Center and installed restricted extras and the ttf-mscorefonts EULA will not  prompt over the existing USC window.. so . .of course it fails unless you drag the window away from center.  Otherwise it will time out. Then you have to remove and re-install all over again.

Edit:

Wow .. seems to have auto resoved itself. That's a strange one.

---

### Post by Cavsfan on 2014-12-01
> **Hazzabin said:**
> My Cairo-dock uses a theme called 'Clear' 

As for 'Software Centre' I've serious issue with it until I figured that it may and sometimes is caused by whatever theme I'm using.....this also applies to 'Applications' pop-up from Cairo-dock totally unreadable

once swtich to a different theme often fixes

I'll check the theming theory out. Strange how it only happens with USC though. My Cairo Dock text looks great. I *think* I'm using default-single theme in cairo dock.
In tweak tool I'm using Gobal Dark theme. I find it hard to change much of the theming besides global dark or not. I did get my favorite icons working Buuf3.10 though. :)

[ATTACH=CONFIG]258313[/ATTACH]


> **ventrical said:**
> I had a bug on one of my gnome3 installs (no flashback installed). I used Software Center and installed restricted extras and the ttf-mscorefonts EULA will not  prompt over the existing USC window.. so . .of course it fails unless you drag the window away from center.  Otherwise it will time out. Then you have to remove and re-install all over again.

Edit:

Wow .. seems to have auto resoved itself. That's a strange one.

:lol: I've seen a few things resolve themselves or work one day and not the next. I guess we are still early. :) I wonder when the first 3.17 kernel will come down the pipe.
I'll bet there shall be breakage. :)

---

### Post by Hazzabin on 2014-12-01
[/QUOTE] I'll bet there shall be breakage. :)[/QUOTE]

Really you think????  :p

It was the dark themes that gave me issues similar to what you said 'unreadable'

---

### Post by harry332 on 2014-12-02
> **Cavsfan said:**
>  :) I wonder when the first 3.17 kernel will come down the pipe.
I'll bet there shall be breakage. :)

Did you mean kernel 3.18?
We already have 3.18 rc7 as of 1 December 2014.

---

### Post by Cavsfan on 2014-12-02
I'll bet there shall be breakage. :)[/QUOTE]

Really you think????  :p

It was the dark themes that gave me issues similar to what you said 'unreadable'[/QUOTE]

Hmm maybe some breakage but hopefully not too much. :p I expect breakage to begin when the Vivid kernel is introduced like it did in Utopic.
I changed it to light theme, rebooted and USC looks more readable now. But in flashback, the top and bottom panels look horrible.
With the dark theme it was a little better. THe light theme mixes white and dark in the panels. Not sure which is worse.

My conky died just before I took this screenie.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-12-02145347.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-12-02145347.php")

There are two items open but you cannot tell by looking at the panel. In the dark theme it was bad too but more readable.


> **harry332 said:**
> Did you mean kernel 3.18?
We already have 3.18 rc7 as of 1 December 2014.

I thought since we are (default) using the 3.16.0-25-generic kernel that the 3.17 kernel would be what Vivid was going to use.
Or are they skipping that and going to 3.18? I'm not talking about building my own like some of you do. I just meant the default kernel.

---

### Post by zika on 2014-12-02
In **ppa:canonical-kernel-team/ppa **there is a very solid 3.18 for quite some time...

---

### Post by Hazzabin on 2014-12-02
My Dark theme with settings

[[img]http://en.zimagez.com/miniature/screenshotfrom2014-12-03064017.png[/img]](http://en.zimagez.com/zimage/screenshotfrom2014-12-03064017.php)

---

### Post by Elfy on 2014-12-02
>  Or are they skipping that and going to 3.18? I'm not talking about building my own like some of you do. I just meant the default kernel. I do the same. I try and run what most people would install and would get support for here.

Kernel meeting was today - [http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:00](http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:00)

Vivid kernel - [http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:01](http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:01)

For those not bothered with the whole logs - 

> ogasawara	The master-next branch of our Vivid kernel has been rebased to the	17:01
ogasawara	v3.18-rc7 upstream kernel.  We have pushed uploads to our team's PPA	17:01
ogasawara	for preliminary testing.  We have still withheld uploading to	17:01
ogasawara	the archive while we iron out some final issues.	17:01

---

### Post by Cavsfan on 2014-12-03
> **zika said:**
> In **ppa:canonical-kernel-team/ppa **there is a very solid 3.18 for quite some time...

But, I don't want to add any special ppa. I want to accept what Vivid defaults will be.
Thanks for that though. :)

> **Hazzabin said:**
> My Dark theme with settings

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-12-03064017.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-12-03064017.php")

I can't change much of anything on there except dark/light and icons.
I don't have that option for Window or most any of the other items.
Guess I'd have to download the GTK+ theme. 

I like that blue though.

---

### Post by Cavsfan on 2014-12-03
> **Elfy said:**
> I do the same. I try and run what most people would install and would get support for here.

Kernel meeting was today - [http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:00](http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:00)

Vivid kernel - [http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:01](http://irclogs.ubuntu.com/2014/12/02/%23ubuntu-meeting.html#t17:01)

For those not bothered with the whole logs -

Thanks for the reply! So 3.18 it is! Let the breakage commence. :p

---

### Post by Hazzabin on 2014-12-04
Well I joined in too and running the new kernel in Gnome 15.04 with flashback, no problems so far after day and a half  :guitar:

---

### Post by Cavsfan on 2014-12-05
But... but... but... what if you install that ppa, install the 3.18 rc kernel and then the 3.18 kernel come down in regular updates...

What do you do then? Purge the ppa?

I don't want to re-install :)

I've been running flashback on the default kernel and it's running pretty smooth. 

```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
But I did just wifi a picture from my android to my pc using airdroid and it uploaded just fine.
But it would not upload to facebook. I tried twice and gave up.

Going to one of my stable systems to do that.

Going to find a better theme first though.

---

### Post by zika on 2014-12-05
> **Cavsfan said:**
> But... but... but... what if you install that ppa, install the 3.18 rc kernel and then the 3.18 kernel come down in regular updates...
What do you do then? Purge the ppa?
I don't want to re-install :)This is You just joking? Right? ;)

---

### Post by ventrical on 2014-12-05
> **Cavsfan said:**
> But... but... but... what if you install that ppa, install the 3.18 rc kernel and then the 3.18 kernel come down in regular updates...

What do you do then? Purge the ppa?

I don't want to re-install :)

I've been running flashback on the default kernel and it's running pretty smooth. 

```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
But I did just wifi a picture from my android to my pc using airdroid and it uploaded just fine.
But it would not upload to facebook. I tried twice and gave up.

Going to one of my stable systems to do that.

Going to find a better theme first though.

 Installing rc kernels does not require a ppa. There is a sudo command to remove the RC kernel from the GRuB bootloader once you have installed a RC kernel.

btw .. on my default Gnome3 box In have had no problems at all.  Only one is the gnome-tweak-tool not holding settings after re-boot .. but I can live without that until it's fixed.

Regards..

---

### Post by Cavsfan on 2014-12-05
> **Cavsfan said:**
> But... but... but... what if you install that ppa, install the 3.18 rc kernel and then the 3.18 kernel come down in regular updates...
What do you do then? Purge the ppa?
I don't want to re-install :)

> **zika said:**
> This is You just joking? Right? ;)

No I wasn't joking. Just a naive question. I'm not up on this stuff like you guys are. :)

> **ventrical said:**
> Installing rc kernels does not require a ppa. There is a sudo command to remove the RC kernel from the GRuB bootloader once you have installed a RC kernel.

btw .. on my default Gnome3 box In have had no problems at all.  Only one is the gnome-tweak-tool not holding settings after re-boot .. but I can live without that until it's fixed.

Regards..

What about that ppa zika mentioned - I thought that was how your got the 3.18 rc kernel)

> **zika said:**
> In **ppa:canonical-kernel-team/ppa **there is a very solid 3.18 for quite some time...

D'oh! #-oWait a minute you are just talking about what is in proposed right? And if I enabled proposed I could supplant my 3.16 kernel with the 3.18 kernel?

Here is a screenshot of some better themes. I installed the Numix theme set with icons and whole nine yards which came with some other stuff too. 

I got it from here [http://www.noobslab.com/2014/05/numix-theme-for-ubuntulinux-mintother.html](http://www.noobslab.com/2014/05/numix-theme-for-ubuntulinux-mintother.html)

Just had to edit it to change vivid to utopic to get the themes, then changed it to vivid and commented out that source line.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-12-05165048.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-12-05165048.php")

Changing the window theme in tweak tool seems to have no effect. Everything else there seems to work except cursor, which I'm not worried about.

Dark theme is no longer dark but mey, I like it.

---

### Post by Hazzabin on 2014-12-05
Yeah I like that one (screenshot) seems nice and a 'clean' look about it

---

### Post by ventrical on 2014-12-06
> **Cavsfan said:**
> No I wasn't joking. Just a naive question. I'm not up on this stuff like you guys are. :)



What about that ppa zika mentioned - I thought that was how your got the 3.18 rc kernel)


Thats not *how* you get the kernel .. it is *where* you get the kernel so when you go to the link : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc7-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc7-vivid/)  you will see the files you need to download ... ones for i386 and others for amd64.  So If you are running amd64 you download all the amd64 files plus xxxall.deb and then put them in a subdirectory and run:

```

sudo dpkg *.deb

```

or better ..

```

sudo dpkg -i *

```

from   : [http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12312412#post12312412](http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12312412#post12312412)

and it will install the rc for you . There is no need to create a ppa.

 Regards..

---

### Post by zika on 2014-12-06
> **Cavsfan said:**
> No I wasn't joking. Just a naive question. I'm not up on this stuff like you guys are. :)



What about that ppa zika mentioned - I thought that was how your got the 3.18 rc kernel)



D'oh! #-oWait a minute you are just talking about what is in proposed right? And if I enabled proposed I could supplant my 3.16 kernel with the 3.18 kernel?

Here is a screenshot of some better themes. I installed the Numix theme set with icons and whole nine yards which came with some other stuff too. 

I got it from here [http://www.noobslab.com/2014/05/numix-theme-for-ubuntulinux-mintother.html](http://www.noobslab.com/2014/05/numix-theme-for-ubuntulinux-mintother.html)

Just had to edit it to change vivid to utopic to get the themes, then changed it to vivid and commented out that source line.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-12-05165048.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-12-05165048.php")

Changing the window theme in tweak tool seems to have no effect. Everything else there seems to work except cursor, which I'm not worried about.

Dark theme is no longer dark but mey, I like it.

> **ventrical said:**
> Thats not *how* you get the kernel .. it is *where* you get the kernel so when you go to the link : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc7-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc7-vivid/)  you will see the files you need to download ... ones for i386 and others for amd64.  So If you are running amd64 you download all the amd64 files plus xxxall.deb and then put them in a subdirectory and run:

```

sudo dpkg *.deb

```

or better ..

```

sudo dpkg -i *

```

from   : [http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12312412#post12312412](http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12312412#post12312412)

and it will install the rc for you . There is no need to create a ppa.

 Regards..
Not having time to respond to all of this, I'll just invite @Cavsfan to read my post above about PPA, look what that PPA is for and...
I just answered to a question about which kernel is and will be in Vivid. Method of using mainline-kernel-PPA (sic!) is well known and used (me included) for years. But that is not he answer to question @Cavsfan asked, as many times before.
About the need to create PPA just read head of that PPA's page. Do not mix automatic kernel upgrade (linux-headers-generic and linux-image-generic packages) and manual one that we are using to try newest kernels... And so on.

---

### Post by ventrical on 2014-12-06
I am trying to keep this topical to gnome3  experience. Installing rcs and ppas can be part of that testing experience but I originally  created this thread for default gnome3 experience.  My bad for not making that more clear.

There is a thread for mainline kernel testing here.

[http://ubuntuforums.org/showthread.php?t=2254925](http://ubuntuforums.org/showthread.php?t=2254925)

hey .. thanks .

Regards..

---

### Post by zika on 2014-12-06
> **ventrical said:**
> I am trying to keep this topical to gnome3  experience. Installing rcs and ppas can be part of that testing experience but I originally  created this thread for default gnome3 experience.  My bad for not making that more clear.

There is a thread for mainline kernel testing here.

[http://ubuntuforums.org/showthread.php?t=2254925](http://ubuntuforums.org/showthread.php?t=2254925)

hey .. thanks .

Regards..You're right. I just succumbed to off-topic-provocation due to @Cavsfan. I'm sorry about that mistake of mine and I will try not to fall in that trap again.  Hope others will, also. Just to clarify, again: @Cavsfan's question was not about mainline kernel testing and I did not mention rcs (as You call them) here. But, hey, it seems that point will not get to be accepted... ;) If we want to be quite on topic than no one could since the name of the topic is about **your** experience... ;)

---

### Post by ventrical on 2014-12-06
> **zika said:**
> You're right. I just succumbed to off-topic-provocation due to @Cafstan. I'm sorry about that mistake of mine and I will try not to fall in that trap again.  Hope others will, also. Just to clarify, again: @Cafstan's question was not about mainline kernel testing and I did not mention rcs (as You call them) here. But, hey, it seems that point will not get to be accepted... ;) If we want to be quite on topic than no one could since the name of the topic is about **your** experience... ;)

I'm open.  Feel free (when you have time permitting) to explain the difference between the two .. because it's new to me also.

> 
If we want to be quite on topic than no one could since the name of the topic is about **your** experience...


 It's just default gnome3. No bells or whistles... that could be anybody's experience.;) 

 Regards..

Edit:

Ok .. I asked that question in thread you started..

---

### Post by zika on 2014-12-06
> **ventrical said:**
> I'm open.  Feel free (when you have time permitting) to explain the difference between the two .. because it's new to me also. I asked that question in thread you started..I'll answer it the same way I did already:
This is You just joking? Right? ;)

---

### Post by ventrical on 2014-12-06
> **zika said:**
> I'll answer it the same way I did already:
This is You just joking? Right? ;)

??

---

### Post by ventrical on 2014-12-06
> **ventrical said:**
> ??

Yeah  .. yeah .. I get it now .. I'm just joking .

---

### Post by zika on 2014-12-06
Serious answer to Your question is given: [http://ubuntuforums.org/showthread.php?t=2254925&p=13181577#post13181577](http://ubuntuforums.org/showthread.php?t=2254925&p=13181577#post13181577)

---

### Post by zika on 2014-12-06
> **ventrical said:**
> Yeah  .. yeah .. I get it now .. I'm just joking .Nice. Good joke... ;)

---

### Post by Cavsfan on 2014-12-06
> **Hazzabin said:**
> Yeah I like that one (screenshot) seems nice and a 'clean' look about it
Thanks!
After all this time of looking at barely readable windows in the bottom panel of flashback I finally have something that I can read very well. :)

Zika, the name is not [SIZE=5]Cafstan[/SIZE] it is [SIZE=5]Cavsfan[/SIZE] but if you want to roll with that we can do that too. ;) I'll call you Zikastan or something. :p
I thought you had made an error but after about the 5th repeat of Cafstan I don't think you've made any mistake.
> You have got to be kitten me. :p 

I'm not going to mention anything more about kernels and I really don't care to. I'll stick with Elfy and wait on the regular updates to get my 3.18 kernel.

BTW has any one checked out the xscreensavers that gnome has to offer? I am seeing some really nice ones that are different than anything I've seen in the past.

That's my gnome experience and I'm sticking with it. :p

Also has anyone seen this at bootup in Gnome?

[[IMG]http://en.zimagez.com/miniature/20141206170501.jpg[/IMG]]("http://en.zimagez.com/zimage/20141206170501.php")

The last 2 lines are just my 1TB USB drive which happens on every single install since I have been Ubuntuing. :p

---

### Post by Hazzabin on 2014-12-06
Hey CAVSFAN  

there here is about the hwdb thingie about half way down 1st page

[http://ubuntuforums.org/showthread.php?t=2254925](http://ubuntuforums.org/showthread.php?t=2254925)

---

### Post by ventrical on 2014-12-06
> **Cavsfan said:**
> Thanks!
After all this time of looking at barely readable windows in the bottom panel of flashback I finally have something that I can read very well. :)
BTW has any one checked out the xscreensavers that gnome has to offer? 

  I have had a gnome-flashback/compiz/metacity DE sitting on top of an  ubuntu installsince utopic (now vivid) which was borked and the gnome-flashback-compiz just started to work!! So there are good things to come for those that wait :) Lots of new , weird xscreensavers too but there is still the errors that warn you .. gnome-screensaver daemon is still running ..  .... etc..
Regards..

edit:

The ccsm settings in Unity will not work in gnome-flashback .. so it's still busted. But thats another topic.:)

Regards.

---

### Post by zika on 2014-12-07
> **Cavsfan said:**
> Zika, the name is not [SIZE=5]Cafstan[/SIZE] it is [SIZE=5]Cavsfan[/SIZE] but if you want to roll with that we can do that too. ;) I'll call you Zikastan or something. :p
I thought you had made an error but after about the 5th repeat of Cafstan I don't think you've made any mistake.First: I do not mind beeing called any name You choose... ;)
Second: I've edited all my mistakes (I found only 4, if You find any other occurrence let me now to correct it, sorry) but there are some in messages that quoted mine. Sorry for my typo(s), I'll be more careful next time... ;)

---

### Post by Cavsfan on 2014-12-07
> **Hazzabin said:**
> Hey CAVSFAN  

there here is about the hwdb thingie about half way down 1st page

[http://ubuntuforums.org/showthread.php?t=2254925](http://ubuntuforums.org/showthread.php?t=2254925)

But, I didn't install the 3.18rc kernel nor am I booting with systemd. I get this using upstart. From that thread I gather the error occurs with people who did install the kernel and are booting with systemd.
So, I'm a bit confused. Or did systemd become the default on Vivid somehow. I have a custom grub entry for upstart and systemd. But that message "starting version 217" certainly points to systemd.
Which make me even more confused.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd
systemd:
  Installed: 217-3ubuntu1
  Candidate: 217-3ubuntu1
  Version table:
 *** 217-3ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status
```

Here are my grub entries for both:
```
menuentry "Vivid Vervet 15.04 Gnome (devel branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 Gnome Systemd (Devel Branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
```

> **ventrical said:**
> I have had a gnome-flashback/compiz/metacity DE sitting on top of an  ubuntu installsince utopic (now vivid) which was borked and the gnome-flashback-compiz just started to work!! So there are good things to come for those that wait :) Lots of new , weird xscreensavers too but there is still the errors that warn you .. gnome-screensaver daemon is still running ..  .... etc..
Regards..

edit:

The ccsm settings in Unity will not work in gnome-flashback .. so it's still busted. But thats another topic.:)

Regards.

Ventrical, you can remove **gnome-screensaver** and have a start up command **xscreensaver -no-splash**. That's what I have done.
The depends was changed to recommends for gnome-screensaver in the package gnome-session-flashback. In the screensaver you can specify lock screen.
Gnome-screensaver should IMO be renamed gnome-lock as that would be more fitting. :)

```
gnome-flashback (3.14.0-3ubuntu6) vivid; urgency=medium

  * Move gnome-screensaver from Depends to Recommends.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Wed, 26 Nov 2014 15:08:57 +0300
```

> **zika said:**
> First: I do not mind being called any name You choose... ;)
Second: I've edited all my mistakes (I found only 4, if You find any other occurrence let me now to correct it, sorry) but there are some in messages that quoted mine. Sorry for my typo(s), I'll be more careful next time... ;)

No worries zika, I was sort of kidding anyway. Having a sense of humor should be a requirement in this life. :p Because not having one makes one a "scrooge". :lol:
 And I think makes one miserable as well. But, thank you sir for the apology.

You can call me anything you want, just don't call me late for dinner. :p (That's a saying we have here in the US, in case you are not familiar with it.)

---

### Post by zika on 2014-12-07
> **Cavsfan said:**
> You can call me anything you want, just don't call me late for dinner. :p (That's a saying we have here in the US, in case you are not familiar with it.)I am... ;)
If You have systemd-sysv installed You've crossed the StartUP<>SystemD border. You've said goodbye to StartUp. Regardless of the init= choice You've made in Grub. There is, actually difference between starting SystemD automatically and via init= but I'll stop here because You've taken me into off-topic again.. ;) My sincere excuse to @ventrical.

---

### Post by ventrical on 2014-12-07
> **zika said:**
> I am... ;)
If You have systemd-sysv installed You've crossed the StartUP<>SystemD border. You've said goodbye to StartUp. Regardless of the init= choice You've made in Grub. There is, actually difference between starting SystemD automatically and via init= but I'll stop here because You've taken me into off-topic again.. ;) My sincere excuse to @ventrical.

No excuse neccessary.  We value your learned contributions. At least I do. Obviously your experience is worth it's weight in gold.  I do not need any convincing of that. Just keep teaching us (if and when time permitting).:) I think thats all we are really asking. 

Regards..

---

### Post by Cavsfan on 2014-12-07
> **zika said:**
> I am... ;)
If You have systemd-sysv installed You've crossed the StartUP<>SystemD border. You've said goodbye to StartUp. Regardless of the init= choice You've made in Grub. There is, actually difference between starting SystemD automatically and via init= but I'll stop here because You've taken me into off-topic again.. ;) My sincere excuse to @ventrical.

I don't have that installed.
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd-sysv
systemd-sysv:
  Installed: (none)
  Candidate: 217-3ubuntu1
  Version table:
     217-3ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
```
And I see init is running instead of systemd as pid 1.

> **ventrical said:**
> No excuse neccessary.  We value your learned contributions. At least I do. Obviously your experience is worth it's weight in gold.  I do not need any convincing of that. Just keep teaching us (if and when time permitting).:) I think thats all we are really asking. 

Regards..

I agree with **ventrical**, **zika** I have learned a lot from you too and I also value your contributions. Kind of makes me feel bad about my previous post.
But, I think we can say we are all friends here. :D Which I highly value. I may have a serious question for you in the future and I am quite sure you'll know the answer. :)

I'm anxious to see what Gnome does next. :)

PS: this is a bit off topic but I think I have too many systems on this pc! I'm going to merge some of them Like Mint 13 and Precise 12.04, which are basically the same thing.
Too many updates to perform and I can't keep track of where I put what! :p

---

### Post by Hazzabin on 2014-12-08
[COLOR=#000000]Too many updates to perform and I can't keep track of where I put what! [/COLOR]:razz:

Thank goodness someone else has this problem, Thought I was the only one :P :)

---

### Post by zika on 2014-12-08
> **ventrical said:**
> No excuse neccessary.  We value your learned contributions. At least I do. Obviously your experience is worth it's weight in gold.  I do not need any convincing of that. Just keep teaching us (if and when time permitting).:) I think thats all we are really asking. 
Regards..> **Cavsfan said:**
> I agree with **ventrical**, **zika** I have learned a lot from you too and I also value your contributions. Kind of makes me feel bad about my previous post.
But, I think we can say we are all friends here. :D Which I highly value. I may have a serious question for you in the future and I am quite sure you'll know the answer. :)Fellows, do not make jokes. My ego died years ago. If I can help about something, here I am, do not have too high hopes about this old mind of mine. Back to Earth, @Cavsfan: so You do not have SystemD as default, yet. I did jump and install package mentioned so I am SystemD for weeks, even months... ;)> [SIZE=1][FONT=sans-serif]Installing systemd-sysv will overwrite /sbin/init with a link to systemd[/FONT][/SIZE]

---

### Post by Cavsfan on 2014-12-08
> **Hazzabin said:**
> [COLOR=#000000]Too many updates to perform and I can't keep track of where I put what! [/COLOR]:razz:

Thank goodness someone else has this problem, Thought I was the only one :P :)

Ha! I see I'm not the only one. :)

> **zika said:**
> Fellows, do not make jokes. My ego died years ago. If I can help about something, here I am, do not have too high hopes about this old mind of mine. Back to Earth, @Cavsfan: so You do not have SystemD as default, yet. I did jump and install package mentioned so I am SystemD for weeks, even months... ;)

We weren't joking zika. I'm nearly 56 and my mind is a wasteland so I know what you mean (I think). Plus I'm on some medication that would put most people to sleep; it merely attempts to keep me normal and it doesn't even do a good job of that. Most of the time I don't know what day it is or which way is up. Everyone struggles in one way or another I guess and age doesn't help.

Back to systemd and Gnome: I will go default systemd when they force my cold dying hands... err wrong place. I mean I will go default when I have to and they do it for me. :)

---

### Post by zika on 2014-12-08
> **Cavsfan said:**
> nearly 56I'm older than You. And, even so, I like SystemD very much for making much things more easier to handle and even faster. I might be wrong, but that is my honest opinion.

---

### Post by Cavsfan on 2014-12-08
> **zika said:**
> I'm older than You. And, even so, I like SystemD very much for making much things more easier to handle and even faster. I might be wrong, but that is my honest opinion.

I'll have to give Systemd more of chance starting tomorrow. Today I spent at least 4 hours in Gnome via Upstart so we'll see if Systemd can do that and more tomorrow. :)

---

### Post by Cavsfan on 2014-12-08
Forgot to mention does any one know when the 3.18 kernel will come through in regular updates? I'm still running the kernel that Utopic has.
And just say no to kernel ppas or building your own too. :p

---

### Post by Cavsfan on 2014-12-09
That was weird! I booted Gnome using Systemd and got a few updates, I didn't think I should worry about any of them. 
Then while in the midst or after the update it said I could choose low graphics mode or tty, etc.
I chose low graphics mode and it went no where. I rebooted and chose upstart first choosing default gnome session.
There didn't seem to be a problem there so I logged out and logged back into flashback with compiz and it came up just fine.
I did notice one update to indicator-power:

```
indicator-power (12.10.6+15.04.20141203-0ubuntu1) vivid; urgency=low

  [ Charles Kerr ]
  * Show the phone menu in the phone greeter.

  [ Christopher Lee ]
  * Fix some minor typos in power testing xml file.

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Wed, 03 Dec 2014 16:26:04 +0000
```

What's the deal with phone menu? :p This aint no phone it's a PC.

---

### Post by ventrical on 2014-12-09
> **Cavsfan said:**
> That was weird! I booted Gnome using Systemd and got a few updates, I didn't think I should worry about any of them. 
Then while in the midst or after the update it said I could choose low graphics mode or tty, etc.
I chose low graphics mode and it went no where. I rebooted and chose upstart first choosing default gnome session.
There didn't seem to be a problem there so I logged out and logged back into flashback with compiz and it came up just fine.
I did notice one update to indicator-power:

```
indicator-power (12.10.6+15.04.20141203-0ubuntu1) vivid; urgency=low

  [ Charles Kerr ]
  * Show the phone menu in the phone greeter.

  [ Christopher Lee ]
  * Fix some minor typos in power testing xml file.

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Wed, 03 Dec 2014 16:26:04 +0000
```

What's the deal with phone menu? :p This aint no phone it's a PC.


If you decide to install unity8mir(next) those packages will be there to handle it.

---

### Post by Cavsfan on 2014-12-09
> **ventrical said:**
> [QUOTE=Cavsfan;13183924]That was weird! I booted Gnome using Systemd and got a few updates, I didn't think I should worry about any of them. 
Then while in the midst or after the update it said I could choose low graphics mode or tty, etc.
I chose low graphics mode and it went no where. I rebooted and chose upstart first choosing default gnome session.
There didn't seem to be a problem there so I logged out and logged back into flashback with compiz and it came up just fine.
I did notice one update to indicator-power:

```
indicator-power (12.10.6+15.04.20141203-0ubuntu1) vivid; urgency=low

  [ Charles Kerr ]
  * Show the phone menu in the phone greeter.

  [ Christopher Lee ]
  * Fix some minor typos in power testing xml file.

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Wed, 03 Dec 2014 16:26:04 +0000
```

What's the deal with phone menu? :p This aint no phone it's a PC.

If you decide to install unity8mir(next) those packages will be there to handle it.[/QUOTE]

Phone menu in phone greeter? Not really a fan of unity so I doubt if I go that route. I like flashback and I'm sticking to it. :)

---

### Post by ventrical on 2014-12-09
> **Cavsfan said:**
> Phone menu in phone greeter? Not really a fan of unity so I doubt if I go that route. I like flashback and I'm sticking to it. :)

Convergence may not be so kind to gnome flashback. We have to test the other options in the arsenal of DEs.

Regards..

---

### Post by zika on 2014-12-10
> **Cavsfan said:**
> Forgot to mention does any one know when the 3.18 kernel will come through in regular updates? I'm still running the kernel that Utopic has.
And just say no to kernel ppas or building your own too. :p[http://www.phoronix.com/scan.php?page=news_item&px=MTg1ODg](http://www.phoronix.com/scan.php?page=news_item&px=MTg1ODg)

---

### Post by Cavsfan on 2014-12-10
> **ventrical said:**
> Convergence may not be so kind to gnome flashback. We have to test the other options in the arsenal of DEs.

Regards..

If convergence kills gnome flashback that will be bad. I'm doing all I can at present. I had to do stuff in windows until 2pm today and I only cried for like 20 minutes. :p

Regards

> **zika said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTg1ODg](http://www.phoronix.com/scan.php?page=news_item&px=MTg1ODg)

Thanks for that zika!

So, like I think it was you who said this: when the 3.18 or later kernels come through in regular updates they will replace the ones we've installed right?
If they are a higher version number it would have to I guess.

---

### Post by ventrical on 2014-12-25
I installed the gnome 3.14 core ppa and now I am getting some bugs (as reported in other thread). So just making a note that this install is no longer fresh ,clean install.

Regards..

---

### Post by ventrical on 2015-02-17
Most recent update 3.18.n-13 killed my machine. I mean literally killed it.

I had just finished updating gnome3-shell and it would not shut down from the panel so I;

Ctrl+Alt+F1

then,

```

sudo reboot

```

and got 

```

starting version 128

```

Then , black screen, fans off and now machine will not start. Green Light is on in motherboard. Tried disconnect cables .. etc..

This is a new one :) lol

---

