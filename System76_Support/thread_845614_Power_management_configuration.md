---
title: "Power management configuration"
date: 2008-06-30
forum: System76 Support
---

### Post by perce on 2008-06-30
When unplugged my laptop (DARU1) reduces the backlight as it is supposed to do. I used to be able to control how much the backlight is reduced through
System > Preferences > Power management, but I don't have that option anymore. Is there something wrong in my computer, or that option was remved in Hardy?

---

### Post by thomasaaron on 2008-07-01
It's been removed from System > Prefs > Power Mgt.

Go to gconf-editor...
Apps > gnome-power-manager > backlight

Double click the brightness-battery line and set the percentage.

---

### Post by ashleycameron on 2008-07-01
Hi mate, tell me at which percentage did brightness will be perfect?

---

### Post by hardyn on 2008-07-01
you are probably the only person who can decide what reduced back light you are happy with.

---

### Post by thomasaaron on 2008-07-01
75% seems about right to me.

---

