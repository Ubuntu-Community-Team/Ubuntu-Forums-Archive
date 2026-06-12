---
title: "[SOLVED] Eliminar particion de Windows y asignarsela a Ubuntu"
date: 2009-08-01
forum: Software
---

### Post by FB91 on 2009-08-01
Actualmente tengo en mi pc instalado Windows y Ubuntu en sus respectivas particiones, lo que quiero hacer es borrar la partición de Windows y que ésta sea "usada" por Ubuntu. 

Gracias ;)

---

### Post by staar on 2009-08-01
```
sudo aptitude install gparted
``` Sistema > Administración > Editor de particiones, seleccionás la partición de Ventanas, y podés hacer varias cosas, le das formatear y le ponés un sistema de archivos libre y bueno (ext3, ext4, reiser, etc), y la usas para guardar datos (la podés montar en el home para que sea accesible más rápidamente), o directamente la eliminás y agrandás la partición de ubuntu para que use todo el espacio que dejó libre...

saludos

---

### Post by FB91 on 2009-08-03
Si quiero agrandar la partición de ubuntu (el /home) no me deja, la opción de redimensionar/mover no aparece habilitada... supongo que antes tengo que desmontarla, pero no me deja.

Otra consulta con respecto a...

>  le das formatear y le ponés un sistema de archivos libre y bueno (ext3, ext4, reiser, etc), y la usas para guardar datos (la podés montar en el home para que sea accesible más rápidamente)

no entiendo bien como sería ya que ya tengo un /home y no me termina de cerrar como quedaría :S acá les dejo una foto de lo que pienso tendría que hacer
[IMG]http://i29.tinypic.com/6p6luw.jpg[/IMG]

---

### Post by staar on 2009-08-03
para redimensionar una partición tiene que estar desmontada, podés hacerlo desde el livecd, pero ojo que tiene que ser continuo el espacio libre y la partición, y en la captura veo que no lo son, en cuyo caso no te convendría, porque tendrías que mover todas las particiones para que queden juntos, y eso toma mucho (mucho) tiempo...

con montarla en tu home no me refería a tu /home, sino a que crees una carpeta en tu carpeta personal, y la montes ahí, sería accesible rápidamente y no notarías la diferencia con una carpeta normal...

saludos

---

### Post by FB91 on 2009-08-03
gracias por la ayuda! entonces voy a hacer eso que me dijiste de montarla en una carpeta dentro de mi home.

una última consulta, la etiqueta (que en la imagen de mi otro post es /home)  quedaría entonces así: /home/micarpeta ?

Gracias! :D

---

### Post by staar on 2009-08-03
la etiqueta es el nombre que le querés poner a la partición, no es obligatorio que coincida con el punto de montaje, son dos cosas diferentes, la etiqueta puede estar vacía...

saludos

---

### Post by FB91 on 2009-08-03
Solucionado! gracias staar!

Para el que este en mi misma situación les digo que me sirvió mucho [esta guía]("http://www.guia-ubuntu.org/index.php?title=Montar_particiones") para montar particiones

Saludos!

---

