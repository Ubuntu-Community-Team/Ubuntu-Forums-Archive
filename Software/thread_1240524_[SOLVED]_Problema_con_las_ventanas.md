---
title: "[SOLVED] Problema con las ventanas"
date: 2009-08-14
forum: Software
---

### Post by lucasgz on 2009-08-14
bueno primero que nada soy nuevo:KS hace poco instale ubuntu 9
el problema que tengo es que cuando quiero abrir una carpeta, sea "equipos", escritorio, carpetas personales o la papelera de reciclaje, me pide tiempo, aparece en la barra de abajo " abriendo equipos" y luego se cierra.

otro problema es que no puedo hacer click derecho en escritorio, no me lo toma.

y tampoco se ven los iconos en escritorio, y estan porque con el editor de texto puedo abrir las carpetas.

ademas no puedo intalar ningun driver porque asi no puedo abrir el cd.



al principio me andaba bien , cuando cambie la resolucion de pantalla ahi se arruino:confused:
google y busque pero no encotre nada de esto, probe cambiar la apariencia virtual(creo q se llama asi) en el archivo xorg.config pero parece q no es eso ,ya probe varias combinaciones

bueno si alguien me puede ayudar se los agradesco porq asi no lo puedo usar:(

ah tmb probe reinstalar y sigue el problema

---

### Post by staar on 2009-08-14
> el problema que tengo es que cuando quiero abrir una carpeta, sea "equipos", escritorio, carpetas personales o la papelera de reciclaje, me pide tiempo, aparece en la barra de abajo " abriendo equipos" y luego se cierra.

otro problema es que no puedo hacer click derecho en escritorio, no me lo toma.

y tampoco se ven los iconos en escritorio, y estan porque con el editor de texto puedo abrir las carpetas. todo eso es un mismo problema, nautilus (el progrma que maneja el escritorio y que sirve de navegador de archivos) se está cerrando, hacé una cosa, abrí un Terminal (en Aplicaciones > Accesorios), poné ```
killall nautilus
``` para matar el que está corriendo, y después poné ```
nautilus
``` para abrirlo de nuevo, intentá entrar de nuevo a Equipo, se te va a cerrar, pero en la Terminal te va a salir el error que reportó antes de morir, copia lo que salga y postealo acá para que te podamos ayudar...

> ademas no puedo intalar ningun driver porque asi no puedo abrir el cd.
ojo, los drivers de Ventanas no funcionan acá, linux incluye la mayor parte de los drivers que vas a necesitar, los únicos que vas a necesitar instalar aparte son los de la placa de video y los de algunas placas wifi, y esto se hace desde Sistema > Administración > Controladores de hardware

> al principio me andaba bien , cuando cambie la resolucion de pantalla ahi se arruino
google y busque pero no encotre nada de esto, probe cambiar la apariencia virtual(creo q se llama asi) en el archivo xorg.config pero parece q no es eso ,ya probe varias combinaciones eso depende de la placa de video que tengas, y de si tenés instalados los drivers privativos desde Controladores de hardware...

saludos

---

### Post by lucasgz on 2009-08-14
bueno me tiro esto

lucas@lucas-desktop:~$ killall nautilus
nautilus: ningún proceso eliminado
lucas@lucas-desktop:~$ nautilus
Fallo de segmentación
lucas@lucas-desktop:~$ nautilus
Fallo de segmentación
lucas@lucas-desktop:~$ 

y por las dudas probe con sesion root


root@lucas-desktop:~# killall nautilis
nautilis: ningún proceso eliminado
root@lucas-desktop:~# nautilus

** (nautilus:3639): WARNING **: Unable to add monitor: No soportado
Fallo de segmentación
root@lucas-desktop:~#

---

### Post by staar on 2009-08-14
tenés instalado ubuntuone?

saludos

---

### Post by lucasgz on 2009-08-14
nose solo intale el ubuntu 9
y lo baje de aca [http://www.ubuntu.com/](http://www.ubuntu.com/) hace 2 o 3 semanas digo por si ese tiene algun fallo o algo raro

---

### Post by pablo.s on 2009-08-14
Actualizá Nautilus
y Gvfs en Synaptic.

---

### Post by lucasgz on 2009-08-15
me puse a ver como poner internet en ubuntu y acualize todo
ya se arreglo muchas gracias:P

---

