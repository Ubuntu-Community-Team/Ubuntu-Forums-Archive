---
title: "Aporte: Problemas al hacer click en objetos Flash"
date: 2010-01-08
forum: Software
---

### Post by FB91 on 2010-01-08
Les comparto esto que para mí fué la solución a un problema bastante molesto que tenía, que era justamente no poder hacer click en objetos flash, como ser videos de youtube o algún que otro jueguito...

Pasos a seguir:

[LIST]
[*]En una terminal escribir ```
sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```
[*]agregar en la penúltima línea ```
export GDK_NATIVE_WINDOWS=1
```
[*]Guardar
[*]Cerrar y volver a abrir el navegador
[/LIST]

Pruebenlo, a mi me funcionó lo más bien usando cualquier navegador! 
ojalá les sirva :D

Fuente: [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

---

### Post by emiliano_raso on 2010-01-16
A mi se me solucionó de un dia para el otro solo. Con alguna actualización supongo.

Lo que me sigue pasando es que los videos embebidos en paginas web, foros, etc, titilan o "pestanean", en cambio los mismos videos vistos en YouTube no pasa.

Te pasa a vos eso?

---

### Post by FB91 on 2010-01-17
a mi los videos embebidos se me ven bien, lo que a veces me "pestanea" son algunos juegos en flash (pero muy pocos)

---

### Post by TIaGoX on 2010-01-17
Yo tuve el mismo problema en las animaciones en flash y lo solucione instalando los plugins para la versión de mi sistema correcto (64 bits)

---

