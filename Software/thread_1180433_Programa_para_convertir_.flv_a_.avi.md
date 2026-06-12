---
title: "Programa para convertir *.flv a *.avi"
date: 2009-06-06
forum: Software
---

### Post by Eddy_Kine on 2009-06-06
Pues es eso, necesito hacerlo y he intentado con ffmpeg y me arroja este error.
¿Existe algún programa que pueda hacerlo? ¿Qué esta mal?

```
luis@luis-desktop:~$ ffmpeg - YouTube_-_Canal_de_hollywoodrecords.flv YouTube_-_Canal_de_hollywoodrecords.ogg
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Unable to find a suitable output format for 'pipe:'
luis@luis-desktop:~$ 

```De antemano gracias

---

### Post by Eddy_Kine on 2009-06-06
Pues, desde que soy miembro de la comunidad (hace 2 años) trato de ser auto suficiente, pero la verdad es que esta situación me estaba haciendo la vida de cuadritos, había tratado de convertir estos vídeos de youtube a avi o mpeg hace rato, pero sin poder hacerlo. Ya resigando postee aquí y en un ultimo intento encuentro el Winff un programa genial!!!! Gracias Ubuntu por ser el mejor SO que he visto.
He logrado convertir videos con el en excelente calidad.
Posteo lo correspondiente para quien este en mi predicamento
```
sudo aptitude install **winff**
```

La configuración es a gusto y como tarea para la casa :KS
Saludos y gracias

PD: Creí mejor crear un nuevo reply para finalizar el post

---

### Post by tuxsarge on 2009-06-06
hola..

yo para eso solamente ocupo el programa devede

me funciona sin problemas, y no tengo que estar recurriendo a la consola para hacer tanto leceo

saludos ):P

---

### Post by nopersona on 2009-06-07
Hola caballero, te doy la mejor solución, a mi juicio, para estos fines... usar un sencillo script... más una sencilla gui!!!

[http://www.gtk-apps.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533](http://www.gtk-apps.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533)

La verdad es que ese conjunto de scripts están muy bien documentados y depurados, además de actualizados constantemente, y respecto a la conversión de video... con dos clicks y listo ;)

---

### Post by Patriciologico on 2009-06-07
Una excelente opcion, es Pytube, que te permite buscar directamente videos de youtube, rescata el ultimo video desde la carpeta temporal, une videos, permite agregar audio, y convierte a .avi .mpg y .ogm entre otras funciones y es una aplicacion livianita con gui.

[Pagina Actual de descarga]("http://www.marcosrodriguez.me/pytube/index.php?option=com_remository&Itemid=2")

[Informacion de la Aplicacion en Genbeta]("http://www.genbeta.com/multimedia/pytube-descargador-conversor-y-editor-de-videos-en-gnulinux")

Saludos!

---

### Post by Eddy_Kine on 2009-06-07
Muchísimas gracias, nunca deja sorprenderme Linux-Ubuntu, es el mejor SO que hay.- ):P

---

### Post by moFeta on 2009-06-08
ffmpeg también te sirve perfectamente, solo te faltó agregar el comando '-i' antes del nombre del archivo .flv para que ffmpeg sepa que es un archivo el que debe leer y no de la entrada estándard (stdin).

Suerte.

---

### Post by 3nG3ndR0 on 2009-06-09
yo ocupo el jdownloader, coloco el link y te pregunta en que formatos lo quieres guardar.

---

### Post by Patriciologico on 2009-06-09
No, no, no. No hagas caso, son demasiadas  opciones, la mia rockea en mala :guitar: hasta el infinito y mas alla:guitar:

---

### Post by yonseiwilly on 2009-06-09
Busco unir Jpg a otros formatos con FFMpeg pero…. pero me arroja un error.
La sentencia sería (usé copy and paste…)
ffmpeg -f image2 -i imagen%d.jpg video.mpg
Con este comando convertiríamos todas las imágenes del directorio actual (con nombres imagen1.jpg, imagen2.jpg, etc…) en un video llamado video.mpg.
Bien… en mi caso necesito mas fotos, toda una carpeta, entonces modificando un poco el comando tendria que ser algo parecido a:
ffmpeg -f image2 -i *.jpg video.avi y deberia tomar gracias al comodin * todas las imegenes jpg de la carpeta descrita y realizar el archivo de video… pero me arroja lo sgte con el sgte error:
FFmpeg version r11872+debian_0.svn20080206-17+lenny1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
configuration: –enable-gpl –enable-libfaad –enable-pp –enable-swscaler –enable-x11grab –prefix=/usr –enable-libgsm –enable-libtheora –enable-libvorbis –enable-pthreads –disable-strip –enable-libdc1394 –disable-armv5te –disable-armv6 –disable-altivec –disable-vis –enable-shared –disable-static
libavutil version: 49.6.0
libavcodec version: 51.50.0
libavformat version: 52.7.0
libavdevice version: 52.0.0
built on Apr 28 2009 02:12:01, gcc: 4.3.2
Input #0, image2, from ‘17_49_54GMT.jpg’:
Duration: 00:00:00.0, start: 0.000000, bitrate: N/A
Stream #0.0: Video: mjpeg, yuvj420p, 640×480 [PAR 0:1 DAR 0:1], 25.00 tb(r)
Unable to find a suitable output format for ‘17_49_55GMT.jpg’
Que estoy haciendo mal?, mejor dicho, que no estoy viendo que otro pueda verlo?? porfis??
Algun iluminado? o alguien con menos problemas que yo que piense mejor??
 
Thankss

---

### Post by Carlos C on 2009-06-09
> **yonseiwilly said:**
> Busco unir Jpg a otros formatos con FFMpeg pero…. pero me arroja un error

...

Que estoy haciendo mal?, mejor dicho, que no estoy viendo que otro pueda verlo?? porfis??
Algun iluminado? o alguien con menos problemas que yo que piense mejor??
 
Thankss
Estimado, debes abrir un nuevo hilo ya que tu problema es distinto al tratado en este thread.

Saludos.

---

### Post by Eddy_Kine on 2009-06-09
> **moFeta said:**
> ffmpeg también te sirve perfectamente, solo te faltó agregar el comando '-i' antes del nombre del archivo .flv para que ffmpeg sepa que es un archivo el que debe leer y no de la entrada estándard (stdin).

Suerte.

Debe ser eso pues el error hace referencia a un "pipe".
Lo verifico y edito este post. ;)

Pd: La verdad es que el Winff es lo mejor que he hallado hasta el momento, pues la calidad del video resultante es mejor, comparando con el Pytube y los demás tips.

*****************
Confirmado, Mofeta tenia razón :)

---

### Post by Abrilla on 2011-02-28
Hola, prueba con SoundTaxi Media Converter o MediaBuddy, que mantienen un montón de formatos, soportan tales vídeo formatos populares como DivX AVI, MP4, Windows Media, Flash Video, 3gp, flv, MPEG4 etc., y se puede elegir la calidad del vídeo
bajar aquí: [http://soundtaxi.org/](http://soundtaxi.org/)
Saludos

---

### Post by nechus on 2011-06-05
Ya debes haber resuelto tu problema, pero no está demás mencionar que me gusta mucho DamnVid: [http://code.google.com/p/damnvid/](http://code.google.com/p/damnvid/)

---

