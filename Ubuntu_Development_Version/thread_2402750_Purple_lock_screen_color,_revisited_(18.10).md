---
title: "Purple lock screen color, revisited (18.10)"
date: 2018-10-04
forum: Ubuntu Development Version
---

### Post by kawazu on 2018-10-04
Hi all;
installed 18.10 beta on one of my devices and just noticed the (for my personal tastes) annoying purple lock screen background is back. I remember messing with that with installing and choosing a different GDM css on earlier versions but this doesn't seem to work anymore.
What's the default way to set up this theme?
Thanks,
Kristian

---

### Post by slickymaster on 2018-10-04
*Thread moved to **Ubuntu Development Version**.*

---

### Post by dino99 on 2018-10-04
Maybe look at  /usr/share/plymouth/themes.

---

### Post by corradoventu on 2018-10-04
I do not understand what you mean, lock screen can be easily changed from system settings -> Background. You can choose a background, a picture or a color.

---

### Post by corradoventu on 2018-10-07
```
gedit admin:/etc/alternatives/gdm3.css
```
change:
```
/*
#lockDialogGroup {
  background: none;
  background-color: none;
  background-gradient-direction: vertical;
  background-gradient-start: #6D2169;
  background-gradient-end: #370026; }
*/

#lockDialogGroup {
  background: #2c001e url(file:///home/corrado/Pictures/CrestedGecko.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center; }

```

---

### Post by corradoventu on 2018-10-11
If for lock screen you intend the screen with Ubuntu and the five dots you can modify the background color: 
```
gedit admin:/usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.script
```
changing - dark-gray ->  dark-gray 
```
Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom
```
to red -> blue
```
Window.SetBackgroundTopColor (0.99, 0.00, 0.00);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.00, 0.00, 0.99);  # an equally nice colour on the bottom

```

---

