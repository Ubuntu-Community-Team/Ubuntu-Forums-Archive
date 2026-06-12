---
title: "So this is a little odd idea I had"
date: 2008-10-21
forum: The Cafe
---

### Post by Nostrafus on 2008-10-21
I've never worked with cluster computing, but I've given some thought into it recently... setting up a small cluster in my house for advanced graphics rendering.

Looking at Newegg prices, I could spend close to $2,000 on a single graphics rendering card.

For the same price I could buy 10 Xbox360's (the price dropped recently) and for a little bit more, install Linux on all 10, and set up a cluster network, with the combined power it would have an equivalent processing power of 96GHz, and be capable of rendering 5 billion tps...

Any thoughts on feasibility?

---

### Post by Scruffynerf on 2008-10-21
I've seen and heard of people using banks of playstations (2 and 3) for similar purposes (clusters - not necessarily graphics). No idea how to set them up through.

---

### Post by mips on 2008-10-21
If the software is available then I suspect it would work.

See the link below for something similair based on PS3:
[http://www.terrasoftsolutions.com/store/index.php?submit=software&submitimg](http://www.terrasoftsolutions.com/store/index.php?submit=software&submitimg)[hardware][solutions]=1
[http://www.terrasoftsolutions.com/support/hardware/](http://www.terrasoftsolutions.com/support/hardware/)

I'm sure you could achieve the same for cheaper though.

---

### Post by dirtylobster on 2008-10-21
I don't know much about graphics/rendering but I have a friend who uses 3DSMAX and Combustion and such Windows programs and was wondering if he could use Linux like this to do his rendering?

---

### Post by mips on 2008-10-21
> **dirtylobster said:**
> I don't know much about graphics/rendering but I have a friend who uses 3DSMAX and Combustion and such Windows programs and was wondering if he could use Linux like this to do his rendering?


[http://linux.omnipotent.net/article.php?article_id=11264](http://linux.omnipotent.net/article.php?article_id=11264)
[http://www.linuxartist.org/3d.html](http://www.linuxartist.org/3d.html)
[http://helmer.sfe.se/](http://helmer.sfe.se/)  Check this out, really cool!!!

Blender would probably be his bet bet.

---

### Post by mips on 2008-10-21
[http://helmer.sfe.se/](http://helmer.sfe.se/)
[http://helmer2.sfe.se/](http://helmer2.sfe.se/) Concept only.

This seems like a relatively cheap & powerfull solution all in one box.

I love DIY projects like this.

---

### Post by dirtylobster on 2008-10-21
> **mips said:**
> Blender would probably be his bet bet.

> Blender is the free open source 3D content creation suite

I'm 99% sure he'd want to continue to use 3DSMAX and Combustion, just use a Linux machine for the rendering.

---

### Post by Nostrafus on 2008-10-21
> **dirtylobster said:**
> I'm 99% sure he'd want to continue to use 3DSMAX and Combustion, just use a Linux machine for the rendering.

I'm doubt the transition would be difficult, there is a bit of a difference, like the default 1 viewport vs. 4 viewports, but it still has a lot of the functionality that 3dsmax has.  The only points people say they're not happy with is no MP3/OGG support for video... which isn't really a problem if you aren't rendering a video and are just doing stills.

Or you could use an actual video editing program like most people do for post-production and insert an audio track there.

Also if I read the tech data right, blender does support .max files.

Unfortunately for myself... it seems the current capacity for it to be done on a 360 is possible, but would not be stable.

The Distro that seems to be preferred for cluster networking seems to be KRUD, and as of now the distro used for the 360 is a homebrew not made for cluster networking so it wouldn't be as simple as installing on each, then just installing MPI software.

May have to look into the PS2 or PS3 (whichever gets more TPS/GHz per $) since they seem to have more support... I was hoping for the 360 since they're cheaper than PS3's.

...

After doing the math... here's what I have come up with.

Were it feasible to do this... for $2000 here's what each would get it in basic spec's...

Xbox360
# 10 Consoles
RAM: 5GB
CPU: 96GHz on 30 Cores
TPS: 5 Billion

PS2
# 25 Consoles
RAM: 800MB
CPU: 7.5GHz on 25 Cores (Though this may have a bit of a different effect as they are running a RISC chip)
TPS: 3.7 Billion

PS3
# 4 Consoles
RAM: 1GB
CPU: 12,8GHz (89.6GHz) on 4 (28.) Cores
TPS: ? (Was unable to find a measurement in Triangles Per Second)

I am also unsure of the PS3's spec's... it says it clocks at 3.2GHz, but... further into the article is states "7 x @ 3.2GHz" which if it means 7 cores, that totals 28 Cores with 4 systems, with a theoretical processing power total of 89.6GHz.

---

### Post by koenn on 2008-10-21
> **Nostrafus said:**
> 
Any thoughts on feasibility?

It has been done before, so feasible=yes.
google for xbox Linux cluster
IIRC, you may need to do some hardware modifications, but maybe that info is outdated.

---

### Post by Lord Xeb on 2008-10-21
Good god this stuff is confusing but so awesome at the same time :D >_> I wonder how fast a cluster could run crysis if you put some good GPUs in them :D

---

### Post by Nostrafus on 2008-10-22
Update on specs, same price @ $2,000

Xbox Original
#: 32 Consoles
RAM: 2GB
CPU: 23GHz
TPS: 928 Million

Strange how a PS2 with less RAM, and a slower CPU with a different architecture can get almost as high a Triangles per second rate that a Xbox360, made years later can.

I'm going to have to research the PS3 and find out if it's running a single core or 7 cores, if it's running 7 cores, it may be my choice with less power draw (And less space used)

Also, adding (Just for thoroughness) a PC cluster

The core system is an [MSI Wind Barebones]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032")
The RAM is a [Kingston 2 Gigabyte Chip]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820134187")

MSI Wind
#: 10 PC's
RAM: 20GB
CPU: 16GHz on 16 Cores (Intel Atom RISC Architecture)
TPS: Estimating 5 Billion, Actual is probably lower (Based on Rate of 160 GPixels Per Second @ TPS = 32 Pixel Triangle)

---

### Post by mips on 2008-10-22
> **Lord Xeb said:**
>  I wonder how fast a cluster could run crysis if you put some good GPUs in them :D

Most likely worse than a single PC with SLI enabled dual gfx cards.

---

### Post by mips on 2008-10-22
Here is another option, [http://fastra.ua.ac.be/en/index.html](http://fastra.ua.ac.be/en/index.html)

Based on 4x nVidia 9800GX2 gpus

---

### Post by Nostrafus on 2008-10-22
> **mips said:**
> Here is another option, [http://fastra.ua.ac.be/en/index.html](http://fastra.ua.ac.be/en/index.html)

Based on 4x nVidia 9800GX2 gpus

Well I do have a very nice desktop, but when it comes to video, rendering isn't as good as I'd like it to be, especially when I bump it to HD rendering, the problem isn't my graphics cards, as I am running 2x9800's, my processing power is my bottleneck.  Even though I am running a 3.2GHz dual core, it's still not enough power to render HD video, or video running with more than 3 or 4 full screen effects simultaneously.

---

