---
title: "Instalacion ubuntu"
date: 2009-07-01
forum: Software
---

### Post by dvanzo on 2009-07-01
Hola!! 

Cansado de reinstarle el Xp a mi hermano, le configuré una instalacion dual-boot. Xp para sus juegos exclusivos Win, y Ubuntu 9.04 para el resto... Despues de tres meses, ya no quiere saber mas nada con el Xp y quiere que le deje todo el disco con Ubuntu!!! Lo que yo estoy pensando hacer es instalar un nuevo Jaunty sobre la particion que ahora ocupa el Xp, y luego pasar su configuracion de usuario de la instalacion actual a la nueva... La duda es si Grub me va a mostrar las dos instalaciones... Lo que queremos es que la PC arranque directamente en la nueva instalacion y que podamos montar la otra para utilizarla normalmente para almacenar datos, etc... ?

Saludos y gracias desde ya!!!!

---

### Post by alfplayer on 2009-07-01
> La duda es si Grub me va a mostrar las dos instalaciones...
Eso debería suceder.

Si entendí bien, querés que queden dos instalaciones de Ubuntu, porque si solo querés que se pueda acceder a los archivos de la instalación existente de Ubuntu desde la nueva instalación no es necesario que aparezca en grub la instalación existente.

---

### Post by dvanzo on 2009-07-02
Hola y gracias por la respuesta!!

En realidad lo que quiero es que quede solo un Ubuntu instalado... En grub no debieran aparecer las dos opciones... Lo que no quiero es borrar la particion actual del ubuntu, para luego transferirla a la nueva...

Saludos!

---

### Post by Spity on 2009-07-02
Yo lo que haría sería con el livecd de ubuntu, borrar la partición de XP y extender la de Ubuntu. El tema del Grub, bueno, se pueden modificar las entradas sin ningún problema. :)

---

### Post by alfplayer on 2009-07-02
Si se está usando ahora grub para bootear el Ubuntu instalado y si la partición donde está el Ubuntu instalado tiene un tamaño adecuado la mejor opción en mi opinión es dejar todo como está (por si no lo sabés, la partición de windows puede ser usada para almacenar datos sin problemas desde el Ubuntu que ya está instalado sin que sea modificada).

---

