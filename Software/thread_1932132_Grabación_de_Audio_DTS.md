---
title: "Grabación de Audio DTS"
date: 2012-02-26
forum: Software
---

### Post by asterix77 on 2012-02-26
Acabo de descargar un cd dts 5.1, mi deseo es reproducirlo en mi sistema home cinema. Los archivos vienen en formato wav. Al dar en propiedades de algún archivo, me arroja Surround 5.1. Se reproducen sin problemas en mi equipo (sonido stereo solamente)


Traté de abrir el archivo con audacity y con ardour para ver las 6 pistas, pero solo logro ver 2 que al reproducirlas con dichos programas solo se oye un ruido uniforme ¿acaso no soporta edición de 5.1?.

Bueno, pero mi consulta es si hay alguna forma de grabar en un cd para reproducirla en mi home cinema, o en su defecto pasarla a otro formato 5.1 y grabarlas en un pendrive y tratar de reproducirlas desde este.  

Uso lucid 32 bit.

Saludos

---

### Post by euzkoarima on 2012-02-27
No conozco mucho del tema audio en general, pero fijate si el link que te paso te ayuda

[http://parumi.wordpress.com/2007/12/12/how-to-create-multichannel-51-ac3-audio-and-video-in-linux/]("http://parumi.wordpress.com/2007/12/12/how-to-create-multichannel-51-ac3-audio-and-video-in-linux/")

Saludos,
Eduardo

---

### Post by asterix77 on 2012-02-29
Gracias por tu respuesta, pero no me resulta. A continuación detallo primero la salida del comando mediainfo del archivo de audio.

$mediainfo 01-Sultans\ of\ Swing.dts
General
Complete name                            : 01-Sultans of Swing.dts
Format                                     : Wave
File size                                    : 58.9 MiB
Duration                                   : 5mn 50s
Overall bit rate mode                 : Constant
Overall bit rate                          : 1 411 Kbps

Audio
ID                                            : 0
Format                                     : DTS
Format/Info                              : Digital Theater Systems
Format settings, Endianness       : Little
Muxing mode                            : LE / 14
Codec ID                                  : 1
Duration                                   : 5mn 50s
Bit rate mode                           : Constant
Bit rate                                    : 1 411.2 Kbps
Channel(s)                               : 6 channels
Channel positions                      :**[COLOR=Black] Front: L C R, Side: L R, LFE[/COLOR]**
Sampling rate                           : 44.1 KHz
Bit depth                                  : 24 bits
Compression mode                   : Lossy
Stream size                              : 58.9 MiB (100%)

Como se puede ver, mi archivo tiene 6 canales (en negritas). Al ejecutar aften me aparece lo siguiente:

$aften -b 448 -cmix 0 -smix 0 -dsur 2 -acmod 7 01-Sultans\ of\ Swing.dts Sultans_of_Swing.ac3

Aften: A/52 audio encoder
Version SVN-r853
(c) 2006-2007 Justin Ruggles, Prakash Punnoor, et al.

input format: Microsoft WAVE Signed 16-bit little-endian 44100 Hz stereo
acmod does not match number of channels


Con lo único que logro algo es con la opciones amod 0, 1 y 2 dejando el archivo mono, con dos canales y stereo respectivamente.


Saludos

---

### Post by euzkoarima on 2012-03-01
Fijate si este [0] otro post te sirve. Yo probaría de hacerlo con ffmpeg

[0] [howto-processing-multichannel-audio-dts.html]("http://juliensimon.blogspot.com/2009/01/howto-processing-multichannel-audio-dts.html")

Saludos,
Eduardo

---

### Post by asterix77 on 2012-03-02
Gracias por responder

Siguiendo tu link, creo que me sirvió a medias, me explico. Instalé todo lo que se recomienda pero me arrojaba un error en el paso N°5

Pero creo que lo instalado me sirvió para lo que hice después. Una vez que tuve el wav, instalé mkverge-gui, aquí agregué de uno en uno los archivos wav quedando con extensión de audio matroska (MKA). Es decir agregaba una canción y la convertía a mka (no me resultaba hacerla todas de un vez). Y este formato si los lee mi home cinema, y también los puedo abrir con audacity y me muestra todas sus pistas y por lo tanto se pueden editar.

Solo el parlante frontal no se escuchó nada, no sé porque sucedió esto, pero el resto si y se oye espectacular

Saludos y gracias

---

