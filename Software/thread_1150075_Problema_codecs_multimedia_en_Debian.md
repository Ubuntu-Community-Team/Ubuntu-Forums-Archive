---
title: "Problema codecs multimedia en Debian"
date: 2009-05-05
forum: Software
---

### Post by ramiro_md on 2009-05-05
Bueno, nuevamente posteando problemas con Debian je. Resulta que instalé Lenny en uan partición más grande y a la hora de instalar los codecs multimedia no libres lo hice de la misma manera que siempre:
```
aptitude install libfaad2-0 libmp4-0 libfaac0 alsamixergui toolame lame libmp3lame0 libdvdnav4 libdvdread3 libdvdcss2 w32codecs  avifile-divx-plugin ffmpeg
```
Obviamente antes ejecuto alsaconf. El tema es que al querer reproducir un archivo, ya sea de audio o de video, de alguno de estos codecs no libres totem me da los siguientes errores, como si no estuvieran instalado los paquetes necesarios para reproducir estos formatos multimedia.
-Al intentar reproducir un mp3:
La reproducción de esta película requiere un complemento decodificador MPEG-1 Layer 3 (MP3) que no está instalado.
-Al intentar reproducir un mpg:
La reproducción de esta película requiere un complemento demultiplexor MPEG-2 System Stream que no está instalado.
-Al intentar reproducir un avi:
La reproducción de esta película requiere los siguientes decodificadores que no están instalados:
decodificador MPEG-1 Layer 3 (MP3)
decodificador DivX MPEG-4 versión 5 (avi)
Obviamente con los ogg no tengo ningún tipo de inconveniente. Realmente he buscado en foros de debian y wikis y todos han instalado los codecs de la misma manera que yo y les ha funcionado.
Por estas cosas de la computación vaya uno a saber por qué en un pasado a mi también me anduvo este metodo y hoy no. Bueno espero alguna sugerencia, consejo o solución :O.
Un saludo, y gracias.

---

### Post by ramiro_md on 2009-05-05
Navegando por synaptic encontré un paquete que debe ser útil para lo que necesito: mpeg3-utils y me dí cuenta que es libmp4v2-0 y no libmp4-0. Aún con estos dos paquetes instalados sigue sin funcionar :S.

---

### Post by ramiro_md on 2009-05-05
BUeno, resolví a media el problema. Con respecto al audio, instalé amarok y salió andando...vaya uno  a saber porque totem no quería reproducir nada.
Instale vlc y los videos mpg los reproduce :) los avi no :(. Con MPlayer no reproduzco nada, aclaro que los audios si se escuchan en los videos.
VLC tira este error en la consola:
> main decoder error: no suitable decoder module for fourcc `DX50'.
VLC probably does not support this sound or video format.
Noté que si abro un archivo con mplayer desde alt + f2 anda bien :confused:

ESpero que con estos datos me puedan dar una mano jeje.

---

