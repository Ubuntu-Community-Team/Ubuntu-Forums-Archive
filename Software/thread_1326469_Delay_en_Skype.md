---
title: "Delay en Skype"
date: 2009-11-14
forum: Software
---

### Post by alejo_joan on 2009-11-14
Segunda pregunta de un inexperto.

Desde el 8.04 que tengo problemas con el Skype y es siempre el mismo, tengo un delay enorme en las conversaciones.

Lo que yo hablo lo escuchan los otros entre 4 y 12 segundos después que lo dije mientras que lo que me dicen lo escucho sin delay.

Sé que hay muchos problemas con el Pulse Audio y Skype y esa es la única opción que me da el Skype en la que escucho algún sonido.

Posiblemente se me esté escapando una tortuga.

Mil gracias por adelantado por la ayuda.

Alejo.

---

### Post by Tolaris on 2009-11-15
I have the same problem on only one of my PCs - 10 seconds between when it sends video and when the other side receives it, even on the same LAN.  From lsusb:

Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

This is on a base karmic i386 install.

---

### Post by guillermolisi on 2009-11-15
> **Tolaris said:**
> I have the same problem on only one of my PCs - 10 seconds between when it sends video and when the other side receives it, even on the same LAN.  From lsusb:

Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

This is on a base karmic i386 install.
Could you post messages in Spanish, please ? There are people cannot understand English here, in the Argentina LoCo Team subforum. Thank you.

Traduccion:
Tengo el mismo problema en una de mis PCs - 10 segundos entre que envia video y es recibido del otro lado, aun en la misma LAN.
(salida del lsusb)

Esto sucede con una instalacion Karmic i386 basica.

---

### Post by aledruetta on 2009-11-15
Bueno, a mí nunca me ocurrió lo del delay, por lo tanto puede ser que lo que voy a decir no tenga nada que ver. Pero como mencionas a PulseAudio, te cuento que yo resolví otros problemas con PulseAudio instalando la versión skype-static que está en los repositorios medibuntu. También hay una versión oss. 

Sería cuestión de probar y ver qué sucede...

Suerte!

---

### Post by Tolaris on 2009-11-15
> **guillermolisi said:**
> Could you post messages in Spanish, please ? There are people cannot understand English here, in the Argentina LoCo Team subforum. Thank you.

Perdóname. Yo no vi el sub-forum.

---

### Post by alejo_joan on 2009-11-19
> **aledruetta said:**
> Bueno, a mí nunca me ocurrió lo del delay, por lo tanto puede ser que lo que voy a decir no tenga nada que ver. Pero como mencionas a PulseAudio, te cuento que yo resolví otros problemas con PulseAudio instalando la versión skype-static que está en los repositorios medibuntu. También hay una versión oss. 

Sería cuestión de probar y ver qué sucede...

Suerte!

Bajé la versión 2.1 (beta) de medibuntu y de Skype a Skype funciona sin delay aunque se entrecorta mucho. Solo falta probar las llamadas a teléfonos fijos.

Muvhas gracias a todos!

Alejo.

---

### Post by juancarlospaco on 2009-11-20
**Empathy+Gtalk** anda barbaro para conversaciones de Audio, 
si le instalas el SofiaSIP tenes soporte para SIP en Empathy.

---

### Post by alejo_joan on 2009-12-23
> **juancarlospaco said:**
> **Empathy+Gtalk** anda barbaro para conversaciones de Audio, 
si le instalas el SofiaSIP tenes soporte para SIP en Empathy.


Si, definitivamente el Empathy es fabuloso pero el tema es que tengo muchos contactos en Skype y quiero hablar con ellos, además suelo usar el servicio de Skype para llamar a fijos que me funciona de manera excelente.

Tengo entendido (soy muy ignorante en sistemas) que Skype no es (o no usa)  SIP, estoy equivocado? Mi experiencia con SIP fue con Ekiga y jamás pude usarlo.

Mil gracias.

Alejo.

---

