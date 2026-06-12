---
title: "Devede | .avi no es video"
date: 2009-07-01
forum: Software
---

### Post by NickCis on 2009-07-01
Hola, tengo problemas con el devede.
Este programa me dice que un archivo de video cone extension avi, no es video, me dice "El archivo no parece ser de video".
Supuse que el problema estaba relacionado con el Mplayer, que por cierto tampoco me lo deja abrir, y no me da un error por consola:
```
newpc@newpc-desktop:~/Downloads/Ed gein$ mplayer "ed gein.avi"
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3800+ (Family: 15, Model: 95, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ed gein.avi.


Exiting... (End of file)
newpc@newpc-desktop:~/Downloads/Ed gein$

```
Usando la interfaz grafica del mplayer como (gmplayer o kmeplayer) tampoco me lo reproduce.

El vlc me lo reproduce perfectamente, me da esta info acerca de los codecs.
```

Emision 1
     Tipo: Audio
     Codec: mpga
     Canales: Estereo
     Tasa de Muestra: 48000 Hz
     Tasa de Bits: 128 kb/s
Emision 0
     Tipo: Video
     Codec: DIV3
     Resolucion: 640x384
     Resolucion de pantalla: 640x384
     Tasa de fotograma: 25

```

Alguna idea de por que puede ser?.

Saludos.

P.d: por favor no me tomen a mal intentando grabar una pelicula bajada de internet. Tuve que recurrir a esto ya que no encontre la pelicula en ningun video club...

---

### Post by pablo.s on 2009-07-01
El problema lo veo con
el codec DIV3. El que haya
utilizado ese codec infame
para pasar la pelicula a
Divx debe ser crucificado.
Probaría con Avidemux a
ver si se puede transferirlo a
MPEG (supongo, ya que
mencionás Devede). Y sino
queda otra, conseguir la
pelicula en un formato que
dé menos asco.

---

### Post by NickCis on 2009-07-01
Mismo problema con el Avidemux, me dice "No se pudo abrir el archivo".

Alguna idea de como se puede pasar de formato?.

Saludos.

---

### Post by pablo.s on 2009-07-01
Con VLC podés hacer una
transcodificación a otro
formato, pero ahi vas a tener
que investigar porque nunca
lo hice. Si te va la idea te 
ayudo si te trabás...

Para empezar, fijate donde
dice Convert - Save

---

### Post by mama21mama on 2009-07-01
Tenes instalado w32codecs ?
proba instalandolo.

Saludos

---

### Post by NickCis on 2009-07-01
Si, los codecs los tengo instalados, todos los del medibuntu, puedo ver peliculas de DVD sin problemas no se por que este archivo me tira problemas :S...

Ahora empeizxo a ver lo del vlc, me hecho una miradita x la pagina y veo si sale a prueba y error, cualqiercosa chiflo, muchas gracias :P.

Saludos.

---

### Post by NickCis on 2009-07-01
El vlc me da opciones como "Desentrelazar" y "Entrada de volcado raw", hay que activarlas?, voy a probar sin tickearlas,,, Ademas me da para elegir un perfil, sobre como va a salir (los codecs), voy a elegir "Video - MPEG-2 + MPGA (TS)" esta bien?.

Bue, va a tardar, por que segun lo qe parece tarda en decodificar, lo mismo qe dura la peli,,, asi qe va a estar un tiempo largo :S...

Saludos., dsp cuento como me fue :P

---

