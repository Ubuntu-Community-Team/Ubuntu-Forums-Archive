---
title: "Changing Gnome Resolution via Shell"
date: 2010-04-05
forum: Ubuntu One (CLOSED)
---

### Post by Mokolodi1 on 2010-04-05
I changed the resolution in Gnome to something that my monitor cannot recognize. However, I can get into the shell, and am wondering if their is a way to change the Gnome resolution via the shell commands.

---

### Post by duanedesign on 2010-04-06
**xrandr** is used to set the size, orientation and/or reflection of the outputs for a screen. It  can also set the screen size.

Issuing the command without any option, will dump the state of the outputs, showing the existing modes for each of them, with a '+' after the preferred mode and a '*' after the current mode.
```
xrandr
```

To change the resolution to 1024x768 for example:

```
xrandr -s 1024x768 
```

I would read the man page:

```
man xrandr
```

Also some information on xrandr and resolutions on [the wiki]("https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution")

best of luck,
duanedesign

---

