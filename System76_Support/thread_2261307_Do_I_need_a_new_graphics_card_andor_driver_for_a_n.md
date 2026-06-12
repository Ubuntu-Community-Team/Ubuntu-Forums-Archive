---
title: "Do I need a new graphics card and/or driver for a new 4k monitor?"
date: 2015-01-17
forum: System76 Support
---

### Post by watchpocket on 2015-01-17
I need a new monitor fast.  I currently use two 28-inch Hanns-G 281Ds and one of them is flaking pretty seriously.  I'm looking at getting [this]("http://www.amazon.com/Acer-B286HK-ymjdpprz-Widescreen-ErgoStand/dp/B00MN2OKKO/ref=sr_1_1?s=pc&ie=UTF8&qid=1421535350&sr=1-1&keywords=Acer+B286HK") Acer B286HK "4k"-resolution display.

[B][I][COLOR=#0000ff]My question is:  Will I need a new graphics card and/or driver for this higher-rez monitor?  [/COLOR]
[/I][/B]
Right now when I go to "System Settings" --> "Display Settings" the choices in the "Resolution" dropdown menu go up ***only*** to "1920 x 1200 (16:10)".

I'm running Ubuntu 12.04.5 (but about to move to 14.04.1 LTS) on a System76 Wild Dog Performance desktop unit, model wilp6, which I bought around Thanksgiving of 2009.  

My graphics card, a GeForce GTS 250, apparently has exactly 1024 MB of memory, which doesn't seem like a whole lot these days.  

One other question is what graphics card(s) will my (somewhat older) machine handle?

Also, will it make sense (or is it even possible) to be using a new monitor at 3840 x 2160 resolution side-by-side with my old monitor running at 1920 x 1200 rez?  Or must they both be set at the same resolutions?

My nVidia driver version is 304.125. 
Server Version Number: 11.0; 
Server Vendor Version: 1.15.1 (11501000);
NV-CONTROL Version: 1.28

One possible item of interest is that I notice in my nVidia X Server Settings, in "X Screen Information", it says: 
"Dimensions:  3840x1200 pixels (1016x318 millimeters); 
Resolution: 96x96 dots per inch; 
Depth: 24" 

  Here is some command-output, thanks for any perspective anyone might have:
```
[rj@rjbox:~]  [v5.0.5]  zsh  1011  --> [COLOR=#0000ff]lsb_release -a[/COLOR] 
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

[rj@rjbox:~]  [v5.0.5]  zsh  1012  --> [COLOR=#0000ff]lspci -nnk | grep -iA3 vga[/COLOR]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [GeForce GTS 250] [10de:0615] (rev a2)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:34c7]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_331_updates, nvidia_304, nouveau, nvidiafb

[rj@rjbox:~]  [v5.0.5]  zsh  1013  --> [COLOR=#0000ff]sudo lshw -C display[/COLOR]
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:e3000000-e301ffff
sudo lshw -C display  4.03s user 0.13s system 97% cpu 4.245 total 
```

Last command output, formatted differently: ```

[TABLE="class: node"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]display[/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]VGA compatible controller[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]G92 [GeForce GTS 250][/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]nVidia Corporation[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"]0[/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"]pci@0000:01:00.0[/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]a2[/TD]
[/TR]
[TR]
[TD="class: first"]width:[/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
[TR]
[TD="class: first"]clock:[/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]pm msi pciexpress bus_master cap_list rom[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]nvidia[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]16[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]e2000000-e2ffffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]d0000000-dfffffff(prefetchable)[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]e0000000-e1ffffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] ioport[/TD]
[TD]:[/TD]
[TD]e000(size=128)[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]e3000000-e301ffff(prefetchable[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

---

### Post by gordintoronto on 2015-01-18
According to this page: [http://www.geforce.com/hardware/desktop-gpus/geforce-gts250/specifications](http://www.geforce.com/hardware/desktop-gpus/geforce-gts250/specifications)

your graphics card can not produce 384x2160 output.

With the appropriate hardware and drivers, you should be able to have two monitors with different resolution.

---

### Post by watchpocket on 2015-01-19
Hm, looks like none of the cards in that 200-series "product family" can do 3840x2160.  I'll have to find out just how high a model GPU my machine can accommodate.  Thanks!

---

### Post by gordintoronto on 2015-01-20
The System 76 web site still shows a Wild Dog Performance, but I assume it is quite different from your 2009 system. You will probably find that the supported video cards depend on three physical factors: the type of slot on the motherboard, the dimensions of the space inside the computer case, and the capacity of the power supply.

From what I have read, nVidia recently introduced some new video cards which are not yet well supported in Linux. Using hardware which was designed later than your OS is often problematic. Just one more thing to be aware of.

---

### Post by JeQhdMD on 2015-01-22
This should do the trick nicely:

[https://system76.com/desktops/leopard](https://system76.com/desktops/leopard)

---

### Post by watchpocket on 2015-01-23
Donations are accepted!

---

