---
title: "Synaptics configuration choice"
date: 2006-09-26
forum: System76 Support
---

### Post by kevinlyfellow on 2006-09-26
Why did you decide on qsynaptics instead of gsynaptics when your using a gnome desktop?

---

### Post by crichell on 2006-09-26
gsynaptics doesn't store configuration data after a reboot - so customers would have to go in and set their touchpad preferences each time the started up.  I'm hoping to see this fixed in gsynaptics soon.

---

### Post by crichell on 2006-09-26
Just to add to that qsynaptics isn't very QT heavy so it's not a burdin on a GNOME desktop (as some KDE apps are).

---

### Post by kevinlyfellow on 2006-09-27
qsynaptics doesn't seem to restore the configuration on reboot.  I needed to putting `qsynaptics -r` in my startup programs in order for it to restore the settings on reboot

---

