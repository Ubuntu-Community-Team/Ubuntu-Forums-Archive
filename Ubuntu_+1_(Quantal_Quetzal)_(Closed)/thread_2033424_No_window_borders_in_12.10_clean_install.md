---
title: "No window borders in 12.10 clean install"
date: 2012-07-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Jimmyfj on 2012-07-26
Now I have this strange problem with 12.10 QQ every time I install the system to my hard drive.

The install itself is running flawless all the way, but when I start using the system, after installing the GNOME-Shell and logs in to the GNOME Classic I have no window borders, AT ALL. 

I have tried numerous settings in Compiz Fusion, none of which gives me the borders back. This is the nVidia driver is this this one:

NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012

And here comes the tricky part: I do not have the problem with my 12.04 install. Neither does the problem appear if I run 12.10 in a VB. Borders and all are as usual in the VM no matter if I choose Unity, Gnome 3, Gnome Classis. 

Any idea where I should be looking for my window borders?

---

### Post by dino99 on 2012-07-26
either purge then reinstall compiz* or use dconf

---

### Post by lonniehenry on 2012-07-26
Gnome-shell uses mutter, not compiz.  Try adding gnome=tweak-tool and trying some of the settings there.

---

### Post by mc4man on 2012-07-26
> **Jimmyfj said:**
> Now I have this strange problem with 12.10 QQ every time I install the system to my hard drive.

The install itself is running flawless all the way, but when I start using the system, after installing the GNOME-Shell and logs in to the GNOME Classic I have no window borders, AT ALL. 
Any idea where I should be looking for my window borders?

Easiest way is to install compizconfig-settings-manager, run it & enable window decoration & possibly a whole lot more.

```
sudo apt-get install -y compizconfig-settings-manager && ccsm


```
At least here I've seen where gnome classic can have no compiz plugins enabled at all. (& I mean None
Ex. - created a new user, logged in to classic - see screen, while a limited view of ccsm there aren't any plugins enabled at all.
( at a min you'd likely want 
window decoration, place, resize, move,  composite, opengl, workarounds, viewport switcher,
(window deco is in the Effects section

---

### Post by dino99 on 2012-07-26
but be aware:

This tool allows you to deeply configure Compiz's settings. Some options may be incompatible with each other. Unless used with care, it is possible to be left with an unusable desktop. :o

---

### Post by arpanaut on 2012-07-26
> NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012This driver has proven to be faulty with unity 3d, you need to log into 2d session and update to nvidia-current-updates 295.49 or get edgers ppa and update to what is there.

That solved it on my 64bit lappy on 12.04. lack of disk space has kept me from trying12.10 there.

---

### Post by mc4man on 2012-07-26
> Quote:
NVIDIA UNIX x86_64 Kernel Module 295.40 Thu Apr 5 21:37:00 PDT 2012 

> **arpanaut said:**
> This driver has proven to be faulty with unity 3d, you need to log into 2d session and update to nvidia-current-updates 295.49 or get edgers ppa and update to what is there.

That solved it on my 64bit lappy on 12.04. lack of disk space has kept me from trying12.10 there.
nice picking up on that, have to wonder if the OP is actually using 12.10 
& if so where is that package coming from...

---

### Post by arpanaut on 2012-07-26
Must have installed it manually?
As I now see that nvidia-current in 12.10 is 302.17

Interesting?

---

