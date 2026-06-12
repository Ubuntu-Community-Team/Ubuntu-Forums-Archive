---
title: "I thought this would be fun"
date: 2009-10-20
forum: The Cafe
---

### Post by BigCityCat on 2009-10-20
If someone feels that this thread should be closed I understand. Some people with Karmic may already know how to do this. Maybe even a better way.

Some people may like the new GDM and splash screens in Karmic. They are ok. I like the way they operate as far as removing the black screen and fading to desktop, but they are not as simple to manipulate as before, but it can be done.

To change the login screen.

> gksudo -u gdm dbus-launch gnome-appearance-properties

Then navigate to the picture you want instead and add it. I found it's easier to place that picture in an empty folder rather than allow it to try and load all your pictures.

Also I noticed a little bug where it may add a assitance technology icon in the panel. To remove this icon.

> gnome-keyboard-properties


Then navigate to accessibility tab and uncheck the top box.

Now to change the splash screens. 

> gksudo nautilus

Navigate to user/share/images/xsplash. Make a back up of the splash screens of your monitor resolution and save them in a different folder. Copy and paste a same size version of your new splashscreen image with the same name as the old version. You should change the image that corresponds with your screen resolution and sometimes the image that is larger in WIDTH as well.

---

### Post by hoppipolla on 2009-10-20
There's no reason to close this, this is what Linux is all about :)

.. There may be cleaner ways to do some of this stuff though! :)

---

### Post by mocoloco on 2009-10-20
Cool, thanks for the tips!

---

### Post by BigCityCat on 2009-10-20
> **mocoloco said:**
> Cool, thanks for the tips!

no problem.

---

### Post by BigCityCat on 2009-10-20
> **hoppipolla said:**
> There's no reason to close this, this is what Linux is all about :)

.. There may be cleaner ways to do some of this stuff though! :)

Cool I was a little worried someone might get upset if they screwed something up, but it's a pretty un intrusive process.

---

