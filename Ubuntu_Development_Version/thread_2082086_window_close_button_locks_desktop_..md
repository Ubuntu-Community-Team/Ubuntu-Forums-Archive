---
title: "window close button locks desktop ."
date: 2012-11-08
forum: Ubuntu Development Version
---

### Post by ronacc on 2012-11-08
In gnome-shell when I try to close a window ,as soon as I hit the close button all mouse clicks are ignored , by that I mean that the mouse pointer moves but nothing , not the desktop , not the window I was trying to close , not the menu bar respond to mouse clicks , the keyboard is active so I can ctrl>alt>F1 and reboot from there . Interestingly running top from the terminal does not show the application I was trying to close . Prior to hitting the close button everything is normal .

Edit: this only happens in gnome-shell , unity and gnome classic (no effects) are ok .

---

### Post by cwsnyder on 2012-11-08
I take it that you are not getting the hint that GNOME shell doesn't want you to close all windows? :-P

Seriously, the way I understand the GNOME shell is that you always have an active window on the desktop, although you may have more than one window.  I use Xfce and am going by what I have read in the reviews.

---

### Post by ronacc on 2012-11-08
if that is the case it is new behavior , I have been using gnome-shell since the start of gnome 3 and have not seen this , my test box is busy right now but when it is free I'll try opening another window before I close the 1st one .

---

### Post by mc4man on 2012-11-08
Same here except it locks up the session completely.
What will fix this is to disable the WM from handling the Desktop which is the intention of Gnome.
To see - 
In dconf-editor > org.gnome.desktop.background
It will be unchecked by default but not really disabled due to an override. So enable, then disable

---

### Post by sammiev on 2012-11-08
I have been having this issue for 5 days now but the latest updates as of an hour fixes the gnome problem. Now Firefox will not load. They are getting closer. :)

---

### Post by sgage on 2012-11-08
> **sammiev said:**
> I have been having this issue for 5 days now but the latest updates as of an hour fixes the gnome problem. Now Firefox will not load. They are getting closer. :)

No problem with Firefox here...

---

### Post by sgage on 2012-11-08
> **mc4man said:**
> Same here except it locks up the session completely.
What will fix this is to disable the WM from handling the Desktop which is the intention of Gnome.
To see - 
In dconf-editor > org.gnome.desktop.background
It will be unchecked by default but not really disabled due to an override. So enable, then disable

I have 'WM handling the desktop' ON, and no problems such as described.

---

### Post by sammiev on 2012-11-08
> **sgage said:**
> No problem with Firefox here...

Firefox was working until two hours a go with gnome3 until I updated. I even tried the trunk version and it's the same. Happy testing. :)

---

