---
title: "how to clean gedit 3 setting files?"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-24
It seems that I have embedded terminal with the proper theme (black on white) in one instance, and another still with the messed up white on white. So looking for a means to fix :)

---

### Post by mc4man on 2012-02-24
The settings are in dconf-editor as shown in screen. If it's having issues with using the theme colors, does here, then you can define your own. If so disable box I've highlighted, then whatever is defined there for background/foreground will apply

---

### Post by prusswan on 2012-02-24
> **mc4man said:**
> The settings are in dconf-editor as shown in screen. If it's having issues with using the theme colors, does here, then you can define your own. If so disable box I've highlighted, then whatever is defined there for background/foreground will apply

Thanks! will try this

---

### Post by Harry33 on 2012-02-24
The user based setting files are here:
  .config/gedit/
  .gconf/apps/gedit-2/plugins
  .gconf/apps/gedit-2/preferences

Just delete those gedit folders.

Then, for universal settings, purge the packages gedit and gedit-common.
Then, reinstall the same packages.

---

