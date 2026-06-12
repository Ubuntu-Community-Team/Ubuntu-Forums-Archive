---
title: "Bases de datos (M$ Acces)"
date: 2011-08-08
forum: Software
---

### Post by daggaz on 2011-08-08
Hola,
Antes que nada, ya he buscado en Google y acá, tengo cierta información,  pero necesito algo más claro y actualizado, pues muchos de los post que  he encontrado tienen cuando menos dos años de haber sido publicados.
 Resulta que estoy trabajando en una empresa que se viene mudando de  M$ a Linux, eligiendo Ubuntu por su facilidad. Casi todo ha quedado  cubierto y bien, con un pequeño problema: Access.
 Yo nunca lo he usado, así que desconozco su uso, pero soy el que más  experiencia tiene aquí con Linux, así que me toca investigar.
 He encontrado tres posibles candidatos a ser el «remplazo» de Access:
 
[LIST=1]
[*]Kexi
[*]SQlite
[*]Libreoffice Base
[/LIST]
 ¿Qué opinión tienen sobre estos tres? ¿Cuál el más compatible y fácil  de entender (sabiendo que aquí manejaban todo con M$)? ¿Cual promete  más a futuro? ¿Qué hay de la integración (Kexi es KDE y Base es de  Libreoffice, que viene por defecto)? ¿Facilidad de instalación?...

---

### Post by alfplayer on 2011-08-08
Otros para evaluar:

[http://www.knoda.org/]("http://www.knoda.org/")
[http://www.gnome-db.org/]("http://www.gnome-db.org/")
[http://www.glom.org]("http://www.glom.org")

---

### Post by guillermolisi on 2011-08-09
> **daggaz said:**
> Hola,
Antes que nada, ya he buscado en Google y acá, tengo cierta información,  pero necesito algo más claro y actualizado, pues muchos de los post que  he encontrado tienen cuando menos dos años de haber sido publicados.
 Resulta que estoy trabajando en una empresa que se viene mudando de  M$ a Linux, eligiendo Ubuntu por su facilidad. Casi todo ha quedado  cubierto y bien, con un pequeño problema: Access.
 Yo nunca lo he usado, así que desconozco su uso, pero soy el que más  experiencia tiene aquí con Linux, así que me toca investigar.
 He encontrado tres posibles candidatos a ser el «remplazo» de Access:
 
[LIST=1]
[*]Kexi
[*]SQlite
[*]Libreoffice Base
[/LIST]
 ¿Qué opinión tienen sobre estos tres? ¿Cuál el más compatible y fácil  de entender (sabiendo que aquí manejaban todo con M$)? ¿Cual promete  más a futuro? ¿Qué hay de la integración (Kexi es KDE y Base es de  Libreoffice, que viene por defecto)? ¿Facilidad de instalación?...
El tema compatibilidad dependera de como se utiliza actualmente Access en ese lugar.

Si hay macros o scripts de VB involucrados habra que reescribirlos (si es que no estan cerrados).

Con Kexi hasta ahora pude abrir todas las bases Access que se me presentaron pero es una herramienta que no esta pensada en un usuario comun, sin conocimientos ni dominio de lo mas basico del funcionamiento conceptual de bases de datos relacionales y como plantear queries. Es decir, no tiene una interfaz que le ayude a definir las relaciones al estilo Access.

Mi experiencia con OO Base desarrollando una pequeña aplicacion no fue muy satisfactoria porque la version que use, creo que la 3, aun estaba algo verde e inestable a tal punto que a cada rato se rompia la base y, por ende, la aplicacion desarrollada.

Desde el punto de vista estetico y funcional, lo mas parecido a Access es OO/LO Base (digo esto sin haber probado Gnome-db y demas alternativas mencionadas fuera de Kexi).

Pero como dije al principio, la mejor adaptacion/compatibilidad esta relacionada con la forma en que se usa Access en la empresa.

---

