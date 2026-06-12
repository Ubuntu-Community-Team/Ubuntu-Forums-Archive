---
title: "Can my HARDWARE run Spore"
date: 2008-12-19
forum: Wine
---

### Post by linuxguymarshall on 2008-12-19
I have the following 


[LIST]
[*]512 MB RAM
[*]NVIDIA 6200 video , 256 mb memory
[*]2.9 Celeron Processor (This is what I am worried about)
[/LIST]

Spore just got released on Steam free of all that nasty DRM so I would like to get it.

---

### Post by spawn. on 2008-12-19
You should be fine. When you play it, it doesn't look like it takes a whole lot of graphics power. It reminded me of N64 graphics. If you were a neighbor, I would've given you the galactic edition I wasted $92 dollars on.

---

### Post by mikedep333 on 2008-12-19
Requirements:
[http://www.spore.com/what/specs_spore](http://www.spore.com/what/specs_spore)

> # FOR WINDOWS XP
# * 2.0 GHz P4 processor or equivalent
# * 512 MB RAM
# * A 128 MB Video Card, with support for Pixel Shader 2.0
# * At least 4 GB of hard drive space, with at least 1 GB additional space for creations.

# FOR WINDOWS VISTA
# * 2.0 GHz P4 processor or equivalent
# * 768 MB RAM
# * A 128 MB Video Card, with support for Pixel Shader 2.0
# * At least 4 GB of hard drive space, with at least 1 GB additional space for creations. 

# Supported Video Cards
# NVIDIA GeForce series
# FX 5900, FX 5950
# 6200, 6500, 6600, 6800,
# 7200, 7300, 7600, 7800, 7900, 7950
# 8400, 8500, 8600, 8800
# 9600, 9800, GTX 260, GTX 280 



Assuming the best case scenario, that you are running this under Windows XP with very little bloated software running:

Memory:
Well, you meet the required memory. I would bet that it will still run slowly.
Graphics:
The extra 128MB of graphics memory being irrelevant, it'll probably work ok as long as you use the bare minimum settings.
CPU:
Your 2.9 ghz celeron is probably as good as a pentium-4. If it is one of the models with only 128KB of cache, probably not. If it is one of the models with 256KB of cache, probably so.
There is no exactly 2.9 ghz celeron. [There is the 128KB 2.8 ghz]("http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors#.22Northwood-128.22_.28130_nm.29") and [the 256KB 2.933 ghz]("http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors#.22Prescott-256.22_.2890_nm.29") (hover over those for links.)

As for running it under wine on linux, it might work if it uses opengl, as that would require less cpu, memory, and graphics power for wine to work with it. If it uses direct3d, I would say forget it. There are mixed reports on the web about whether or not it is opengl on the web.

---

### Post by compiledkernel on 2008-12-19
Points to what Mike has stated.

---

### Post by the8thstar on 2009-01-03
How about my specs (posted in the signature)? Has anyone tried playing with that?

---

### Post by Toffeeapple on 2009-01-03
> **linuxguymarshall said:**
> I have the following 


[LIST]
[*]512 MB RAM
[*]NVIDIA 6200 video , 256 mb memory
[*]2.9 Celeron Processor (This is what I am worried about)
[/LIST]

Spore just got released on Steam free of all that nasty DRM so I would like to get it.

My son plays it just fine on a celeron 2.4 based system, he a has a better GF card though, a GeForce 8500GT 256DDR2, runs nicely though, with eye candy. That's through wine on Arch.

That's not through Steam though.

---

