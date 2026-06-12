---
title: "Can't add wireless HP printer - gnome-control-center printer"
date: 2016-10-05
forum: Ubuntu Development Version
---

### Post by makitso on 2016-10-05
Ubuntu gnome, 16.10 updated;  when selecting Printers and then trying to install a wireless printer,  its found but errors out "Failed to add new printer" is displayed.

However, if one installs the system-config-printer-gnome package then printing works correctly.  system-config-printer-gnome is not installed by default in ubuntu-gnome.

---

### Post by dino99 on 2016-10-05
The missing package should be installed by the desktop's metapackage at least: which one is installed on your system ?
This package provides the GTK frontend.
If ubuntu-gnome have forgotten to add that dependency, then send a request.

---

### Post by fthx on 2016-10-06
gnome-control-center (1:3.20.1-2ubuntu3) yakkety; urgency=medium

  * Add 08_lowercase_user_names.patch:
    - Copy patch from unity-control-center to disallow upper-case
      letters in user names for compliance with adduser (LP: #1600638)
  * Depend on system-config-printer-gnome instead of -common.
    Ubuntu's s-c-p packaging differs and we need scp-dbus-service.py
    (LP: #1623150)

---

