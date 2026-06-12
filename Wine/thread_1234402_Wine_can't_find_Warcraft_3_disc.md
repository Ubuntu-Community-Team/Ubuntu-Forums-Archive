---
title: "Wine can't find Warcraft 3 disc"
date: 2009-08-07
forum: Wine
---

### Post by rossmc92 on 2009-08-07
So I'm trying to run Warcraft 3 through wine. It installed fine and Wine HQ reports no problems yet it can't seem to find the disc. Care to enlighten me?

---

### Post by BoltBlue on 2009-08-07
> **rossmc92 said:**
> So I'm trying to run Warcraft 3 through wine. It installed fine and Wine HQ reports no problems yet it can't seem to find the disc. Care to enlighten me?

You need to install this patch;

[http://ftp.blizzard.com/pub/war3/patches/PC/War3ROC_124a_English.exe](http://ftp.blizzard.com/pub/war3/patches/PC/War3ROC_124a_English.exe)

That will solve your problem.

---

### Post by rossmc92 on 2009-08-08
Thanks a lot, now I seem to have yet another problem. After disallowing the window manager to decorate and control windows I managed to get it full screen. Now it has a terrible frame rate and generally runs awful. anything I can do to fix this? It's supposed to run flawlessly. Here's the specs;

Jaunty (9.04)
memory: 1.5gb
Processor: Inter pentium M processor 1.73ghz.

---

### Post by BoltBlue on 2009-08-08
What graphics card do you have?

---

### Post by rossmc92 on 2009-08-08
> **BoltBlue said:**
> What graphics card do you have?

Well I got Intel GMA 900 (integrated) 128mb ram from [http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,39190556,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,39190556,00.htm)

If there's a more accurate way to check then I don't know it. I'm aware thats it's an old intergrated intel one but surely it can run a game this old?

---

### Post by NightMKoder on 2009-08-08
Won't run too well on your graphics card... Your best bet right now is either to try karmic (note its alpha) or wait for karmic to get released.

---

### Post by BoltBlue on 2009-08-08
> **rossmc92 said:**
> Well I got Intel GMA 900 (integrated) 128mb ram from [http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,39190556,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,39190556,00.htm)

If there's a more accurate way to check then I don't know it. I'm aware thats it's an old intergrated intel one but surely it can run a game this old?

Did you pay £999 for that? If so you have been totally ripped off.

---

### Post by BoltBlue on 2009-08-08
Actually nevermind, I see how that site operates now.....:rolleyes:

---

### Post by Mike_IronFist on 2009-08-08
> **NightMKoder said:**
> Won't run too well on your graphics card... Your best bet right now is either to try karmic (note its alpha) or wait for karmic to get released.

That doesn't quite sound right, the game only needs 256 mb of ram and a 600 MHZ processor. He's got double the minimum processor speed and about 5 times the RAM.

Rather, have you ever run Warcraft 3 on the same computer using Windows? How does it run then?

---

### Post by rossmc92 on 2009-08-08
> **Mike_IronFist said:**
> That doesn't quite sound right, the game only needs 256 mb of ram and a 600 MHZ processor. He's got double the minimum processor speed and about 5 times the RAM.

Rather, have you ever run Warcraft 3 on the same computer using Windows? How does it run then?

Well I'd be running Windows if the initial setup didn't decide to restart  every time I booted.  I honestly thought Warcraft would run fine on this.

---

### Post by no1wantdthisname on 2009-08-08
Run in opengl.

```

wine war3.exe -opengl

```

I'd recommend using a patched wine as well.
It'll fix the focus loss bug, inability to host, and missing chat issues.

---

### Post by hikaricore on 2009-08-08
The problem isn't the processor or the ram, it's the "video" hardware.
If i read correct the OP has Intel for video which can be hit or miss depending on the model of the integrated chipset.

---

