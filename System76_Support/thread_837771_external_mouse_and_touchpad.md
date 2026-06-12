---
title: "external mouse and touchpad"
date: 2008-06-22
forum: System76 Support
---

### Post by jeamer on 2008-06-22
Hey, I have a Panv2 and I was wondering if there was a way to set it up so that when you plug in an external mouse or mouse type device (like a tablet) it temporarily disables the touchpad? I'm admittedly a lazy typer, and when I'm doing papers and things I always jump all over the paper and delete/add things I shouldn't because the lower right hand side of my left palm always grabs the upper corner of the touchpad. Thanks!

---

### Post by jdb on 2008-06-22
I don't know if it will work on the kind of touchpad a Panv2 has, but on my Daru2 I use gsynaptics.
It doesn't disable the touchpad automatically when you plug in a mouse, but it makes it very easy to enable/disable the touchpad manually.
It also lets you turn off tapping which really limits the damage if the touchpad isn't diasbled.

jdb

---

### Post by thomasaaron on 2008-06-23
Yes, gsynaptics worked with the PanV2. Good ideas.

Theoretically, you could write a script that detected a usb mouse being plugged in and then ran: sudo modprobe -r psmouse to disable the mouse.
The gysynaptics way sounds like less of a hassle though.

---

### Post by jeamer on 2008-06-24
Thanks, appreciate it!

---

### Post by brennydoogles on 2010-11-26
Don't know if this helps, but I recently wrote a tutorial that may solve your problem. [http://ubuntuforums.org/showthread.php?t=1629433](http://ubuntuforums.org/showthread.php?t=1629433)

---

