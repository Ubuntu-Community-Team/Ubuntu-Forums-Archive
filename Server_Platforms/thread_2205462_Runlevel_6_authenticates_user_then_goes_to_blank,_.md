---
title: "Runlevel 6 authenticates user then goes to blank, grey screen with no menus"
date: 2014-02-14
forum: Server Platforms
---

### Post by TimeHorse on 2014-02-14
I installed the latest Ubuntu Server this morning before spending 5 hours shoveling snow and it took a while to get Apache to work again and still need to remember to add Chrome back to the list of package sources but that's neither here nor there.

My issues is the most infuriating one of booting to X, logging in, then being faced with a totally grey background with no menu bar, no windows, just a hidden item in the upper right to shut-down or restart, change volume or turn on accessibility options.  What's more, I can't even right-click a menu.  So it's impossible to get a terminal under X.  I can get to the TTY consoles just fine, I can SSH in and run tunneled X apps just fine, but my desktop is FUBAR.  I've searched all over the Internet, installed all kinds of window managers, tried gnome and lightwm, nothing seems to install menus or enable right-click menus.  Help!

---

### Post by ian-weisser on 2014-02-15
It won't work on runlevel 6.

Here's the start stanza from /etc/init/lightdm.conf. It shows the conditions under which lightdm should start. It's an example, lots of other important system code has similar conditions :
```
start on ((filesystem
           and **runlevel [!06]**    <---- start on runlevels 1-5. Not 0 or 6.
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)

```

I suppose you could change all the Upstart and SysV runlevel conditions, but your changes will be overwritten by each update.
A fresh install of Ubuntu operates at Runlevel 2. Runlevels 3-5 are unused (available). 6 usually is used for reboot. See [http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

### Post by TimeHorse on 2014-02-15
Sorry, yes, it is Runlevel 2.  I recall Runlevel 5 is what I used to use back in the 1990s and conflated that up a number but my Server is configured Runlevel N 2.  But the problem still stands: I authenticate, the login prompt disappears and I can do absolutely nothing.  The X11 screen has no menus, no right-click, no left-click, no middle click menus.  Just a hidden power off, accessibility and volume menus in the upper-right corner.  Changing window managers does nothing.  All I can do is switch to a TTY on 1-6 and do command line stuff.  It's very frustrating.

---

### Post by steeldriver on 2014-02-16
How are you "booting to X"? are you using a display manager (lightdm? gdm?) and if so what desktop session are you choosing?

---

### Post by TimeHorse on 2014-02-19
Yes, I have it boot to X.  Tried setting lightdm with the gdm reconfigure but it seems stuck on gdm.  I've tried all 7 or so desktop sessions and they all have the same result.  It's most perplexing.

---

### Post by brokenhachi on 2014-02-20
Tried uninstalling lightdm and then reconfigure gdm and gnome? 
```
sudo apt-get purge lightdm
sudo dpkg-reconfigure gdm && sudo dpkg-reconfigure gnome
```

---

