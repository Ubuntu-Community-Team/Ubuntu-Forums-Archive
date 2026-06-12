---
title: "lcd brightness on Serp5 w/ Jaunty"
date: 2009-06-12
forum: System76 Support
---

### Post by OldDirtyTurtle on 2009-06-12
I've been running Jaunty just over a week and have really liked it.

A day or so ago after a power manager induced hibernation, my lcd is extremely dim and the keyboard brightness controls don't work.  Until then I hadn't adjusted the brightness so I don't know if the keys worked prior to the event.

I've searched some related threads and it looks like a dead-end/deal with it type issue until the bug is fixed.

It is really hard to work on this machine with the screen this dim, so I'm posting here in hopes that there is a way around it since it did involve a system hibernation.  Your thoughts?

---

### Post by thomasaaron on 2009-06-12
Try running your System76 driver and rebooting. I'm not hearing of this problem on other Servals (yet). 

If that doesn't fix the brightness keys, right-click on your upper panel, select "Add to Panel" and add the Brightness Applet. Does that applet work?

---

### Post by OldDirtyTurtle on 2009-06-12
The applet doesn't work - in fact, when I add the applet it has a circle w/ slash on it.  Weird.  I tried the applet with and without the gnome power manager killed.

I'll run system restore and see what happens.

---

### Post by OldDirtyTurtle on 2009-06-12
Well - I ran the Sys76 driver and no change.  Ran system restore, no change.

Hmmm...

---

### Post by thomasaaron on 2009-06-12
try...

sudo apt-get --reinstall install gnome-power-manager

...and if that doesn't work, shoot me an email

Did this happen after an update? Or just after hibernation?

---

### Post by OldDirtyTurtle on 2009-06-12
Did the power manage reinstall, no change. Email sent.

---

