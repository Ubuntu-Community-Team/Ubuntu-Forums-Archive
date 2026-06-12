---
title: "I'm finally trying a different WM"
date: 2008-05-11
forum: The Cafe
---

### Post by cardinals_fan on 2008-05-11
I want a little help deciding on a WM.  Openbox is great, but I need something new to play with.  Here are my needs:

* It should be in Pkgsrc.  Check at [http://pkgsrc.se/wm](http://pkgsrc.se/wm)
* Keyboard shortcuts must be configurable.  This is not negotiable.
* I use most of my apps full screen.  Maybe 70% of my time is spent in a fullscreen web browser or terminal.  Another 20% is in Abiword, Gnumeric, Evince or PCManFM, all fullscreen.  That leaves only 10% in non-fullscreen windows.
* Alt-tab window switching is nice.
* Virtual desktops (or perhaps the Ratpoison workspace system) are a must.  This is required.
* Conky support should be good - it's my lifeline :)
* Easy to understand config files
* Lightweight (of course ;) )

---

### Post by brunovecchi on 2008-05-11
Have you tried **[awesome]("http://awesome.naquadah.org/")**? It's what I'm using right now, I find it better than wmii. It fulfills all of the requirements you just posted!

And... (I couldn't resist, sorry)

it's awesome.

---

### Post by chucky chuckaluck on 2008-05-11
i would also say awesome. i think it meets most of your requirements, though i'm not sure about conky (i don't use it).

---

### Post by urukrama on 2008-05-11
Try Pekwm. It is an awesome window manager.

---

### Post by chris4585 on 2008-05-11
> **urukrama said:**
> Try Pekwm. It is an awesome window manager.

I'm a openbox fan, and I don't plan on leaving it any time soon.  I've always wanted to try awesome, or wmii, or pekwm, all of those I want to try, but right now I have my system as I like it, please inform us of your experiences :D

---

### Post by cardinals_fan on 2008-05-11
> **urukrama said:**
> Try Pekwm. It is an awesome window manager.
Don't get me wrong, Pekwm is great.  But I prefer Openbox.  I mostly want to try a very lightweight, perhaps tiling, WM.  Awesome looks good for the tiling front.  Has anybody tried Ratpoison?

---

### Post by zmjjmz on 2008-05-11
Try vtwm
It prolly isn't in pkgsrc, bit it may meet all your other requirements. (expect lotsa configgin, and it won't be pretty)
Edit: It's in pkgsrc

---

### Post by urukrama on 2008-05-11
> **chris4585 said:**
> please inform us of your experiences :D

I've been using Pekwm almost constantly for the last few months. It isn't as polished as Openbox, but I really like it. It has a lot of the great features of Openbox, some of the good things of Fluxbox (tabbing!), and some nice additional ones (screen edges!).

---

### Post by chucky chuckaluck on 2008-05-11
> **cardinals_fan said:**
> Don't get me wrong, Pekwm is great.  But I prefer Openbox.  I mostly want to try a very lightweight, perhaps tiling, WM.  Awesome looks good for the tiling front.  Has anybody tried Ratpoison?

i've found ratpoison a bit awkward when compared to wmii, dwm, awesome and xmonad.

---

### Post by cardinals_fan on 2008-05-11
I've pkg_added awesome.  Would any of you awesome users mind starting me out with an awesomerc?

---

### Post by chris4585 on 2008-05-11
> **urukrama said:**
> I've been using Pekwm almost constantly for the last few months. It isn't as polished as Openbox, but I really like it. It has a lot of the great features of Openbox, some of the good things of Fluxbox (tabbing!), and some nice additional ones (screen edges!).

What do you mean tabbing, and screen edges?

---

### Post by msrinath80 on 2008-05-11
I use Windowmaker almost exclusively. It has been my favorite since 1998.

---

### Post by cardinals_fan on 2008-05-11
> **chris4585 said:**
> What do you mean tabbing, and screen edges?
Tabbed windows are great.  Middle-click a window and drag it onto another one, and the two will merge into a tabbed window.  Click between the tabs on the top of the window border.  Screen edges let you launch apps from the edges of the screen - think Compiz.

---

### Post by chris4585 on 2008-05-11
> **cardinals_fan said:**
> Tabbed windows are great.  Middle-click a window and drag it onto another one, and the two will merge into a tabbed window.  Click between the tabs on the top of the window border.  Screen edges let you launch apps from the edges of the screen - think Compiz.

Thanks for the info, but that's what virtual desktops are used for imo, I see virtual desktops as grouping places.

---

### Post by brunovecchi on 2008-05-11
> **cardinals_fan said:**
> I've pkg_added awesome.  Would any of you awesome users mind starting me out with an awesomerc?

Here's a great, complete guide:
[Setting up AwesomeWM]("http://ubuntuforums.org/showthread.php?t=678902&highlight=setting+awesomeWm")

May I suggest you throw in xcompmgr for transparency support and nice shadows? I followed [this guide]("http://www.jabberoo.net/index.php/2008/03/16/my-perfect-arch-x-and-awesome/") for that (bottom line of the article).

Hope it helps.

---

### Post by kerry_s on 2008-05-11
> **cardinals_fan said:**
> I want a little help deciding on a WM.  Openbox is great, but I need something new to play with.  Here are my needs:

* It should be in Pkgsrc.  Check at [http://pkgsrc.se/wm](http://pkgsrc.se/wm)
* Keyboard shortcuts must be configurable.  This is not negotiable.
* I use most of my apps full screen.  Maybe 70% of my time is spent in a fullscreen web browser or terminal.  Another 20% is in Abiword, Gnumeric, Evince or PCManFM, all fullscreen.  That leaves only 10% in non-fullscreen windows.
* Alt-tab window switching is nice.
* Virtual desktops (or perhaps the Ratpoison workspace system) are a must.  This is required.
* Conky support should be good - it's my lifeline :)
* Easy to understand config files
* Lightweight (of course ;) )


good for you, you should try new things when ever you can, not just wm's, try different programs to. the repo is full of alternatives. :)

---

### Post by cardinals_fan on 2008-05-12
> **kerry_s said:**
> good for you, you should try new things when ever you can, not just wm's, try different programs to. the repo is full of alternatives. :)
I already have a perfect assortment of 'alternative' programs.  It's a relative term because NetBSD doesn't have a lot in the way of defaults ;)

---

### Post by cardinals_fan on 2008-05-14
I think I've narrowed things down some.  The three left on my list are Xmonad, wmii, and dwm.  Awesome was buggy.  Of the three above, what experiences have you had?

---

### Post by init1 on 2008-05-14
> **cardinals_fan said:**
> Don't get me wrong, Pekwm is great.  But I prefer Openbox.  I mostly want to try a very lightweight, perhaps tiling, WM.  Awesome looks good for the tiling front.  Has anybody tried Ratpoison?
I tried ratpoison, but never used it for very long. I guess I just prefer ion and dwm.

---

