---
title: "Counter-Strike: Source + WINE"
date: 2010-01-20
forum: Wine
---

### Post by zandertk on 2010-01-20
Hi!
I'm new to the community so first of all I'd like to say hello to you all :)

Now my problem is that I want to play CS:S on Ubuntu 9.10 using Wine, but I'm having some problems. When I played on Windows I was getting about 300 fps with about 15 people in a server.
Now, in a empty server, I'm getting no more than 150. But that's not the problem, because a human can't even notice the difference. The problem is that even though I have 150 fps, it's very VERY laggy. It's not a server's fault because in a local server I'm still laggy.
So I'd like to know how to solve this. I've been reading a lot about cs:s + wine, I've tried changing dxlevel to 90, 80 or even 70, no change.

These are my system specs:
- AMD Phenom II X4 965 3.4Ghz
- ASUS M4N78
- nVidia GeForce 9600GT (driver v173)
- 4GB RAM DDR2 800Mhz

GLXGears info:
31516 frames in 5.0 seconds
29224 frames in 5.0 seconds
32056 frames in 5.0 seconds
34131 frames in 5.0 seconds
26017 frames in 5.0 seconds

At first I was getting 50k frames, then I changed the driver from 173 to 185, and started getting 16k, so I switched back to 173 and I'm now getting ~30k.

What can I do?

---

### Post by gradinaruvasile on 2010-01-20
Download the latest driver. I dunno why you installed the old driver for that card. For cards from 6 series the latest batch of drivers are recommended (Currently 195.30 is the latest beta, i use it on 3 comps, it rocks).

Glxgears its NOT a testing tool. I saw weak cards outperform stronger ones in it and choke in games. Also saw  driver versions that were lower in glxgears score but far better in actual gaming.
So dont use it as a comparison tool.

I played CS:S on a IGP 8200 card and never had lag except graphical one (15-20 FPS because of the hardware).

---

### Post by Simpsoni28 on 2010-01-20
I found with Wine, that the latest nvidia drivers don't work.

Once I removed them and installed the proprietary Ubuntu drivers "SYSTEM --> ADMINISTRATION --> HARDWARE DRIVERS" then everything ran fine.

---

### Post by beastrace91 on 2010-01-20
> **Simpsoni28 said:**
> I found with Wine, that the latest nvidia drivers don't work.

**for me** should be at the end of the above statement - for many. Myself included the latest and greatest drivers work just fine - I'd recommend upgrading to at least the 190.53 nVidia drivers.

~Jeff

---

### Post by zandertk on 2010-01-24
I installed the latest drivers (190.53) but it's still laggy.
I ran the counter-strike source video test and got ~30fps, but when ingame i get about 150fps (although they change very fast, i mean, first 50fps, then 200, then 150, then 30,...).
I'm taking a tournament next monday but I don't want to reinstall windows...

---

### Post by zandertk on 2010-01-24
Updated wine to 1.1.31, got 57fps on the video test, still too laggy ingame.

---

### Post by beastrace91 on 2010-01-24
Right click on CSS from your Steam games menu and select properties and then launch options. Add "-dxlevel 81" to the launch options - then try playing.

Regards,
~Jeff

---

### Post by zandertk on 2010-01-24
> **beastrace91 said:**
> Right click on CSS from your Steam games menu and select properties and then launch options. Add "-dxlevel 81" to the launch options - then try playing.

Regards,
~Jeff

Already did. Still laggy :(

---

### Post by beastrace91 on 2010-01-24
Then my last piece of advice would be to try looking for an FPS optimization CFG for CSS. Beyond that you simply need more powerful hardware to run 3D applications on Linux under Wine. Its a pitty but the truth none the less.

For example even though I have a 260 GTX I still dual boot to play Bioshock because it gets around 15fps running under Wine where is it is well over 100 on Windows. There is not always this much reduction, but in some cases it is the sad truth. For some more information on the subject check out the [benchmarks](http://jeffhoogland.blogspot.com/2010/01/wine-cxgames-and-windows-7-performance.html) I ran comparing Win7 and Wine.

Regards,
~Jeff

---

