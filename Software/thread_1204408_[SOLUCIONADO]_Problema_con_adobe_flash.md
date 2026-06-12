---
title: "[SOLUCIONADO] Problema con adobe flash"
date: 2009-07-04
forum: Software
---

### Post by zhelo on 2009-07-04
siempre que me meto a una pagina que soporta el plugin de adobe flash
me aparece 
esa ventana con el botno play

[http://i44.tinypic.com/260ej9u.png](http://i44.tinypic.com/260ej9u.png)

los mismo apsa con firefox.....

lo intersante es que apreto el boton play y se pone la pantalla negra xD
en youtube lo apreto y carga lento y ademas al reproducir se pega

que onda?

---

### Post by pagondel on 2009-07-05
```
sudo aptitude remove swfdec-gnome swfdec-mozilla
sudo aptitude install flashplugin-nonfree flashplugin-nonfree-extrasound
```

---

### Post by zhelo on 2009-07-05
> **pagondel said:**
> ```
sudo aptitude remove swfdec-gnome swfdec-mozilla
sudo aptitude install flashplugin-nonfree flashplugin-nonfree-extrasound
```

si funco gracias =)

---

