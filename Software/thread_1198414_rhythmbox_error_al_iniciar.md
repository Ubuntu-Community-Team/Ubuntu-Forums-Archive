---
title: "rhythmbox error al iniciar"
date: 2009-06-27
forum: Software
---

### Post by granjero on 2009-06-27
hola amigos ubunteros... les cuento. actualicé a 9.04. estoy contento. lo único raro es que cada vez que abro el rhythmbox me tira este error. en 8.04 con la misma carpeta de musica no me daba ningún error.

me ofrce buscar un plugin pero cuando le pongo que busque el plugin no lo encuentra. lo que quiero hacer es borrar ese archivo pero no lo encuentro. no se como buscarlo.

```
jm@pcjm:~$ rhythmbox
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|Demultiplexor Etiqueta ID3|decoder-application/x-id3
Rhythmbox-Message: No installation candidate for missing plugins found.
```


se les ocurre algo?

gracias de antemano!

---

### Post by pablo.s on 2009-06-27
Podés instalar

```
sudo apt-get install libid3tag0 gstreamer0.10-plugins-base gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad
```

---

### Post by granjero on 2009-06-27
> jm@pcjm:~$ sudo apt-get install libid3tag0 gstreamer0.10-plugins-base gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad
[sudo] password for jm: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
libid3tag0 ya está en su versión más reciente.
fijado libid3tag0 como instalado manualmente.
gstreamer0.10-plugins-base ya está en su versión más reciente.
gstreamer0.10-plugins-ugly ya está en su versión más reciente.
gstreamer0.10-plugins-bad ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

no anduvo che! :confused:

---

### Post by pablo.s on 2009-06-27
Rhythmbox está actualizado
a la versión más reciente?

Actualizaste a Jaunty desde
Hardy? Me parece que por
ahi viene el tema.

---

### Post by granjero on 2009-06-27
no no actualicé, reisntalé todo de cero porque cuando instalé por primera vez no sabía que iba a adoptar linux como SO y dejé mis datos en una partición en FAT32 y ahora formatié todo y tengo todo en ext3. 

así que debe estar instalado el rhythmbox que viene con el ubuntu 9.04 i386 desktop.

> 
Rhythmbox 0.12.0 Software de organización y reproducción de música para GNOME. Copyright © 2005 - 2008 The Rhythmbox authors
Copyright © 2003 - 2005 Colin Walters
Copyright © 2002, 2003 Jorn Baayen esto dice el "acerca de"

salud! :D

---

### Post by granjero on 2009-06-28
no hay forma de encontrar el archivo que provoca el error?

salud!

---

### Post by granjero on 2009-06-30
bueno está parcialmente solucionado el tema. lo que hice fue destildar la casilla que chequea la biblioteca cada vez que inicia. pero me gustaría de solucionar el problema de raíz...

salud!

---

### Post by pablo.s on 2009-06-30
Supongo que con eso 
estaría solucionado.
El tema es que id3 es
el formato de metadatos
de los archivos MP3, y
según parece, Rhythmbox
trata de bajar los datos de
los temas de algún servidor,
calculo para mostrar la tapa
del disco.

---

