---
title: "screen noise (solution... Is correct?)"
date: 2016-07-10
forum: Ubuntu Development Version
---

### Post by oklokl on 2016-07-10
[Problems]
[https://youtu.be/PCCKJ23UWoI](https://youtu.be/PCCKJ23UWoI)
[http://prod.danawa.com/info/?pcode=2833349#bookmark_product_information](http://prod.danawa.com/info/?pcode=2833349#bookmark_product_information)
UDEA EDGE 23F(monitor)

[http://www.gigabyte.com/products/product-page.aspx?pid=5347&kw=GA-B85M-HD3-A1.0#bios](http://www.gigabyte.com/products/product-page.aspx?pid=5347&kw=GA-B85M-HD3-A1.0#bios)
GA-B85M-HD3-A (Motherboard)


[solution??]
[https://youtu.be/NxQpp8sUKHY](https://youtu.be/NxQpp8sUKHY)
Ubuntu pc screen noise Fix?
Setting Ubuntu) monitor) changes on the monitor
Launcher arrangement (monitor)
All windows and content (Monitor)
[ATTACH=CONFIG]270062[/ATTACH]


I do not currently occurring.
Two days elapsed.

This will affect the monitor BIOS.(guess)
[B]In my opinion..... Highest resolution (bugs) here.

My guess is the scenario.
Thank you..[/B]

---

### Post by Skaperen on 2016-07-10
can you *describe* more?

---

### Post by grahammechanical on 2016-07-10
Please run this command to show the correct screen resolution.

```
xrandr
```

You will see something like this

> graham@Ub1604:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i    60.00*+  50.00    59.94  
   1920x1080     24.00    23.98  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    70.07    60.00  
   1440x480i     59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94 

Please copy the printout into this thread. The correct screen resolution for your monitor is 1920 x 1080 at 60 Hz. How long does it take to load Ubuntu 16.10? What video adapter? Nvidia or AMD? Are you using the open source video driver or a proprietary video driver. Go to System Settings>Software & Updates>Additional Drivers tab. 

It is normal for the video signal to switch on and off during the loading of Ubuntu. The motherboard uses a default screen resolution and Linux loads with the same screen resolution and uses a display server called X Server until it is time to load a video driver. With a video driver loaded a different screen resolution is set. Then Ubuntu logs into Linux and Ubuntu loads a display manager called LightDM (Light Display Manager) to give us a login screen. This process of switching video drivers and display mangers causes the video signal to switch on and off. This switching should be hidden by a splash screen but often the splash screen does not appear. This is normal.

Regards.

---

### Post by oklokl on 2016-07-11
My pc is hdmi2.0.
Sign woobunteu (full screen)
Noise ... menu does not appear.
(Often several times .. only .. power switch resolved) =
Cause => (Ubuntu + cache associated monitor BIOS) [my thoughts]


so..
Checked your computer clean.
Cleaning Remove any parts on pc ..
BIOS initialization (mercury batteries)

Then set (Monitor fix)
Then .. pc does not bother me. ^^ ;;

```
xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1360x768      60.02  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

Linux tester-B85M-HD3-A 4.7.0-999-lowlatency #201607092202 SMP PREEMPT Sun Jul 10 02:06:02 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
lshw
WARNING: you should run this program as super-user.
iudhfgiu-b85m-hd3-a       
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 6944MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU G1840 @ 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2799MHz
          capacity: 2800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer xsave rdrand lahf_lm abm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust erms invpcid xsaveopt dtherm arat pln pts cpufreq
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:25 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:f7d14000-f7d17fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:24 memory:f7d00000-f7d0ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:28 memory:f7d1e000-f7d1e00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7d1c000-f7d1c3ff
        *-multimedia:1
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:f7d10000-f7d13fff
        *-pci:0
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 0c
                serial: 40:8d:5c:14:87:6a
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=|Privacy ^^ ;;| latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:26 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19
           *-pci
                description: PCI bridge
                product: 82801 PCI Bridge
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7d1b000-f7d1b3ff
        *-isa
             description: ISA bridge
             product: B85 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7d1a000-f7d1a7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d19000-f7d190ff ioport:f040(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by Smask on 2016-07-11
Are you using good cabling? When I had trouble with my monitor, it boiled down to a crappy VGA cable that wouldn't let me use the full resolution.
The monitor I'm using now is becoming long in the tooth and I'm getting circuit noise when I use the mouse (DVI + USB + audio)

---

### Post by oklokl on 2016-07-11
[Thank edit my answer.]
I am using a nice cave ^^ ..(I've tried various tests ... No problem. My cable)
Thank you for answer.
Is the monitor bug .. or .. or .. Is motherboard bugs.(In my opinion ...)
Is Ubuntu bug ... find out why.

But now ...

My pc is stopped, bug .. ^^

So this is ...

Monitor settings in Ubuntu.

I just ... curious.(How did it resolved?) The extent ... ^^;;
(This symptom affects Windows 10.)



{After fixed ... story ...}
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1600601](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1600601) (My) Once the message out.
There was such a thing.
After initializing the BIOS .. .. ..
BUG message output.
[Everything is normal.]


Clean pc .. then came the message
Followed by the message has not been repeated.


Additional Information
(My backup program clonezilla)
Use usb(I use efi.) to boot.
The program offers its own graphics settings.

---

