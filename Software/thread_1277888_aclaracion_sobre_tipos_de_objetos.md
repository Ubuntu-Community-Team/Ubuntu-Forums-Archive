---
title: "aclaracion sobre tipos de objetos"
date: 2009-09-28
forum: Software
---

### Post by LolaMora on 2009-09-28
Buenas noches.

Las iniciales de estos ejemplos indican el tipo de objeto.

crw-rw----  1 root   root     10,  63 2009-09-28 16:27 ecryptfs
lrwxrwxrwx  1 root   root          13 2009-09-28 16:27 fd -> /proc/self/fd
brw-rw----  1 root   floppy    2,   0 2009-09-28 16:27 fd0
prw-------  1 root   root           0 2009-09-28 16:27 initctl
drwxr-xr-x  4 root   root         300 2009-09-28 16:29 input
srw-rw-rw-  1 root   root           0 2009-09-28 16:27 log

la "d" es directory (carpetas)
la "l" es link (enlaces)

Necesitaría saber, por favor ¿La "s", la "b", la "p" y la "c" que representan?

Gracias de antemano.

---

### Post by staar on 2009-09-28
la b es de dispositivo de bloque, la c de dispositivo de caracteres, la s de socket, y la p de pipe, toda esta info (y más) la podés encontrar en la página info del comando ls, corriendo en la consola ```
info coreutils ls
``` (está en inglés)

saludos

---

### Post by LolaMora on 2009-09-28
Listo. Quedó aclarado.

A partir de tu dato, encontré información en la wikipedia.

Cuando leí lo que era, vi que era una pavada. 

Uno se complica solito. :P



Gracias Staar

---

