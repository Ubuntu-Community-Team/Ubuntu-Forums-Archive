---
title: "ctrl+space not working (what is intercepting it?)"
date: 2014-02-23
forum: Ubuntu Development Version
---

### Post by buntuyu on 2014-02-23
I just upgraded to 14.04 and something is hijacking my ctrl+space. I am seeing this in the center of my screen when I press the keys, before releasing Ctrl:  [http://www.flight.us/misc/what_is_this.jpg](http://www.flight.us/misc/what_is_this.jpg)

This key combo is essential to emacs and other apps (eclipse as well, I think)

please help identify and disable this keybinding.  I am using metacity Gnome.  I have de-selected "IBus" in "Languages Support", "Keyboard input method system:", and been through "Keyboard" "Shortcuts" thorougly, and don't see "Ctrl+space" there.

thanks

---

### Post by brainwash on 2014-02-23
Run "ibus-setup" and change the kb shortcut or remove ibus completely if you don't need it.

[https://launchpad.net/bugs/1278569](https://launchpad.net/bugs/1278569)

---

### Post by QIII on 2014-02-23
*Moved to **Ubuntu +1***

---

### Post by zika on 2014-02-23
> **brainwash said:**
> Run "ibus-setup" and change the kb shortcut or remove ibus completely if you don't need it.

[https://launchpad.net/bugs/1278569](https://launchpad.net/bugs/1278569)Before removing ibus check if simple```
 ibus exit
```fullfills Your needs not closing the door completely...

---

### Post by nealmcb on 2014-09-18
This is very sad - in order to put in a "transitional solution in trusty" (an LTS!) for a gnome problem, they broke all the other desktops and apps like emacs, eclipse, netbeans etc.
See details at [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1278569](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1278569)

---

### Post by cariboo on 2014-09-18
Nothing to do with utopic, thread closed.

---

