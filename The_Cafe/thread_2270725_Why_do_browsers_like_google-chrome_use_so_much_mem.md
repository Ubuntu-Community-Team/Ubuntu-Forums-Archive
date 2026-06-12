---
title: "Why do browsers like google-chrome use so much memory?"
date: 2015-03-25
forum: The Cafe
---

### Post by CantankRus on 2015-03-25
Why does google-chrome use upwards of 500mb memory when starting to a bank page with history and cookies erased.
Same with opera-developer.
Just seems a lot just to open.

Recently upgraded from 2G to 4G memory and just not used to seeing over 2G memory used.
Does google-chrome use more memory if it's there to be used?

From a cold boot, start off around 700g ... open google-chrome ...up to 1.3G ...open 3 or 4 tabs  and I'm up to 1.8G.

---

### Post by kerry_s on 2015-03-25
to me it seems to always try to use up to half the ram available, so for example i have 2gb it will use just up to a gig, i've got netflix running on 1 screen & on the other screen a few tabs i'm at 897.4mib(49%). i think it just uses what it can. like you i plan on upgrading to 4gb as well, it's already on it's way, hopefully i get it this week. :)
i've tested other browsers, there about the same, except for midori which used about 500+mb, but midori is very crashy. also chrome is the only 1 that can do netflix, i tried using it just for netflix & another browser for just web browsing but resource use is about the same so no point.

---

### Post by CantankRus on 2015-03-25
Yeah , my main browser is opera-developer which is built on chromium and I see the same memory usage.
The reason I upgraded to 4 gig was the modern browsers were using so much memory.
Just appear to be behaving like the tax man.... the more you got the more they want. :P8-[

---

### Post by DuckHook on 2015-03-25
So much of our lives revolve around the browser these days that it's like the central star in a solar system. When you think about it, one can view videos, get news, read books, listen to music, play games, create and edit docs/spreadsheets/slides, e-mail, message and do our taxes, all without leaving the browser. Crazy.

It's the single most important app on a desktop. It is also the most sophisticated and versatile. It must be capable of multiple scripting, large dedicated caching, juggling dozens of tabs and web pages, running hundreds of child processes, accepting dozens of plug-ins and extensions, morphing into a web app that looks like a completely different and unrelated animal, and yet make this incredible juggling act look seamless and effortless. It's quite the feat guys. And it's no wonder that it takes up an obscene amount of resources.

If you want a skimpy browser, try *links2*. It is totally Mickey Mouse next to the heavyweights, but it allows you to read static web pages well and it's as fast as greased lightning. Oh, and it uses probably 5% of the resources that the bloated monsters do.

---

### Post by robsoles on 2015-03-26
I think flash is the biggest culprit in terms of memory acquired by browsers, maybe it isn't any more but it certainly was the last time I did anything to try to work it out.

I love your sig DuckHook :)

---

### Post by DuckHook on 2015-03-26
> **robsoles said:**
> I love your sig DuckHook :);)

---

### Post by user1397 on 2015-03-26
> **DuckHook said:**
> So much of our lives revolve around the browser these days that it's like the central star in a solar system. When you think about it, one can view videos, get news, read books, listen to music, play games, create and edit docs/spreadsheets/slides, e-mail, message and do our taxes, all without leaving the browser. Crazy.

It's the single most important app on a desktop. It is also the most sophisticated and versatile. It must be capable of multiple scripting, large dedicated caching, juggling dozens of tabs and web pages, running hundreds of child processes, accepting dozens of plug-ins and extensions, morphing into a web app that looks like a completely different and unrelated animal, and yet make this incredible juggling act look seamless and effortless. It's quite the feat guys. And it's no wonder that it takes up an obscene amount of resources.

If you want a skimpy browser, try *links2*. It is totally Mickey Mouse next to the heavyweights, but it allows you to read static web pages well and it's as fast as greased lightning. Oh, and it uses probably 5% of the resources that the bloated monsters do.
Sing, you canary

---

### Post by DuckHook on 2015-03-26
> **ubuntuman001 said:**
> Sing, you canary:redface:

---

### Post by Matthew_Harrop on 2015-03-26
I have a question then: 

Why do we demand so much from our web browsers when we demand so little from others? 

And has this demand created the product? or has the product created the demand?

---

