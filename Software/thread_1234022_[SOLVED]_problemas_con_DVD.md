---
title: "[SOLVED] problemas con DVD"
date: 2009-08-07
forum: Software
---

### Post by drazhe on 2009-08-07
se que esta recontra posteado, pero no encuentro nada ni en google ni en el propio buscador de este foro.

en principio no puedo reproducir dvds, me saltan carteles de eror y cosas por el estilo, como si faltaran los codecs para decodificarlo, pero cuando le doy al buscar, no encuentra nada y sigo con el problema.

Cuando por fin encontre un dvd que no me haga eso, la reproduccion del mismo es entrecortada.

---

### Post by jpoeta on 2009-08-07
Que errores te aparecen podrías específicar más tal vez podrías subir un par de imagenes  ( capturas de pantalla ) 
Has instalado ya los codecs privativos? 
Saludos 
Jpoeta:popcorn:

---

### Post by drazhe on 2009-08-07
ahora no me aparecen los errores, directamente como que no carga el dvd... con los que si carga, se ven entrecortado, (audio y video)
que codecs privativos tendria que instalar? yo creo que lo hice, pero no estaria mal volverlos a instalar.. solo que no sale ningun cartel ahora...

---

### Post by guillermolisi on 2009-08-07
> **drazhe said:**
> ahora no me aparecen los errores, directamente como que no carga el dvd... con los que si carga, se ven entrecortado, (audio y video)
que codecs privativos tendria que instalar? yo creo que lo hice, pero no estaria mal volverlos a instalar.. solo que no sale ningun cartel ahora...
Cuando todo parece ser problemas de codecs, [lo mejor es leer este thread]("http://ubuntuforums.org/showthread.php?t=1207458")

---

### Post by drazhe on 2009-08-07
guillermolisi

osea que hago esto? y con eso bajara los codecs?

Hola:
Yo lo instale de la siguiente manera:

Añadimos el repositorio de MEDIBUNTU:
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Añadimos la clave del repositorio:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

y desde el siguiente enlace la lista de aplicaciones disponibles. 
[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

¿ cual es la diferencia ?
Gracias, por la respuesta.

---

### Post by drazhe on 2009-08-07
despues de hacer lo que dice el post que me recomendo guillermosi (perdon si escribi mal su nombre) el dvd que antes ni siquiera cargabam ahora lo hace, pero cuando le doy al play aparece un cartel que dice "Ha ocurrido un error, No se puede abrir la direccion, quizas no tiene permiso para abrir el archivo"

los otros que se veian entrecortados, siguen viendose entrecortados...

---

### Post by staar on 2009-08-07
instalá el paquete [libdvdcss2]("apt://libdvdcss2")

saludos

---

### Post by drazhe on 2009-08-07
> **staar said:**
> instalá el paquete [libdvdcss2]("apt://libdvdcss2")

saludos

despues de instalar ese paquete, el que no se veia carga pero es terrible el entrecortado... digamos que no puedo salir de la pantalla que dice "universal" con el mundito.. y eso es el titulo del fabricante nomas.. jejeje.... los anteriores siguen viendose entrecortados... aunque mucho menos, pero aun no es fluida la imagen...


hice lo mismo en otra maquina en la cual tambien tengo ubuntu 9.04 y pasa lo mismo, los dvds que se ven, se ven entrecortados, y este de roger water que se ve que tiene drm directamente no sale de la pantalla de universal... 

tambien trate de abrir los archivos con otro reproductor que no sea el totem, pero pasa lo mismo.. y si se ven arrancan desde cualquier parte y no desde el principio...

---

### Post by staar on 2009-08-07
tenés instalados los drivers con aceleración 3d de tu placa de video?

saludos

---

### Post by drazhe on 2009-08-07
> **staar said:**
> tenés instalados los drivers con aceleración 3d de tu placa de video?

saludos

si, y el conpiz fusion y todo los chiches.. todo anda joya menos la reproduccion de dvd en ambas maquinas.tambien probe deshabilitando el pimpiz y los efectos y todo eso pero aun asi, tengo los problemas detallados anteriormente con el dvd

---

### Post by josecuervo86 on 2009-08-07
Que programa usas para ver los DVDs?

---

### Post by drazhe on 2009-08-07
> **josecuervo86 said:**
> Que programa usas para ver los DVDs?

1ero trate de hacerlo con el que me trajo ubuntu, creo que se llama totem, con este los dvds se ven entrecortados y los que tienen DRM pude ver solo el logo de universal y termine entrecortandose muchisimo mas. despues lo intente con uno que se llama MPlayer movie player, con ese se ven bien, aunque comienza a reproducirse desde cualquier parte del dvd, en vez de ver las instros y cosas asi se ven desde la mitad del documental por ejemplo, al darle al siguiente comienza a reproducir el tema 3 del recital, al otra vez el siguiente y pasa a los extras...

---

### Post by staar on 2009-08-07
totem es malo (en líneas generales), mplayer es mucho mejor, pero la versión que está en los repos de ubuntu creo que no tiene activado el soporte para menús de dvd (algo relativamente nuevo en este reproductor), por lo que tenés que pasar los títulos a mano (podés probar smplayer, un excelente frontend para mplayer)...

también podrías probar vlc o xine (viejito, pero anda bien), aunque los dvd con drm no creo que puedas verlos en linux...

saludos

---

### Post by josecuervo86 on 2009-08-07
+1 para **vlc**, el cortaplumas suizo de los videos (?)

---

### Post by drazhe on 2009-08-07
> **staar said:**
> totem es malo (en líneas generales), mplayer es mucho mejor, pero la versión que está en los repos de ubuntu creo que no tiene activado el soporte para menús de dvd (algo relativamente nuevo en este reproductor), por lo que tenés que pasar los títulos a mano (podés probar smplayer, un excelente frontend para mplayer)...

también podrías probar vlc o xine (viejito, pero anda bien), aunque los dvd con drm no creo que puedas verlos en linux...

saludos


mmmmmmmm y como instalo el vic o el xine? sudo apt-get xine y lo mismo para el vic?

---

### Post by josecuervo86 on 2009-08-07
> **drazhe said:**
> mmmmmmmm y como instalo el vic o el xine? sudo apt-get xine y lo mismo para el vic?

```
 sudo apt-get **install** vlc 
``` Asi de facil. O si no desde synaptic

---

### Post by drazhe on 2009-08-07
Gracias a todos, el VIC funciono perfectamente, incluso con el dvd de roger water que tiene DRM.. 

una pregunta mas, no me molesta, pero seria mejor que no lo hiciera, es normal que pegue unos saltos entre videos? es decir, entre el titulo de universal, al menu de seleccion de recital, temas, sonido, etc, pegua como un salto la pantalla.. es normal que pase eso? si se lo puede solucionar mejor...

---

### Post by josecuervo86 on 2009-08-07
No se si normal, pero a mi a veces me lo hace.

---

