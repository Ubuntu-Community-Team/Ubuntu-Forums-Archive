---
title: "Trolls and Gnomes"
date: 2007-07-19
forum: The Cafe
---

### Post by original_jamingrit on 2007-07-19
I've been an Ubuntu user for a while now.  I have a question I've been trying to figure out for a while, I've read up as much as I could about it, so I thought I may as well ask it here:

What are the technical differences between KDE and GNOME?  I do understand that they are software toolkits, and that there's a big division in the linux community caused by them.  But, why can't any particular GUI-based program like Amarok or the GIMP support (or be supported by) both of them, or other toolkits at the same time?  Do these toolkits have more to do with a program than its front-end?

---

### Post by lamalex on 2007-07-19
simply put, QT and GTK are libraries/tool kits that these programs are built on, this is the technical difference between the two, but IMO the bigger difference is the philosophical difference, GNOME tries to be simple and professional, KDE tries to give you billions of options.

---

### Post by koenn on 2007-07-19
Any KDE application will happily run on a gnome desktop, or any other linux system with an Xserver. 
It's just that applications rely on libraries. KDE and Gnome use seperate sets of libraries. Applications that are written for KDE (all the K-apps) will depend on KDE libraries while gnome apps don't. 
Mixing KDE en Gnome on the same system causes  you to install both sets. 
Then, each desktop has its own mechanisms for integration, eg to create menu items for newly installed applications, or the let apps inherity the theme (color schemes, look and feel) of the desktop. Again, Gnome will use different software to accomplish this than KDE. 
S, theoretically, to make a KDE application depend on gnome libraries would require e re-write of the program, or at least replace all calls to KDE libraries with calls to gnome libraries and possibly additional coding to handle differences in the returns from these calls - if this is at all possible, i don't know

---

### Post by original_jamingrit on 2007-07-19
Okay.  I was always under the impression it was just GUI libraries thing, and that never quite clicked for me.

Cheers.

---

### Post by DoctorMO on 2007-07-19
> Then, each desktop has its own mechanisms for integration, eg to create menu items for newly installed applications, or the let apps inherity the theme (color schemes, look and feel) of the desktop. Again, Gnome will use different software to accomplish this than KDE.

Not quite true since both KDE and Gnome are moving towards LSB which defines a whole brace of things which both desktops must use for things like Desktop, apps menu etc etc.

---

### Post by koenn on 2007-07-19
OK, I could be a little behind on new developments, but as you say yourself : 
> **DoctorMO said:**
> ...  moving towards ... 

---

### Post by SunnyRabbiera on 2007-07-19
I wonder if its possible to become a forum gnome :D

---

### Post by tbroderick on 2007-07-19
If you are using KDE, try installing gtk-qt-engine. It does an ok job of making gtk2 applications look like your qt applications. If that doesn't work well enough for you, try using a theme like qtcurve which is designed for people who want a consistent appearance between GNOME and KDE.

---

### Post by loell on 2007-07-19
i wonder with all this comparative talks with GNOME and KDE,    XFCE is almost always out of the picture
is it because XFCE is also gtk based, and gets swallowed by gnome automatically? :popcorn:

---

### Post by kodoku on 2007-07-19
> **loell said:**
> 
is it because XFCE is also gtk based, and gets swallowed by gnome automatically? :popcorn:

Precisely, XFCE looks like a simplified Gnome

---

