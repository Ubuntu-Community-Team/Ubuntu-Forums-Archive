---
title: "How to boot to a command line?"
date: 2005-11-12
forum: Server Platforms
---

### Post by oborysm on 2005-11-12
I have Breezy 5.10 (Gnome) installed and running nicely... but how do I get it to boot to a command line? I tried a few things already and had difficulty; note my previous post:

[http://ubuntuforums.org/showthread.php?t=88979](http://ubuntuforums.org/showthread.php?t=88979)

Note that I don't want to remove the GUI components and I don't want to reinstall in server mode - I just want to boot to a command line by default. 

Is this possible?

thanks

---

### Post by Juippisi on 2005-11-12
Of course. Install BUM (apt-get install bum), then launch it with (sudo bum). Look for the GDM on every tab and disable it. !BE CAREFUL! - if you disable something important, your system wont boot in the worst case.

You can also try apt-get remove gdm

If you want to start Gnome, command "startx /usr/bin/gnome-session".

---

### Post by oborysm on 2005-11-12
Doesn't Ubuntu provide a simple way to boot to a command line? 

[QUOTE=Juippisi]Of course. Install BUM (apt-get install bum), then launch it with (sudo bum). Look for the GDM on every tab and disable it. [/QUOTE]

Tried that, still didn't work. Now I've tried several different methods of disabling gdm - rcconf, bum, update-rc.d. All of them remove the gdm symlinks from the init scripts, which always borks my Ubuntu (see my previously linked post to the Installation forum).

It starts to boot, then hangs shortly after entering run level 2. I can't get it to boot successfully until I restore the gdm entries. 

Is that how Ubuntu is supposed to react when gdm is disabled? or do I have something else wrong with my config?

And if I apt-get remove gdm, that uninstalls gdm, right? I don't want that. I want to be able to start Gnome when I want to. 

thanks

---

### Post by Juippisi on 2005-11-12
[QUOTE=oborysm]And if I apt-get remove gdm, that uninstalls gdm, right? I don't want that. I want to be able to start Gnome when I want to. [/QUOTE]

Umm, I said "If you want to start Gnome, command "startx /usr/bin/gnome-session"."

And, you can try a little trick. Can you log on into a console from the GDM? Because on KDM you can. And KDM starts the previous session, which would be console after that. Try it, if it doesn't work, then I don't know.

And Ubuntu should be booting even if you have GDM/KDM disabled, because I didn't use those for a long time. Actually just installed KDM.

---

### Post by Wide on 2005-11-12
Just install "rcconf" run it & choose what run level you like to boot to

You just need to startx if you want X:)

---

### Post by oborysm on 2005-11-12
Thanks... I may have some other config problem. I did apt-get remove gdm, and reboot still hangs on runlevel 2. There is another post that indicates this boot problem may be somehow related to an nvidia driver - bizarre! 

[http://ubuntuforums.org/archive/index.php/t-77588.html](http://ubuntuforums.org/archive/index.php/t-77588.html)

...ughhh.. now I have to get my head around this nvidia driver issue and see if that's really the problem. 

Yes, I can log onto a console... I have openssh and freenx installed, so even when the Ubuntu boot is hanging I can remote into the Ubuntu box into a command line or even the desktop - that's how I keep restoring it.

---

