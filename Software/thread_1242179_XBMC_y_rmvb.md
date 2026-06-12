---
title: "XBMC y rmvb"
date: 2009-08-16
forum: Software
---

### Post by Fak89 on 2009-08-16
Estuve buscando por varios lugares y no pude encontrar algo que realimente me ayudara.
Mi problema es que quiero reproducir películas en formato rmvb con el media center XBMC y obviamente, no puedo..
Alguien me podría explicar como hacer para que XBMC use los codecs?

Pd. tengo codecs instalados ya que Totem reproduce estos archivos, aunque MPlayer no lo hace tampoco..

---

### Post by Mister X on 2009-08-17
tengo entendido que xbmc usa sus propios codecs y no los que tengas instalados

---

### Post by totolinux on 2009-08-17
Hola: mirá yo tengo instalado xbmc y el formato rmvb se ve bien, lo que si tarda muuucho en arrancar pero xbmc definitivamente si los reproduce. Me parece que es por eso que no encontras nada, proba con otro archivo rmvb y esperá un rato 2 0 3 min. saludos y contanos como te fue.

---

### Post by Fak89 on 2009-08-17
Bueno, espere 2 minutos y.. no pude mas jaja..
Igual no quiero perderme los primeros 5 minutos de las peliculas jaja

Alguien tiene idea algun comando para pasar este formato a avi sin que pierda la calidad ni resolucion?

---

### Post by guillermolisi on 2009-08-17
Fijate si [lo que esta en este post]("http://ubuntuforums.org/showpost.php?p=7750200&postcount=8") funciona para vos

---

### Post by totolinux on 2009-08-17
Que lastima que no te funciona, pero no te perdes nada de el video porque solo esperas que arranque desde el inicio. Lo que si me parece, que no a todos se nos comporta de la misma manera. He leído que algunos miran tv con determinado script pero yo no puedo y algún skin me lo cuelga por completo.
Va, no me cierra del todo. En realidad me gusta más Elisa pero me trae dolores de cabeza peores. como la resolución en la tv que no puedo modificar pero es otro tema. saludos

---

### Post by Fak89 on 2009-08-17
> **guillermolisi said:**
> Fijate si [lo que esta en este post]("http://ubuntuforums.org/showpost.php?p=7750200&postcount=8") funciona para vos

Me tira esto despues de el comando, no puedo reconocer que me falta

```

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
[NULL @ 0xd9b780]Unsupported video codec
Input #0, rm, from '/home/facundo/Peliculas/Bourne_Ultimatum/p-JasBourne03.rmvb':
  Duration: 01:48:25.21, start: 0.000000, bitrate: 502 kb/s
    Stream #0.0: Audio: cook, 44100 Hz, stereo, s16, 64 kb/s
    Stream #0.1: Video: rv40, yuv420p, 640x272, 430 kb/s, 12 tbr, 1k tbn, 12 tbc
    Stream #0.2: Data: 0x0000
File '/home/facundo/Peliculas/Bourne_Ultimatum.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to '/home/facundo/Peliculas/Bourne_Ultimatum.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 640x272, q=2-31, 200 kb/s, 90k tbn, 12 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec for output stream #0.0

```Parece que me faltan coedecs :S estoy instalando los ubuntu-restricted-codecs que aparentemente me habia olvidado de instalar..
Cuando termine de instalar intento a ver si me tira lo mismo y les aviso

> **totolinux said:**
> Que lastima que no te funciona, pero no te perdes nada de el video porque solo esperas que arranque desde el inicio. Lo que si me parece, que no a todos se nos comporta de la misma manera. He leído que algunos miran tv con determinado script pero yo no puedo y algún skin me lo cuelga por completo.
Va, no me cierra del todo. En realidad me gusta más Elisa pero me trae dolores de cabeza peores. como la resolución en la tv que no puedo modificar pero es otro tema. saludos

Claro, el problema es que a mi si me reprodicia los primeros minutos (y seguramente toda la pelicula) pero solo el sonido, sin imagen.
Voy a instalar eso que me falta y vemos que pasa.. encontre un post en Taringa donde dice un trio de cosas para instalar (uno de ellos el que estoy instalando) y teoricamente deberia poder ver todo tipo de archivos

---

### Post by guillermolisi on 2009-08-17
Los de medibuntu, si no los tenes aun, tambien instalalos (por las dudas)

---

### Post by Fak89 on 2009-08-17
Gracias por el dato Guille.
Bien, todavia no puedo hacer que reproduzca rmvb.. y para empeorar un poquito, mi teoria de que el programa usa mplayer murio, ya que mplayer ahora me reproduce este formato, pero el programa todavia no..
Voy a hacerla mas corta y convertir las peliculas en formato avi a medida que las voy descargando..

Si de casualidad encuentro la solucion para que reproduzca el formato este programa la posteo..
Gracias por la ayuda a todos, saludos!

:popcorn:

---

### Post by sp33d3rs on 2009-09-28
Yo tengo otro problema, si bien se reproducen los rmvb, cada un tiempo se tilda la imagen por un segundo (el sonido sigue funcionando, pero la imagen queda estatica apenas un segundo) luego como que se "apuran" las imagenes para igualar al sonido y sigue funcionando bien. Este problema se repite 3 o 4 veces cada 10 minutos. La verdad me descilucione mucho.
Si alguien sabe por que, se lo agradezco.
NOTA: Si habro cualquier reproductor, se ve muy bien. Ya lo corri con geexbox y con elisa y se ve 10 puntos; mi problema es que xbmc tiene muy buen entorno y me gusta mas...:lolflag:
 
Con respecto a lo que te ocurre con la "no reproduccion" del formato rmvb, yo instale ubuntu 9.04 en una pc desde cero...
La computadora tiene un procesador de 2.8ghz, 512ram, 160gb de hdd y tan solo 64mb nvidia de gráfica (solo me interesa la salida tv)...
Me "copie" casi todo lo de este blog:
[http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/](http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/)
fijate q onda :P

---

### Post by faktorqm on 2009-09-29
probaste el vlc?

---

