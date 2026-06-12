---
title: "Why do windows repaint slowly"
date: 2008-11-01
forum: The Cafe
---

### Post by cl333r on 2008-11-01
hi folks,
I'm using Ubuntu for like 2 years, I ran it on nvidia and intel graphics cards and on same computers I also have windows. What I clearly noticed is that Ubuntu (perhaps all distros, not just Ubuntu) manage to repaint windows pretty slowly compared to windows. In some cases I can almost watch the parts being repainted despite having binary graphics drivers installed.
I would appreciated a lot if someone points me to some link or comment on why this is so slow (compared to window$), what needs to be improved (the X server, the graphics drivers or something else..).
I'm learning C and as I 'grow up' I would consider investing my time into fixing this issue.
I uploaded a demo to
[http://xlinuks.googlepages.com/video.ogv](http://xlinuks.googlepages.com/video.ogv)
but due to the video frame rate one can't actually see what I'm talking about.
Both Gnome and KDE are slow, except that KDE (3 & 4) seems a bit faster.
The only post I found somewhat similar to mine is:
[http://ubuntuforums.org/showthread.php?t=188738](http://ubuntuforums.org/showthread.php?t=188738)

---

### Post by billgoldberg on 2008-11-01
> **cl333r said:**
> hi folks,
I'm using Ubuntu for like 2 years, I ran it on nvidia and intel graphics cards and on same computers I also have windows. What I clearly noticed is that Ubuntu (perhaps all distros, not just Ubuntu) manage to repaint windows pretty slowly compared to windows. In some cases I can almost watch the parts being repainted despite having binary graphics drivers installed.
I would appreciated a lot if someone points me to some link or comment on why this is so slow (compared to window$), what needs to be improved (the X server, the graphics drivers or something else..).
I'm learning C and as I 'grow up' I would consider investing my time into fixing this issue.
I uploaded a demo to
[http://xlinuks.googlepages.com/video.ogv](http://xlinuks.googlepages.com/video.ogv)
but due to the video frame rate one can't actually see what I'm talking about.
Both Gnome and KDE are slow, except that KDE (3 & 4) seems a bit faster.
The only post I found somewhat similar to mine is:
[http://ubuntuforums.org/showthread.php?t=188738](http://ubuntuforums.org/showthread.php?t=188738)

Could be a bad drivers, hardware, ...

All I can say is that I and I'm sure most people don't have this problem.

If it's really buggin you, try another WM like Fluxbox, it might help.

---

### Post by eldragon on 2008-11-01
i know what you mean, ive felt this too. but what leaves me with no worries is that this windows repainting does not correlate with operating system performance..

i actually find linux to be much better at multitasking than windows (aka, couple of intensive tasks share resources better under linux compared to windows). the windows repaint is a nuisance and nothing more. i think (and dont quote me on this) its related to gnome and the gtk toolkit. you could try different desktop environments and check the results...

---

### Post by Grant A. on 2008-11-01
> **billgoldberg said:**
> Could be a bad drivers, hardware, ...

If it's really buggin you, try another WM like Fluxbox, it might help.

+1

That's exactly what I was thinking. However, if you REALLY want speed use wmii.

---

### Post by cl333r on 2008-11-01
I have the GeForce 7600 GT 256MB with the proprietary drivers that Ubuntu suggested, unfortunately there are no better drivers I think. I have the same issue on my (second) 64 bit computer (also nvidia) and at work on intel graphics. I don't think in all these cases I have bad drivers, I think it's something else.
I tried other desktops, fluxbox and icevm I think (about 1 year ago) but IMHO there's a usability gap compared to Gnome and KDE.
I heard somewhere that this is because (allegedly) the graphics drivers in window$ are built-in into the window$ kernel, while Gnome and KDE are merely working on top of X server, hence the performance gap. I'm not sure if this is true, but I know that window$ works faster and I wanna help change that as I know C better. I'm saying this because it actually bothers me, but if I have to choose sticking to window$ and viruses, or choosing slower-graphics Linux without viruses, I choose the later.

---

