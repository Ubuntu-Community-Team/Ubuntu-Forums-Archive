---
title: "*REQUEST* InitNG"
date: 2005-06-23
forum: Ubuntu Backports
---

### Post by Gnobody on 2005-06-23
We need initNG!  This will half our boot times!!  :razz: 


[Click Me!](http://gentoo-wiki.com/Initng)

---

### Post by Burgundavia on 2005-06-23
Ok, there are 2 things wrong with this. (Well maybe there are more)

1. Backports are not the place to ask for such low level stuff
2. Init-ng is seriously untested, and maybe considered for Breezy+1
3. Breezy does not have init-ng

Corey

---

### Post by jdong on 2005-06-23
Corey, that's 3 ;) LOL

What he said. I've installed initng on a test machine before... In its current state, it's more of a Gentoo toy than anything else... Supporting initng will require a complete rewrite of all init scripts on the system.. not something I can do... heck not something Ubuntu can do for quite a while.

---

### Post by 8FootSativa on 2005-06-25
There are Debian packages for InitNG...I've wanted to try it but I'm worried it will bork things.

[http://forum.initng.thinktux.net/viewtopic.php?t=29](http://forum.initng.thinktux.net/viewtopic.php?t=29)

---

### Post by Burgundavia on 2005-06-25
InitNG requires a whole lot of changes, at a very low level. That is not the kind of thing I would undertake unless you know the boot sequence forward and backward.

Corey

---

### Post by AndersAA on 2005-06-25
[QUOTE=Burgundavia]InitNG requires a whole lot of changes, at a very low level. That is not the kind of thing I would undertake unless you know the boot sequence forward and backward.

Corey[/QUOTE]

[QUOTE=jdong]What he said. I've installed initng on a test machine before... In its current state, it's more of a Gentoo toy than anything else... Supporting initng will require a complete rewrite of all init scripts on the system.. not something I can do... heck not something Ubuntu can do for quite a while.[/QUOTE]

current svn (and the latest version) should boot an ubuntu system without any modification needed to any scripts. (I'm neuron, one of the ubuntu dev's)

---

### Post by 8FootSativa on 2005-06-25
[QUOTE=AndersAA]current svn (and the latest version) should boot an ubuntu system without any modification needed to any scripts. (I'm neuron, one of the ubuntu dev's)[/QUOTE]

So I can just install the .deb and boot using InitNG? No  changing Grub or anything? I'd like to try it on my Kubuntu box...

---

### Post by AndersAA on 2005-06-25
[QUOTE=8FootSativa]So I can just install the .deb and boot using InitNG? No  changing Grub or anything? I'd like to try it on my Kubuntu box...[/QUOTE]

you will have to modify grub manually

---

### Post by 8FootSativa on 2005-06-25
[QUOTE=AndersAA]you will have to modify grub manually[/QUOTE]

O-tay.  :)

---

### Post by Gnobody on 2005-06-25
I get a bunch of errors on boot and I get "failed to initialize HAL daemon" when I log in to Gnome.  This is with the latest SVN build of InitNG.

---

### Post by tristan on 2005-06-26
I had a play with v0.1.3 of initNG and while it did speed up boot times a bit (not dramatically), I also had the dbus/hald problem which prevents gnome-volume-manager from working (ie no removable media automounting).

Looks like promising software, but I think it might be a  bit immature to replace init on the next release of ubuntu....

---

### Post by AndersAA on 2005-06-26
[QUOTE=Gnobody]I get a bunch of errors on boot and I get "failed to initialize HAL daemon" when I log in to Gnome.  This is with the latest SVN build of InitNG.[/QUOTE]

"bunch of errors on boot" doesn't really tell me much...

[QUOTE=tristan]I had a play with v0.1.3 of initNG and while it did speed up boot times a bit (not dramatically), I also had the dbus/hald problem which prevents gnome-volume-manager from working (ie no removable media automounting).

Looks like promising software, but I think it might be a  bit immature to replace init on the next release of ubuntu....[/QUOTE]

should be fixed in svn atleast.


and it's defenatly not ready to replace sysvinit

---

### Post by kamstrup on 2005-06-26
[QUOTE=Gnobody]I get a bunch of errors on boot and I get "failed to initialize HAL daemon" when I log in to Gnome.  This is with the latest SVN build of InitNG.[/QUOTE]
 Same here. But it *almost* works :D It is very fast indeed, but it doesn't work after I reboot. - Have to reboot with ordinary init to get it working again.

I totally agree with the backporters. This is not exactly backport material...

---

