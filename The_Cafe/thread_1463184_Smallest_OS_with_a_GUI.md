---
title: "Smallest OS with a GUI?"
date: 2010-04-26
forum: The Cafe
---

### Post by JamezQ on 2010-04-26
I don't need it, I just have always wondered how small exactly can a OS be with a gui. 

It doesn't have to do a lot. I am not looking for any special features(Although if it can do something cool, that would be lovely). I just want to know how small can you get a gui.

It doesn't have to be linux based. 

The smallest I have found so far is 1.4 MB

[http://etricks.in/2010/02/kolibri-os-smallest-os-with-gui.html](http://etricks.in/2010/02/kolibri-os-smallest-os-with-gui.html)

Anyone know of one below 1 MB?

---

### Post by MichealH on 2010-04-26
Nope not that I know of...

Also BTW, Cool!

---

### Post by Random_Dude on 2010-04-26
I has going to say DSL, but damn...

---

### Post by ronnielsen1 on 2010-04-26
> The smallest I have found so far is 1.4 MB

Oh Wow. Makes Tiny Core bloatware

:lolflag:

---

### Post by Dayofswords on 2010-04-26
i dont think its gets smaller

---

### Post by MaxIBoy on 2010-04-26
A-Linux ([This one]("http://asm.sourceforge.net/asmutils.html"), not [this one]("http://alinux.tv/")) is 787.6 Kib. It uses asmutils (first link.) Asmutils is a set of standard UNIX utilities, such as ls, cat, mv, etc, which are totally written in x86 assembly code.

Doesn't have a GUI per-se, but it can use a VESA framebuffer to display graphics.

---

### Post by undecim on 2010-04-26
There's also MenuetOS
[http://www.menuetos.net/](http://www.menuetos.net/)

EDIT: Just realized Kolibri is based on Menuet

---

### Post by WinterRain on 2010-04-26
I thought tiny core was small, but geez. Tried it out in vbox and is pretty cool. Boots in literally 1 second.

---

### Post by JamezQ on 2010-04-26
> **MaxIBoy said:**
> A-Linux ([This one]("http://asm.sourceforge.net/asmutils.html"), not [this one]("http://alinux.tv/")) is 787.6 Kib. It uses asmutils (first link.) Asmutils is a set of standard UNIX utilities, such as ls, cat, mv, etc, which are totally written in x86 assembly code.

Doesn't have a GUI per-se, but it can use a VESA framebuffer to display graphics.


In there anyway to make framebuffer repeat over and over to make a gui like thing?

---

### Post by phrostbyte on 2010-04-26
QNX Research used to distribute a 1.4 MB copy of their OS on their website for personal use. It came with a full HTML3 compliant web browser (with JS support!), GUI, some kind of network support, and some GUI apps. Unfortunately I don't think you can [legally] acquire it anymore.

---

### Post by angry_johnnie on 2010-04-26
I'd say [KolibriOS]("http://www.kolibrios.org/").  It's only about 3 Mb including GUI.

---

### Post by JamezQ on 2010-04-26
> **angry_johnnie said:**
> I'd say [KolibriOS]("http://www.kolibrios.org/").  It's only about 3 Mb including GUI.

Thats the one I already found ^ ^

---

### Post by JamezQ on 2010-05-03
Ok... [http://www.kolibrios.org/](http://www.kolibrios.org/) is 1.4 mb, but is that REALLY the smallest os with a gui.

Is it smaller then the first mac?

[http://lowendmac.com/history/1984dk.shtml](http://lowendmac.com/history/1984dk.shtml)
The damn thing tells me the memory it took to run(128k) however I can't find how big the actual OS is.

[http://www.pcanswer.com/2009/01/21/larry-magids-1984-la-times-review-of-original-mac/](http://www.pcanswer.com/2009/01/21/larry-magids-1984-la-times-review-of-original-mac/)
[http://inventors.about.com/library/weekly/aa051599.htm](http://inventors.about.com/library/weekly/aa051599.htm)
Here we go, I'm not sure if says the size of the OS, but considering:
> The system is driven by a 32 bit Motorola 68000 central processing unit. It comes with 128K of Random Access Memory (RAM), 64K of Read Only Memory (ROM) and one 400K disk drive.

I mean, all that adds up to 592k so the OS in the first mac which did have a GUI **had** to be smaller then 592k right? And that is much smaller then the 1400k OS, if I am correct.
..........................

And is 1.4 MB larger then the OS in the Xerox Alto?

[http://altogether.brouhaha.com/](http://altogether.brouhaha.com/)
[http://altogether.brouhaha.com/download/](http://altogether.brouhaha.com/download/)

The downloads for this, that is supposed to simulate the Alto are 32 and 49k! However I may just not know what I am talking about, perhaps simulation can be smaller then the OS and the source code may be bigger then the compiled version.

[http://toastytech.com/guis/alto.html](http://toastytech.com/guis/alto.html)
[http://www.velocityguide.com/computer-history/xerox-alto.html](http://www.velocityguide.com/computer-history/xerox-alto.html)

This says the Alto has a 2.5 mb remove-able storage.
.................................
[http://catb.org/~esr/writings/taouu/html/graphics/lisamw2.png](http://catb.org/~esr/writings/taouu/html/graphics/lisamw2.png)


Here is an interesting picture, I'm not sure exactly what it means but it gives a lot of info on size. In the System Folder it shows 165k, does this mean the system is smaller then 165k? Or is the system a size of 1932k, also shown.

[http://catb.org/~esr/writings/taouu/html/graphics/amiga.png](http://catb.org/~esr/writings/taouu/html/graphics/amiga.png)

This says the OS is 93% full, with 39M free and 543M in use. I'm guessing M refers to KB because I feel it does not refer to 543KB of ram, or 543MB of storage. But correct me if I'm wrong, but does this mean the amiga 1000 OS, with a gui has to at least be smaller then 543K?
..........................
Sorry for the long rant, but I just want to know if 1.4mb is really the smallest. I mean, none of this has any real use, computers are holding terrabytes now, but I am just interested in finding an answer I am comfortable with.

---

### Post by phrostbyte on 2010-05-03
M is Megabytes in this context.

Apple Lisa, or Xerox Alto might be the smallest. It didn't have such things we take for granted today like pre-emptive multitasking however.

Regardless, even 1.4 MB is pretty damn impressive, even in the context of the 80s. Making software that small and actually efficient is a lost art. We tend to prefer flexibility and ease of programming over raw performance these days.

---

### Post by JamezQ on 2010-05-03
> **phrostbyte said:**
> M is Megabytes in this context.

Apple Lisa, or Xerox Alto might be the smallest. It didn't have such things we take for granted today like pre-emptive multitasking however.

Regardless, even 1.4 MB is pretty damn impressive, even in the context of the 80s. Making software that small and actually efficient is a lost art. We tend to prefer flexibility and ease of programming over raw performance these days.

For good reason, computers can handle it now. However I am not asking for a OS with supa-cool features, I am asking for the smallest GUI, thats all. Honestly for if I want a small OS with a GUI that is awesome and full of features, I use puppy linux, nothing beats that. But yea, I guess you can put it down to, how much code does it take to make it so you can move a mouse cursor on a screen.

Are you sure M refers to MB? 543MB back then is a darn lot.

[http://oldcomputers.net/amiga1000.html](http://oldcomputers.net/amiga1000.html)

I'm not saying your wrong, you probably know something I don't, but wikipedia says:

> Removable Storage:
3.5" DD Floppy drive, capacity 880 KB

Maybe they could use multiple ones at the same time, but that is still over 500 Floppys...

---

### Post by mmix on 2010-05-03
Contiki with GUI(optional)
[http://en.wikipedia.org/wiki/Contiki](http://en.wikipedia.org/wiki/Contiki)

colorforth
[http://en.wikipedia.org/wiki/ColorForth](http://en.wikipedia.org/wiki/ColorForth)

parallax
[http://en.wikipedia.org/wiki/Parallax_Propeller](http://en.wikipedia.org/wiki/Parallax_Propeller)

uclinux with fbui, octaos, solar os, movitz(not yet bootable), 
retroforth, ...

maybe port framebuffer to homebrewcpu ;-)

---

### Post by JamezQ on 2010-05-03
> **mmix said:**
> Contiki with GUI(optional)
[http://en.wikipedia.org/wiki/Contiki](http://en.wikipedia.org/wiki/Contiki)

colorforth
[http://en.wikipedia.org/wiki/ColorForth](http://en.wikipedia.org/wiki/ColorForth)

parallax
[http://en.wikipedia.org/wiki/Parallax_Propeller](http://en.wikipedia.org/wiki/Parallax_Propeller)

uclinux with fbui, octaos, solar os, movitz(not yet bootable), 
retroforth, ...

maybe port framebuffer to homebrewcpu ;-)

Thanks for these :D Does the os that ColorForth comes with have a GUI?

---

### Post by cammin on 2010-05-03
Oops, guess I was too slow.

---

### Post by JamezQ on 2010-05-03
> **cammin said:**
> Oops, guess I was too slow.

???

---

### Post by sanderd17 on 2010-05-03
I knew about SliTaz, that's about 30 MB but I see here that's definatly not the smallest :P.  I didn't now somethin under 10 MB would be possible.

---

### Post by JamezQ on 2010-05-03
I think we have a winner.

```
http://www.rayslogic.com/propeller/Programming/RaysStuff/Main_small.JPG
```

[http://www.youtube.com/watch?v=U57KSBturww](http://www.youtube.com/watch?v=U57KSBturww)

.............................
Now those look like the same program, and I could be wrong, but the code in that program comes down to 288.7k! Again, maybe there is more coded stored somewhere, but if not, this is pretty cool.(Even though it doesn't really "do" anything I can see but point and click... but thats all I want :P)

There is also another program of his that is a demo, and that is only 191.5k. It looks like it only has one box with a few buttons and options that you can change, pretty cool.

---

### Post by K.Mandla on 2010-05-03
There are 8-bit GUI systems that have been around for decades.

[http://en.wikipedia.org/wiki/GEOS_%288-bit_operating_system%29](http://en.wikipedia.org/wiki/GEOS_%288-bit_operating_system%29)

KolibriOS is probably one of the best that will run on "modern" systems. DexOS is similar.

[http://kmandla.wordpress.com/2010/04/07/another-one-disk-wonder-dexos/](http://kmandla.wordpress.com/2010/04/07/another-one-disk-wonder-dexos/)

---

### Post by JamezQ on 2010-05-03
> **K.Mandla said:**
> There are 8-bit GUI systems that have been around for decades.

[http://en.wikipedia.org/wiki/GEOS_%288-bit_operating_system%29](http://en.wikipedia.org/wiki/GEOS_%288-bit_operating_system%29)

KolibriOS is probably one of the best that will run on "modern" systems. DexOS is similar.

[http://kmandla.wordpress.com/2010/04/07/another-one-disk-wonder-dexos/](http://kmandla.wordpress.com/2010/04/07/another-one-disk-wonder-dexos/)


Thanks for the links, so, was GEOS smaller in size then the Alto?

And I might ask later for the for the most portable os, that would be fun, but for now I'm still just looking for the smallest GUI. I have had quite a few fun links to look at so far, it has been fun. I would prefer if I could run the OS in some VM, but it is not necessary.

---

### Post by CLOUD666 on 2010-05-03
The smallest OS with GUI is DexOS, its less than 100k including GUI, its got a desktop GUI and a game sys like GUI, and even with its full TCP/IP stack its less than 120k.
It runs on x86 32bit pmode (built in menuetOS function wrap, so it can run any app for that OS).

But if we are talking small the same maker coded a 32bit pmode OS with high res 640x480 32bpp basic GUI, with built in cdplayer that fits on the boot sector of a floppy, yes thats right less than 512bytes in size ;) .
see here
 [http://www.dex4u.com/cdpod.htm](http://www.dex4u.com/cdpod.htm)
or here:
[http://dex.7.forumer.com/viewtopic.php?t=573&start=0](http://dex.7.forumer.com/viewtopic.php?t=573&start=0)

---

### Post by blueturtl on 2010-05-03
If Microsoft hired an army of guys like the ones behind DexOS and Kolibri... I wonder how small Windows 7 could have been...

Watching these guys makes me feel like the insignificant programmer that I am. :D

---

### Post by del_diablo on 2010-05-03
> I wonder how small Windows 7 could have been...I wonder how small Windows 7 could have been...I wonder how small Windows 7 could have been...

Since 5-6 gigabyte is dedicated to the worst enginnering decision i have seen(winsxs), i doubt it.

---

