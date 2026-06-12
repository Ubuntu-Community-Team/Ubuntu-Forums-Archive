---
title: "Driver Video Silicon Integrated Systems (SiS)"
date: 2012-07-31
forum: Uruguay Team
---

### Post by carl tabarez on 2012-07-31
Lo prometido es deuda.

Como mi vieja PC tiene una video integrada a la placa base, lamentablemente no pude deshacerme de la deficiente pieza de hardware de video llamada SiS Mirage 3+.

La empresa (que como toda empresa lucrativa) parece que al fabricarlas se le dio por ahorrar demasiado, y ahi tenemos la calidad de esta basura.
Como a muchos les pudo haber pasado, sólo hizo controladores para el famoso sistema operativo de las ventanas, pero se olvidó de que habian muchos otros de sus clientes que no usan ese sistema, sino que usan GNU/Linux o algun otro sistema menos difundido.

En un esfuerzo por sortear el problema, un grupo de usuarios decidió escribir un controlador genérico y libre para la mayoría de las placas de video de esta empresa, todo desde cero.

Se logró mucho desde entonces, pero el controlador sólo provee lo básico: ajustar la pantalla a su resolucion nativa adecuada y una considerable aceleracion 2D. 
Pero ni se les ocurra jugar a nada que tenga 3D, porque no les andará nada bien (no tiene aceleracion grafica).

Este controlador (o más precisamente su código) es mantenido por alguno miembros de RedHat y de FreeDesktop.

Encontrarán un link aquí:

Controlador algo anticuado (no sé si tiene soporte), pero con una gran cantidad de informacion útil
[http://www.winischhofer.net/linuxsisvga.shtml](http://www.winischhofer.net/linuxsisvga.shtml)

Freedesktop (misteriosamente el desarrollo revivió - último desarrollador Dave Airlie). Este es el más nuevo, pero deberán tener la versión mas nueva de la biblioteca **pciaccess**
[http://cgit.freedesktop.org/xorg/driver/xf86-video-sis/](http://cgit.freedesktop.org/xorg/driver/xf86-video-sis/)

Otro link que utiliza una version un poco vieja del driver (pero es funcional, ya que esta es la que uso):
[http://www.taringa.net/posts/linux/14806799/Driver-SiS-Mirage-3_-672-con-resolucion-1366x768-en-Linux.html](http://www.taringa.net/posts/linux/14806799/Driver-SiS-Mirage-3_-672-con-resolucion-1366x768-en-Linux.html)
y el mismo post en ingles: 
[http://www.socialphy.com/posts/computers-technology/13565/Video-driver-for-SiS-videocards-under-Linux.html](http://www.socialphy.com/posts/computers-technology/13565/Video-driver-for-SiS-videocards-under-Linux.html)

Las únicas dos o tres tarjetas de video soportadas oficialmente (por la empresa fabricante) en GNU/Linux:
[http://w3.sis.com/support/support_faqs_16.htm](http://w3.sis.com/support/support_faqs_16.htm)

Un blog que trató el mismo problema, pero para 11.04 Natty Narwhal:
[http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)

Espero que a alguien le haya podido ser útil.:):popcorn:

---

