---
title: "Kdenlive se cierra solo (Gnome)"
date: 2008-12-02
forum: Software
---

### Post by Zeq on 2008-12-02
Instale el Kdenlive para editar videos en mi Ubuntu Intrepid (y en Hardy tambien).
Y ni bien lo abro, se me cierra solo.
Tendra que ver con que uso Gnome?

Si intento abrirlo por consola esto es lo que me sale:

$ kdenlive
kbuildsycoca running...
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.


A alguien le paso y me da una mano con esto?

---

### Post by Hei Ku on 2008-12-03
Puede ser alguna dependencia que te falte. Por lo que parece, no tenes instalado nada de KDE
Ni siquiera llega a colgarse de una manera elegante, como para obtener algun dato mas.

---

### Post by jpmorelli on 2008-12-03
A mi me pasó lo mismo, pero probé algo y me funcionó.
Fuí al directorio .kde/share/apps/ y borré el directorio creado "kdenlive". Después de eso abrí el programa y funcionó sin problemas. Igual te digo que por lo menos la versión que está ahora en los repositorios deja mucho que desear. Si no me equivoco acaba de salir la versión 0.7 con soporte para KDE4 pero todavía no está actualizada en los repos.
Suerte !

---

### Post by Zeq on 2008-12-03
Lei en launchpad que este error les pasa a muchos.

Lo que yo hice para arreglarlo fue:
1 : sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev
2 : borrar los archivos de configuracion (~/.kde/share/config/kdenliverc)

Si con eso no funciona hay que tratar deshabilitando Compiz.

Igual eso me dio la sensación de que quedo todo medio atado con alambres, espero que en la version 0.7 se corrijan estas cosas.

Una cosa que no probe pero que dicen y lo pongo por si a alguien le falla todo esto es ejecutar 'kdenlive -nograb'

Espero que le sirva a alguien.

---

