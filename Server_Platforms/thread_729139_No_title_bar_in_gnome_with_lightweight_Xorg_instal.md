---
title: "No title bar in gnome with lightweight Xorg install on Server 7.10"
date: 2008-03-19
forum: Server Platforms
---

### Post by Wavicle on 2008-03-19
First I apologize upfront if this is in the wrong place. It's my first post to ubuntuforums - be gentle!

I have a fresh install of Gutsy (that's 7.10 right?) Server 64 bit. For various reasons that I'm sure will offend most of you I needed to install Xorg, but I was NOT willing to install everything. So I did this:

```
sudo aptitude install xserver-xorg gnome-core gdm
```

The base x-windows system seems to get installed correctly, except that after logging in I have no window manager. Trying to do alt-f2 doesn't work because that too requires a window manager. I can open a terminal, start metacity manually and I get all the proper window bars.

I think I chased the problem down to a few lines in /usr/bin/gnome-wm:

```
# If not exist, set to compiz.
if [ ! -x "$DEFWM" ]; then
    gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/bin/compiz --type string
    DEFWM=/usr/bin/compiz
fi
```

The problem here is that I do not have compiz installed. Now I did fix the problem for me by using gconftool-2 to change my default to metacity (which is installed). In the general case I suppose I could fix the issue, for my particular system, by adding WINDOW_MANAGER="metacity" to /etc/bash.bashrc. However I am curious:

1. Are these "fixes" the best ones to make?
2. Is it a bug to have compiz the default wm when compiz is not installed? The code in question could easily contain a list of known window managers and search for the first one that actually exists.

---

### Post by crouton on 2008-03-21
Consider uninstalling gnome-core and using xfce-desktop instead.  It's a lightweight WM that does most of what you will need in a GUI on a server.

As for compiz, I thought that was a program that sat on top of gnome to handle desktop effects, but I could be wrong...

---

### Post by koenn on 2008-03-22
> **Wavicle said:**
>  However I am curious:
2. Is it a bug to have compiz the default wm when compiz is not installed? 

That piece of code says : if no default window manager is set (in the DEFWM variable), then use compiz.
It's maybe not the most failsafe solution, but you *are* using a gnome config that has been customized for use on Ubuntu desktop, and ubuntu/Canonical decided to have compiz enabled by default in its desktops - that's probably where this comes from. 

The obvious solution is to make sure you have your choice of window manager set a default; I'm not sure where and how.

Gnome may not be the best choice for a server GUI : it's a desktop environment, i.e a lot more than just a window manager. If all you need is something with windows and click thingies, consider xfce, fluxbox, ...

---

