---
title: "Can gnome possibliy use this idea from QT 4.4?"
date: 2007-08-09
forum: The Cafe
---

### Post by triptoe on 2007-08-09
[http://labs.trolltech.com/blogs/2007/08/09/qt-invaded-by-aliens-the-end-of-all-flicker/](http://labs.trolltech.com/blogs/2007/08/09/qt-invaded-by-aliens-the-end-of-all-flicker/)

> an application with windowless child widgets is much more light-weight and resource friendly as we don&#8217;t allocate native windows for every single widget

There has been something that has really irked me since i have used gnome. I have used ATI cards, And nvidia ones.. i have tried open source drivers.. and the proprietary ones.. and there seems to be in common.. an innefficieny of the windowing system... where it will spike the cpu and become resource intensive when you drag it around.

i made a video showing exactly what i mean here: [http://www.youtube.com/watch?v=8gh7ABSs1NY](http://www.youtube.com/watch?v=8gh7ABSs1NY)

I have read that it is in reality just a synchronization issue. but that would mean it was just a visual glitch and would not be affecting the processor like it does.

I am not familiar much with gnome and GTK so forgive me if something like this is already implemented.. but could gnome learn from this?

I am seriously considering leaving gnome once KDE gets the QT 4.4 or whatever. I have always been a user of gnome and never even gave KDE a chance before

---

### Post by vexorian on 2007-08-09
you mean GTK? If this feature works out well for QT then I guess you can expect GTK to include it in a later version.

Edit: Saw the demo and I am pretty sure GTK developers will be forced to copy it...

---

### Post by triptoe on 2007-08-10
> As long as X11 is asynchronous (with all its benefits, by all means), resize and move operations will also be asynchronous, and flicker will appear as X11 first clears the exposed area (or leaves a trail of junk behind), then sends an expose notification, allowing the client to redraw. You can probably avoid the flicker with clever use of XFlush, but that will mean performance goes down the drain. With this solution, we don’t only remove the flicker, and remove the need to wait for X11 roundtrips, but we also free up X11 resources as Qt no longer needs the subwidgets on the server side. Which means less memory consumption :->. And on Windows, it means people can create more widgets than they could before…


:guitar:

---

### Post by georg_H on 2008-05-07
Hi all,

I know this is an old post, but I will answer it for everyone who finds it through search engines, as I did today.

The flicker you see in this post's video (http://www.youtube.com/watch?v=8gh7ABSs1NY) is the repainting done when a hidden part of a window is exposed again and quickly, because it forces a redraw. The effect is exaggerated by the way Firefox 2.0 paints to the window. Try any 'normal' (non-XUL) GTK application and it will be way less noticeable. This issue is easily solved by having the window fully drawn all the time and let a 'compositor' paint the actual screen. 

That is exactly what Compiz, cairo-compmgr and xcompmgr do. Compiz is accelerated by OpenGL: you will have a faster and snappier desktop with compiz than without it! I find most effects annoying, but I love compositing, so I simply disable almost all of them.

The problem solved in QT 4.4 is a completely different thing. GTK does not suffer from that flicker: I have been madly resizing windows without any flickering, and, in fact, I think it is pretty fast. In this particular case (GTK window resizing), disabling the compositor gives a faster redraw (in my Gutsy MacBook pro with the nvidia proprietary driver), but I still prefer the composited desktop.

You can also have a composited desktop on older systems where OpenGL-accelerated compositing is not available. Use 'xcompmgr -s' (server-side compositing); it does a pretty good job, but has some bugs that can be annoying. Unfortunately, since Compiz-like compositors appeared, this application has been unmantained and is not developed anymore.

I hope this is more clear now. :-)

---

