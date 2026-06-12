---
title: "No input language indicator in gnome-shell"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Wise Ferret on 2012-09-18
Title says it all. I can still change input languages using the shortcuts defined in the control centre, but there is no visual indication on the gnome-shell panel.
Am I missing a package? Does it have something to do with ibus (I do not use Chinese/Japanese/etc.)? Does anybody else have a language indicator in gnome-shell?

---

### Post by RavisPohan on 2012-09-18
I have the same problem on a fully updated Gnome remix (64 bit) using the Ricotz/testing ppa.

---

### Post by jbicha on 2012-09-18
Please see [bug 1045914]("http://pad.lv/1045914") for an explanation. Basically, GNOME did a bunch of risky work with ibus this cycle that could have caused problems for Ubuntu users who need input method support. Ubuntu is delaying that transition until 13.04.

I think we'll eventually add the new ibus to the GNOME3 PPA for Quantal but neither Rico nor I have much experience with that package.

---

### Post by Wise Ferret on 2012-09-18
Thank you very much for the information, jbicha.

This bug is especially frustrating when I have to type passwords, and cannot see what I type. In the case of ubuntu's software updater, an erranous password just closes the window neatly, and I have to restart it and update apt all over again before I can retry.

---

