---
title: "gazp5 Restars X on Logout"
date: 2007-12-15
forum: System76 Support
---

### Post by DBO on 2007-12-15
Every time I logout of my Gazelle X is restarted.  It's done this since I got it, X logs show nothing that interesting really.  Any inputs?

---

### Post by yabbadabbadont on 2007-12-15
That is one of the options for GDM (the login manager).  I always turn it on myself.  You can check to see if it is enabled on your machine by going to System->Administration->Login Window.  Then, on the General tab, make sure that "Restart the Xserver with each login" is unchecked.

---

### Post by DBO on 2007-12-15
I dont seem to have that option

---

### Post by yabbadabbadont on 2007-12-15
What version of Ubuntu do you have installed?

---

### Post by DBO on 2007-12-15
7.10

---

### Post by thomasaaron on 2007-12-17
Have you tried:

System > Preferences > Sessions > Session Options?

---

### Post by DBO on 2007-12-17
> **thomasaaron said:**
> Have you tried:

System > Preferences > Sessions > Session Options?

Nothing there either, it's not a big deal, just minorly curious as to whats causing it as the Xorg logs dont seem to indicate a crash.

---

### Post by thomasaaron on 2007-12-17
That is very interesting.
What flavor of Ubuntu are you using? X / K?

System > Prefs > Sessions should be standard on any Ubuntu installation.
By default, it does NOT save programs that were open when logging out.
You've got to enable that feature.

If you're running a version other than Ubuntu, you sould be able to find that setting somewhere.

---

### Post by DBO on 2007-12-19
Im sorry, i wasn't clear.  The menu items are present, its just there is no option to disable Xorg from restarting when I log out.  Everytime I log out Xorg (and maybe GDM?) restart which slows down the whole user switching process a little bit.

---

### Post by yabbadabbadont on 2007-12-19
Edit /etc/gdm/gdm.conf and make sure that the following setting is present in the "[daemon]" section of the file:
```
AlwaysRestartServer=false
```

---

