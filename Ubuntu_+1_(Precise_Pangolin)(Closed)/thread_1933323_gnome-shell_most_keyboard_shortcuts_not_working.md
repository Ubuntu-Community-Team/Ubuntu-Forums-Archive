---
title: "gnome-shell most keyboard shortcuts not working"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by travishume on 2012-02-29
Jumped onto the precise band wagon tonight (which I usually do around beta time) and my gnome-shell keyboard shortcuts stopped working. Specifically, Ctrl+Alt+t no longer opens a terminal, my maximization shortcuts no longer work, navigation shortcuts don't work. I've defined and redefined them in the shortcut editor w/out luck.

Strangely enough, custom app shortcuts do work.

Running gnome-shell v3.3.90 on a Lenovo Thinkpad 410s.

---

### Post by jbicha on 2012-02-29
The problem is that gnome-shell 3.4 has switched to gsettings/dconf for its keyboard shortcuts but Unity still uses gconf. System Settings in Precise was patched to support gconf but it ought to support gsettings also (or at least when GNOME Shell is running).

---

### Post by travishume on 2012-02-29
Thanks for the explanation. That sounds like it doesn't work and it isn't going to work anytime soon.

---

### Post by travishume on 2012-02-29
Thanks to your reply I was able to track down a solution. It's possible to use dconf-editor to set keybindings in org.gnome.desktop.wm.keybindings

:D

---

### Post by pedro.nariyoshi on 2012-03-03
Good to hear that. 

Hey jbicha, is there any chance the keyboard shortcuts will be able to be changed through the keyboard application instead of dconf? For some reason, G-S 3.3 performs much better than 3.2 in my computers.

---

### Post by jbicha on 2012-03-03
Pedro, yes, it's definitely possible as it's a bug that it doesn't work. It just needs someone to fix the gnome-control-center patches so that they support GNOME Shell 3.3, at least when run in GNOME Shell 3.3. It's been pretty busy with the UI freeze, beta 1, etc. so no one has got to it yet. Contributions are of course welcome!

---

### Post by pedro.nariyoshi on 2012-03-03
I have never dealt with any Gnome stuff. I'm assuming gnome-control-center is written in C. I have some experience with C (a little C++ and Java).

How could I get involved?

---

### Post by lucazade on 2012-03-26
this issue is still present.. any bug report for this?

---

### Post by jbicha on 2012-03-26
I don't think there's a bug specifically for this yet.

---

### Post by lucazade on 2012-03-26
should I file a new one against gsettings-desktop-schemas or gnome-shell?

---

### Post by jbicha on 2012-03-26
File it against gnome-control-center.

---

### Post by lucazade on 2012-03-27
thanks jbicha...
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965921](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965921)

---

### Post by Bazon on 2012-03-29
> **travishume said:**
> Thanks to your reply I was able to track down a solution. It's possible to use dconf-editor to set keybindings in org.gnome.desktop.wm.keybindings

:D
Thanks, that helped me as well!
*bookmark*

---

### Post by Bazon on 2012-03-29
PS:
What's the name for the right Super Key there in dconf? 
(I don't have a left one...)

---

