---
title: "no me va sonido en ubuntu 9.10"
date: 2009-11-12
forum: Software
---

### Post by sitodonosti on 2009-11-12
hola, he instalad ubuntu 9.10 en el portatil, el caso es que al principio si que tenia sonido y tal pero ahora de repente asi sin venir aceunto se me ha ido el sonido, he mirado en preferencias de sonido hardware y no me aparece ninguna tarjeta de sonido, es una intel, pogo la salida lspci:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

sabeis proque peude ser¿

un saludo gracias

---

### Post by guillermolisi on 2009-11-12
Fijate si podes inicar Alsamixer en una terminal/consola y verificar que los controles esten al maximo y sin silenciar.

Si esta todo activo y al maximo y aun asi no hay sonido, dale una ledia a [este thread]("http://ubuntuforums.org/showthread.php?t=1306815&highlight=sonido").

---

### Post by sitodonosti on 2009-11-13
hola he peusto lo que me dijiste en consola y me aparece la imagen agregada, después también he peusto lo que ponia en el foro y sale eso:
 0 snd_hda_intel

Tengo que hacer algo más? esque lo que me parece muy muy raro es que al principio si me vaya el sonido y que de la noche a la mañana no vaya nuse es muy muy raro.

un saludo

---

### Post by josecuervo86 on 2009-11-13
A ver, pusiste **alsamixer** en consola y no te aparecio nada? ok, en una terminal pone:

```
gstreamer-properties
```

y fijate que controladores tenes para la salida de audio.

---

### Post by sitodonosti on 2009-11-13
ostia soy tonto se me ovlido añadir la foto joder!!jaja lo siento aki va la foto

poniendo gstreamer-properties me sale:
la otra foto

---

### Post by josecuervo86 on 2009-11-13
Si subis el **Master** al tope (en alsamixer) que pasa? Si en gstreamer en vez de autodetectar (en output) pones ALSA?

---

### Post by sitodonosti on 2009-11-13
no pasa nada, no se escucha nada, estado intentado con todos pero nada no hay forma, y poniendoel master a tope tampoco 
:(

---

### Post by sitodonosti on 2009-11-18
Buenas vuelvo a las andadas, he reisntalado el sistema pero nada, al principio el sonido funciona pero una vez que empiezo a instalar medibuntu, build-essential ubuntu-restricted-extras

se va, lo unico que estabez al instalar w32codecs y free-codecs me aparece este error, nose si tiene que ver:
Los siguientes paquetes tienen dependencias incumplidas:
  w32codecs: Depende: libstdc++5 (>= 1:3.3.4-1) pero no es instalable
E: Paquetes rotos

y por supuesto el sonido sigue sin funcionar que puedo hacer?

---

### Post by sitodonosti on 2009-11-18
Valeeeee he conseguido solucionarlo!!!

El caso es que en controladores de hardware me aparecia para instalar el modem, en el que ponia: 
The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa supportand intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

Este controlador activa el uso de muchos módem por software, muy habituales en portátiles.

Si no activa el controlador, no podrá usar su módem.

He desactivado esto y ya me va perfectamente el sonido!!

Un saludo y gracias!

---

### Post by guillermolisi on 2009-11-18
Felicitaciones !! :D

---

