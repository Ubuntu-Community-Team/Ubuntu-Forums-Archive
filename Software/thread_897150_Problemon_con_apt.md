---
title: "Problemon con apt"
date: 2008-08-21
forum: Software
---

### Post by sdm_cacto on 2008-08-21
Bueno, resulta q queria ahorrar espacio en el disco y me parecio una gran idea eliminar la carpeta /var/cache/ (pensando q era una carpeta temporal). El tema es q ahora no anda apt-get ni synaptic ni nada para actualizar el sistema.

Este es el error q tira:

> Falta el directorio de archivos /var/cache/apt/archives/partial.
E: No se puede escribir en /var/cache/apt/
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

sudo dpkg-reconfigure aptitude no funciona.

Que debo hacer? compilaro desde cero o dejarme de joder y reinstalar??

gracias por leerme

---

### Post by Hei Ku on 2008-08-21
pone su mkdir /var/cache/apt

despues corre un update otra vez, y fijate que otras carpetas te va pidiendo. Pero me parece que estás en problemas.

La proxima, para ahorrar espacio, hace un clean o autoclean

---

### Post by faktorqm on 2008-08-22
yo tengo, /var/cache/apt; adentro una carpeta archives y adentro de archives tengo una carpeta partial, un archivo de bloqueo (lock) y los paquetes que bajo apt.
yo tengo un ubuntu en un disco de 4.3gb, y lo que hice es borrar la ayuda, ahora no me acuerdo exactamente en que carpeta estaba, pero vos cada vez que abris un programa y vas a ayuda o apretas F1 te abre algo de esa carpeta. lo borre y salve unos 400mb tranquilos. lo que no me anime a borrar son las paginas man de los comandos, creo que eso mejor dejalo jajajaj
despues como dijo hei ku hay que hacer apt-get clean, autoclean lo que hace es desinstalarte y borrarte del sistema los paquetes que quedaron obsoletos luego de una actualizacion.
despues otra cosa que ocupa lugar son los themes, yo en mi caso le tire la interfaz grafica abajo, es un gnome practicamente sin sensacion 3d, todos los botones planos, todo rapido pero feo y  borre los iconos, los temas, los salvapantallas, los fondos, y todo lo que sea """"""eyecandy"""""" default de la instalacion.
Despues tambien con el synaptic fui paquete por paquete desinstalando absolutamente todo lo que no necesitaba.
No se si necesitas tan extremo pero por lo menos te tire algunos tips. Salu2!!

---

### Post by sdm_cacto on 2008-08-22
Jaaja joya, lo solucione con el primer post, y el segundlo es un gran consejo.
tengo q controlarme un poco la proxima.

gracias gente

---

### Post by Hei Ku on 2008-08-22
y la medallita???? :lolflag: :p

---

