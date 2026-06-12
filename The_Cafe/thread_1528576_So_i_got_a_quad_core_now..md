---
title: "So i got a quad core now."
date: 2010-07-10
forum: The Cafe
---

### Post by themarker0 on 2010-07-10
What are some programs that use more then one core? Is there a list somewhere?

---

### Post by Bachstelze on 2010-07-10
> **themarker0 said:**
> What are some programs that use more then one core? Is there a list somewhere?

Making a list would be impossible. Just watch your per-core CPU usage while a program is runing and find out.

---

### Post by lisati on 2010-07-10
When I had Jaunty on my laptop (a dual core) remastersys was able to use both cores.

---

### Post by jpeddicord on 2010-07-10
Try compiling things. 4 at a time if they're using automake on a single thread, or watch the speed of one cmake or waf build. :D

---

### Post by Bachstelze on 2010-07-10
> **jpeddicord said:**
> 4 at a time if they're using automake on a single thread

[font=monospace]make -jN[/font] much?

---

### Post by stmiller on 2010-07-11
[http://handbrake.fr/](http://handbrake.fr/)

Handbrake uses all the cores you can through at it. 2, 4, 8... :)

Handbrake will max out all of your cores.

---

Gimp is multicore aware as well:

[http://i.imgur.com/cxDur.png](http://i.imgur.com/cxDur.png)

---

There's also a cool program fraqtive that maxes out all cores you have available when zooming around:
```

sudo apt-get install fraqtive

```

---

### Post by jpeddicord on 2010-07-11
> **Bachstelze said:**
> [font=monospace]make -jN[/font] much?

#-o of course.

---

### Post by 3rdalbum on 2010-07-11
My program Blacklight (which encodes video for Sony Walkmans) does symetrical-multiprocessing in an interesting way.

Walkmans only understand two video formats: MPEG-4 and H.264. For reasons of convenience (to myself and to the user) I chose my program to work only with MPEG-4, but the MPEG-4 encoder does not scale well across multiple cores. So if the user wants to encode multiple files, then Blacklight will send a video file to each core. Got a quad-core? You can encode four videos simultaneously.

Now I've since noticed that [Sound Converter]("apt:soundconverter") does multiprocessing in the same way. The LAME MP3 encoder doesn't do multithreading, so Sound Converter sends a file to each core for processing.

So, if your programs don't take up more than one core each, then you'll just have to run four such programs simultaneously.

---

### Post by undecim on 2010-07-11
Start running Folding@Home

[https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu/HowTo](https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu/HowTo)

---

### Post by NMFTM on 2010-07-11
> **themarker0 said:**
> What are some programs that use more then one  core? Is there a list somewhere?
[Supreme  Commander]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4051") was the first computer game to utilize more than one core. I still prefer the original [Total Annihilation]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=155") though.  Besides that, computer game packaging is pretty standardized at this point.  It should say on the back of the packaging if it utilizes multi-cored  CPU's.

Also, Windows 7 seems to utilize more of my Phenom II X4 965's processing power than Ubuntu 10.04. It idles at about 2-6% while Ubuntu idles at about 0-1%. Oh wait, that's a bad thing :p.

What quad core CPU do you have?

---

### Post by BigSilly on 2010-07-11
/Is sadly stuck with dual core for the foreseeable future

/Is skint

/Cries

Enjoy your quad! :)

---

### Post by themarker0 on 2010-07-11
> **NMFTM said:**
> [Supreme  Commander]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4051") was the first computer game to utilize more than one core. I still prefer the original [Total Annihilation]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=155") though.  Besides that, computer game packaging is pretty standardized at this point.  It should say on the back of the packaging if it utilizes multi-cored  CPU's.

Also, Windows 7 seems to utilize more of my Phenom II X4 965's processing power than Ubuntu 10.04. It idles at about 2-6% while Ubuntu idles at about 0-1%. Oh wait, that's a bad thing :p.

What quad core CPU do you have?

I think this is it, without finding the box.
[http://ark.intel.com/Product.aspx?id=35365](http://ark.intel.com/Product.aspx?id=35365)

---

