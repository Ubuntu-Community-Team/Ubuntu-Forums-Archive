---
title: "gconf editor nor ubuntu tweak work"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fantab on 2012-09-25
After the recent update my "appearance" customizations have vanished...  I tweak  the appearance using gconf-editor... 

For example: 
gconf-apps-gwd to give that glassy effect to windows title bars. Since the updates the effect is gone and when I retry from gconf it says "This key has no schema". Overall gconf-editor is not working.

Also Ubuntu tweak is not working... 

What changed?

---

### Post by diesch on 2012-09-25
Gnome and Unity are switching to gsettings/dconf instead of gconf.

Use dconf-editor (package dconf-tools).

---

### Post by fantab on 2012-09-25
Thanks...

I suspected that. Yet Ubuntu Tweak is not working and if only you could help me enable it from dconf Editor--apps--ubuntu-tweak--tweaks=[ ]. Wonder what goes between [ ] ?

---

### Post by dino99 on 2012-09-25
ubuntu-tweak works from the System Tools -> System Settings menu

---

### Post by mc4man on 2012-09-25
gwd is in dconf - (dconf-editor
org.compiz.gwd

---

### Post by funicorn on 2012-09-25
In the latest upgrade to unity 6.60, gconf are completely abandoned. Many has to be reset in gsettings.

---

