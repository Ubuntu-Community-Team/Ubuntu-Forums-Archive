---
title: "Call for testing: Ubuntu themes on GNOME"
date: 2017-05-23
forum: Ubuntu Development Version
---

### Post by jbicha on 2017-05-23
Check out today's post asking for bug reports for Ubuntu's themes on GNOME.

[http://blog.3v1n0.net/informatica/linux/ubuntu-goes-gnome-theming-stays-test-and-tune-it/](http://blog.3v1n0.net/informatica/linux/ubuntu-goes-gnome-theming-stays-test-and-tune-it/)

---

### Post by wildmanne39 on 2017-05-23
I want to ask before I install the themes, I am running ubuntu gnome 17.10 can I install them on it or do I did to go the route stated and install ubuntu then gnome shell?
Thanks

---

### Post by jbicha on 2017-05-23
You can start with Ubuntu GNOME. Just install light-themes and change your theme to Ambiance.

Ubuntu 17.10 will have some different default apps than Ubuntu GNOME 17.04, but we do want all the GNOME apps to look good, regardless of whether they are installed by default.

---

### Post by #&amp;thj^% on 2017-05-23
Well here is a quick peek:
```
System:    Host: me-750-417c Kernel: 4.10.0-22-lowlatency x86_64 (64 bit)
           Desktop: Gnome 3.24.1 Distro: Ubuntu 17.04
           gnome-wayland


```

---

### Post by wildmanne39 on 2017-05-24
Ubuntu Gnome 17.10
```
Linux 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
I am guessing the menu bar with the close, open and minimize buttons on it should not look that way?

The screenshots cut off the top to much to see but the bar is still white and the letters are very fuzzy and a gray color.

Edit:

Added a third image that shows the top menu bar.

---

### Post by P-I H on 2017-05-25
It looks this way on my system. I don't like the orange color and it's changed with gtk-theme-config.
[https://www.dropbox.com/s/4w0q9q04jh5ywf1/Screenshot%20from%202017-05-25%2007-33-44.png?dl=0](https://www.dropbox.com/s/4w0q9q04jh5ywf1/Screenshot%20from%202017-05-25%2007-33-44.png?dl=0)

---

### Post by Frogs Hair on 2017-05-25
I see no pointed corners which was the problem with the other themes.

---

### Post by fthx on 2017-05-27
So... I know there is a bug report procedure but we could simply list here what the Ambiance theme (gtk+, ubuntu-dark icons) does wrong :
- misplaced title separator (vertical rule) in Gnome Tweak Tool header bar (it seems that the search icon on top left is misplaced, causing that) ;
- the attachment bar in a message (to be read) window appears very small, to be shown right after clicking a second time (see the difference against Adwaita, which does it directly right;
- maybe matter of taste, but the Gnome ON/OFF switches are ugly, seem to me that their orange color go outside of the buttons borders too ;
- battery icon is too small ;
- ...

---

### Post by jbicha on 2017-05-27
Please do file bugs. You can't expect the theme developers to look here for bug reports. :)

---

