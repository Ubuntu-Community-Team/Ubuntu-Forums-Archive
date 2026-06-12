---
title: "&quot;Enable delete&quot; from right-click menu?"
date: 2011-12-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2011-12-17
Does anyone have any hints about the setting "enable delete" that used to add direct delete to the right click menu in nautilus? It used to be set in gconf through gconf-editor, but that isn't being used as far as I can see, and I don't know if this tweak has come back somewhere else yet.

---

### Post by mc4man on 2011-12-17
nautilus > edit > preferences
or
dconf-editor > org > gnome > nautilus > preferences
or 
```
gsettings set org.gnome.nautilus.preferences enable-delete true
```

(if you wish a delete in a root nautilus browser then open one and use first method or sudo gsettings ...

---

### Post by scradock on 2011-12-18
> **mc4man said:**
> nautilus > edit > preferences


Thanks mc4man!

---

