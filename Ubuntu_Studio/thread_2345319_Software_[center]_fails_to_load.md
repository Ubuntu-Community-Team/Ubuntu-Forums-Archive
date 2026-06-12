---
title: "Software [center] fails to load"
date: 2016-12-02
forum: Ubuntu Studio
---

### Post by jimmypants on 2016-12-02
Hello, I have a fresh install of Ubuntu Studio 16.04.1 on a Lenovo T530 with i7 processor and 16 GB RAM.

After performing the recommended updates, the Software center does not load from links in the Start menu.  It comes up briefly, then crashes after a few seconds.  No app / package icons appear -- the skeleton of the GUI is blank.

...so I tried to load it from terminal (I hope I did it right...) and here is the error code generated:

```
jimmy@Linux-TP-T530:~$ gnome-software
```

```
(gnome-software:3418): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:3418): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:3418): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:3418): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:3418): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:3418): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed

(gnome-software:3418): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-weather.png': Error opening file: Too many open files

(gnome-software:3418): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-weather-bg.png': Error opening file: Too many open files

(gnome-software:3418): GLib-ERROR **: Creating pipes for GWakeup: Too many open files

Trace/breakpoint trap (core dumped)
```

I am a clueless newbie to Linux.
Any ideas on how to fix this?

---

### Post by jimmypants on 2016-12-02
Woohoo!!!  Yes!

**A software update for "Software"** (i.e. Gnome software center) [B]just appeared in "Software Updater" within the last hour or so.
I applied the update, and it has fixed my problem![/B]

Thank you to the developers!

This means a great deal to a newbie like me.  I spent most of this week looking at a bunch of other OS because I did not know whether I could trust Ubuntu Studio if the Software Center did not even work correctly.  I was especially checking out Xubuntu, Manjaro and Linux Lite.  Now, to figure out why my mouse sometimes disappears and why my wifi indicator sometimes goes from active symbol to double arrows and its controls get greyed-out...

---

