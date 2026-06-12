---
title: "Error de proprocion en videos con Totem"
date: 2012-10-17
forum: Software
---

### Post by Chogogo on 2012-10-17
Hola!

Tengo Ubuntu 12.04 recién instalado y con los Codecs de medibuntu instalados.

Tengo algunos videos con codec de video H.264 y al tratar de verlos con el reproductor Totem o Gnomeplayer, la imagen aparece desproporcionada (es decir, mas grade y cuadrada ). El video se reproduce "normalmente" en la parte superior de el reproductor, imagen y sonido claros. Pero el tamaño que el reproductor le asigna a el video, es mas grande que la imagen real del video, asi que el espacio restante aparece "rellenado" con una zona verde o negra abajo. Los videos con otro codec, se reproducen sin ningún problema

El problema es solo con videos con codec H.264, y solo bajo Totem o GnomePlayer. Todos los videos se reproducen correctamente en VLC. tamaño y sonidos correctos y sin franjas verdes abajo

Alguna sugerencia?, Se trata de algún Bug, problema de estos dos reproductores o hay algo que se pueda hacer para arreglarlo?.

Un saludo y que Dios los bendiga!

---

### Post by Chogogo on 2012-10-18
Me acabo de dar cuenta que los todos los reproductores detectan un tamaño de fotograma de 720x720 (información de el archivo). Estos videos fueron creados con tamaños de 720X480. No entiendo la razon por la cual los reproductores ahora detectan un tamaño mas grande. De ahi la razón de la "zona verde" en la parte de abajo del visor. Es espacio vacio. Pero no entiendo porque VLC, que tambien detecta el mismo tamaño 720x720, no muestra la zona verde sino que ajusta el tamaño del visor al tamaño real del fotograma.

---

### Post by Chogogo on 2012-11-03
Hola a Todos!!

Bueno gracias a Dios logré encontrar una solución a este problema en una página en Inglés:
[http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html)

Es un Bug en el GStreamer, está reportado en este sitio:
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

Para 32 bit pegar en terminal :
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak

y para 64 bit:
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak


Dice no causar ningún problema, pero de llegar a haberlo simplemente es renombrar
"libgstvideoparsersbad.so.bak" de vuelta a "libgstvideoparsersbad.so"


Nuevamente todo ha vuelto a la normalidad en mis SO.

Muchas gracias y que Dios los bendiga.

---

### Post by Eddy_Kine on 2013-03-06
Valgame! En hora buena. Y por lo que veo has perseverado y solucionado tu mismo sin asistencia de la comunidad.
Gracias por la información no tenia conocimiento de ese bug.
Y...Ubunteros una llamada de atención por dejar esto sin responder.

PD: He retornado de un laaaargo auto exilio :P

---

