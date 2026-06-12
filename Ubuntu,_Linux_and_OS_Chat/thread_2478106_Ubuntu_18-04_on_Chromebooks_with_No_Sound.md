---
title: "Ubuntu 18-04 on Chromebooks with No Sound"
date: 2022-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by gilbertdl on 2022-08-16
[COLOR=#000000][FONT=Arial]My Samsung Chromebook 5 recently reached its Auto End of Updates. Since I can’t afford to invite malware and run out of date Chrome browsers, the Chromebook was no longer of use to me. Besides it was terribly slow. I used GalliumOS notes and firmware to enable USB boot. I didn’t like GalliumOS software so I installed Ubuntu 18.04 LTS instead. Ubuntu runs perfectly on my Chromebook except that there is no sound. But under GalliumOS the sound card worked. Since I know that it is possible to make the sound card work, why can’t Canonical add new sound card drivers so that expired Chromebooks can install Ubuntu and have sound. This will potentially save thousands of Chromebooks from ending in the garbage pile and creating an environmental hazard. There are 17 million Chromebooks that expired this year.[/FONT][/COLOR]

---

### Post by TheFu on 2022-08-17
18.04 support for the gnome3 version ends in about 6 months after a long run.  All other DE flavors lost support a few years ago.
You are likely running over 50% unsupported software on your chromebook.

If you want supported software and newer driver support, move to 20.04 or 22.04 releases.
I suppose you could install a newer kernel on the old release too, but that isn't recommended for non-experts and it forces kernel patching to be 100% manual going forward.

If you will install and run 
```
$ inxi -Fxxz
```
we'll have an overview of the system and someone may be able to help. 
There is also a sound trouble shooter script, that is useful to the sound experts.

Not all chromebook hardware is the same, so acting like 1 tiny change is needed to magically support 50 different chromebook models isn't true. Heck, some run ARM and others run Intel CPUs, so even the binaries between those systems are 100% incompatible.

BTW, don't confuse the GUI with the OS.  For most version of Linux, we can completely change the GUI from what the distro ships with in about 5 minutes.  GalliumOS has drivers for your chromebook.  Perhaps the better solution would be to stick with that as the base OS, but change the GUI to one you like better?

---

### Post by coffeecat on 2022-12-07
Old, abandoned and totally misplaced thread closed to prevent further thread hijacks. If you need help with Ubuntu on a Chromebook, please start your own thread, **but in a support sub-forum**, not here.

---

