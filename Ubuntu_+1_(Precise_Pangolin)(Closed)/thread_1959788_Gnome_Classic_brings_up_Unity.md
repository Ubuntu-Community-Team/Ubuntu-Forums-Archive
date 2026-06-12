---
title: "Gnome Classic brings up Unity"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-04-16
When I select Gnome Classic from the LightDM login, I end up in Unity 3D, with the addition of the Gnome Classic bottom panel (the top panel is Unity's).

Gnome Classic (No Effects) works normally.

Anyone else seeing this, or have a fix/workaround?

---

### Post by mc4man on 2012-04-16
Log into Classic (with effects), open ccsm & disable the unity plugin
(to double ck. first that you are in a gnome classic session run from terminal
echo $DESKTOP_SESSION

---

### Post by sgage on 2012-04-16
> **mc4man said:**
> Log into Classic (with effects), open ccsm & disable the unity plugin
(to double ck. first that you are in a gnome classic session run from terminal
echo $DESKTOP_SESSION

That was easy, thanx!

---

