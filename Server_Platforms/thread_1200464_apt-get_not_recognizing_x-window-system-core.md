---
title: "apt-get not recognizing x-window-system-core ?"
date: 2009-06-30
forum: Server Platforms
---

### Post by dragos2 on 2009-06-30
This is very strange, I have done some local testings in Virtual Box using the
same exact Ubuntu Server 8.04 64 bit and the below command worked with
no problems, now on the remote server that is a new install of Ubuntu Server 8.04
64 bit the command throws these errors:

$ sudo apt-get install x-window-system-core xserver-xorg gnome-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package x-window-system-core is a virtual package provided by:
  xorg 1:7.3+10ubuntu10.2
You should explicitly select one to install.
E: Package x-window-system-core has no installation candidate

Any ideas of what I did wrong ?

---

### Post by dragos2 on 2009-06-30
A little correction. In Virtual Box I have Server 9.04 64 bit so I think that
in the repository of 8.04 there is no x-window-system-core ?

If I do it like this in Server 8.04 it asks me if I want to install but I haven't tested
it locally yet to give an Y, so I said no.

sudo apt-get install xserver-xorg gnome-core

Will the command below be the same as 

sudo apt-get install x-window-system-core xserver-xorg gnome-core

?

---

### Post by kerry_s on 2009-06-30
it's just "xorg" now:

**sudo apt-get install xorg gdm gnome-core**

---

### Post by dragos2 on 2009-06-30
No gmd :D

It is weird, did it changed in 9.04 too ?

Is there xorg-core ?

---

### Post by dragos2 on 2009-06-30
Also, I don't like the look of 

xorg,

the look of  x-window-system-core xserver-xorg gnome-core is better for
what I need.

is there a way to achieve that look using xorg ?

---

### Post by kerry_s on 2009-06-30
> No gmd 

with out a login manager your going to get policykit hell, cause it won't recognize your logged in. you'll have to do a lot of work around's.

> Is there xorg-core ? 

no, theres xserver-xorg-core, but you should really use "xorg" or you might not get a working X.

> 
Also, I don't like the look of

xorg,

the look of x-window-system-core xserver-xorg gnome-core is better for
what I need.

is there a way to achieve that look using xorg ? 


i have no idea what you mean, X is a combination of many packages.

---

### Post by dragos2 on 2009-06-30
> **kerry_s said:**
> with out a login manager your going to get policykit hell, cause it won't recognize your logged in. you'll have to do a lot of work around's.


Hmm, I am mostly interested to get it working with nxserver, now I installed it
without gdm and I manually startx and its working almoust fine.

The reason that I would like to avoid gdm is that it replaces the text boot
which has a lot of useful info (I am using a PCI KVM board to see the boot
, change settings in bios remote etc).

But if you say that gdm is recommended I will install it since I want the server
functional for at least 2-3 years.

> **kerry_s said:**
> i have no idea what you mean, X is a combination of many packages

I will make some scrrenshots, but the interface from xorg is more polished than the
one from x-window-system-core xserver-xorg gnome-core, I don't want it with all
those effects.

But I am more interested of how to have a verbose gdm instead ?

---

### Post by dragos2 on 2009-06-30
I also like the ubuntu-desktop look but it is bloated with tons of applications,
and it seems that there is no ubuntu-desktop-core :(

---

### Post by kerry_s on 2009-06-30
if you was using this " x-window-system-core xserver-xorg gnome-core " it's from at least a year ago, there have been many changes since then.

> I don't want it with all those effects.


not sure what you mean there, the last time i used gnome-core there wasn't nothing fancy. i don't use gnome any more though, that policykit junk sucks, i now use xfce4 on debian testing. i installed a base system and built up from there, theres still polictkit, but it's not all integrated like it is in gnome, you don't have to click "unlock" just to do some simple thing.

anyways why use a desktop? sounds like you would be fine with just a window manager, then you can use your startx &  all that. sounds like you haven't used linux in a while, just play around with different things, get familiar. use this install as a test install, figure out what you want then do a fresh install with what you actually want.

---

