---
title: "A Window Manager with the smallest HDD and memory footprint"
date: 2009-07-21
forum: The Cafe
---

### Post by hellmet on 2009-07-21
I'm trying to create a customized version of Ubuntu for our thin clients. I wanted to know which Window Manager, from your experience takes up the least amount of HDD and/or memory space. All the functionality I'd need is the ability to run a browser and to connect to the network. A quick Google showed up a lot of options, but I'd really appreciate if you could help me choose one as it might take up significant time to research each WM.

And hey, how about an alternative to GDM/KDM login manager? I would want to eliminate gnome and its packages to the best extent possible to keep things light and fast.

Thanks a million!

---

### Post by Grenage on 2009-07-21
I used to use fluxbox, that has a small footprint and is quite quick to navigate.

---

### Post by kerry_s on 2009-07-21
the smallest would probably be tinywm, i've used it on kiosks, but it might not have enough functions for your needs.
[http://incise.org/tinywm.html](http://incise.org/tinywm.html)

i suggest looking at openbox.

---

### Post by hellmet on 2009-07-21
Any idea how much space Fluxbox or Openbox exactly use up?

---

### Post by kerry_s on 2009-07-21
fluxbox = 6787kb
openbox = 8008kb

according to synaptic

---

### Post by sertse on 2009-07-21
[http://www.gilesorr.com/wm/](http://www.gilesorr.com/wm/) is pretty much the definitive guide to wm resource usage I think. the old xwinman.org is also pretty useful.

Tinywm is the absolute smallest, but imo evilwm (floating) or dwm (tiling) are the smallest usable ones, though it takes some getting used to.

---

### Post by itreius on 2009-07-21
> **hellmet said:**
>  And hey, how about an alternative to GDM/KDM login manager?
[SLiM](http://slim.berlios.de/)

---

### Post by Sublime Porte on 2009-07-21
[Heliwm](http://www.cc.rim.or.jp/~hok/heliwm/) (Pronounced Helium) would have to be one of the smallest WM's around. The source to download is a whopping 26kb. You can compile it with the 'alpha particle' option to do away with window decorations to make it even lighter.

> I used to use fluxbox, that has a small footprint and is quite quick to navigate.

Perhaps compared to Gnome, KDE or other DE's, but not as far as plain WM's go.

---

### Post by hellmet on 2009-07-21
I think I might skip installing a login manager and do an auto login..

---

### Post by swoll1980 on 2009-07-21
JWM  was the lightest I could find. When I ran DSL, the system used only 12 MB RAM with the desktop running. Fluxbox pushed it to 18 MB RAM. Either way, you really can't go wrong.

---

### Post by RiceMonster on 2009-07-21
evilwm - this is about as minimal as it gets. Openbox and Fluxbox look like giants compared to it. The install size, I believe is around 20KB. The memory usage is also really small, but I forget how much exactly. Tinywm may be the only thign lighter, but I've never tried it. 

By the way, you can connect to the net and run a browser in any wm.

---

### Post by Grant A. on 2009-07-21
dwm is the lightest. It's only one 2,000 line header file.

---

### Post by chucky chuckaluck on 2009-07-21
dwm is the lightest, in my experience (i've tried everything, but i'm just an end user). dwm prides itself on having very little code and making it efficient. it's a tiling wm, so that may or may not be desirable.

---

### Post by RiceMonster on 2009-07-21
> **Grant A. said:**
> It's only one 2,000 line header file.

No it isn't. It's two files: dwm.c and config.h. A program can't be just a header file.

That said, dwm is a great choice as well. Very minimal, yet very usable.

---

### Post by leef on 2009-07-21
> **hellmet said:**
> I think I might skip installing a login manager and do an auto login..

have a look into at mingetty which is very small (no gui) and has autologin, once logged in you can add something like this to your users ~/.bashrc file;

```
if [ $(tty) == "/dev/tty1" ]; then
	startx
fi

```

---

### Post by .Maleficus. on 2009-07-21
Dwm.  It's tiny, still has tons of features and is easy to use (though it does take getting used to).

---

