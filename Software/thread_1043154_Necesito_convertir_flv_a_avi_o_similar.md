---
title: "Necesito convertir flv a avi o similar"
date: 2009-01-18
forum: Software
---

### Post by KaKuS on 2009-01-18
Hola gente, les comento.

Ya encontré un pluging para el firefox que me permite bajar los vídeos embebidos en los sitios. La mayoría está en formatos flv (Flash), y estoy buscando una manera de convertirlos a AVI o MOV o MPEG.

Estuve probando con un Ogg converter, pero los archivos que genera no son fácilmente reproducibles (sin instalar codecs o soft adicional) en otros sistemas operativos (Windows principalmente).

¿Me podrían orientar o sugerir algún otro programa que realice la conversión? (si no es mucho pedir con interfaz X :P)


Saludos

---

### Post by Air23 on 2009-01-18
Una manera muy sencilla de hacerlo es la siguiente (es desde la terminal pero no es nada del otro mundo como para preocuparse)

Instalar ffmpeg
```
sudo apt-get install ffmpeg
```
Luego la conversion se hace de la siguiente manera
```
ffmpeg -i video.flv video.avi
```
Donde video es el nombre del flv (el nombre del avi no tiene pq ser el mismo que el del flv)

Otra manera (en mi caso los videos quedan mejores con este método)

Instalar mencoder
```
sudo apt-get install mencoder
```
Conversion
```
mencoder video.flv -ovc lavc -oac mp3lame -o video.avi
```

En ambos casos acordate de moverte desde la terminal al lugar donde tenes los vídeos (o colocar estos en tu home y listo)

Mas data:
[http://mundogeek.net/archivos/2008/08/27/convertir-videos-flv-a-avi/](http://mundogeek.net/archivos/2008/08/27/convertir-videos-flv-a-avi/)
[http://ubuntulife.wordpress.com/2007/03/15/convertir-de-flv-a-avi/](http://ubuntulife.wordpress.com/2007/03/15/convertir-de-flv-a-avi/)
[http://bewatermyfriend-free.blogspot.com/2007/12/gua-rpida-de-ffmpeg-flv-avi-flv-mpg-avi.html](http://bewatermyfriend-free.blogspot.com/2007/12/gua-rpida-de-ffmpeg-flv-avi-flv-mpg-avi.html)

Saludos

---

### Post by gjoellee on 2009-01-18
> **Air23 said:**
> Una manera muy sencilla de hacerlo es la siguiente (es desde la terminal pero no es nada del otro mundo como para preocuparse)

Instalar ffmpeg
```
sudo apt-get install ffmpeg
```Luego la conversion se hace de la siguiente manera
```
ffmpeg -i video.flv video.avi
```Donde video es el nombre del flv (el nombre del avi no tiene pq ser el mismo que el del flv)

Otra manera (en mi caso los videos quedan mejores con este método)

Instalar mencoder
```
sudo apt-get install mencoder
```Conversion
```
mencoder video.flv -ovc lavc -oac mp3lame -o video.avi
```En ambos casos acordate de moverte desde la terminal al lugar donde tenes los vídeos (o colocar estos en tu home y listo)

Mas data:
[http://mundogeek.net/archivos/2008/08/27/convertir-videos-flv-a-avi/](http://mundogeek.net/archivos/2008/08/27/convertir-videos-flv-a-avi/)
[http://ubuntulife.wordpress.com/2007/03/15/convertir-de-flv-a-avi/](http://ubuntulife.wordpress.com/2007/03/15/convertir-de-flv-a-avi/)
[http://bewatermyfriend-free.blogspot.com/2007/12/gua-rpida-de-ffmpeg-flv-avi-flv-mpg-avi.html](http://bewatermyfriend-free.blogspot.com/2007/12/gua-rpida-de-ffmpeg-flv-avi-flv-mpg-avi.html)

Saludos

+1 amigo/amiga

---

### Post by KaKuS on 2009-01-18
Gracias por la data!

---

### Post by z37a on 2009-01-18
Con el avidemux no se puede hacer esto tampoco? Por que si se puede te permite mas opciones, no solo a avi si no a otros formatos(mp4, 3gp, etc...)

---

### Post by Hei Ku on 2009-01-18
con el avidemux se puede, pero es mucho mas dificil de manejar

---

### Post by Air23 on 2009-01-18
Buscando un poco encontre una GUI para ffmpeg llamada WinFF (aunque me sigue pareciendo mas sencillo hacerlo desde la terminal)

[http://winff.org/html/](http://winff.org/html/)

No esta en los repositorios de ubuntu pero se puede agregar el repositorio oficial del WinFF siguiendo estas instrucciones:

[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

---

### Post by zeroadrenaline on 2009-01-19
Tan simple como meterte en synaptic, instalar ffmpg mancoder y winff.
Despues te vas a Aplicaciones > Multimedia > WinFF y ahi haces toooooooodas las conversiones que se te antojen!.
Suerte!.

---

### Post by Abrilla on 2011-02-21
Hola, prueba con **SoundTaxi Media Converter o MediaBuddy**, que mantienen un montón de formatos**, **soportan tales vídeo formatos populares como DivX AVI, MP4, Windows Media, Flash Video, 3gp, flv etc.,
  bajar aquí: 
  [http://soundtaxi.org/](http://soundtaxi.org/)
  Saludos

---

### Post by quedefantasma on 2011-02-23
Este funciona muy bien, es gratuito, simple y funciona tanto en ubuntu y mac como en win.

Tiene funciones de trim y crop, subtitulos, convierte directo desde youtube...etc.

Sin problemas hasta el momento.

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

Suerte...

---

### Post by Abrilla on 2011-02-28
Hola, recomiendo usar SoundTaxi Media Converter o MediaBuddy, que mantienen un montón de formatos, soportan tales vídeo formatos populares como DivX AVI, MP4, Windows Media, Flash Video, 3gp, flv, avi etc., y se puede elegir la calidad del vídeo
Saludos

---

### Post by Abrilla on 2011-02-28
Hola, recomiendo usar SoundTaxi Media Converter o MediaBuddy, que mantienen un montón de formatos, soportan tales vídeo formatos populares como DivX AVI, MP4, Windows Media, Flash Video, 3gp, flv, avi etc., y se puede elegir la calidad del vídeo

---

