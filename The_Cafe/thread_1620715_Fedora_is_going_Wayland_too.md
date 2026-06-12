---
title: "Fedora is going Wayland too"
date: 2010-11-13
forum: The Cafe
---

### Post by weasel fierce on 2010-11-13
[http://digitizor.com/2010/11/12/wayland-may-be-included-in-fedora-as-fedora-15/](http://digitizor.com/2010/11/12/wayland-may-be-included-in-fedora-as-fedora-15/)

Looks like Wayland is going to be the way to go

---

### Post by KdotJ on 2010-11-13
No surprise there then...
I'm quite excited by all this Wayland business, but will the user notice anything different really? How great will the advantages be?

---

### Post by Lucradia on 2010-11-13
> **KdotJ said:**
> No surprise there then...
I'm quite excited by all this Wayland business, but will the user notice anything different really? How great will the advantages be?

It says there will be no tearing, I've seen this a lot with compiz wobbly windows and dragging while viewing contents, as well as via Metacity's Compositor (via dragging while viewing contents.)

---

### Post by weasel fierce on 2010-11-13
> **KdotJ said:**
> No surprise there then...
I'm quite excited by all this Wayland business, but will the user notice anything different really? How great will the advantages be?

Im not that techy, but I imagine if it relies on openGL, it'd let us offload some stuff to the GPU

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-11-13
The "no-tearing" better apply to multi-monitor systems as well. I've tried just about everything, but for the life of me I can't figure out how to get vsync on both monitors if they have different refresh rates (gnome, compiz, nvidia, proprietary drivers). If wayland sorts that out I'm sold.

---

### Post by madhi19 on 2010-11-13
The system monitor will need an upgrade because right now it does not keep track of video memory use. Am not an expert but Wayland use of GPU memory will free up some ram that xorg use to hog. Provided that after a transition most if not every application become native on Wayland. Not likely if only Ubuntu make the move but if Fedora and a few more distro follow suit developers will likely start porting their codes. Nobody want to waste resource running both Wayland and Xorg for too long after all. If we end up running both for the sake of compatibility for more than one or two release than what the point?

---

### Post by I'mGeorge on 2010-11-13
well sure it's not that I have much against the old X server anyway but a little bit of a technological leap into the future won't hurt anyone. I hope Debian will do the switch too 'cause I'm using both.

---

### Post by Ctrl-Alt-F1 on 2010-11-13
That's cool.  The more major distros we can get on the bandwagon the faster development SHOULD progress.

---

### Post by Paqman on 2010-11-13
> **KdotJ said:**
> No surprise there then...
I'm quite excited by all this Wayland business, but will the user notice anything different really? How great will the advantages be?

From the sound of it, the main advantage is going to be for devs. X is getting old and creaky, and taking it where they want to is going to be a horrendous amount of work. It's time to kick it into touch and start from scratch with something designed for the modern environment.

---

### Post by DeadSuperHero on 2010-11-13
I'm personally pretty excited to see this. 

What I'd really love to see (and this is more of a pipe dream right now than anything) is how well Qt will perform on top of Wayland without X or any necessary compatibility mode.

I would then [love to see it use Skia]("http://blog.rburchell.com/2010/11/qt-on-skia.html") as a backend rather than Cairo, and [be compiled in LLVM/Clang]("http://labs.qt.nokia.com/2010/10/29/compiling-qt-with-clang/"). I imagine it could be crazy fast, and crazy good.

A nerd can dream.

---

### Post by wojox on 2010-11-13
It's no surprise. Red Hat started Wayland. Intel and Nokia plan to adopt Wayland in MeeGo when it's ready..

---

### Post by Decatf on 2010-11-13
> **Paqman said:**
> From the sound of it, the main advantage is going  to be for devs. X is getting old and creaky, and taking it where they  want to is going to be a horrendous amount of work. It's time to kick it  into touch and start from scratch with something designed for the  modern environment.


If it benefits the developers then the end user will benefit from it too.

---

### Post by Dragonbite on 2010-11-13
Well that helps alleviate any worries about Wayland since Fedora is usually better handling of my hardware than any other distro.

---

### Post by 3Miro on 2010-11-13
Some of concerns:

1. All modern computers ship with OpenGL capable hardware, but not all drivers are FOSS, so this will cause some headache.

2. Wayland will not work on older computers, so we will have to see a "legacy" flavor of Ubuntu.

3. How will Wayland and wine work together. Right now, when playing games it is best to not use OpenGL effects (no Compiz, no Kwin effects).

3 will be a temporary setback at most (but unpleasant for some of us), 2 will require an extra effort by the community, but it is only temporary anyway. 1 is the worst, since convincing the manufacturers to release their source will be very hard.

---

### Post by MasterNetra on 2010-11-13
> **I'mGeorge said:**
> well sure it's not that I have much against the old X server anyway but a little bit of a technological leap into the future won't hurt anyone. I hope Debian will do the switch too 'cause I'm using both.

I'd imagine they might but it will be a good while before a stable release sees wayland

---

### Post by MasterNetra on 2010-11-13
> **3Miro said:**
> Some of concerns:

1. All modern computers ship with OpenGL capable hardware, but not all drivers are FOSS, so this will cause some headache.

2. Wayland will not work on older computers, so we will have to see a "legacy" flavor of Ubuntu.

3. How will Wayland and wine work together. Right now, when playing games it is best to not use OpenGL effects (no Compiz, no Kwin effects).

3 will be a temporary setback at most (but unpleasant for some of us), 2 will require an extra effort by the community, but it is only temporary anyway. 1 is the worst, since convincing the manufacturers to release their source will be very hard.

1. Same is with non-openGL capable hardware, this wouldn't be new.

2 & 3 don't know. I would think a fall back to xorg at least with the first Ubuntu release with would be done, but don't know. As for 3 I would say its probably too early to tell, but then again I'm not currently testing Wayland so couldn't say.

---

### Post by 3Miro on 2010-11-13
> **MasterNetra said:**
> 1. Same is with non-openGL capable hardware, this wouldn't be new.


There are generic FOSS drivers for Xorg that will give you at least basic functionality. Of all the window managers, Compiz is the only one that requires OpenGL and fallback to metacity is much easier than fallback to another graphical server. From what I understand Wayland will not start at all unless you have an OpenGL capable driver.

Non FOSS drivers are a problem as is, but I fear that Wayland will make those worse.

---

### Post by zekopeko on 2010-11-13
> **3Miro said:**
> There are generic FOSS drivers for Xorg that will give you at least basic functionality. Of all the window managers, Compiz is the only one that requires OpenGL and fallback to metacity is much easier than fallback to another graphical server. From what I understand Wayland will not start at all unless you have an OpenGL capable driver.

Non FOSS drivers are a problem as is, but I fear that Wayland will make those worse.

Compiz now supports 2D so it can act like metacity.

---

### Post by dh04000 on 2010-11-14
> **zekopeko said:**
> Compiz now supports 2D so it can act like metacity.


Cool, did not know that. Did that drop in the 0.9x series? I love how compiz has been reborn and is really showing its power and flexibility.

---

### Post by Nightstrike2009 on 2010-11-14
I see no issue, it makes sense as long as we have usable open-source and closed-source drivers that work with it (ATI, Nvidia, Intel, etc). X11 is getting on a bit now and has been well overdue for retirement for a bit.

---

### Post by Dragonbite on 2010-11-14
> **3Miro said:**
> Some of concerns:

1. All modern computers ship with OpenGL capable hardware, but not all drivers are FOSS, so this will cause some headache.

2. Wayland will not work on older computers, so we will have to see a "legacy" flavor of Ubuntu.

3. How will Wayland and wine work together. Right now, when playing games it is best to not use OpenGL effects (no Compiz, no Kwin effects).

3 will be a temporary setback at most (but unpleasant for some of us), 2 will require an extra effort by the community, but it is only temporary anyway. 1 is the worst, since convincing the manufacturers to release their source will be very hard.

Yes, the drivers will be an issue. Yes Wine will be an issue. Yes these will be temporary setbacks but once the community is behind it it will get these things fixed.

Seriously, this isn't like when Apple moved from OS 9 to OS X (and Unix).  Now that was a more major change in EVERYTHING!

---

