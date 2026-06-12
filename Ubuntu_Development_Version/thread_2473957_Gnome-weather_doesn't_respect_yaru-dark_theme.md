---
title: "Gnome-weather doesn't respect yaru-dark theme"
date: 2022-04-19
forum: Ubuntu Development Version
---

### Post by mdintisar on 2022-04-19
Gnome-weather doesn't respect dark theme in Ubuntu 22.04

May be it is a problem with libadwaita but I am not sure.

---

### Post by Claus7 on 2022-04-19
Hello,

gnome-weather uses the now so called Legacy Applications option, so if you would like to change the theme of that application you should check there, until is ported to gtk4.

Regards!

---

### Post by mdintisar on 2022-04-19
In gnome tweaks, I see that legacy application is set to yaru-dark. But gnome-weather is not respecting that. And in Ubuntu settings appearance I have set to dark mode with orange accent.

---

### Post by Claus7 on 2022-04-20
Hello,

I see what you are talking about. I nearly messed my system, since, changing themes while weather was open, could not change back to my preferences. Luckily, logging out and back in, issue got fixed. Indeed trying some yaru-dark themes from legacy applications did not change the weather app. Have in mind that this is an app that is about to transfer to gtk4. Irrespective of that you could choose another legacy application theme that has a dark accent, which will change also weather appearance.

Regards!

---

### Post by mdintisar on 2022-04-20
Is there any chance that gnome-weather theming issue will be fixed in Ubuntu 22.04 through updates?

---

### Post by Claus7 on 2022-04-20
Hello,

just for a workaround I would suggest you to check out a theme from here: 
[https://www.gnome-look.org/p/1214931](https://www.gnome-look.org/p/1214931)

you can come across a black theme that will be respected from weather app, when chosen from legacy applications.

Regards!

---

### Post by mdintisar on 2022-04-20
Thanks for your suggestion. I tried it and it works. But I really like yaru themes. If yaru-dark would only support it would have been much more cohesive.

---

### Post by mdintisar on 2022-04-20
If I use


> GTK_THEME=Yaru-dark gnome-weather

Gnome-weather respects dark version of yaru theme. 

I am thinking it may be a bug with the settings of themes in Ubuntu 22.04.

---

### Post by mdintisar on 2022-04-21
It is now confirmed as a bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-weather/+bug/1967630](https://bugs.launchpad.net/ubuntu/+source/gnome-weather/+bug/1967630)

---

