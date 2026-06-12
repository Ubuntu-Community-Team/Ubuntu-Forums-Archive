---
title: "Custom shortcuts stopped working"
date: 2013-03-09
forum: Ubuntu Development Version
---

### Post by zika on 2013-03-09
Is it only me (i.e. my machine) or someone else has problems with custom shortcuts?
In GnomeShell and its derivatives (fallback) even non-custom do not work...
I have ricotz and G3 PPAs turned on...

---

### Post by midfingr on 2013-03-09
Hi,
Do you mean custom launchers, sim links and specifically Gnome shell + fallback?

I can no longer create a custom launcher in 13.04 alpha (Unity) due to nautilus. Drag and drop web links onto the desktop work fine however.

---

### Post by zika on 2013-03-10
> **midfingr said:**
> Hi,
Do you mean custom launchers, sim links and specifically Gnome shell + fallback?

I can no longer create a custom launcher in 13.04 alpha (Unity) due to nautilus. Drag and drop web links onto the desktop work fine however.
I mean: In gnome-control-center/keyboard there are two groups of shortcuts: one with 8 subgroups of „fixed“ and a group „Custom“. Those „Custom“ stopped working. They do not work either in GnomeShell (and its daughters: fallback, etc.) and in Unity. They worked nicely up to yesterday... I can change them, but they simply do not respond...

---

### Post by zika on 2013-03-10
It seemed that I've now lost even Ctrl-Alt-T (terminal) but it is back...
For example Alt-F2 and such are working... None of Custom Shortcuts is working...
Never mind Awesome is there to save a day... ;)

---

### Post by midfingr on 2013-03-10
Ah, I see. Strange behavior. I haven't lost any keyboard shortcuts 'yet'. Although I completely lost the date/time application and had to re-install it--lol!

---

### Post by zika on 2013-03-11
I will welcome any idea about what packages to reinstall to get shortcuts back... ;)

---

### Post by zika on 2013-03-11
Partial success: I have regained use of my shortcuts in Gnome shell. In fallback(with or without compiz) and unity no luck still... I can not report now how I did that because I changed themes and some other stuff. Once I get real picture what causes shortcuts to stop working I will report here. So, it is not (as many times up to now) borked system it is just a battle between unity, GS, and others... Self-inflicted od course, if I were to follow vanilla path with Ubuntu (unity) I would have escaped this problem, but would have learned less and...

---

### Post by mc4man on 2013-03-11
On a new install the other day with gnome3 & gnome3 staging ppa's custom shortcuts were fine in Gs but broke in a ubuntu (unity) session with upgrades to g-s-d & g-c-c, which one don't know, they're joined at the hip..

---

### Post by zika on 2013-03-11
> **mc4man said:**
> On a new install the other day with gnome3 & gnome3 staging ppa's custom shortcuts were fine in Gs but broke in a ubuntu (unity) session with upgrades to g-s-d & g-c-c, which one don't know, they're joined at the hip..I did not understand Your message on the first reading... I think I'm getting a grip and this evening I'll be able to decipher it... I'll have to look in g-s-d and g-c-c changelogs...

---

### Post by mc4man on 2013-03-11
sorry - 
g-s-d = gnome-settings-daemon
g-c-c = gnome-control-center

