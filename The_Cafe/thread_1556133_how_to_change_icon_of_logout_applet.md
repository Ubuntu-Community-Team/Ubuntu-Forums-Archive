---
title: "how to change icon of logout applet"
date: 2010-08-19
forum: The Cafe
---

### Post by Screwdriver0815 on 2010-08-19
Hi,

I am using now Fedora, besides Ubuntu and have a small question:

As Fedora does not have the logout menu like in Ubuntu, just the user switcher applet, I have put the logout applet into the panel and I wonder, how can I change it's icon? 

Does anyone know where the icon for this applet is stored? I already searched all folders in /usr/share/icons and in /~.icons.. I didn't find anything.

a little help would be very much appreciated!

---

### Post by kerry_s on 2010-08-19
if it's an applet check gconf-editor-> apps-> panel-> the logout applet

---

### Post by utnubuuser on 2010-08-19
if it's changeable, try right-clicking the icon and selecting properties, then clicking on the icon in the popup dialog window

---

### Post by Screwdriver0815 on 2010-08-19
> **kerry_s said:**
> if it's an applet check gconf-editor-> apps-> panel-> the logout applet

this worked. Thanks!!

defined a custom icon and selected "use custom icon"

---

