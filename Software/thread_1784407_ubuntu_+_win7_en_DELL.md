---
title: "ubuntu + win7 en DELL"
date: 2011-06-16
forum: Software
---

### Post by krakc on 2011-06-16
hola

tengo una DELL nueva (vostro 3550) que viene con win 7 pro, la cuestion es que quiero instalarle ubuntu dejando el win7 que trae por defecto, se puede sin dañar la particiòn de recovery etc...

que pasos debo seguir?

gracias.

---

### Post by marohds on 2011-06-17
Hola,
 
Supongo que no tendría problemas en redimensionar la partición del W7 y generar un espacio libre para Ubuntu con cualquier manager de disco... eg Gparted Live
 
Aunque acá hay una guía que lo hace desde el mismo W7 y te explica cómo instalar Ubuntu luego:
 
[http://sliceoflinux.com/2011/04/28/instalar-ubuntu-11-04-paso-a-paso/](http://sliceoflinux.com/2011/04/28/instalar-ubuntu-11-04-paso-a-paso/)
 
Otro tutorial actualizado a Ubuntu 11.04
 
[http://www.datanoia.com/tutorial-como-instalar-ubuntu-9-04-sin-formatear-windows.html](http://www.datanoia.com/tutorial-como-instalar-ubuntu-9-04-sin-formatear-windows.html)
 
 
Suerte!

---

### Post by asterix77 on 2011-06-17
Efectivamente con gparted live no hay problemas en redimensionar la partición de win7. De hecho alguna vez lo hice de esa forma. Mi único "error", fue el haber creado solo una partición "raíz" para ubuntu, ya que al cabo de poco tiempo apareció una nueva versión de ubuntu al cual quise actuaizar desde un live-cd, y tuve que respaldar todo mi home primero y luego formatear.

Ahora tengo una partición para el directorio "raiz", y una para mi directorio "home" y he quitado win. De modo que no tengo nada que respaldar antes de formatear e instalar una nueva versión.

Suerte y saludos

---

### Post by mano negra on 2011-06-18
Hola,
  Luego de tantas veces preguntar, ahora voy a responder. 
  Te cuento mi experiencia. No soy un experto. Yo tengo una inspiron nuevita. Con el  gparted del live-cd lo haces. Lo que si fijate bien cuanta memoriavas a necesitar en win7, porque sino vas a tener que formatear todo de vuelta,  no podes cambiar de lugar así porque si con el gparted (me pasó).
  Pero lo más importante: hay un programa que viene de fábrica con las dell que sirve para crear un un disco de respaldo con toda la configuración de fábrica, entre otras cosas. Como ser, que te borra el grub cuando optas por usar win7 en el arranque. He visto algunas soluciones que eran muy laboriosas porque tenía que manipular las particiones que venían de fábrica. Así que la solución más directa fue eliminar el susodicho programa.

Salu

---