(being a 2 finger typist I look for the short way

---

### Post by zika on 2013-03-11
> **mc4man said:**
> sorry - 
g-s-d = gnome-settings-daemon
g-c-c = gnome-control-center

(being a 2 finger typist I look for the short way
I figured that, I just have to see (hopefully in changelogs) what happened...
It is a bit time consuming since gnome-tweak-tool works (literally) in GS only and similar stuff...
And I do not have enough spare time on my hands at this moment... ;)
After decades of working with mouse, I finally got a hold of a trackball and I'm getting used to it (no scroll)... My learning curve is much better than I thought it would be...
Update&#8321;: Most interesting thing is that I've discovered this a second before I would have started ppa-purge for Gnome3+ricotz in an effort to regain shortcutkeys... So, I remain GS user even better because of the fact that Alt-< works nicely here and in Unity I have to struggle with HUD to regain that combination... Yes, Unity got many new shortcuts, but I need mine... ;)
Update&#8322;: It seems that it also has to do something with GDM... LightDM does not make that trouble with GS, Unity is still to be checked again... StartX works with GS, now, Unity is also to be checked...
(I mean custom shortcutkeys, to be precise, everything other works fine... for now... knock-knock-knock...)

---

### Post by quazi on 2013-03-11
I have a similar problem running Unity. Under Keyboard in the settings, I can make a custom shortcut, which then works fine. Subsequently however, the shortcut doesn't seem to work until I reset the accelerator. This is annoying.

---

### Post by zika on 2013-03-11
> **quazi said:**
> I have a similar problem running Unity. Under Keyboard in the settings, I can make a custom shortcut, which then works fine. Subsequently however, the shortcut doesn't seem to work until I reset the accelerator. This is annoying.What do You mean by „accelerator“...?

---

### Post by quazi on 2013-03-23
I mean reset the key combination that activates the hotkey: 
[img]http://i.imgur.com/IKivqHSl.jpg[/img]

---

### Post by zika on 2013-03-26
It seems that scope-activity is more important than shortcuts... ;)
Just to report that shortcuts do not work still... ;)
One scope could help this I hope...
In GnomeShell they work if I load gnome-settings-daemon which, ironically, comes from the place that should work in Unity, I guess...

---

### Post by mc4man on 2013-03-26
> **zika said:**
> It seems that scope-activity is more important than shortcuts... ;)
Just to report that shortcuts do not work still... ;)
One scope could help this I hope...
In GnomeShell they work if I load gnome-settings-daemon which, ironically, comes from the place that should work in Unity, I guess...

If you're using any of the gnome3 ppa's then breakage in an ubuntu session would be quite likely, the extent of which would depend on what was upgraded.
If custom shortcuts are broken in a non ppa install then that would be something to fix in 13.04, though they work fine here & I assume most others not using ppa packages

Post 13.04 Ubuntu will need to deal with reconciling gnome-3.8 & an ubuntu session, atm they don't work well together at all.
(in particular g-c-c, g-s-d & nautilus, if keeping.

---

### Post by zika on 2013-03-26
> **mc4man said:**
> If you're using any of the gnome3 ppa's then breakage in an ubuntu session would be quite likely, the extent of which would depend on what was upgraded.
If custom shortcuts are broken in a non ppa install then that would be something to fix in 13.04, though they work fine here & I assume most others not using ppa packages

Post 13.04 Ubuntu will need to deal with reconciling gnome-3.8 & an ubuntu session, atm they don't work well together at all.
(in particular g-c-c, g-s-d & nautilus, if keeping.You're quite right... I hoped that Unity and GnomeShell were kept sort of separate, but it seems I was wrong... Nevertheless I imagine that this is not a big deal since it sort of works cross-over style... I'll stand in my corner corrected and will not raise this question until/when I do ppa-purge of all GS stuff... Or I will wait for rolling time...

---

### Post by mc4man on 2013-04-06
One thing I did notice is that in a gnome session many shortcuts don't work unless a window is open (assuming no fm handling desktop, ie. show-desktop-icons false

---

### Post by leonid870721 on 2013-10-09
My (one and only) shortcut was working fine until just a moment ago! Tried resetting the accelerator to no avail. I also discovered that my calculator special key (my keyboard has one) doesn't work too, but dash (Windows) key works fine, as do all the regular shortcuts (terminal, Alt + TAB etc.).

---

### Post by mc4man on 2013-10-09
> **leonid870721 said:**
> My (one and only) shortcut was working fine until just a moment ago! Tried resetting the accelerator to no avail. I also discovered that my calculator special key (my keyboard has one) doesn't work too, but dash (Windows) key works fine, as do all the regular shortcuts (terminal, Alt + TAB etc.).

Maybe see here - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1237564](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1237564)

I've tracked it down **here **to 'gnome-screensaver' not being installed with the new gnome-settings-daemon package

---

### Post by leonid870721 on 2013-10-10
> **mc4man said:**
> Maybe see here - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1237564](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1237564)

I've tracked it down **here **to 'gnome-screensaver' not being installed with the new gnome-settings-daemon package

That explains it, since I have xscreensaver! Thank you for the info!

The shortcuts are back after a reboot, though, let's see how long it takes them to fail again. They worked for over a month.

ps.: I'm using Ubuntu 13.04.

---

