---
title: "Ubuntu Hardy no apaga"
date: 2009-01-10
forum: Software
---

### Post by lucasfava on 2009-01-10
Mas especifivo Ubuntu 8.04.1 LTS.
El problema es que al apagar, no se corta la energía. El disco esta particionado con Xp, y con Xp se apaga.  

El mother es Amptron M810, procesador AMD (Duron) 800mHz.
Se que hay un bug en Ubuntu pero no se solucionarlo.

Re editado
Use los siguientes comandos, pero pasa lo mismo, la pantalla en negro diciendo sistema detenido

> 
sudo halt (pide password)

y
> 
gnome-power-cmd.sh shutdown (no pide password)


---

### Post by euzkoarima on 2009-01-12
Solo se me ocurren dos cosas, en un server sin GUI yo uso ```
sudo poweroff
``` para apagar.

La otra, si no apaga y no se colgo, tira ```
ps aux
``` a ver si da una pista (sobre todo a alguno que sepa más que yo) de algún proceso que quede trabado y por eso no apague.

Saludos,
Eduardo

---

