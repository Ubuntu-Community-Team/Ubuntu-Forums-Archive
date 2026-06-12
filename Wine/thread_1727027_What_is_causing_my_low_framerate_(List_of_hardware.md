---
title: "What is causing my low framerate? (List of hardware, etc included)"
date: 2011-04-12
forum: Wine
---

### Post by Murdoc419 on 2011-04-12
I have recently installed Ubuntu on my old desktop after finding that my laptop will have a very hard time running World of Warcraft even though it has superior hardware just because it has an Intel chipset. Anyway I have WoW up and running and everything is great except the framerate. I am only getting around 1-5 fps inside of towns and 5-15 outside of them. I followed the directions at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) minus the installation instructions. (I had previously installed wow on a Windows machine and just transferred it) With glxgears I am getting around 1620 fps. Ok so here is my hardware:

description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: c
          bus info: cpu@0
          version: 15.11.1
          slot: Socket AM2
          size: 1GHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz

description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:23 memory:fb000000-fbffffff memory:e0000000-efffffff me

And 1GB of RAM.

The driver I am using for my GPU is version 260.19.06. The PC I am using is a Dell Inspiron 531s which is a slim desktop. I'm not sure if my issue is due to subpar hardware or maybe an issue with the driver or possibly some other problem. I'm very new to Ubuntu. Anyway, if someone happens to know what the problem is I would very much appreciate the help. Thanks in advance.

PS: If any additional information is needed let me know and I'll get it up here with haste.

---

### Post by madjr on 2011-04-12
is it running in directx mode or opengl mode?

---

### Post by Murdoc419 on 2011-04-12
OpenGL. Also I followed the registry tweak in the guide from the link. Didn't seem to cause any change.

---

### Post by madjr on 2011-04-12
ok, lets see if something here can help you.

which version of ubuntu you have? is it installed on its own partition? is the binary proprietary driver installed?

have you disabled 3d desktop effects?

lower game resolution and effects.

the geforce 6150 is pretty old/low end, but i think you could squeeze some more frames, specially if in windows wow was doing better.

you can try some other games equivalent to wow graphics see if they also run slow (be it native linux or with wine).

