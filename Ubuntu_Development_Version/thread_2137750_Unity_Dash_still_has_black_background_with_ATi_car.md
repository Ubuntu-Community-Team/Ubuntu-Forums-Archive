---
title: "Unity Dash still has black background with ATi cards"
date: 2013-04-21
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-04-21
Todays daily (raring-desktop-i386.iso) *still* produces black background Unity dashes with ATi cards. Will this ever be fixed or is this now the standard for older ATI cards?

---

### Post by QueenZ on 2013-04-26
I have the same problem, the Unity dash background is totally black....[ATTACH=CONFIG]241825[/ATTACH]

---

### Post by QueenZ on 2013-04-27
there has to be a fix right?

---

### Post by screaminj3sus on 2013-04-27
It looks like you are in unity's "low graphics mode". In this mode dash blur is disabled and its totally opaque.

---

### Post by rrich1974 on 2013-04-28
at my laptop, take a look:

---

### Post by ventrical on 2013-04-28
> **rrich1974 said:**
> at my laptop, take a look:

 I get the exact same thing on my Acer Extensa AMD Dual Core Radeon Express 1250, but only with raring.

---

### Post by cactus john on 2013-04-28
> **screaminj3sus said:**
> It looks like you are in unity's "low graphics mode". In this mode dash blur is disabled and its totally opaque.

Is there a fix for this?
Like others, I only get this in Raring.

---

### Post by rrich1974 on 2013-04-28
i get this on raring too, on 12.04 it looks okay. 
i dont think we need a fix for this since the unity works fine. it is not slow or something. 
the problem seems to be related to the radeon graphic driver since i get about 33 FPS on glxgears versus 29 fps on 12.04.

---

### Post by ventrical on 2013-04-29
> **rrich1974 said:**
> i get this on raring too, on 12.04 it looks okay. 
i dont think we need a fix for this since the unity works fine. it is not slow or something. 
the problem seems to be related to the radeon graphic driver since i get about 33 FPS on glxgears versus 29 fps on 12.04.

I tried switching monitors but that didn't work. Tried two of the same types of ATi graphics cards on different systems. No go. They work great (excellent) on Quantal - but I don't get why they have bugged out during the raring cycle. If I use nomodeset during install then I get llvmpipe which is the most horrible desktop experience you can imagine.

---

### Post by rrich1974 on 2013-04-29
i think we should report a bug.


later edit:
i just have reported a bug. take a look: 
[https://bugs.launchpad.net/unity/+bug/1174285](https://bugs.launchpad.net/unity/+bug/1174285)

---

### Post by ventrical on 2013-04-29
> **rrich1974 said:**
> i think we should report a bug.


later edit:
i just have reported a bug. take a look: 
[https://bugs.launchpad.net/unity/+bug/1174285](https://bugs.launchpad.net/unity/+bug/1174285)

+1

  but I am wondering if it is Unity or ATi driver.

Good bug report. Hope it gets fixed because it affects a lot of not so old ATi cards.

---

### Post by rrich1974 on 2013-04-29
i do not know what is the exact cause of this, i only can guess that it has something to do with radeon driver....
but maybe is an issue between unity and radeon driver.
so, i am talking about opensource driver, the proprietary driver is long gone by now!

---

### Post by ventrical on 2013-04-29
here is lshw for qq
```

0000000-dfffffff
           *-display:0
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master vga_palette cap_list rom
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
                capabilities: cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff memory:e5010000-e501ffff

```


Here is lshw for rr on same machine:

```

0000000-dfffffff
           *-display:0
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master vga_palette cap_list rom
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
                capabilities: cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff memory:e5010000-e501ffff

```

So they are both the same. Quantal will not detect  and report the adpated or driver in >settings>about this computer but RR does.

On Quantal it works just fine with compiz and ccsm. Almost defintely needs to be a Unity or kernel patch.

---

### Post by rrich1974 on 2013-04-29
here is my partially glxinfo
> OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS690
OpenGL version string: 2.1 Mesa 9.1.1
OpenGL shading language version string: 1.20


---

### Post by ventrical on 2013-04-29
Read this msg from Grahamechanical. I think this is the core problem.

[http://ubuntuforums.org/showthread.php?t=2140220&p=12624927#post12624927](http://ubuntuforums.org/showthread.php?t=2140220&p=12624927#post12624927)

---

### Post by woodp on 2013-04-29
Are you certain this is an ATI problem? I'm running an Intel 3000 chipset in a Lenovo laptop and if I select "Color & Gradients" for my background, I get a *black* background regardless of color selection.

This was a clean 13.04 install.

---

### Post by rrich1974 on 2013-04-29
to be honest, i didn't get the message...

---

### Post by ventrical on 2013-04-29
> **rrich1974 said:**
> to be honest, i didn't get the message...

  I think that perhaps there had been some video driver regression with the newer kernels as one of the possibilities.

---

### Post by rrich1974 on 2013-04-30
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1167018](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1167018)
this is the bug: it seems that someone was faster than me.

---

### Post by faida on 2013-05-03
it happens when you change the background of launcher to custom color

---

### Post by rrich1974 on 2013-05-03
i use the default config. i did not change anything!

---

