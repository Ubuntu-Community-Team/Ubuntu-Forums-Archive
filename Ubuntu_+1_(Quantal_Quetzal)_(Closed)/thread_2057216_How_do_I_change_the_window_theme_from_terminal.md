---
title: "How do I change the window theme from terminal?"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jokerdino on 2012-09-13
I seem to remember being able to change the window theme using gconf. 

This is the exact command that I remember using earlier:

```
gconftool-2 --type=string --set /apps/metacity/general/theme 'Ambiance'
```


However, giving recent changes and settings being ported to gsettings, the above command doesn't seem to work. Does anyone know if I can still change the window theme or have to rely purely on GUI to switch between them?

---

### Post by jokerdino on 2012-09-13
Never mind. I figured it out. The updated command should be:

```

gsettings set org.gnome.desktop.wm.preferences theme Ambiance 
```

---

### Post by dino99 on 2012-09-13
i'm too lazy , so i use the gui :p

---

### Post by jokerdino on 2012-09-13
> **dino99 said:**
> i'm too lazy , so i use the gui :p
Actually, I am lazier than you. I just set up a bash script to switch themes depending on the desktop environment. ^.^

---