for your intel card, you might check here:
[http://ubuntuforums.org/showpost.php?p=10524789&postcount=3](http://ubuntuforums.org/showpost.php?p=10524789&postcount=3)


and you may check this thread for wow/wine discussion.
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

you may also try reinstalling wow from scratch using playonlinux, some people have reported either graphics or frame improvement, over just copying the folder from windows (but for many that option is fine if they have good hardware)

if everything else fails, you could try getting a cheap nvidia cards, like the 8400 (or better). Most games i tried on it run well and is very affordable.

---

### Post by cwwilson721 on 2011-04-12
The tweaks, etc, aren't going to help much.

The issue is the integrated vid chip, the 6150.

I have the identical chip on my board, and if I run WoW/wine on it, I get the same framerates.

If you look at the specs of the chip, you'll see the reason why:
[LIST]
[*]Core clock: 425 MHz
[*]Vertex processors: 1
[*]Pixel pipelines: 2
[/LIST]
That is VASTLY underpowered for WoW after patch 4.0

Before patch 4.0, I did use it on occasion, but never could do more than a 5man instance. Raids, BGs, etc, were out of the question, because FPS would drop to 2 or less, so...

Your only hope is to have an expansion slot on your motherboard that can take a 9600 (Not GS, or GT 210) or higher Nvidia card. 

BTW, the 8400 is NOT a good card either. Check out this list at [Tom's Hardware]("http://www.tomshardware.com/reviews/best-gaming-graphics-card-geforce-gtx-590-radeon-hd-6990,2879-7.html")

---

### Post by cogadh on 2011-04-12
> **cwwilson721 said:**
> 
BTW, the 8400 is NOT a good card either. Check out this list at [Tom's Hardware]("http://www.tomshardware.com/reviews/best-gaming-graphics-card-geforce-gtx-590-radeon-hd-6990,2879-7.html")
That's quite a useful list. Bookmarked for future reference, thanks!

---

### Post by Murdoc419 on 2011-04-12
@ Madjr

I am running Ubuntu 10.10 and it is the only OS on my PC. Not sure about the binary proprietary driver, is there a command I can use to check that? I would prefer not to lower the resolution (I am using a Sony Bravia 32" as my monitor) I have all the game settings on low except that I have projected textures on (Kind of a necessary thing with some of the game mechanics) I will try installing it through PlayOnLinux. It will take a while for me to see those results as it is a long download process. 

Would the 8400 work with my motherboard? Like I said it is a slim desktop so I'm guessing I would have to use a special GPU. I will post the details of my motherboard at the end. (Sorry I'm especially a noob when it comes to hardware.)

@cwwilson721

What GPU would you suggest? I would like to stay at least under $100 so I'm not sure what I could get with that. 

Info about my motherboard:

```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1015MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          version: 15.11.1
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
          resources: ioport:c000(size=4096) memory:fde00000-fdefffff memory:fd900000-fd9fffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:fdef0000-fdefffff ioport:cc00(size=8)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe028000-fe02bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1a:a0:75:15:4e
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:42 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:b000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:a000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:23 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:40000000-4001ffff
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

```

BTW, sorry for such a long list. Wasn't sure exactly which info would be needed so I just pasted it all.

---

### Post by Tweak42 on 2011-04-12
Low frame rate is definitely the onboard video.  I looked at the specs for the Inspiron 531s (slim) and it does have a PCI Express 16x slot needed for a video card.  Look in your manual and there should be a picture diagram of the motherboard.

Since you have the slim model case, you must use a **low profile video** card.  I would not recommend a 8400 unless that's all you can afford.  A good fit for your system would be one of the Geforce GT 430 series cards.  Price range from $50-$80.  Just make sure that the low profile brackets are included, and beware there are 64bit and 128bit memory bus models in addition to 512MB and 1GB video memory models.

There are some faster low profile cards that cost more, but you gotta watch out for physical size, power requirements, and skip if they are ATI/AMD since drivers are still not that great.

---

### Post by Murdoc419 on 2011-04-12
> **Tweak42 said:**
>  Since you have the slim model case, you must use a **low profile video** card.  I would not recommend a 8400 unless that's all you can afford.  A good fit for your system would be one of the Geforce GT 430 series cards.  Price range from $50-$80.  Just make sure that the low profile brackets are included, and beware there are 64bit and 128bit memory bus models in addition to 512MB and 1GB video memory models. 

So would you suggest [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130633](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130633) ?

Would you happen to know if it is compatible with my system or if I would need a larger power supply? Or perhaps tell me how I could find out. Sorry I'm asking for so much I'm just a complete noob when it comes to hardware and I don't want to buy something I can't use.

Also are CPUs fairly easy to replace? And is this a fairly good model? [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103903](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103903)

---

### Post by cwwilson721 on 2011-04-12
> @cwwilson721

What GPU would you suggest? I would like to stay at least under $100 so I'm not sure what I could get with that. 

A quick Newegg search of low profile Nvidia cards (I left out ATi/AMD, because of two things. 1: Support for older cards is dreadful, if at all, and 2: Linux drivers are still behind and can be difficult) comes up with :

[A GT 520 for 59.95 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130632")
It's 1 1GB card w/64 bit memory width
Or, even better, a [Sparkle GT 430 for 64.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187121") with a 128-bit memory path.

And that was a very quick search.

---

### Post by Murdoc419 on 2011-04-12
I was more or less unsure of what type of video card I should be looking for. As you can see I searched and found the same EVGA card lol. I may go with the Sparkle if it is better for just 5 more bucks. I hate to ask even more but do you know if that would fit in my PC or is there perhaps a place online that could tell me the compatibility? I'm guessing there's a good chance I would have to upgrade my power supply but I don't know what it currently is or what these cards would require.

---

### Post by cwwilson721 on 2011-04-13
It's a low profile card, which is a standard height.

If you do a Google search for the card, it will give you the manufacturers page, which *should* tell you length, extra power connectors, power supply needs, etc. Then compare to what your system has, and will allow as far as size (Look on the manufacturer's web site) 

Remember: GOOGLE IS YOUR FRIEND!

lol

---

### Post by Tweak42 on 2011-04-13
> **Murdoc419 said:**
> So would you suggest [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130633](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130633) ?

Nvidia model numbering is 1st number = family generation, following numbers = speed rated on scale 10-90.  So the GT 520 is supposed to be slower than the GT 430, and a GT 240 is supposed to be faster than GT 430. Since the GT 430 has a 128bit bus vs.the GT 520 64bit, this is likely, though actual benchmarks should be run to confirm.
> 
Would you happen to know if it is compatible with my system or if I would need a larger power supply? Or perhaps tell me how I could find out.

You should check the manufacture specs, but I'm fairly certain your Dell will handle one of these cards because: a) Dell should have built in some spare capacity power since there are open expansion slots b) video cards that lack separate power connectors and have small fan/heatsinks don't suck gobs of power.
> 
Also are CPUs fairly easy to replace? And is this a fairly good model? [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103903](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103903)

Processors are physically pretty simple to replace, but finding one that is compatible is tricky.  The one linked is a socket AM3, and your system is socket AM2 so it won't fit.  It's not a performance bottleneck so I'd leave it alone.  What is a bottleneck is you only have 1GB of system memory, which is **really** cramped if you plan to run Wow (2GB+ recommended).  Again google the specs.

I'd be a little cautious of the Sparkle card cwwilson721 linked because I can't tell if the low profile bracket is included in the package (it maybe, just not pictured).  I bought a EVGA GT 430 and they charge $5 separately for the low profile bracket, which I fortunately didn't need.

---

### Post by cwwilson721 on 2011-04-13
$5 ??

I've got 2 laying around here...lol..Maybe I should just sell them.

But seriously, those were just examples. To answer Tweak42's questions about benchmarks, the 430 is a bit 'faster'.

Nvidia's numbering system can be a bit confusing. That was why I posted the 'hierarchy' link. To see a significant speed difference, you should look 3 or more 'tiers' above one card to the next. What I mean by 'significant' is something you can actually tell, rather than a '1-2 FPS increase'. A 3 tier jump is almost a order of magnitude jump in those charts. While you may see a FPS increase in just 2 tiers, or maybe 1, a 3 tier jump is very noticeable.

The basic 'specs' you want in a Nvidia card are (min):
[LIST]
[*]48 cores
[*]128-bit memory 
[*]GDDR3 if possible. GDDR5 is much better, but with GDDR2 you would want even higher memory bandwidth (192-bit or 256) 
[*]Min 512 ram. This is only a 'big deal' when using AA. If you do, then the more, the better. DO NOT, EVER, GET A TURBO-CACHE CARD!!!!
[*]500 Mhz clock, 750 Memory
[/LIST]

All these are mins I would use if I was to buy a new card for WoW.

In the 2 examples I linked to before, memory clock speeds (400), memory types (DDR3, so 400*3=1200), and amount are the same (1GB)
The differences are the core clock (the 520 is 810Mhz, the 430 has 700Mhz), while the stream processors (cores) are 48 on the 520, and 96 on the 430. Combine that with a 64-bit memory path on the 530, and a 128-bit path on the 420, the 420 pushes out many more textures per clock cycle. 

Ex: 810x48x64 (theoretical max on the 530)is 2.48 GB, while the 420 is 700x96x128 or 8.6 G (This is JUST examples. Reality is MUCH different. But the numbers mean the 420 is DEFINATELY the 'better buy'). 

So for $5 USD more, the 420 is 'better', even if you have to get a LP bracket.

So, in conclusion, read the specs of the card for Memory type, Clock speeds (both core and memory, or RAMDEC), Memory bus width, and power requirements.

And, for the OP, if it's a 'Low Profile' card, too. (The 'low profile ready' usually means no bracket)

---

### Post by hip2theehop on 2011-04-15
Could you please post a copy of your Xorg.conf file. I had the same problem with some other games and I noticed that my system was using the wrong driver which is conf in your Xorg.conf file.

Thanks ahead of time.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by cwwilson721 on 2011-04-15
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```
Just the standard Xorg created by Ubuntu after installing the Nvidia proprietary ( current )drivers.

---

### Post by hip2theehop on 2011-04-15
I would suggest using nvidia X server settings and turning AA (Anti-Aliasing) to off and make sure all your setting are correct (to how you like them) then go to the display configuration tab and save to x configuration. Then let me know how well it responds.

also if you could post a lspci prinout.

```
lspci -v -k
```

---

