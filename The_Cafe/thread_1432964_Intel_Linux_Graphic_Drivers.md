---
title: "Intel Linux Graphic Drivers"
date: 2010-03-18
forum: The Cafe
---

### Post by _h_ on 2010-03-18
nVidia has been the leader on Linux for it's outstanding graphic drivers, and ATI has finally boarded ship and has started actually producing decent drivers.

However, us people with Intel and the short end of the stick are left with absolute garbage drivers.

My question is, how long do you think it will take Intel to get on board with nVidia and ATI and start producing good linux drivers?

---

### Post by chris200x9 on 2010-03-18
delete

---

### Post by Psumi on 2010-03-18
[http://ubuntuforums.org/showthread.php?t=1385703](http://ubuntuforums.org/showthread.php?t=1385703)

A CPU that can do better than most graphics cards of today.

---

### Post by cascade9 on 2010-03-18
From what I know, the intel drivers are OK. Its just that Intel onboard video, to be honest, lacks the 3D power of the ATI and nVidia GPUs. 

> **Psumi said:**
> [http://ubuntuforums.org/showthread.php?t=1385703](http://ubuntuforums.org/showthread.php?t=1385703)

A CPU that can do better than most graphics cards of today.

Hardly. That video on the link wasnt exactly convicing IMO. Besides that, if CPUs can beat GPUs now, why would intel be working on larrabee? 

[http://en.wikipedia.org/wiki/Larrabee_%28microarchitecture%29](http://en.wikipedia.org/wiki/Larrabee_%28microarchitecture%29)
[]("http://en.wikipedia.org/wiki/Larrabee_microarchitecture")

---

### Post by alexfish on 2010-03-18
> **_h_ said:**
> nVidia has been the leader on Linux for it's outstanding graphic drivers, and ATI has finally boarded ship and has started actually producing decent drivers.

However, us people with Intel and the short end of the stick are left with absolute garbage drivers.

My question is, how long do you think it will take Intel to get on board with nVidia and ATI and start producing good linux drivers?


When God does a remake of the 10 Commandments

---

### Post by mickie.kext on 2010-03-18
@ _h_

Intel makes very nice open source drivers, just their graphics are pure crap and no drivers can help with that. 

@cascade9

Intel canceled Larrabee.

---

### Post by cariboo on 2010-03-18
I have an Atom powered media center pc with the Intel 945 chipset, it is currently running XBMX Live based on Karmic. It runs better than I expected, no video tearing, or any other problems. As far as I'm concerned the Intel drivers work well.

---

### Post by Psumi on 2010-03-18
> **cariboo907 said:**
> I have an Atom powered media center pc with the Intel 945 chipset, it is currently running XBMX Live based on Karmic. It runs better than I expected, no video tearing, or any other problems. As far as I'm concerned the Intel drivers work well.

Is it GM or just plain 945? If so, you may remember me having one back in 2006/7.

---

### Post by cascade9 on 2010-03-18
> **mickie.kext said:**
> 
@cascade9

Intel canceled Larrabee.

Nope. Well, sotr of, but not totally- 


> So today's announcement was not SO surprising.  To be fair, **Intel is not canceling the entire Larrabee project**, they are just basically admitting that the first iteration of this architecture was not going to be released in any retail form.

Snip!

With Intel officially calling this a "delay" rather than a scrubbing of the entire idea, we have to wonder WHAT would cause Intel to admit defeat now?[http://www.pcper.com/article.php?aid=826](http://www.pcper.com/article.php?aid=826)

> But, Larrabee is not dead. Development on Larrabee will continue, and when it is a competitive product, it will hit stores. This could be 2011, 2012, later, or never.[http://vr-zone.com/articles/intel-larrabee-canceled-but-not-dead/8131.html](http://vr-zone.com/articles/intel-larrabee-canceled-but-not-dead/8131.html)

Theres a ton of other links around, all with pretty much the same tone.

I'm not really holding out that much hope for Larrabee myself, but I'm old enough to remeber the horrid mess from last time intel tried to lauch a standalone video card (i740).

---

### Post by JDShu on 2010-03-18
My G41 chipset had shader issues in games out of the box with 9.10, but after upgrading through the ppa to Mesa 7.6.1 and now I can run Nexuiz and Sauerbraten flawlessly. For me, the Intel drivers are fine. The nice people over at Phoronix told me that we can expect even more improvements in 7.7.

---

### Post by mickie.kext on 2010-03-18
> **cascade9 said:**
> Nope. Well, sotr of, but not totally- 
...
Theres a ton of other links around, all with pretty much the same tone.

I'm not really holding out that much hope for Larrabee myself, but I'm old enough to remeber the horrid mess from last time intel tried to lauch a standalone video card (i740).

That is what I meant:KS.

They cancelled that thing we know as Larrabee, but they might make some new thing in future and recycle the codename.

They already did that it the past. Remember Netburst and Prescott? Remember that Tejas was announced to be their new 5Ghz P4 core, and Nehalem was anuonced as successor of Tejas and is expected to go 10Ghz. Then they put down their crack pipes, cancelled Tejas and Nehalem and gone multicore with Presler in 2006. 

In 2008, they rolled out Nehalem (Core i7), except that code name was only thing in common with old Netburst-based Nehalem which was cancelled. 

So yeah, Larrabee is dead but long live Larrabee. :popcorn:

They definitely want to make graphics card but I do not think that they will manage to do it by gluing x86 cores together.

---

### Post by Psumi on 2010-03-18
> **mickie.kext said:**
> They definitely want to make graphics card I do not think that they manage to do it by gluing x86 cores together.

Most high end graphics cards have over 100 cores, all at around 600 to 1000 MHz each. They aren't 16, 32, 64 nor 128 Bit though, and are usually a higher bitdepth than processors can currently be (with 128-bit processors around the corner though, we might see 512-bit GPUs.)

---

### Post by mickie.kext on 2010-03-18
> **Psumi said:**
> Most high end graphics cards have over 100 cores, all at around 600 to 1000 MHz each. They aren't 16, 32, 64 nor 128 Bit though, and are usually a higher bitdepth than processors can currently be (with 128-bit processors around the corner though, we might see 512-bit GPUs.)
Those bits on graphics card you see are not to be compared with CPU word bits. NVIDIA GTX285 has **512-bit memory bus**. That can be compared to 192-bit (triple chanel) memory bus on Core i7 CPU, but has nothing to do with 64-bit CPU instructions and such. 

NVIDIA GTX260 is midrange card and have 216 "cores", while 4850 has 800 "cores". But that again can not be compared with CPU cores because those are much different and much more ineficient because x86 drags 40 years of backward compatibility. 

Intel with Larrabee tried to change the game by gluing 48 undersized (Atom-like) x86 CPU cores on one chip... 

But I think we are off topic here. We can make another topic for discussing chips? :lolflag:

---

### Post by Psumi on 2010-03-18
> **mickie.kext said:**
> But I think we are off topic here. We can make another topic for discussing chips? :lolflag:

[http://ubuntuforums.org/showthread.php?t=1433095](http://ubuntuforums.org/showthread.php?t=1433095)

---

### Post by doorknob60 on 2010-03-18
When they start making cards that can compete with Nvidia and ATI, not just integrated stuff...

---

### Post by GeoPrude on 2010-03-18
> **_h_ said:**
> ...ATI has finally boarded ship and has started actually producing decent drivers...

No they haven't. Maximizing windows still takes a couple of presidential terms.

---

### Post by NightwishFan on 2010-03-18
Perhaps is there a thread or perhaps an Ubuntu Community Documentation article where Ubuntu or Linux specific Intel tips are? I know there are some PPAs with updated drivers, but they do not bring any performance gains for me.

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

### Post by GeoPrude on 2010-03-18
> **NightwishFan said:**
> Perhaps is there a thread or perhaps an Ubuntu Community Documentation article where Ubuntu or Linux specific Intel tips are? I know there are some PPAs with updated drivers, but they do not bring any performance gains for me.

One small tip for Intel and open source ATI. Install driconf, and select yes for the;

> Enable S3TC texture compression even if software support is not available

Option under the Image Quality tab. It solved quite a few 3D issues with Intel for me.

---

### Post by Psumi on 2010-03-18
> **GeoPrude said:**
> [QUOTE=_h_;8988127]...ATI has finally boarded ship and has started actually producing decent drivers...
No they haven't. Maximizing windows still takes a couple of presidential terms.[/QUOTE]

You sir...

[SIZE="7"]HAVE WON THE GAME[/SIZE]

---

### Post by GeoPrude on 2010-03-18
> **Psumi said:**
> You sir...

[SIZE="7"]HAVE WON THE GAME[/SIZE]

Where's my cookie?

---

### Post by NightwishFan on 2010-03-18
I have a little better performance by installing the drivers in this PPA.
[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

Does anyone know where I can find 2.10 drivers in Karmic?

---

### Post by NightwishFan on 2010-03-21
Correction of above post! I improved performance magnificently in Lucid by creating a blank /etc/X11/xorg.conf and adding the following to it:
```
Section "Device"
        Identifier    "Configured Video Device"
        # ...
        Option        "AccelMethod" "uxa"
EndSection
```

I testing using Compiz Benchmark Plugin. Intel drivers seem to use Sync to Vblank, so compiz only achives a MAX of 60fps. On default configuration the FPS goes down to 20 when I launch the Compiz Expo plugin. With the option above it stays in high 50s and is stable. I will benchmark other stuff as well when I get the chance.

---

