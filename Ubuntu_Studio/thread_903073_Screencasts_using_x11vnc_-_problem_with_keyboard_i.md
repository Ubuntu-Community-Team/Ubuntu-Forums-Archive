---
title: "Screencasts using x11vnc - problem with keyboard input"
date: 2008-08-27
forum: Ubuntu Studio
---

### Post by memories on 2008-08-27
I have the vnc2swf.py script, and I have a VNC server running (tightvnc). I have two problems.

First, keyboard input isn't working properly. It's as if the windows key/hyper key is being held down in the VNC screen. On my desktop, WinKey+t opens a terminal, for example, but on the VNC screen, just pressing 't' opens a terminal. Keys that aren't mapped get displayed properly.

Also, this isn't that big of a deal I think, but when the screen loads, there is no background/desktop. SOMETIMES the desktop loads in the VNC screen, but it only shows a portion of the desktop, I'm not sure how to scroll around (say, to show my panels, or bottom right corner of the screen).

---

### Post by krunge on 2008-08-28
> **memories said:**
> 
First, keyboard input isn't working properly. It's as if the windows key/hyper key is being held down in the VNC screen. On my desktop, WinKey+t opens a terminal, for example, but on the VNC screen, just pressing 't' opens a terminal. Keys that aren't mapped get displayed properly.


If you, using a vncviewer to connect, tap both winkeys (left and right) does that eliminate the problem?  I.e. does that release a pressed down winkey? (also called Super_L and Super_R)

---

