---
title: "Figured it out - why Ubuntu, Xubuntu, Lubuntu, etc. didn't feel right on new laptop"
date: 2014-03-14
forum: Ubuntu, Linux and OS Chat
---

### Post by slooksterpsv on 2014-03-14
Everytime I installed Ubuntu, Xubuntu, Ubuntu-Gnome or Lubuntu something didn't seem right and I didn't figure it out until tonight.

I just installed Xubuntu because well it's Xubuntu it's fast, clean, friendly (until Elementary OS Isis comes out maybe...) and noticed it didn't feel right, something seemed to be wrong.

I have to run Xorg -configure each time I install because the kernel doesn't have drivers for the Radeon HD 8400, and afterwards none of the fglrx drivers would work and 13.12 didn't either. I found some possible fixes like nomodeset, but didn't try them as I found one post that said 14.1 beta drivers worked. Well I'm running 14.2 beta drivers (13.35) and they work wonderfully.

But before I could get those drivers working, it still felt and looked like something was wrong. Then it hit me, I was playing one of my games and the colors seemed to be off on the gradient, instead of a smooth gradient it was rough and more solid between gradient areas.

The graphics! Every time I ran a variation it seemed like the colors were off, it didn't sparkle, didn't look the same. I thought maybe it was an aesthetic design that I hadn't noticed, but when I got on my nieces laptop (the asus I gave her) my linux looked wonderful to where I about traded her my more powerful computer for that one.

I didn't realize how much colors would make an impact on OS use.

Also I've been taking an edX Computer Science course and they use XFCE on Fedora, and have a nice look to it, so I decided to mimic it a bit.

---

### Post by mastablasta on 2014-03-14
also screen (again contrast and display brightness) and screen cover glare or mat

---

### Post by buzzingrobot on 2014-03-14
Lighting, screen angle, time of day, etc., all can also impact the appearance of images and text on a display. 

On this ThinkPad, for example, the top of the screen is usually angled backed a few degrees. For example, if I run an interface with two horizontal panels, and set them to be identical colors, the colors will, nonetheless, appear to be different.

I can be pretty fanatic about font rendering issues:  It's better in natural light on the laptop than on artificial light. But, there's no apparent difference on a 24-inch Dell display.

Even the same displays, made at different times, can display colors differently.  And, of course, color perception is not identical in everyone.

---

### Post by PondPuppy on 2014-03-14
Processing digital photographs is a study in compromise for me. Colors that look beautiful on my laptop can be garish on another monitor. Some of the pics posted on Panoramio, even some of my own earlier ones, look either under- or over-saturated. I imagine it's because I'm not viewing them on the same equipment as that on which they were processed.

---

### Post by buzzingrobot on 2014-03-14
> **PondPuppy said:**
> Processing digital photographs is a study in compromise for me. Colors that look beautiful on my laptop can be garish on another monitor. Some of the pics posted on Panoramio, even some of my own earlier ones, look either under- or over-saturated. I imagine it's because I'm not viewing them on the same equipment as that on which they were processed.

You can color calibrate your display to create a color profile (admittedly easier said than done on Linux).  You would do that if you were running off prints, to ensure colors matched all around.

But, I'm afraid we're stuck with not being able to control how images look on other displays.

Some online photo sites apply compression or otherwise alter images to reduce storage demands.

---

