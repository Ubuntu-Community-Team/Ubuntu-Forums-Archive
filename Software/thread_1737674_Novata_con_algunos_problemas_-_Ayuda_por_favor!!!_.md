---
title: "Novata con algunos problemas - Ayuda por favor!!! Gracias"
date: 2011-04-23
forum: Software
---

### Post by lorenafavario on 2011-04-23
Hola a todos:

Despues de varios meses dando vueltas he migrado completamente a linux (Por fin!!!)
Mi ubuntu es un 10.10 y estoy super contenta con el... pero.....
Tengo 3 problemitas que aun no les he encontrado la vuelta.

1) Quiero convertir mis videos (formatos varios como mpeg, flv, directo desde un dvd, etc) a mp4 o 3 gp para poder verlos en mi celular (es un GD330 de LG). Desde que tengo linux no encuentro como hacerlo y el codec que acepta del celu para los mp4 es H263 y no el H264. 

2) Extraño mucho un juego online que usaba antes con windows, se llama IMVU y es un chat 3D tipo entorno virtual. Trate con wine y nada. Tengo el Play on linux pero no estoy segura de que tengo que hacer.

3) Otro juego que quisiera seguir jugando es Los SIMS 3 pero tampoco me doy idea de como hacerlo andar en mi ubuntu 10.10 y en la comunidad de sims nadie la tiene demasiado clara.

Realmente agradeceria que me ayuden asi mi experiencia seria completamente fuera de este mundo.

Tambien agradecere toda info sobre manuales y tutoriales que tengan que ver con edicion de video y sonido ya que soy una fanatica de filmar y editar mis cosas.

---

### Post by gmunioz on 2011-04-24
Respecto de juegos, nada, solo pysolfc.
Respecto de conversión de video:

Prueba utilizar enkodeur (ekd), para instalarlo en Maverick:

Bajas este archivo:
[http://glouk.legtux.org/gmic_apt/pool/contrib/g/gmic/gmic_1.4.8.2_i386.deb](http://glouk.legtux.org/gmic_apt/pool/contrib/g/gmic/gmic_1.4.8.2_i386.deb)
Dando doble click sobre el desde Nautilus, lo instalas.

A continuación
En una consola (Aplicaciones - Accesorios - Terminal) ejecutas:

sudo su

wget [http://download.tuxfamily.org/ekdforum/ekd/cle-ekd.key.asc](http://download.tuxfamily.org/ekdforum/ekd/cle-ekd.key.asc) -O- | apt-key add -

gedit /etc/apt/sources.list

En el archivo agregas al final esta línea

deb [http://download.tuxfamily.org/ekdforum/ekd](http://download.tuxfamily.org/ekdforum/ekd) maverick contrib

Guardas el archivo
Cierras gedit
Continuas ejecutando:

apt-get update

apt-get install ekd libsox-fmt-all libsox-fmt-alsa libsox1a libsox-fmt-ao libsox-fmt-base libsox-fmt-fmpeg libsox-fmt-mp3 libsox-fmt-oss libsox-fmt-pulse mplayer mencoder subversion python-qt4 python-imaging python-numpy ffmpeg ffmpeg2theora imagemagick lame mjpegtools

Luego de instalado, edita el menu y en comando donde dice /usr/bin/ekd deja solo ekd

Su manual de uso esta aquí:
[http://ekd.tuxfamily.org/index.php/Documents/LinuxEnglish](http://ekd.tuxfamily.org/index.php/Documents/LinuxEnglish)

---

### Post by lorenafavario on 2011-04-24
Gracias x tu respueta!!!!

Lo pruebo y te cuento como salio la cosa.
Espero que bien ya que extraño muchos mis videos...

Un abrazo
Lorena:KS

---

### Post by juancarlospaco on 2011-04-26
> **lorenafavario said:**
> 
1) Quiero convertir mis videos (formatos varios como mpeg, flv, directo desde un dvd, etc) a mp4 o 3 gp para poder verlos en mi celular (es un GD330 de LG). Desde que tengo linux no encuentro como hacerlo y el codec que acepta del celu para los mp4 es H263 y no el H264. 

[Arista Transcoder]("http://apt.ubuntu.com/p/arista")

> **lorenafavario said:**
> 
2) Extraño mucho un juego online que usaba antes con windows, se llama IMVU y es un chat 3D tipo entorno virtual. Trate con wine y nada. Tengo el Play on linux pero no estoy segura de que tengo que hacer.

No conosco que es, pero encontre esto: 
[http://www.imvu.com/catalog/modules.php?op=modload&name=phpbb2&file=viewtopic.php&t=160996](http://www.imvu.com/catalog/modules.php?op=modload&name=phpbb2&file=viewtopic.php&t=160996)

> **lorenafavario said:**
> 
3) Otro juego que quisiera seguir jugando es Los SIMS 3 pero tampoco me doy idea de como hacerlo andar en mi ubuntu 10.10 y en la comunidad de sims nadie la tiene demasiado clara.

No se si es lo mismo, pero es Libre y de Genero parecido:
[http://wildfiregames.com/0ad/](http://wildfiregames.com/0ad/)
[http://wildfiregames.com/0ad/page.php?p=14425](http://wildfiregames.com/0ad/page.php?p=14425)

Este Juego es un Clon Libre de SIMS, pero no se si esta terminado aun:
[http://www.la-vida-game.co.uk/?page_id=11](http://www.la-vida-game.co.uk/?page_id=11)

> **lorenafavario said:**
> 
Tambien agradecere toda info sobre manuales y tutoriales que tengan que ver con edicion de video y sonido ya que soy una fanatica de filmar y editar mis cosas.

Podes comenzar explorando la web de OpenShot:  [http://www.openshotvideo.com/](http://www.openshotvideo.com/)
:)

---

### Post by lorenafavario on 2011-04-28
Hola Gabriel:

Aca estoy nuevamente. La verdad es que no pude hacer lo que me dijiste x que no entiendo muy bien como usar el terminal y le tengo miedo a hacer desastre.
Pero baje Acidrip y Movil Media converter.
el video obtenido se veia en mi celular pero.... se trababa mucho para reproducirlo asi que no me dejo conforme.
Vere si averiguo mas sobre el terminal y como se usa y ahi pruebo otra vez...
Gracias x tu ayuda.
Lorena

---

### Post by lorenafavario on 2011-04-28
Hola Juan:

Arista no funciono los videos no funcionan mi celular y no usa H263.
En un rato chequeare el link de IMVU pero todo lo que busque y lei y probe no funciono.
El juego clon de los SIMS aun no es jugable y el otro no es como los que me gustan, pero igual es bueno es dato, gracias.
Open Shot Video editor es el programa que ya estoy usando y anda que es una belleza. Muy bueno.
Gracias y despues te cuento como salio lo de IMVU.
Lorena

---

