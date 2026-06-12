---
title: "What's wrong with the XFCE package in both jaunty and Karmic?"
date: 2009-10-14
forum: The Cafe
---

### Post by Warpnow on 2009-10-14
Tried this twice, once on each, in a VM. When you install the xfce package after a minimal install you don't get the default icons on the application menu. 

Any idea why this is? It makes these ugly red boxes.

---

### Post by anonymous_user on 2009-10-14
You need an icon theme like Gnome or Tango.

---

### Post by Warpnow on 2009-10-14
shouldn't the package xfce4-icon-theme be a dependency of xfce?

---

### Post by anonymous_user on 2009-10-14
I think it is, but iirc it has less icons than Tango or Gnome.

---

### Post by sertse on 2009-10-14
Ubuntu package search is down for me, but iirc:

Xfce 4.6, because of properly following free desktop standards had the side effect of making it's custom icon theme (rodent), to not be complete. The recommended action, which Ubuntu adopted is to make tango icon theme as recommended package for xfce.

---

