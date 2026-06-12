---
title: "logmein"
date: 2007-10-01
forum: The Cafe
---

### Post by rgraves22 on 2007-10-01
Can I view a windows PC from a linux box using logmein? My setup at work, or where I would use logmein, I have a linux box on the side running ubu 7.04, but would remote into a windows xp box. Is there going to be an issue with compatability? I can't find anything on their FAQ on their site.

---

### Post by Jose Catre-Vandis on 2007-10-01
Use VNC

Set up UltraVNC or TightVNC on your Windows PC, then you can VNC to it from Ubuntu with code similar to:
```
vncviewer yourWindowsPC-IP:0
```

---

