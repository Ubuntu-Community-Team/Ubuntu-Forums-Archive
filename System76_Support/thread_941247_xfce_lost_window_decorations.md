---
title: "xfce lost window decorations"
date: 2008-10-07
forum: System76 Support
---

### Post by andrewdied on 2008-10-07
I was trying out xfce on my system 76 serval performance laptop.  Last week I wound up having to reinstall ubuntu, so this was a very fresh install.  I had reinstalled the system 76 driver.

Anyway, in xfce all the window decorations disappeared.  I _think_ it was while I was using the touchpad, but that's not clear.  Does anyone know either what I could have done, or how to undo it?

I tried logging out and back in, and the effect hasn't changed.  Also, the virtual desktops disappeared from the bar -- I just have one desktop now.

In the xfce settings manager, I tried managing window tweaks and decorations, but it says my window manager is now "(unknown)".

Thanks for the help.

---

### Post by jeamer on 2008-10-08
have you tried running metacity --replace from the command line? If that brings your window decorations back, add /usr/bin/metacity to startup programs in sessions

---

### Post by andrewdied on 2008-10-08
> **jeamer said:**
> have you tried running metacity --replace from the command line? If that brings your window decorations back, add /usr/bin/metacity to startup programs in sessions

That did it.  Well, I was working on it from memory, and what I did was metacity & from the command line, and clicked save session when I logged off.  When I logged back in the window manager was running, which is a Good Thing (TM).

Thanks for the help.  I had no idea what wm xfce was using.

---

### Post by andrewdied on 2008-10-08
Turns out that wasn't quite what I wanted.  The default window manager for xfce is xfwm4, which you run in the back ground as xfwm4 --daemon.  So, by finding the metacity PID by uname aux | grep meta, I could then "sudo kill pid; xfwm --daemon".

---

