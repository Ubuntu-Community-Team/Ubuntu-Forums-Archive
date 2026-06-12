---
title: "Problema con video en Cheese Webcam Booth"
date: 2009-07-25
forum: Software
---

### Post by DrKenobi on 2009-07-25
Hola.

Hace un tiempo instale el programa Cheese Webcam Booth.
Las fotos las saca muy bien, pero los videos no, anda tomo muy lento y graba cualquier cosa.
En las FAQ de este programa dice como solucionarlo, pero eso no me ayudo en nada.
Alguien mas lo usa/sabe como solucionar el problema?

Esto es lo q dicen las FAQ's
> I'm getting a really slow response with the video, the video is sluggish and everything looks quite slow, like as the video lags, what could i do?

You may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.

Where can I set those things mentioned in the answer above?

Just execute gstreamer-properties (or in the menu: Multimedia Systems Selector) and change it there 

[http://live.gnome.org/Cheese/FAQ#head-fb51597a3f48dfc21f2d288bf07cf78ce00b2802]("http://live.gnome.org/Cheese/FAQ#head-fb51597a3f48dfc21f2d288bf07cf78ce00b2802")

---

### Post by staar on 2009-07-25
hiciste eso y no se arregló? de que hardware estamos hablando?

saludos

---

### Post by DrKenobi on 2009-07-25
Asi es. Hice lo que decian las FAQ's y nada, todo igual.

Te paso las especificaciones de mi PC:

> Processor: 1.8 GHz-M on Mobile Intel Pentium 4 processor
Cache Memory: 512 KB L2 cache
Memory:	768 MB 266 MHz SDRAM DDR SDRAM
Hard Drive: 30-GB 4200 rpm SMART Hard Drive
Video Memory: 32MB
Optical Drive: 8XDVD
Graphics: ATI Mobility Radeon 7500 4X AGP graphics controller with 32 MB DDR VRAM

Gracias

---

