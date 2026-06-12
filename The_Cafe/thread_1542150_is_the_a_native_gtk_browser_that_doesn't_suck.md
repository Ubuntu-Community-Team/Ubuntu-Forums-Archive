---
title: "is the a native gtk browser that doesn't suck?"
date: 2010-07-30
forum: The Cafe
---

### Post by 2cute4u on 2010-07-30
Ive been going back and forth between midori and epiphany, but i'm not really happy with either one.  Midori does some really weird rendering at times, and Crashes a lot. Epiphany doesn't give you very much control, it has a bookmark system, that I really don't like, and frequently won't launch.   

Firefox and Chrome are not  native GTk browsers, and don't support either gnome-globalmenu or indicator-appmenu..

---

### Post by Lucradia on 2010-07-30
I'd have to go with Midori. Did you update to the latest using their PPA?

May solve some crashing/etc.

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

Need this PPA first: [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by 2cute4u on 2010-07-30
i use ppa's for a lot of stuff, including midori and epiphany.

---

### Post by Lucradia on 2010-07-30
> **2cute4u said:**
> i use ppa's for a lot of stuff, including midori and epiphany.

You won't get any better than Midori, sorry.

Unless Firefox goes GTK native (which they can't, to stay cross-platform. Seeing as I haven't seen GTK for MacOS.)

---

### Post by DoubleClicker on 2010-07-30
> **Lucradia said:**
> You won't get any better than Midori, sorry.

Unless Firefox goes GTK native (which they can't, to stay cross-platform. Seeing as I haven't seen GTK for MacOS.)

They could use gtk+, cross platform ( [http://www.gtk.org/download-macos.html](http://www.gtk.org/download-macos.html) ) but it would better if they went native on every platform.

What is worse, is Chrome uses GTK but doesn't have a GTK native interface. What's the point in using a toolkit, if you're just going to break it?

---

### Post by Lucradia on 2010-07-30
> **DoubleClicker said:**
> What's the point in using a toolkit, if you're just going to break it?

Google uses their own Web Server, GWS, it wouldn't surprise me that they'd make everything bend to their will.

---

### Post by RiceMonster on 2010-07-30
> is the a native gtk browser that doesn't suck?

Nope.

---

### Post by DeadSuperHero on 2010-07-30
I like Epiphany.

---

### Post by Mr. Picklesworth on 2010-07-30
> **2cute4u said:**
> Ive been going back and forth between midori and epiphany, but i'm not really happy with either one.  Midori does some really weird rendering at times, and Crashes a lot. Epiphany doesn't give you very much control, it has a bookmark system, that I really don't like, and frequently won't launch.   

Firefox and Chrome are not  native GTk browsers, and don't support either gnome-globalmenu or indicator-appmenu..

Chrome is, in fact, built with native GTK+. It just doesn't look like it because the main interface overrides a lot of drawing functions. If you explore the browser, though, you'll notice it uses regular, unmolested GTK widgets (and, more importantly, conventions) where it counts. For example, text boxes (including the address bar), menus, tooltips and anything outside the main window! The other unusual looking widgets are still completely intact in terms of functionality.

Unlike a lot of browsers that use GTK, it also supports all the standards good modern Linux apps should be using. For example, XDG user dirs (~/.cache, ~/.config, ~/.local/share, etc.), your local settings for which applications to open files with, Gnome's proxy settings tool, and (soon) your nearest keyring daemon (be it gnome-keyring or kwallet). Many other such goodies appear when they're needed.

As for the big part of the interface that has the overridden drawing functions, I'm not sure what was wrong before (or how they fixed it), but in the more recent versions (in the dev channel), the "Use GTK+ theme" option works as it should &#8212; especially with [a good icon theme]("http://ubuntuforums.org/showthread.php?t=1541306") :b
(With an ugly one, you lose a lot because Chrome's default look demonstrates exactly why monochrome action icons are a great idea, so losing them is like torture for the eyes).

So, while it does look different, you don't need to feel too bad using it.


Have you tried Epiphany *recently*? 2.30 had a lot of nice changes. It uses Webkit now, so it's a lot faster (and less bulky) than it was. That may help&#8230;
I agree the bookmarking takes some getting used to, but when I used Epiphany &#8212; before I gave in to Chromium (Feedly controls my life) &#8212; I came to love how that bit worked. One really fun thing is using the toolbar editor to add some Topic menus.

---

### Post by WinterMadness on 2010-07-30
i actually dont mind epiphany even though it sucks in so many areas. but if you dont like epiphany i dont know what you will like thats gtk native.

---

### Post by murderslastcrow on 2010-07-30
Reminds me of why I use KDE now.

Seriously, Midori really is the best experience you're going to get outside of Firefox in Gnome. So far.

Kazekahase was pretty good, but apparently it's out of date and unsupported. It was pretty neat in its time, the fastest gecko browser around.

I really don't know what to tell you other than that. I haven't found anything else of Firefox/Chrome's quality and configurability outside of those two.

---

### Post by sertse on 2010-07-30
> **murderslastcrow said:**
> Reminds me of why I use KDE now.


Umm, KDE? Konqueror or Arora or Rekonq?  I wouldn't say any of them are really better than Midori, let alone the "non-native" stuff like Firefox/Chrome/Opera.

Anyhow, I like Midori, most rendering problems in Midori would be fixed if your set your user agent to Safari. 

It has some decent addons -  sure no where was near as Firefox/Chrome etc, but step back - It's almost funny seeing people complaining that a browser had not fulfil every quirky need a user has which 10000's of extension were made...

---

### Post by murderslastcrow on 2010-07-30
I prefer Rekonq to Midori. I'd say they're about the same.

It's more about integration and speed to me, than anything else. I don't need tons of plugins and extensions to try and 'facilitate'/interrupt my browsing experience. I'm very minimalistic when it comes to browsing, in the end, and UIs in the first place to be honest.

But yeah, I also think Konqueror is quite nice compared to Firefox, and it's fully native. Arora is also quite nice, and completely native. Not to mention Konqueror will soon support the use of Webkit, which is very interesting, since it's perfectly adequate as-is.

Also, the smooth-scrolling really gets me. ^_~

---

### Post by smellyman on 2010-07-31
I think Epiphany rocks now.

If you haven't used it in a while, I would highly recommend it.

---

