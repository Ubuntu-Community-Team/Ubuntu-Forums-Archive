---
title: "[SOLUCIONADO] Problema menu &quot;Lugares&quot;"
date: 2009-06-12
forum: Software
---

### Post by Transgenic on 2009-06-12
Esto empezo a suceder hoy, sin hacerle nada a Ubuntu (9.04). Trato de acceder a mis carpetas desde el menu Lugares, y me sale el siguiente error: No se puede abrir el lugar «file:///home/usuario/Escritorio» No hay ninguna aplicación registrada para manejar este archivo
Ayer solo instale gnome colors, shiki y desinstale rhythmbox y una mascota virtual (xD) que se instalaba como "amor" por medio de la consola.. no sabia como desintalarla y por ahi lei que con *sudo apt-get purge amor* se podia, y asi fue.. pero no creo que eso halla sido el causante.. ¿o si? :(

---

### Post by CdK1 on 2009-06-12
Trata de hacer lo mismo pero en una consola pon esto:

tail -f .xsession-error

y pega lo que sale...

---

### Post by Transgenic on 2009-06-12
```
usuario@asdf-desktop:~$ tail -f .xsession-error
tail: no se puede abrir «.xsession-error» para lectura: No existe el fichero ó directorio
tail: no queda ningún fichero
```:|

Por cierto, puedo explorar las carpetas si abro la Papelera.

---

### Post by CdK1 on 2009-06-12
Tienes "nautilus" instalado? y ademas pegame lo que sale con este comando:

 ls -l /home/$USER/.x*

---

### Post by Transgenic on 2009-06-13
Nautilus si esta instalado. 

Aca el resultado:

```
transgenic@X-458-desktop:~$ ls -l /home/$USER/.x*
-rw-r--r-- 1 transgenic transgenic  129 2009-06-05 15:59 /home/transgenic/.xscreensaver-getimage.cache
-rw-r--r-- 1 transgenic transgenic 5242 2009-06-13 10:36 /home/transgenic/.xsession-errors

/home/transgenic/.xine:
total 24
-rw-r--r-- 1 transgenic transgenic 23911 2009-05-31 17:52 catalog.cache

/home/transgenic/.xmms:
total 16
-rw-r--r-- 1 transgenic transgenic 1737 2009-06-12 16:13 config
drwxr-xr-x 2 transgenic transgenic 4096 2009-06-12 16:13 Plugins
drwxr-xr-x 2 transgenic transgenic 4096 2009-06-12 16:13 Skins
-rw-r--r-- 1 transgenic transgenic    8 2009-06-12 16:13 xmms.m3u

```


--

Ahora que recuerdo, estuve viendo alguna configuracion que no recuerdo, pero tenia efecto en el navegador de archivos, en la solapa Informacion... ahi se ve el icono de la carpeta y abajo habian botones para abrir la carpeta con determinados programas y/o comandos (Reproductor de peliculas, Banshee, XMMS)... no recuerdo como llegue a la configuracion de esos botones, y ahora no estan... quizas pudo influir en algo :(

---

### Post by Transgenic on 2009-06-13
Sorry por el doble post, pero solucione el tema!
Lo que hice fue hacer click derecho en una carpeta cualquiera y poner Abrir con otra aplicacion, luego elegi Navegador de archivos y ahora todo el menu Lugares funciona bien :D

Ojala no le pase a nadie xD
Gracias!

---

