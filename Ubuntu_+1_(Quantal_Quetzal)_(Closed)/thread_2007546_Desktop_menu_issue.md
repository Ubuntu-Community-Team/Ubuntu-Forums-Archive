---
title: "Desktop menu issue"
date: 2012-06-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Curtis6767 on 2012-06-20
For about a week, I've been having a couple of different things happen on the desktop. Not sure which update did it, but for a time I had no items on the task bar in the upper right hand corner. I had to shut down using 'shutdown now'. In the past couple of days, I've gotten the menu item back, but now I have this issue where a couple of those drop down menus are kinda' whited out. See image below. Not sure what's causing this and not sure it's of any real importance and clueless about how to fix it. 

This is 12.10 in Virtual Box and now with the new 3.5 kernel. Maybe it's just because its a VB install. Don't know.

Worth bothering about?

---

### Post by SpaceCeph on 2012-06-21
Here the same without VB.

---

### Post by philinux on 2012-06-21
Do a unity --replace and it will fix the whiteout menus.

---

### Post by Curtis6767 on 2012-06-21
> **philinux said:**
> Do a unity --replace and it will fix the whiteout menus.

Nope. I just get a bunch of error messages which I can't copy & paste because nothing works. The process hangs and I have to force the terminal to quit. Then I get a duplicate launcher to the right of the other launcher. After a while that launcher disappears but those drop down menus are still whited out.

As far as I can tell, this issue is not impacting anything else so I'm inclined to leave well enough alone and see if it fixes itself over time.

Thanks

---

### Post by philinux on 2012-06-21
> **Curtis6767 said:**
> Nope. I just get a bunch of error messages which I can't copy & paste because nothing works. The process hangs and I have to force the terminal to quit. Then I get a duplicate launcher to the right of the other launcher. After a while that launcher disappears but those drop down menus are still whited out.

As far as I can tell, this issue is not impacting anything else so I'm inclined to leave well enough alone and see if it fixes itself over time.

Thanks

Try this then

First do:-

gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'
then
gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'

---

### Post by dino99 on 2012-06-21
Seems to be the faulty change:

[https://launchpadlibrarian.net/107546060/gtk3-engines-unico_1.0.2-0ubuntu1_1.0.2-0ubuntu2.diff.gz](https://launchpadlibrarian.net/107546060/gtk3-engines-unico_1.0.2-0ubuntu1_1.0.2-0ubuntu2.diff.gz)

might need to revert to previous package release

---

### Post by jerrylamos on 2012-06-22
22 June daily build, installed, can't even select Appearance > Pictures. Drop down menu function does not work.

Only way I was able to get installed was to

gsettings set org.gnome.desktop.interface gtk-theme Adwaita

because "Change" selection in Something Else refuses to do anything but quiver.

What is so screwed up about drop down menus in default gsettings?

Please do not change Adwaita. It works. Hard to read screen, but it works. Have to mouse over some selections to read them, but it works.

Cannot set up wireless security WPA because drop down menu refuses to work.

Appreciate any help or workarounds that anyone suggests.

Bug #1015497 little activity or interest from Development.  

Thanks, Jerry

---

