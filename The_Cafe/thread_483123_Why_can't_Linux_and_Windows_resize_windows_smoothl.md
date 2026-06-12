---
title: "Why can't Linux and Windows resize windows smoothly?"
date: 2007-06-24
forum: The Cafe
---

### Post by v8YKxgHe on 2007-06-24
Hey,

Something that has always caught my eye with Linux and Windows, is that when you resize a window it is never smooth, as in it will jump and skip. However, with MacOSX when you resize a window it is so, so smooth and perfect in every way.

I'm just wondering, how come Linux and Windows can't get it right?

---

### Post by macogw on 2007-06-25
Not sure what you mean.  I just did it and the window itself resized smoothly.  The stuff inside had to be redrawn to grow and shrink.  It could be to do with the graphics card or something, since Macs have their own "special" hardware.

---

### Post by BuffaloX on 2007-06-25
My system has one of the fastest graphics cards available, and resizing isn't smooth.
So I don't get how MacoGW can have smooth resizing.
On my system resizing causes flickering, which is a clear indicator that resizing isn't synced to monitor,
And the resizing updates less than 25 times per second. Lookinf at it, I'd say about 3-4 times/sec.

I guess the reason quite simply is that it has not been considered an issue by the devs.
Or maybe to prevent the GUI from taking up too much CPU power.

---

### Post by macogw on 2007-06-25
Well, like I said, the contents of the windows don't go smoothly, they're obviously redrawn, but I don't see jolts when I resize.  It (window edge / borders) definitely is going by my mouse's location the whole time, not lagging 50px behind then jumping or anything.

---

### Post by BuffaloX on 2007-06-25
> **macogw said:**
> Well, like I said, the contents of the windows don't go smoothly, they're obviously redrawn, but I don't see jolts when I resize.  It (window edge / borders) definitely is going by my mouse's location the whole time, not lagging 50px behind then jumping or anything.

Funny, on my system it's the other way round, content is pretty smooth, but window border flickers.

Just tried to enable Beryl, with Beryl the flicker is gone, but updates are slow and lagging.

---

### Post by Jonne on 2007-06-25
I don't get any flickering, both in Windows and in Ubuntu, on 2 different machines. I guess it depends on which app you're resizing too. In some applications (browsers with pages that have lots of floats, gui's that have floating elements, ...) you'll have stuff jumping around.

 I see applications like finder on OS X avoid this by not expanding the icon view to the full width of the window, thus giving a horizontal scrollbar if you make it smaller, while Nautilus, Explorer and Konqueror will reflow the icons when you resize. (IMHO, avoiding horizontal scrollbars is more important than giving a smooth window resize experience, especially since resizing isn't something you'll do constantly).

Another thing you might mean is the following option in Windows: display properties >appearence >effects >show window contents while dragging. If this option is off, Windows will show a box when resizing/moving windows, which isn't very natural (but great on older systems). I'm not sure if this option is on or off by default. In Ubuntu I think it depends on whether you use desktop effects or not.

---

### Post by samjh on 2007-06-25
Never had this problem.  Window resizing has always been pretty smooth in both Ubuntu and Windows.

---

### Post by DoctorMO on 2007-06-25
The redrawing of windows is not only dependant on Xorg but also on what ever tool kit the programmer used to create their program.

Mac OSX has been using Aqua/Carbon/whatever for ages and it's a very good proprietory gui stack which depends on 3Dfx hardware; once compiz or which ever makes it stable and is integrated into Xorg from the start you will see something like Mac OSX window rendering in Gtk or Qt no doubt.

The motto has always been that the software must work without fancy hardware. Mac OSX will NOT work on none 3D hardware so the question is do we deny users of older computers access to new software?

---

### Post by Jonne on 2007-06-25
> **DoctorMO said:**
> Mac OSX will NOT work on none 3D hardware so the question is do we deny users of older computers access to new software?
Actually, it does. OS X runs fine in VMWare, which has no 3D accelleration. It even runs some of the effects like a regular OS X install on real hardware (the genie effect and the dock effects don't use 3D at all).

The OS X effects are written in such a way that they degrade gracefully. If the gfx card can't handle the effect, it will fall back to a 2D representation of whatever it is you were doing, and it will use the CPU instead of the GPU.

GNOME already does such a thing too (in some parts). If you have special media keys on your keyboard to control the sound volume (and they were detected properly), the OSD will look different whether you have a compositor (compiz, beryl) or not (Metacity).

---

### Post by macogw on 2007-06-25
> **Jonne said:**
> 
Another thing you might mean is the following option in Windows: display properties >appearence >effects >show window contents while dragging. If this option is off, Windows will show a box when resizing/moving windows, which isn't very natural (but great on older systems). I'm not sure if this option is on or off by default. In Ubuntu I think it depends on whether you use desktop effects or not.

By default, the contents are shown.  They want a "pretty" (yeah, with the Luna theme?) experience OOTB, but any computer from the early days of XP now requires setting it to not show contents to run at a reasonable pace

---