### Post by kerry_s on 2015-03-26
> **CantankRus said:**
> Why does google-chrome use upwards of 500mb memory when starting to a bank page with history and cookies erased.
Same with opera-developer.
Just seems a lot just to open.

Recently upgraded from 2G to 4G memory and just not used to seeing over 2G memory used.
Does google-chrome use more memory if it's there to be used?

From a cold boot, start off around 700g ... open google-chrome ...up to 1.3G ...open 3 or 4 tabs  and I'm up to 1.8G.

so i just got my 4gb ram & installed bringing me up from the 2gb(1.9gb usable) to 3.7gb usable, i only have netflix running & 1 tab open, it's already over a gig in gnome system monitor, so it's taking advantage of the extra ram, before the same would only be around 800mb used, maybe it'll change when the ram breaks in.

---

### Post by DuckHook on 2015-03-26
> **Matthew_Harrop said:**
> I have a question then: 

Why do we demand so much from our web browsers when we demand so little from others? 

And has this demand created the product? or has the product created the demand?Related questions, I think. My impression is that it is one of those iterative processes where an addition to the browser creates novel demands that then funnel back into even more innovation in the browser. Look at HTML5. It's doing away with flash, which is a wonderful development, but it has to keep evolving to remain relevant.

---

### Post by CantankRus on 2015-03-26
The reason I went to 4Gb was because I thought I needed it and it would make things more zippy.
When on 2Gb I don't remember ever using swap so I don't understand why the extra memory usage
when I have 4GB, unless chrome just allocates itself a % of free memory.

I boot up using about 550Gb.
With a few autostarts enabled and shutter running I'm at 810Gb... 
start google-chrome to a blank page and I'm at 1.4Gb.

I'm not complaining just curious, hence the Cafe thread.

---

### Post by kerry_s on 2015-03-26
i think it's fine, that's why we get more ram to use. it would suck if it just sat there half empty all the time. ;)
to bad my cpu sucks, i only got 1.3ghz x2 other wise i might consider some vbox.

---

### Post by kerry_s on 2015-03-26
forum hiccup.

---

### Post by CantankRus on 2015-03-26
Cheap motherboard and amd cpu where purchased with the ram....
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **inxi -b**
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1800.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (12.9% used)
Info:      Processes: 243 Uptime: 46 min Memory: 1613.6/3934.9MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by kerry_s on 2015-03-26
> **CantankRus said:**
> Cheap motherboard and amd cpu where purchased with the ram....
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **inxi -b**
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1800.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (12.9% used)
Info:      Processes: 243 Uptime: 46 min Memory: 1613.6/3934.9MB Client: Shell (bash) inxi: 1.9.17
```

that's a sweet rig to me, this laptop was dropped on the floor & shoved into a drawer for a few years, it was in a few pieces, hd was shot. a little glue, my ssd from my netbox & hey it lives.
the big thing for me, it was "FREE" lol.

---

### Post by CantankRus on 2015-03-26
At least you have an ssd. :o

---

### Post by kerry_s on 2015-03-26
> **CantankRus said:**
> At least you have an ssd. :o

lol, took advantage of those sales @ xmas time.

---

### Post by DuckHook on 2015-03-26
> **kerry_s said:**
> that's a sweet rig to me, this laptop was dropped on the floor & shoved into a drawer for a few years, it was in a few pieces, hd was shot. [COLOR=#ff0000]***a little glue***[/COLOR], my ssd from my netbox & hey it lives.
the big thing for me, it was "FREE" lol....not duct tape? :lolflag: You're kidding us right? Right??

---

### Post by CantankRus on 2015-03-26
> **kerry_s said:**
> lol, took advantage of those sales @ xmas time.

No one else is going to get you the present you want. :p

---

### Post by kerry_s on 2015-03-26
> **DuckHook said:**
> ...not duct tape? :lolflag: You're kidding us right? Right??

i'm actually out of duct tape :(
nope, not kidding i glued the pieces back together, there are a few small pieces missing but no big deal.

---

### Post by kerry_s on 2015-03-26
> **CantankRus said:**
> No one else is going to get you the present you want. :p

true that. you know when i had 2gigs i had issues watching 2 vids at a time, now it's all good, 4gig upgrade was worth it to me. plus i love having a extra screen.

---

