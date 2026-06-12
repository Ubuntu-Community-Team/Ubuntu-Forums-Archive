---
title: "wicd or wicked?"
date: 2013-04-15
forum: The Cafe
---

### Post by Kleenux on 2013-04-15
Is *wicd* to be pronounced *wicked*?

I installed wicd from the package manager - it was not working well so decided to uninstall it for good (apt-get purge wicd).

Next reboot: wicd ask for my password to "access my network cards"!

a `find / -iname "*wicd*"` showed it was everywhere (excerpt)
```
/etc/rc...d/K00wicd (ok that's a K)
/etc/xdg/autostart/wicd-tray.desktop
/etc/dbus-1/system.d/wicd.conf
/etc/wicd
/etc/default/wicd
/etc/init.d/wicd
/var/lib/wicd
/var/lib/update-rc.d/wicd
/home/kleenux/.wicd
/usr/bin/wicd-client
/usr/bin/wicd-gtk
/usr/lib/python2.7/dist-packages/wicd
/usr/lib/python2.7/dist-packages/wicd-1.7.2.3.egg-info
/usr/lib/pm-utils/sleep.d/55wicd
/usr/sbin/wicd
/usr/share/app-install/desktop/wicd-gtk:wicd.desktop
/usr/share/app-install/desktop/wicd-kde:kde4__wicd-kde.desktop
/usr/share/app-install/icons/wicd-gtk.png
/run/wicd
```

Something seems strange with that prog... 
(Ubuntu 12.04)

---

### Post by azzamite on 2013-04-15
Wrong forum, but anyway.

You need to disable network-manager for wicd to work.

---

### Post by Kleenux on 2013-04-16
Thanks... but I don't need it anymore - this was not the point of my post.

Isn't that strange that the uninstall keep so many active elements everywhere?

---

