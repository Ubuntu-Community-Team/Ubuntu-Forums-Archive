---
title: "Ayuda con creacion de menu BOOT para reinstalacion en Netbooks"
date: 2008-12-27
forum: Software
---

### Post by miguelon.- on 2008-12-27
Hola! que tal,queria saber como se podria crear un menú que permita seleccionar varias opciones,en este caso sistemas operativos. La idea es hacer un USB con Ubuntu y un Windows XP para poder instalar uno de ellos a mi elección en una Netbook( mini notebook SIN lectora de cd/dvd).
Mi idea es algo asi:

Menú selección de SO
********************
1- Instalar Ubuntu 8.10
2- Instalar Windows XP


Espero que se entienda lo que necesito, muchas gracias.

---

### Post by Hei Ku on 2008-12-27
Hay varias herramientas para customizar instaladores. Y esas herramientas incluyen la posibilidad de bootear de otra partición, que sería lo que querés hacer en este caso para instalar XP. La forma de hacerlo depende de cada herramienta en particular.

---

### Post by miguelon.- on 2008-12-27
ajam, y no se puede hacer como una especie de script o archivo bat para hacer el menu? una especie como el menú del hiren boot. La verdad que no se mucho del tema y me gustaria poder hacer esto,ya que puedo tener muchos SO en un pendrive y a la hora de reinstalar elegir cual quiero. muchas gracias por ayudar igual.:)

---

### Post by Hei Ku on 2008-12-27
Si, supongo que se puede. Pero en ese caso tendrías que buscar algo no-linux me parece. No sé cuál es tu idea, si usar GRUB u otra herramienta. De eso va a depender cómo lo hagas.

En resumen, me parece que no tenés claro cómo es la arquitectura general de tu solución. Yo empezaría por ahí antes de preocuparme por el menú, que va a depender de decisiones previas en ese sentido.

---

### Post by miguelon.- on 2008-12-27
claro,la verdad no se como crearlo,pero en base lo que quiero es conectar mi pendrive y que cuando bootee desde él,me aparesca un menú que me permita elegir que instalar,la verdad no se como hacerlo,ayuda porfa! :confused::P

---

### Post by faktorqm on 2008-12-28
Para hacer instaladores de Linux tenes Unetbootin, remastersys y el paquete liveusb por ejemplo. (este ultimo creo que no sirve para lo que queres hacer).
Un buen bootloader, GRUB, para hacer la instalacion de linux. De "lo otro" ni idea. Salu2!

---

