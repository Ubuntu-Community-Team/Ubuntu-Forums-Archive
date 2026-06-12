---
title: "compiz segfault with 0.9.8+bzr (from proposed)"
date: 2012-06-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-06-26
Updated Compiz from proposed. Segfaults. Is it just me? :D

Running gnome-fallback (with effects). Metacity works as normal (good job). Will try Unity [s]and gnome-shell[/s] in a bit, though I can't see Unity working if standalone Compiz segfaults. [edit 1] gnome-shell works fine. [edit 2] Unity also works fine. It's just gnome-classic. Hmm... might be a PPA thing...

Catalyst 12.6 beta (fglrx 8.980), 3.4 kernel, xserver 1.11.

```
compiz:
  Installed: 1:0.9.8+bzr3249-0ubuntu1
  Candidate: 1:0.9.8+bzr3249-0ubuntu1
  Version table:
 *** 1:0.9.8+bzr3249-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1:0.9.7.8-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages

```

---

### Post by ScislaC on 2012-06-27
Thankfully not seeing it, using the NVIDIA driver from xorg-edgers ppa.

---

### Post by cecilpierce on 2012-06-29
Just did aptitude safe-upgrade and compiz won't change workspaces with the mouse or key board, only the workspace switcher, anyone else ?

:confused:

---

### Post by jfernyhough on 2012-06-29
That can happen when an upgrade comes through that resets the Compiz settings to make sure Unity will load. Just go back into CCSM and check the screen edges for Expo.

---

### Post by cecilpierce on 2012-06-29
Here is what it looks like, what an I suppose to do to screen edge ?

---

### Post by jfernyhough on 2012-06-29
So, if you want to show all desktops by pointing to the top left, click on the top left red bit to turn it green. Super-e should also work by the looks of it.

---

### Post by cecilpierce on 2012-06-29
OK, I tried that (right screen) and it brings up the 4 screens and I can use the mouse wheel to select but I use to be able to just use the wheel by it self to switch screens ???

Thanks for the help  ):P

---

### Post by cecilpierce on 2012-06-29
Just checked my other QQ and the mouse wheel switches work spaces and the new update take out compiz plugins and put in a new and crappy one ! 
:lolflag:

---

### Post by jfernyhough on 2012-06-29
Ah, the plugin you need to activate for this one is Viewport Switcher. Check Desktop-based Viewport Switching, Move Next and Move Prev need to be set to match your mouse's wheel (probably button 3 and button 4).

---

### Post by mc4man on 2012-06-29
> **cecilpierce said:**
> Just checked my other QQ and the mouse wheel switches work spaces and the new update take out compiz plugins and put in a new and crappy one ! 
:lolflag:
The plugins per package have been changed & installing ccsm no longer pulls in any additional plugin packages

So many that would have previously been seen need you to explicitly install - "compiz-plugins"

---

