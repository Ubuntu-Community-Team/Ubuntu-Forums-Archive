---
title: "que me informa el comando ls -l"
date: 2009-08-25
forum: Software
---

### Post by LolaMora on 2009-08-25
Buenas.

Alguien me podría asesorar que significan los números cuando hacemos "ls -l"? Ejemplo:

ls -l

total 15096

drwxr-xr-x 3 alumno alumno    4096 2009-08-25 20:11 Escritorio
-rw-r--r-- 1 alumno alumno     357 2009-08-22 17:18 examples.desktop
drwxr-xr-x 2 alumno alumno    4096 2009-08-25 18:18 Fotos
drwxr-xr-x 2 alumno alumno    4096 2009-08-22 18:24 Imágenes
-rw-r--r-- 1 root   root      5924 2009-08-22 20:12 index.html
-rw-rw-rw- 1 root   root      5906 2009-08-22 20:12 index.html.1
-rw-r--r-- 1 alumno alumno       0 2009-08-24 21:41 lista

Me refiero los números que están a continuación de los permisos.(3, 1, 2..)

Hasta pronto.

---

### Post by Mauro22 on 2009-08-25
Ese numero es el contador de enlaces que tiene ese objeto... el 'hard link'::


Segun nuestro amigo la wikipedia:

[http://es.wikipedia.org/wiki/Enlace_duro](http://es.wikipedia.org/wiki/Enlace_duro)

---

### Post by LolaMora on 2009-08-25
Muchas gracias Mauro22 por desasnarme.  :)

---

### Post by moicartagena on 2011-05-07
> **Mauro22 said:**
> Ese numero es el contador de enlaces que tiene ese objeto... el 'hard link'::


Segun nuestro amigo la wikipedia:

[http://es.wikipedia.org/wiki/Enlace_duro](http://es.wikipedia.org/wiki/Enlace_duro)


Y el *total 15096* que significa?

---

