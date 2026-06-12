---
title: "Gnome-shell GDM and DE background settings"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-18
I am using Gnome-shell (3.5.91) DE with the default theming (Adwaita) and with the default Gnome display manager, GDM (3.5.91).
This setup has a nice timing based background. Three different backgrounds are used and changed from one to another by a gradual mixing (transition period).

The package gsettings-desktop-schemas_3.5.91-0ubuntu2 also set the GDM to use the same background setup from
/usr/share/themes/adwaita/backgrounds/

However, this has been changed back again.
Now gsettings-desktop-schemas_3.5.92 will set GDM to use the background from
/usr/share/backgrounds/warty-final-ubuntu.png.

Why this change again?

---

### Post by mc4man on 2012-09-18
Maybe the override file in the new package is affecting your gdm?
(/usr/share/glib-2.0/schemas/10_gsettings-desktop-schemas.gschema.override

> [org.gnome.desktop.background]
show-desktop-icons=true
picture-uri='file:///usr/share/backgrounds/warty-final-ubuntu.png'

Don't see that file in the old package

---

### Post by Harry33 on 2012-09-18
So that seems to an ubuntu patch then.

---

### Post by mc4man on 2012-09-18
> **Harry33 said:**
> So that seems to an ubuntu patch then.

Well they have the exact same in ubuntu-settings package
/usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override

so possibly the presumption/default is lightdm/unity greeter even for repo Gs users?? (or fallback

edit: I'm not clear on how these .override files work, if they kick in by just being installed (likely), then maybe that override shouldn't be in gsettings-desktop-schemas

---

### Post by jbicha on 2012-09-18
grr... Looks like the last upload accidentally re-added those overrides to the individual package.

---

### Post by bmbaker on 2012-09-18
hmmmm welll gdm is borked for me at the moment had to switch to lightdm, though the lock screen doesn't wk.
GDM loads but when you sign in it flickers loads the purpley screen and resets back to GDM again!

---

### Post by Harry33 on 2012-09-18
The background issue is now fixed with gsettings-desktop-schemas_3.5.92-0ubuntu2.

Thanks Jeremy!

---

