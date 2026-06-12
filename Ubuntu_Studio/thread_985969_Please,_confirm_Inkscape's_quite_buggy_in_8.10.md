---
title: "Please, confirm: Inkscape's quite buggy in 8.10"
date: 2008-11-18
forum: Ubuntu Studio
---

### Post by Telegram Sam on 2008-11-18
Hi,

Trying to open Inkscape, I am facing a bug with an application window. Part of it is rolling out under lower Gnome panel and it is impossible to get it out there. The application window do not allow resizing. Clicking on various options, making situation even worse, there are another instance opening, window bar fading, etc.

Is it my personal luck or wide-known bug?

---

### Post by Stochastic on 2008-11-18
It works just fine for me, though I've only used it mildly - no massive art projects.

If you need to move a window in gnome a nice feature is to hold down the Alt button when you click on the window - this will allow you to move it around without having to grab the top window bar.

---

### Post by Telegram Sam on 2008-11-18
Thanks!

Will try to figure something out... btw, Xara Xtreme is not stable too.

---

### Post by rylleman on 2008-11-21
Do you have any desktop effects like compiz running?
I've had similar problems in the past that were caused by Compiz. Turning it off solved the situation for me.

---

### Post by UtopiaTheory on 2008-11-21
Yeah, I have to turn compiz off in order for Inkscape to run smoothly in 8.10.  It was fine in Hardy though.

---

### Post by Dan_Dranath999 on 2008-12-08
I'm using hardy and can't maximize Inkscape, it gets under the gnome panel.

---

### Post by meho_r on 2008-12-08
Works fine here (8.10, 64bit, with Compiz on)

---

### Post by Stochastic on 2008-12-08
I have compiz running (8.10, 32-bit) and everything is fine.

Those who do experience troubles are encouraged to report their bugs on launchpad.net so as to help developers fix any problems that might exist.

---

### Post by Dan_Dranath999 on 2008-12-11
after switching the toolbox to "small icons", the problem goes away...

(I suppose, this'won't work for you if you are using a small screen resolution)

---

### Post by wx672 on 2008-12-12
I have the same problem on my Dell mini 9 netbook, which has a 9 inch small screen with 1024x600 resolution.

I don't have compiz nor any other screen effect things installed. 
In a very basic(plain) ubuntu desktop environment, the bottom edge of the Inkscape window is far below my screen bottom edge, and the height of the window can not be shortened any more, nor can I maximiz the window by any means.

---

### Post by xerman on 2009-02-14
Hello there, 


As someone posted before, the issue is related to size of toolbar icons. If maximize window, can not fit in small screens. In big screen no problem at all.

In my laptop, 1280x800, i can not maximize with compiz on, as part of the window hides beneath the bottom panel, always will try to arrange itself to the top, and making click on menu quite difficult.

This is not just issue of inkscape. I've noticed many gnome apps have oversized dialogs for open/close/save that extend screen size, mostly downwards, but some even widewards in small screens.

Maybe is a bug in the Gnome Human Interface Guidelines, maybe a bug in GTK libs, or maybe a bug in app code. Even could be a bug in user's brain.

Other from this, i found inkscape working well. I just do not maximize, i just drag window to almost full screen, and then i can work quite wel. And I use Inkscape to do all my graphic work.

20090227: I recently modified the window aspect to a metacity theme smaller and thinner, and now i can maximize inkscape fitting 1280x800 screen with no issues regarding this.

As I told before, there is some misunderstanding of Gnome HUG when designing interfaces. Seems some programmers think everyone has a 30'' screen and no one uses laptops. GIMP dialogs still grow out of the screen everytime. At least, apps should have different layouts depending on the screen size.

By the way, sometimes i feel Inkscape does things by itself, as zooming in and selecting-unselecting. But I am not sure is Inkscape related or Trackpad related, as trackpad and buttons behave weird sometimes. Mostly with right click.

Regards

---

### Post by cb951303 on 2009-02-14
using it daily, no problems at all

ubuntu 8.10 32 bit

---

### Post by benjaminsuman on 2009-06-29
I have found that on my Dell Mini 9 Inkscape will not resize correctly due to the vertical tool box.  If I hide or float the toolbox then the Inkscape window will resize, maximize, and go to full screen mode correctly.  It seems to be a problem with the toolbox's fixed vertical size and the low resolution of the screen on my Mini 9.  While not ideal, floating the toolbox at least makes Inkscape usable.

---

