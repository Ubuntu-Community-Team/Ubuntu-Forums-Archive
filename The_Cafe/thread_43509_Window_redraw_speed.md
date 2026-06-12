---
title: "Window redraw speed"
date: 2005-06-22
forum: The Cafe
---

### Post by jnoreiko on 2005-06-22
Move a window around in Ubuntu and you see blank space where it was for a second or so. With some apps I even get ugly trails from the window borders.

Why is this? Which component is at fault? Is it Xorg, Metacity, GNOME, or the apps themselves?

On OS X, this never happens, and AFAIK it's because the contents of windows are always drawn, even when not visible. It's why their Expose feature is so fast.

Are smoother graphics in the pipeline for linux?

---

### Post by Lovechild on 2005-06-22
That problem will be fixed by XDamage, and yes it's greatly annoying.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=jnoreiko]Move a window around in Ubuntu and you see blank space where it was for a second or so. With some apps I even get ugly trails from the window borders.

Why is this? Which component is at fault? Is it Xorg, Metacity, GNOME, or the apps themselves?[/QUOTE]

Metacity and Gnome. If you have a Nvidia card you can turn on compositing and that ugly stuff goes away.

> 
Are smoother graphics in the pipeline for linux?

Always. Just not as fast as everybody wants.

---

