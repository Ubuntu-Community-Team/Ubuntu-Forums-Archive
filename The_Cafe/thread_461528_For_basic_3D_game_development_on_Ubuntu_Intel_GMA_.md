---
title: "For basic 3D game development on Ubuntu: Intel GMA 950 or Nvidia GeForce Go 7300?"
date: 2007-06-01
forum: The Cafe
---

### Post by chombee on 2007-06-01
So I´m looking at buying a laptop to run Ubuntu, looking for some advice. I do some basic game development on Ubuntu as part of my university study, using the game engine Panda3D. My games have a medium polygon count and amount of collision detection going on, and basic 3D graphics, no fancy shaders or reflections or shadows or any special effects beyond the odd basic particle effect. It´s a research prototype so although it is a proper 3D game, fancy graphics are no priority, just have to be acceptable. So I want a laptop that I´ll be able to do some of this programming on.

I´ve been looking at the System76 Gazelle Performance:

[INDENT]
Celeron M 410 1.46GHz 1MB 533 FSB
512 MB DDR2 667 MHz
Graphics: nVidia GeForce GO 7300 with 128MB VRAM
Sound: Intel High Definition Audio
[http://system76.com/product_info.php/cPath/1/products_id/192](http://system76.com/product_info.php/cPath/1/products_id/192)
[/INDENT]

And Linux Emporium´s Lenovo 3000 N100:

[INDENT]
Intel® Celeron Mobile 430 1.7 GHz
512 Mb RAM
Intel Graphics Media Accelerator 950 WXGA
[http://www.linuxemporium.co.uk/products/laptops/](http://www.linuxemporium.co.uk/products/laptops/)
[/INDENT]

Both are about the same price. I was surprised that a laptop from a UK store would cost about the same as a roughly equivalent laptop in the US, but there you go.

The desktop in my office (which is far higher spec than either of these) has an nvidia card and the driver seems to work very well on Ubuntu. Do Intel´s drivers for the GMA 950 work equally well? I´m trying to figure out whether this GMA onboard graphics will do the job of basic 3D graphics for game development, or whether it´s a melon. Some reviews seem to say it´ll handle the basic mainstream gaming stuff, others say no way, but they seem to be looking at high-end games like Doom3 and Farcry. Then there is the additional question of whether the linux driver is any good.

I think I´ve missed my window for ordering the system76, as they won´t deliver to the UK, but if I know the GMA950 is a no-go, I can hunt around for a low-end (price-wise) laptop with that rare Nvidia 128mb card.

---

### Post by tseliot on 2007-06-02
I have moved this thread to the Cafe since it was not a technical support thread.

---

### Post by yatt on 2007-06-02
The Nvidia will be sinificantly faster. Some of Beryl's effects are too hard for the Intel IGC to handle, so if you want to make something more intense than Beryl, get the Nvidia.

---

### Post by maniacmusician on 2007-06-02
If you're going to be doing 3D rendering, I'd say that both of those laptops are much too weak, especially as far as processors go.

The nVidia will be better of course. Anyways, 3D rendering on laptops is quite expensive, since everything needs to be fairly high end, and laptop parts are always more expensive. Most people that are serious about 3D rendering should probably use desktops, where you can get higher quality parts for the same or less amount of money.

But I dunno. you're looking for a low end laptop, and want to do 3D design/rendering on it? I don't know how feasible that really is. especially with the small amount of RAM, and celeron netburst-based processors

---

### Post by jpeddicord on 2007-06-02
> **yatt said:**
> The Nvidia will be sinificantly faster. Some of Beryl's effects are too hard for the Intel IGC to handle, so if you want to make something more intense than Beryl, get the Nvidia.
Out of curiosity, what slows down in Beryl using Intel for you? I have the 950 chipset in a C2D 2GHz, and every single effect, including rain, runs at around 50/60fps with no slowdowns.

---

### Post by maniacmusician on 2007-06-02
> **jacobmp92 said:**
> Out of curiosity, what slows down in Beryl using Intel for you? I have the 950 chipset in a C2D 2GHz, and every single effect, including rain, runs at around 50/60fps with no slowdowns.
water is usually problematic with the 950 chipsets. Perhaps it works with the new drivers?

I'm getting a santa-rosa based laptop that will come with the X3100 (965 chipset), and it's really leaps and bounds above the GMA 950. I think it's pretty cool how integrated video is becoming more and more powerful.

---

### Post by happy-and-lost on 2007-06-02
If you're going to be compiling stuff, the Celeron processor will be a little... lacking. Might want to try to find a Pentium M or x64.

---

### Post by mips on 2007-06-02
> **happy-and-lost said:**
> If you're going to be compiling stuff, the Celeron processor will be a little... lacking. Might want to try to find a Pentium M or x64.

Yeah, Celeron really sucks big time!

---

### Post by igknighted on 2007-06-02
> **maniacmusician said:**
> water is usually problematic with the 950 chipsets. Perhaps it works with the new drivers?

I'm getting a santa-rosa based laptop that will come with the X3100 (965 chipset), and it's really leaps and bounds above the GMA 950. I think it's pretty cool how integrated video is becoming more and more powerful.

Ouch... have fun with that.  ATI isn't bad if you can use the open community drivers, but fglrx is worthless.  The only 3d support that matters on linux is composite and fglrx can't do it.  Even most games struggle with fglrx.

@ the OP: I would go with Intel.  For basic 3d rendering, either of those machines are overly sufficient, so go with the intel because (a) it has a slightly faster processor, (b) the intel drivers are open source which let the community keep them current long past when nvidia drops support, and (c) it uses open source drivers, which means no tainting of the kernel with proprietary modules, just a clean OSS system, with 3d, with no setup required.

---

### Post by maniacmusician on 2007-06-02
> **igknighted said:**
> Ouch... have fun with that.  ATI isn't bad if you can use the open community drivers, but fglrx is worthless.  The only 3d support that matters on linux is composite and fglrx can't do it.  Even most games struggle with fglrx.

@ the OP: I would go with Intel.  For basic 3d rendering, either of those machines are overly sufficient, so go with the intel because (a) it has a slightly faster processor, (b) the intel drivers are open source which let the community keep them current long past when nvidia drops support, and (c) it uses open source drivers, which means no tainting of the kernel with proprietary modules, just a clean OSS system, with 3d, with no setup required.
lol the X3100 is the new intel GPU.... it's essentially GMA965 as opposed to GMA950

and your advice is innacurate. the GMA950 chipset in that laptop is only strong enough for basic 3D drawing, and can't really do full-blown 3D design or rendering very effectively.

---

### Post by sloggerkhan on 2007-06-02
I know a number of engineering students who use solidworks on laptops with GMA950 at my college.

I won't say it works well for rendering. But apparently it's ok for modeling. As well as playing WOW.

That said, I'd never use it, because even then it can stil play games, it's usually on really low settings, and if you start building really complex models with lots of parts, it seems to start choking.

---

