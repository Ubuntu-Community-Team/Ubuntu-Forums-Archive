---
title: "Can't run ubuntu 17.10 in Virtualbox 5.2 (session freezes at login)"
date: 2017-11-02
forum: Virtualisation
---

### Post by Neffscape on 2017-11-02
Dear all,

I’m running ubuntu Mate 17.10 on a VirtualBox VM (version 5.2, with Guest Additions 5.2.1 manually downloaded by Oracle’s VirtualBox website). The system runs very fast and smoothly, even with many compiz effects enabled (3D cube, rotate etc). However, because I really would like to try the new ubuntu desktop (gnome shell), I manually installed the ubuntu-desktop package and chosed gdm3 as default login manager.

This time everything went wrong. Gdm doesn’t display the login field, and if I try to log in using lightdm, the graphic session freezes showing a purple background and the mouse pointer, but refusing to load gnome shell.

I tried several times logging in, using xorg instead of wayland and I eved decided to start with a fresh installation of ubuntu, using the official 17.10 ubuntu iso, but the same thing happens after I install VB Guest Additions.

At this point, I really think there’s a compatibility issue with GNOME shell, Gdm3 and VirtualBox Guest additions 5.2.1.
Btw, I tried to install other versions of VirtualBox guest additions (5.2 and even the included 5.1 in the ubuntu repositories aka virtualbox-guest-additions-iso package).

Did somebody manage to install ubuntu 17.10 in VirtualBox?

Thanks in advance for your help and for your kind support.

Neff

---

### Post by ajgreeny on 2017-11-02
Yes I have 17.10 running on VBox; it worked fine on VBox 5.2.0 but other VMs did not (Debian 9), so I returned to VBox 5.1.30.

I have it working very fast using 4GB RAM out of my 8GB total on my Xubuntu 16.04 64bit host, and using the 5.1.30 guest additions, and it is using all the default settings after boot, ie wayland graphics system, not X11, and the tweaked gnome DE that comes out of the box.

So far I like it a lot; better than the 17.04 Ubuntu-Gnome version I also have as a VM.

---

