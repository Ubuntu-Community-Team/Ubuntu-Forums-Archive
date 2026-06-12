---
title: "Problema al escuchar radio"
date: 2009-12-21
forum: Software
---

### Post by asterix77 on 2009-12-21
Estimados:

Quisiera saber si se puede escuchar radio, especificamente "el conquistador fm". No logro hacerlo ni por firefox, ni por consola.

Al hacerlo por consola aparece lo siguiente:

#mplayer mms://200.27.86.250/radioconquistador
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://200.27.86.250/radioconquistador.
STREAM_ASF, URL: mms://200.27.86.250/radioconquistador
Resolving 200.27.86.250 for AF_INET6...
Couldn't resolve name for AF_INET6: 200.27.86.250
Connecting to server 200.27.86.250[200.27.86.250]: 1755...
connect error: Connection refused
Resolving 200.27.86.250 for AF_INET6...
Couldn't resolve name for AF_INET6: 200.27.86.250
Connecting to server 200.27.86.250[200.27.86.250]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving 200.27.86.250 for AF_INET6...
Couldn't resolve name for AF_INET6: 200.27.86.250
Connecting to server 200.27.86.250[200.27.86.250]: 80...
Server returned 404: Not Found
No stream found to handle url mms://200.27.86.250/radioconquistador


Exiting... (End of file)

No puedo abrirlo con ningún programa (vlc-totem, etc). Otras emisoras si puedo hacerlo, solo esta es el problema. Tengo los codecs win32codecs que recomiendan.

Al revisar el códig fuente de la página web, aparece esa dirección. Lo curioso es que en windows si funciona.

Si alguien me puede ayudar con eso lo agradecería.

Saludos

---

### Post by moreback on 2009-12-21
Yo la agregué a mi [Banshee]("apt:banshee") y la estoy escuchando en este preciso momento.

Creo que no estás ejecutando correctamente el mplayer y por eso te da error. ¿Leíste la documentación de mplayer?

---

### Post by asterix77 on 2009-12-22
No hay caso, he intentado varias cosas y no he podido determinar donde está el problema.
He instalado y desinstalado varios programas, mplayer, vlc, rhythmbox, banshee.

No sé que significa lo siguiente que me aparece: "No stream found to handle url mms://200.27.86.250/radioconquistador"


Saludos

---

### Post by CdK1 on 2009-12-22
Antes que nada en tu log leo:

Server returned 404: Not Found

Ahora probé y no tuve ningún problema...:

CdK1@Caturra:~$ mplayer mms://200.27.86.250/radioconquistador
MPlayer SVN-r29980 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://200.27.86.250/radioconquistador.
STREAM_ASF, URL: mms://200.27.86.250/radioconquistador
Resolving 200.27.86.250 for AF_INET6...
Couldn't resolve name for AF_INET6: 200.27.86.250
Connecting to server 200.27.86.250[200.27.86.250]: 1755...
Connected
unknown object
unknown object
unknown object
unknown object
file object, packet length = 2261 (2261)
unknown object
stream object, stream ID: 1
data object
mmst packet_length = 2261
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Señal Hi-Fi
 author: El Conquistador FM
 copyright: 2009
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:607807.2 (168:50:07.1) of 1844674428928.0 (-24.-8)  2.0% 21% 

MPlayer interrupted by signal 2 in module: decode_audio


MPlayer interrupted by signal 2 in module: enable_cache
A:607807.2 (168:50:07.1) of 1844674428928.0 (-24.-8)  2.0% 21% 
Exiting... (Quit)
CdK1@Caturra:~$

---

### Post by moreback on 2009-12-22
A lo mejor estás teniendo problemas con algún filtro instalado en tu red, ya sea un firewall bloqueado conexiones o un proxy transparente que recolecta información para el Gran Hermano (o la SCD y/o similares) jojojo

---

### Post by asterix77 on 2009-12-23
Bueno

Revisé las configuraciones de firestarter, y agregué la regla para que acepte las conexiones de mplayer. Aunque por lo que creo usa el puerto http 80, y no tengo ningún problema al menos para navegar. Por lo que creo que el problema no es el cortafuegos; lo del proxy mmmmm no sabría decirte.....

Uso banda ancha movil entelpcs, por lo que probé en un equipo con jaunty y no tuve ningún problema en escuchar la radio. También probé en un equipo con vista, y tampoco me dió dramas, por lo que asumo que el problema es en mi pc.

El problema es con las emisoras tipo mms.

Saludos

---

### Post by moreback on 2009-12-23
El puerto por defecto para mms es el 1755, tal como lo nombran en este reporte.

Parece ser un bug de mplayer también.

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2002-December/026462.html]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2002-December/026462.html")

Saludos.

---

### Post by asterix77 on 2009-12-23
Estaba viendo la posibilidad que se trate de un bug, ya que he encontrado varios que tienen el mismo problema. Pero igual tengo la duda ya que si fuera un bug de mplayer, otros reproductores tendrían que funcionarme (amarok, vlc, banshee, rhythmbox, etc), y no es el caso.

¿Será que mi pc es de 64 bit?. Hasta el momento igo igual, y ya no se me ocurre que hacer.


Saludos

---

### Post by asterix77 on 2009-12-23
Bueno al parecer el problema efectivamente radicaba en el cortafuegos. He abierto el puerto 1755 y en estos momentos ya estoy escuchando la radio sin problemas:guitar:.

Saludos y gracias a todos por sus aportes

---

