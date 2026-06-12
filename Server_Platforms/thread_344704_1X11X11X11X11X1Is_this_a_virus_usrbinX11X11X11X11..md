---
title: "1/X11/X11/X11/X11/X1Is this a virus? /usr/bin/X11/X11/X11/X11..."
date: 2007-01-23
forum: Server Platforms
---

### Post by joseantmm on 2007-01-23
I have discovered that I have a folder X11 repeated ad infinitum. Is this a virus/worm?

usr/bin/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11

---

### Post by jr.gotti on 2007-01-23
Hmm...

Go into the first X11 folder that is EMPTY (Make sure you dont delete anything important,) and run "sudo rm -r *"

Then check in awhile to see if they're all back. If not...it was prolly just a stupid script you ran. If they are back, check your cron files for that stupid script. lol

---

### Post by chavo on 2007-01-23
/usr/bin/X11 is a symlink to /usr/bin, it is there for compatabilty sake. It is no longer used by the latest versions of xorg, but some older apps might try to write there. 
The reason you see the redundancy is that when you change to the folder /usr/bin/X11 it is still pointing to itself. It's a little confusing, but not a bug or virus.

---

### Post by joseantmm on 2007-01-23
Hi and thanks for the quick replies. Actually, none of the repeated X11 folders are empty: they all have repeat the very same files. Do you still think I should delete them?

---

### Post by kerry_s on 2007-01-23
> **joseantmm said:**
> Hi and thanks for the quick replies. Actually, none of the repeated X11 folders are empty: they all have repeat the very same files. Do you still think I should delete them?

No, your not getting it, it's a short cut to the folder your looking at so when you click the short cut it brings you back to the same folder over and over. If you delete it will screw up applications that look for executables in /usr/bin/X11/(executable) in stead of /usr/bin/(executable).

/usr/bin/X11/(executable) <-old way-kept for  applications that still use it
/usr/bin/(executable)<-new way where the applications should be looking.

Short verse- DON"T DELETE

---

### Post by Catsworth on 2007-01-23
Man that's just fracked up :) 

A recursive shortcut :lolflag:

---

### Post by joseantmm on 2007-01-23
Ok, I got it and will leave them alone. Now I am wondering if what Chavo said has anything to do with an unsolved problem I have, to wit:

Any change I make to the etc/X11/xorg.conf seems not to be applied and when I do a $ sudo setxkbmap -layout, my xorg.conf file is changed. I have been trying to solve this for weeks now, with no results. 

The thing is that my laptop has an English keyboard but I need it to be able to write Spanish accented characters with the help of the right alt key. Any idea of what's happening? I copy below my xorg.conf. And thanks again.

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "thinkpad"
Option "XkbLayout" "es"
Option "XkbVariant" "sundeadkeys"
Option "XkbOptions" "lv3:ralt_switch"

---

### Post by kerry_s on 2007-01-23
Any changes in xorg.conf requires a X restart(ctrl+alt+backspace) to take effect.

---

