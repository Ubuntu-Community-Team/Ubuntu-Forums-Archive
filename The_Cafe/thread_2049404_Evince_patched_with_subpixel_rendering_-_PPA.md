---
title: "Evince patched with subpixel rendering - PPA"
date: 2012-08-28
forum: The Cafe
---

### Post by Helkaluin on 2012-08-28
Dear fellow forumites,

Upstream Evince has been unable to follow fontconfig's settings in rendering text with subpixel-rendering since 2005, resulting in sub-par quality text when using an LCD screen.

Bugs in question:
[https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/80921](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/80921)
[https://bugs.freedesktop.org/show_bug.cgi?id=3307](https://bugs.freedesktop.org/show_bug.cgi?id=3307)

Up till mid-2011, Tobias Wolf has been maintaining a PPA of a patched Evince that renders text with Cairo subpixel forced on: [https://launchpad.net/~improved-lcd-filtering/+archive/ppa]("https://launchpad.net/%7Eimproved-lcd-filtering/+archive/ppa")

Seeing there aren't recent updates to Tobias' PPA, I've set up a new PPA for this patched Evince.  Currently it builds for Precise only.

XPS support is also flipped on.

Hope that this helps fellow Ubuntu users who reads PDFs on an LCD screen.

 Link to PPA: [https://launchpad.net/~helkaluin/+archive/evince-subpixel]("https://launchpad.net/%7Ehelkaluin/+archive/evince-subpixel")

Pics for comparison:
[Unpatched Evince, greyscale rendering]("http://i.imgur.com/i8Xcd.png")
[Patched Evince, subpixel rendering]("http://i.imgur.com/SeUMg.png")

---

### Post by rgbrown on 2012-08-28
Thanks! I've been wishing something like this existed for ages. Evince's grayscale smoothing has been driving me batty (and giving me a headache).

---

### Post by Helkaluin on 2012-08-31
> **rgbrown said:**
> Thanks! I've been wishing something like this existed for ages. Evince's grayscale smoothing has been driving me batty (and giving me a headache).
Glad to have helped. ;)

I've updated the build config and now Evince is built with alpha-quality XPS support.

---

