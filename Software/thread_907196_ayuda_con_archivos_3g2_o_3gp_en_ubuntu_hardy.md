---
title: "ayuda con archivos 3g2 o 3gp en ubuntu hardy"
date: 2008-09-01
forum: Software
---

### Post by darkarcangel_sam on 2008-09-01
hola ¡¡¡

mmmm ...

quiero saber si alguien sabe como reproducir los archivos 3g2 o 3gp q son para celular en ubuntu hardy.

lo q pasa es q toda una serie completa de anime la tengo en ese formato y pues como es calidad dvd pues x eso no la quiero borrar 

asi q si saben diganme o diganme si hay agun convertor de archivos q sea bueno para ubuntu 



SAM
:guitar:

---

### Post by sebasthian777 on 2008-09-01
> **darkarcangel_sam said:**
> hola ¡¡¡

mmmm ...

quiero saber si alguien sabe como reproducir los archivos 3g2 o 3gp q son para celular en ubuntu hardy.

lo q pasa es q toda una serie completa de anime la tengo en ese formato y pues como es calidad dvd pues x eso no la quiero borrar 

asi q si saben diganme o diganme si hay agun convertor de archivos q sea bueno para ubuntu 



SAM
:guitar:

a mi me funco este mira...
[http://grk-t.blogspot.com/2008/03/ver-videos-3gp-en-ubuntu.html](http://grk-t.blogspot.com/2008/03/ver-videos-3gp-en-ubuntu.html)

en cuanto a convertilos no busque tdb :P suerte y contame!

---

### Post by gmunioz on 2008-09-01
Hola dar....:
Un conversor muy bueno es ffmpeg
Lo instalas con:
sudo apt-get install ffmpeg
Lo ejecutas con:
ffmpeg -i nombrearchivo.3gp -f avi -acodec mp3 nombrearchivo.avi 
ó con
ffmpeg -i nombrearchivo.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 nombrearchivo.avi
Tambien sirve para otros formatos:
Flv a avi
ffmpeg -i nombrearchivo.flv nombrearchivo.avi
Flv a mpeg 
ffmpeg -i nombrearchivo.flv nombrearchivo.mpeg
Avi a 3gp
ffmpeg -i nombrearchivo.avi-s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y nombrearchivo.3gp
Mpg a 3gp
ffmpeg -i nombrearchivo.mpg -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -ab 32 -y nombrearchivo.3gp
En modo gráfico puedes intentarlo con avidemux.
Saludos.
Gabriel.
*Solo doy soporte a Ubuntu* - **6666 **- *Más malo que el diablo*

---

### Post by Kabezon on 2008-09-01
Perdón, los videos 3g2 no son los que graban los celulares? Eso con cualquie reproductor funcan o.O Lo que pasa es que te deben faltar codecs... 

Agregá el repo de Medibuntu primero:
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Y después instalá todos los codecs que necesitás para reproduccir prácticamente cualquiercosa (Al menenos hasta el día de hoy lo que le tire me lo reproduce) **OJO**, este comando si no estás en Ubuntu Hardy Heron 8.10 de 32bits no lo usés... Si usás otra distro seguí el link que te doy más abajo.
> sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

**[Guía: Multimedia en Ubuntu]("http://quekabeza.blogspot.com/2008/08/gua-multimedia-en-ubuntu.html")**

Uh, recién leo bien el título entero del thread xD

---

### Post by darkarcangel_sam on 2008-09-02
gracias a los 3 me sirvio :) ...

hice casi todo e instale algo de todos muchas gracias 

SAM

---

