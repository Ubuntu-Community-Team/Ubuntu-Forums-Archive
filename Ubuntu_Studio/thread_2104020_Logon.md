---
title: "Logon"
date: 2013-01-11
forum: Ubuntu Studio
---

### Post by Heavy Mars on 2013-01-11
Now i want to know how change the bored and cold logon picture that Ubuntu Studio show in the monitor by default . There's one way to do?

---

### Post by CrocoDuck on 2013-01-12
If "how to change the login manager's wallpaper" is what you mean I found this way:

As the picture used in the login manager is /usr/share/xfce4/backdrops/macinnis_wallpaper.png I downloaded a picture I like, stored in home, changed it's name into macinnis_wallpaper.png (setting other stuff with The Gimp). Then as **root** I copied  the picture /usr/share/xfce4/backdrops/macinnis_wallpaper.png into a safe place then I replaced it with the one I downloaded and renamed. So at next login lightdm will use /usr/share/xfce4/backdrops/macinnis_wallpaper.png as always, but the picture is different, as I swapped it. If you don't have idea on how to do it and you don't know what **sudo and root** are please repost, then I'll give to you some link and a example. Is very important you **properly understand what sudo is**.

---

### Post by jejeman on 2013-01-12
Change the icon in this file>
/usr/share/lightdm-gtk-greeter/greeter.ui
Change the theme and background in this file>
/etc/lightdm/lightdm-gtk-greeter.conf

---

