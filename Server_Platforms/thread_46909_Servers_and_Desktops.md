---
title: "Servers and Desktops"
date: 2005-07-06
forum: Server Platforms
---

### Post by ZephyrXero on 2005-07-06
Does the server version of Ubuntu come with some sort of Desktop Environment, or is it completely command line?

If so...which DE should I use? I'm building a small webserver with some old parts. Pentium2 400Mhz w/ 256MB of RAM... I've heard lots of good stuff about XFCE. I'll also be hosting a radio station off this machine, so a good portion of my processor will probably go into transcoding and such. Thanks for any tips :)

---

### Post by nocturn on 2005-07-07
The server installation does not install a graphical environment (this makes sense on most servers).

If you do want it, look at something lite like Xfce.  There is a howto on this forum to install Xfce without Gnome, it starts from the server install, so it should be helpful to you.

---

### Post by notos on 2005-07-07
well i recomed you use only the command line because its fun!!! :P

but if you want to install a minimal DE

sudo apt-get install x-window-system-core [Desktop/WM] [DisplayManager]

for example for a XFCE plug GDM you could use

sudo apt-get install x-window-system-core xfce4 gdm

i think you can remove the Display manager and use startx command :)

---

