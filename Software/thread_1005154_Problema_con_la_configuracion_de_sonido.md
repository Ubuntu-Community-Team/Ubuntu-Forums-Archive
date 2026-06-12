---
title: "Problema con la configuracion de sonido"
date: 2008-12-08
forum: Software
---

### Post by hexbase on 2008-12-08
Desde que instale ubuntu, no me funciona el controlador de volumen(el parlantito del panel), ya que lo pongo en silencio y sigue funcionando a todo volumen.
Otra cosa que no me anda es el Ardour. Pedi ayuda en el canal de irc de ardour y un usuario me intento guiar para que funcionara. Llegamos a un punto en que el Ardour y jack estaban bien conectados, pero igual no salia sonido de Ardour. Entonces descartamos dichos programas y deducimos, porque el qtjackctl no mostraba todos(9) los input ports que deberia tener, que es algo con alsa o alguna config que esta mal hecha y no deja que la placa de sonido funcione bien.

Alguna sugerencia?

---

### Post by sajnox on 2008-12-08
Hola,

Postea la salida del comando 

```
asoundconf list
```

---

### Post by hexbase on 2008-12-08
hexbase@HEXBASE:~$ asoundconf list
Names of available sound cards:
CA0106


Eso es el output.

---

### Post by sajnox on 2008-12-09
Yo tenia esa placa, si mal no recuerdo es una Genius soundvalue (o algo asi era el nombre)

El tema del parlantito de sonido: Hace doble click en el parlantito y ajusta las opciones, el tema es que el control de volumen del "parlantito" esta apuntado a otra cosa y no a tu placa de sonido, es por eso que no manejas el sonido desde ahi. Cambiale algunas configuraciones y con eso vas a andar tranquilo

En la opcion de sonido fijate que server de audio usas.

Saludos

---

### Post by hexbase on 2008-12-09
En la configuracion es lo que quiero arreglar.
La placa es una sound blaster audigy live.

---

### Post by sajnox on 2008-12-10
La Audigy, perdon. Es la que compre despues de la Genius.

---

### Post by pabloatilio on 2008-12-10
> **sajnox said:**
> Hola,

Postea la salida del comando 

```
asoundconf list
```

Hola a todos, yo también tengo casi el mismo problema

Cuando pongo el comando asoundconf list me tira "NVidia"

Mi equipo es una asus a6tc, en la selección de lo que el 
applet del parlantito me puede controlar me sale :

-- realtec alc660
(y las opciones volúmen, linea de entrada, micrófono,cd, pcm-2
 ganancia de entrada, digital-1)
-- playback ALSA PCM on front:0 (ALC861 A...
( y la opción master)
-- Capture: Monitor source of ALSA PCM on...
(y la opción master)
-- Capture ALSA PCM on front:0 (ALC861 A...
(y la opción master)

puedo configurar que me de bola el control del parlantito (pongo lo mismo en los dos lados),
pero no funca el volumen, probé varias formas pero no acierto con niguna

En las opciones de sonido tengo : 
-- Si3054 Modem
-- ALC861 Digital
-- ALC861 Analog
-- ALSA - Advanced linux Sound Architecture
-- OSS - Opend Sound System
-- PulseAudio Sound Server

¿alguien sabe como va o donde leer material que explique el tema ?
Gracias, Saludos

PabloA

---

