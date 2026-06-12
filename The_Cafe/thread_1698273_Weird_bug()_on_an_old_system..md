---
title: "Weird bug(?) on an old system."
date: 2011-03-02
forum: The Cafe
---

### Post by jwbrase on 2011-03-02
I have a nearly 10-year-old box that I installed Vector Linux on a while ago, and I've been trying to figure out what exactly the motherboard is. I haven't found that out yet, but I did find something really weird: Whereas the front of the box rates the CPU at 766 MHz, /proc/cpuinfo reports a 1 GHz processor, as does dmesg.

Googling the bug (if it is a bug) just turns out a lot of people wondering why their processors are *slower* than reported on the front of the box, which can be explained by frequency scaling.

I'm not sure whether it's just that /proc/cpuinfo is returning bogus results, or whether there actually is a 1 GHz CPU in the box and the manufacturers sold themselves short. Any thoughts?

---

### Post by cascade9 on 2011-03-02
8-9 year old machine, probably a P3, with a sticker......and you believe the sticker? 

Check your BIOS, the CPU speed should be listed in there as well, and should be accurate.

---

### Post by jwbrase on 2011-03-02
> **cascade9 said:**
> 8-9 year old machine, probably a P3, with a sticker......and you believe the sticker?

Celeron, actually.

I can well believe that a manufacturer would *overrate* a CPU, but *underrating* it seems strange. 

> 
Check your BIOS, the CPU speed should be listed in there as well, and should be accurate.

I thought of that. It will involve dragging the monitor back over here, though (I'm currently operating it off of a serial console connected to my laptop, as I needed the monitor to run a program on another machine that required a specific 4:3 resolution, and the other machine only has a 16:9 flat panel).

---

### Post by LowSky on 2011-03-02
If you purchased it used, its possible that the owner replaced the CPU for a faster one.

Or in rare cases, a company would sell a model, and somewhere in the middle of manufacturing the company would run into a supply issue and need to a new model chip which was usually faster. Or even simplier explanation, the person whi installed the CPU inserted the wrong model or put the wrong label on the box.

Just check the BIOS it will tell you the CPU speed and the motherboard manufacturer in some way, sometimes just hte serial code.

Or use the command

```
sudo lshw
```

---

### Post by mips on 2011-03-02
> **jwbrase said:**
> ... and I've been trying to figure out what exactly the motherboard is.

Open the case and look at the MB for make & model.

---

### Post by jwbrase on 2011-03-02
> **LowSky said:**
> If you purchased it used, its possible that the owner replaced the CPU for a faster one.

Nope. Purchased brand new.

> 
Or in rare cases, a company would sell a model, and somewhere in the middle of manufacturing the company would run into a supply issue and need to a new model chip which was usually faster.

But then why not label the ones with the faster CPU's as being faster? That way you can ask more for them, or sell them faster for the same price.

> Or even simplier explanation, the person whi installed the CPU inserted the wrong model or put the wrong label on the box.

A definite possibility.

> 
Just check the BIOS it will tell you the CPU speed and the motherboard manufacturer in some way, sometimes just hte serial code.

Or use the command

```
sudo lshw
```

Actually, the distro I have on it doesn't include lshw... But it's not critical that I find out, just a curiosity...

---

