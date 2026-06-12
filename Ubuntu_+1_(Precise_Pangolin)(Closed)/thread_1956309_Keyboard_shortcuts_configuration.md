---
title: "Keyboard shortcuts configuration"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ayozito on 2012-04-10
Hi!

First of all I'm using Gnome 3.4 and compiz is uninstalled.

I have some actions configured on shortcuts like for example move with window or show desktop that aren't working. For example for move with window I have SUPER + direction however the one that is working is CTRL + SHIFT + ALT + direction. For show desktop I have SUPER + D but either this one or CTRL + ALT + D aren't working.

According to that, there must be any other place where I can change this kind of options, because how can be possible that I have an action configured as SUPER + dir and work as CTRL + ALT + SHIFT + dir??

If I had compiz installed there would be the place. But as I said, I have it uninstalled (and all related packages)

It is only happening on 12.04. On 11.10 or in Mint 12 just modifying the shortcuts inside keyboard menu is working great.

---

### Post by jbicha on 2012-04-10
This has been answered a few times already. Basically, GNOME Shell uses gsettings for keyboard shortcuts but Ubuntu has patched System Settings to still set gconf shortcuts (which work in Unity, Unity 2D and the GNOME Classic sessions). You can install dconf-editor and manually set shortcuts. Look in org.gnome.desktop.wm.keybindings.

If nobody beats me to it, I'm going to fix several of the gsettings shortcuts to match what's used in Unity in 12.04.

---

### Post by ayozito on 2012-04-11
Ok I did it! But I'm 100% sure that on 11.10 or Mint 12, using Gnome Shell on both, I hadn't to do this.

---

### Post by jbicha on 2012-04-11
Right, this is a problem with GNOME Shell 3.4 in Ubuntu 12.04. It was not a problem with Ubuntu 11.10 and won't be a problem with 12.10 either.

---

### Post by ayozito on 2012-04-11
And I'm wondering... why should be it a problem on 12.04? is still beta so they can fix it before final release.

---

### Post by jbicha on 2012-04-11
It's a difficult problem that is very unlikely to be fixed for Ubuntu 12.04. Unity uses gconf for keyboard shortcuts and it was determined that it was too risky (and/or not enough developer time) to convert Unity's keyboard shortcuts to gsettings for this LTS release.

While someone could compile gnome-settings-daemon and gnome-control-center without the gconf keyboard shortcut patches, System Settings then wouldn't be able to control keyboard shortcuts for Unity, Unity 2D, or the GNOME Classic sessions. Therefore, it breaks things too much to go into the normal GNOME3 PPA.

---

