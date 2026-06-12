---
title: "Latest image panel issue"
date: 2017-09-07
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-09-07
On current image install (and maybe a couple of days prior) the gnome panel is not rendered correctly unless a window is touching it.

---

### Post by Chanath on 2017-09-07
Better off without system extensions?
No extensions installed as you see. Super key pushed.

---

### Post by Frogs Hair on 2017-09-07
> **mc4man said:**
> On current image install (and maybe a couple of days prior) the gnome panel is not rendered correctly unless a window is touching it.

Wasn't sure if that was intended because I only see with the default theme.

---

### Post by Frogs Hair on 2017-09-07
> **Chanath said:**
> Better off without system extensions?
No extensions installed as you see. Super key pushed.

I had the same breakage and I think dash-to-dock was the cause. Reinstalled last night and no problems so far. Removing the extensions and schema for dash-to-dock and ubuntu-dock extensions didn't solve the problem.

---

### Post by Chanath on 2017-09-07
> **Frogs Hair said:**
> I had the same breakage and I think dash-to-dock was the cause. Reinstalled last night and no problems so far. Removing the extensions and schema for dash-to-dock and ubuntu-dock extensions didn't solve the problem.

I think Ubuntu Dock is buggy. It is also an extension, just like others.

---

### Post by Frogs Hair on 2017-09-07
Getting off topic from the original post , but I setup ubu-dock the way I want it and am leaving as is!

---

### Post by mc4man on 2017-09-07
Turns out this is an upstream (Gnome) feature, i.e. suspect design. 
Could possibly be reverted by Gnome or Ubuntu..

---

