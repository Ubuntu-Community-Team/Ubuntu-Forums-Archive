---
title: "Gnome 3 - is there a way to assign which programmes use the dark adwaita theme?"
date: 2012-04-10
forum: The Cafe
---

### Post by Macfunky on 2012-04-10
Having a look through the themes folder but haven't figured out how to do it yet. There are one or two programmes i would like to use the dark adwaita theme. Does anyone know how the theme assigns which programmes use the dark theme?

---

### Post by Bandit on 2012-04-10
> **Macfunky said:**
> Having a look through the themes folder but haven't figured out how to do it yet. There are one or two programmes i would like to use the dark adwaita theme. Does anyone know how the theme assigns which programmes use the dark theme?

LOL I been asking this same question on multiple forums for weeks now.. 

All I can say that I have been through every style sheet file in the theme and none of them point out which one should use the darker theme set. I have been searching for this setting in every file I can think of and still no dice. If anyone knows, cause sure someone did to make Adwaita theme. I would love to know and be grateful for the info..

---

### Post by kiirokurisu on 2012-04-10
There is no way (currently) for the user to specify this. The application itself must include code to tell its StyleContext to use the dark variant of the theme. So it could only be achieved by patching whatever applications you wanted to have displayed with the dark variant.

---

### Post by Macfunky on 2012-04-11
> **kiirokurisu said:**
> There is no way (currently) for the user to specify this. The application itself must include code to tell its StyleContext to use the dark variant of the theme. So it could only be achieved by patching whatever applications you wanted to have displayed with the dark variant.

Is there a common file for each application where i would be able to change this and if so where would i find it? For instance with Totem, where would i find the file and what in the file should i be looking for?

---

### Post by Bandit on 2012-04-11
> **kiirokurisu said:**
> There is no way (currently) for the user to specify this. The application itself must include code to tell its StyleContext to use the dark variant of the theme. So it could only be achieved by patching whatever applications you wanted to have displayed with the dark variant.

There must be a way. If there wasn't then Totem and EOG wouldn't be doing it. I have even scaled somewhat through the programs UI XML files to see if it suggests an alternative reference to it. I may be wrong but pretty sure its not done during the configure/compile process. So there has to be a file somewhere. Also when you change your theme, totem and eog take on the look of the new theme.

---

### Post by urukrama on 2012-04-11
I'm not sure how this works on GTK 3, but with GTK 2 this was quite easy: [http://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/](http://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/)

I don't use Gnome 3 or Gtk 3, so I can't quite test this, but perhaps this is easily translatable to the new syntax.

---

### Post by Perfect Storm on 2012-04-11
In Gnome 3.4 adwaita gtk-dark.css is referring to 
```
@import url("resource:///org/gnome/adwaita/gtk-main-dark.css");
```

So I thought I could find its settings via dconf, but without luck.
Anyone have an idea where in the system its referring to?

---

### Post by kiirokurisu on 2012-04-12
Sorry folks, but like I said it is done in the application's code (e.g. EOG). Source: I have done this in one of my own apps. If you don't believe me, go and ask on the Gnome-dev list :)

---

