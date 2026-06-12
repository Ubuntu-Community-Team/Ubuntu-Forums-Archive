---
title: "Open Source Dev"
date: 2008-07-13
forum: The Cafe
---

### Post by yahn on 2008-07-13
I've mainly developed for Windows only in the past, so I've never really used projects like wxWidgets.  I'm wondering what the standard seems to be for open source cross platform development.

I was thinking that I should use wxWidgets for windows, OpenGL for rendering, Corona for images, OpenAL and Vorbis for sound, Open Input System for input.  Is this a fairly standard practice or am I missing something?  Additionally, I've tried to find some documentation on using some of these things together, but I havn't been too successful.

Does anyone know of any good websites or forums dealing specifically with open source development?  I googled and was fairly surprised that nothing came up.

One last thing -- What do I do without Photoshop?  Is Gimp the only alternative?  Gimp just doesn't cut it.  Do you guys just switch over to Windows when you need to do some art?

---

### Post by LeoSolaris on 2008-07-14
Well..   for the documentation you're looking for, I can't really help ya there. I'm no dev.

As for Gimp...   Gimp is useful, but it has it's limits, too. Photoshop is also useful, but it has limits just like Gimp. Check out Inkscape, and there are a few others. Each of them have their merits and flaws. I've heard good things out of Krita.

[ Here's]("http://linuxappfinder.com/alternatives") a pretty decent website for software replacements available for Linux. It maybe of some use to you.

If you give Wine's devs enough time, they may get Photoshop working under Wine.

Leo

---

### Post by Canis familiaris on 2008-07-14
YOu could always run Photoshop CS2 in WINE. Or you could use VIrtualbox to run all your favourite Windows programs,

---

### Post by yahn on 2008-07-14
How do you get OpenGL working on Ubuntu?  I figured this would already be installed, but I guess it is not.  I searched and couldn't find anything other than people saying that they are having trouble.  I installed the drivers for my graphics card, so I figured that I would have OpenGL, but I don't and I don't see how to get it.

---

### Post by Polygon on 2008-07-14
if you have installed the correct drivers for your video card, and you get 'yes' when you type this into the terminal:

glxinfo | grep direct

then you should have 3d acceleration. if it returns a no, then you did something wrong.

and you may want to post on the programming forum about whats commonly used.

---

### Post by jomiolto on 2008-07-14
> **yahn said:**
> I've mainly developed for Windows only in the past, so I've never really used projects like wxWidgets.  I'm wondering what the standard seems to be for open source cross platform development.

I was thinking that I should use wxWidgets for windows, OpenGL for rendering, Corona for images, OpenAL and Vorbis for sound, Open Input System for input.  Is this a fairly standard practice or am I missing something?  Additionally, I've tried to find some documentation on using some of these things together, but I havn't been too successful.

I'd recommend taking a look at Qt. I haven't done anything major on it (yet), but it seems like an amazing tool kit from the little experience I've had with it. Included in Qt is Phonon, a multimedia tool kit, which has at least some form of support for audio (and video too!).

---

### Post by damoxc on 2008-07-14
Could take a look at SDL?

[http://www.libsdl.org/](http://www.libsdl.org/)

---

### Post by yahn on 2008-07-14
Well, it says yes when I type glxifno | grep direct.  The only problem I'm having now is that I can't link to GL.  It's finding the headers now, but -lGL isn't working.  What am I supposed to put in?

---

### Post by Polygon on 2008-07-14
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

this forum ^ might be able to help you

---

