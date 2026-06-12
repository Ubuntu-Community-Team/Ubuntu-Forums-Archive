---
title: "Hola, no puedo instalar ni desinstalar nada!"
date: 2009-10-28
forum: Software
---

### Post by Don_Chester on 2009-10-28
Hola, comunidad!
soy un user de ubuntu desde hace ya un buen rato [llevo como 2 años], jamás tuve problemas, hasta hace un rato atrás.

Les explico:
queria desinstalar unos programas que ya casi ni uso, como pa alivianarme un poco y reorganizarme.
Pero cuando accedí en un principio a Aplicaciones>Añadir y quitar, me aparece este mensaje. 
[IMG]http://i33.tinypic.com/2dw50ly.png[/IMG]



A continuación veo en el área de notificaciones lo sgte: 
[IMG]http://i37.tinypic.com/2lsjs47.png[/IMG]

Cuando pongo el cursor sobre el círculo rojo me aparece este mensaje: 

**"Ha ocurrido un error; por favor, ejecute el Gestor de paquetes desde el menú contextual o apt-get en una terminal para ver dónde está el problema. El mensaje de error fue: 'Error: Abriendo la caché (E:Type 'sudo' in not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.)'Normalmente, esto significa que ha instalado paquetes cuyas dependencias no se han podido satisfacer"**



También revisé en Synaptic: 

[IMG]http://i36.tinypic.com/mkwyu8.png[/IMG]

Espero que me puedan ayudar.

Gracias



Don_Chester

---

### Post by Carlos C on 2009-10-28
mira tu archivo /etc/apt/sources.list y fíjate en la línea 54. Copia acá lo que aparece en esa linea.

Saludos.

---

### Post by themasterdark on 2009-10-28
debe ser que esa linea que te indica, es indebida tiene algun fallo en la forma que deberia estar escrita.

Como te dijieron pega la linea 54 de /etc/apt/sources.list

para ver que le pasa.
Saludos

---

### Post by Don_Chester on 2009-10-29
no pude adjuntar el archivo, pero esto es lo que tengo 
[http://rapidshare.com/files/299831183/sources.list.html](http://rapidshare.com/files/299831183/sources.list.html)

es más no me llega a la linea 54
 :S

ojala que se pueda resolver, por si les sirve uso ubuntu 9.04 [aunque estoy descargando la actualizacion, pero qiero ver si es posible resolver esto]


gracias

---

### Post by AlexDDR on 2009-10-30
borra donde dice 

sudo apt-key add -


no se como se coló eso ahí pero esta demás y asegurate de que el archivo no tenga varias lineas en blanco mas alla de la ultima 

saludos

---

### Post by Don_Chester on 2009-10-31
gracias, alexddr!
editando el archivo en cuestion, ahora puedo instalar o desinstalar los programas que se me antojen 

ahora, ¿como se me paso "sudo apt-key add -"? ni yo lo sé.

Gracias por la aclaración




CASO CERRADO!

---

### Post by moreback on 2009-10-31
> **Don_Chester said:**
> ahora, ¿como se me paso "sudo apt-key add -"? ni yo lo sé.

De seguro que estabas aplicando una guía para instalar algun programa y no te fijaste que ejecutaste un comando erróneamente. Ese comando es típico al agregar llaves gpg de algún PPA.

Para la otra pon más atención a lo que escribes en la consola y sobretodo si ejecutas con sudo.

Saludos.

:KS

---

### Post by AlexDDR on 2009-10-31
solo para complementar, seguro llego ahi con el comando ECHO que agrega lineas al sources list y quedo dentro de lo que agrega el comando siguiente que agrega y las claves de ppa

saludos

---

