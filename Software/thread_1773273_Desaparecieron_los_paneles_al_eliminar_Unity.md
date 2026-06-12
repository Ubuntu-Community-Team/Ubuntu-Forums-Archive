---
title: "Desaparecieron los paneles al eliminar Unity"
date: 2011-06-01
forum: Software
---

### Post by nemodot on 2011-06-01
Hola, les comento más detalladamente. Venia usando Ubuntu 10.10 sin actualizar porque probé Unity una vez y no me gusto para nada.

Al fin hoy me convenci de actualizar para luego volarlo y volver a GNOME. Había leido que borrando unity del software center lo resolvías y eso es lo que hice. Pero me quede sin paneles.

Busqué como hacía para volver a poner los paneles pero no funcionó.  Usé estos comandos que no me fueron útiles:
```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

Tengo algún otro modo de volver a ver mis preciados paneles?

---

### Post by nemodot on 2011-06-02
Pude resolverlo forzando a que se abra al inicio el programa "gnome-panel", en Preferencias de las aplicaciones al inicio.

[IMG]http://i.imgur.com/d5y7s.png[/IMG]

---

