---
title: "Sin sonido de sistema en Jaunty, pero Sonido mp3 y videos OK..."
date: 2009-05-13
forum: Software
---

### Post by jMont on 2009-05-13
Hola, soy nuevo en el mundo de Ubuntu, y en el foro :P, linux probé MUY POR ARRIBA hace unos años, el SuSE, pero esto es otro mundo :D ... el tema es el siguiente, instalé Jaunty hace aprox. 3 semanas, todo perfecto hasta hace una semana mas o menos que me dejó de funcionar el audio del sistema, o sea, el reproductor de musica (uso Audacious) funca perfecto, los videos (uso SMPlayer) perfecto, pero no tengo sonidos de inicio, los videos de youtube por ejemplo puedo verlos perfectamente pero sin sonido :( , aclaro nuevamente que TODO esto funcionaba perfectamente hasta hace unos días, tambien aclaro que probé muchas cosas, puse todo en (Preferencias->Audio) automático, en Pulse Audio, en ALSA, probé todas las opciones y nada, puse en el gstreamer-preferences el audio en automatico y nada... no se que mas hacer, aclaro que tambien desinstale Pulse Audio desde el Synaptic, y nada, aclaro tambien que en un primer momento no me andaba el sonido del audacious ni del SMPlayer, pero en la config. de sonido de ambos, puse como dispositivo "OSS" y anduvo, pero el sonido del sistema nunca volvio, y no puedo escuchar videos de internet con el Firefox, ni ningun otro explorador... estoy bastante desconcertado... si alguien me puede dar una mano dese ya agradecido, slaudos.

---

### Post by guillermolisi on 2009-05-14
> **jMont said:**
> Hola, soy nuevo en el mundo de Ubuntu, y en el foro :P, linux probé MUY POR ARRIBA hace unos años, el SuSE, pero esto es otro mundo :D ... el tema es el siguiente, instalé Jaunty hace aprox. 3 semanas, todo perfecto hasta hace una semana mas o menos que me dejó de funcionar el audio del sistema, o sea, el reproductor de musica (uso Audacious) funca perfecto, los videos (uso SMPlayer) perfecto, pero no tengo sonidos de inicio, los videos de youtube por ejemplo puedo verlos perfectamente pero sin sonido :( , aclaro nuevamente que TODO esto funcionaba perfectamente hasta hace unos días, tambien aclaro que probé muchas cosas, puse todo en (Preferencias->Audio) automático, en Pulse Audio, en ALSA, probé todas las opciones y nada, puse en el gstreamer-preferences el audio en automatico y nada... no se que mas hacer, aclaro que tambien desinstale Pulse Audio desde el Synaptic, y nada, aclaro tambien que en un primer momento no me andaba el sonido del audacious ni del SMPlayer, pero en la config. de sonido de ambos, puse como dispositivo "OSS" y anduvo, pero el sonido del sistema nunca volvio, y no puedo escuchar videos de internet con el Firefox, ni ningun otro explorador... estoy bastante desconcertado... si alguien me puede dar una mano dese ya agradecido, slaudos.
Por casualidad, en esa revisacion que hiciste te fijaste en cual es el Master Control de audio en la consola/Mix ?

De paso, fijate que los controles de volumen esten cerca del maximo y anda probando. No seria la primera vez que algunos sonidos no se escuchan porque el control que maneja su volumen esta al minimo o silenciado.

---

### Post by jMont on 2009-05-15
> **guillermolisi said:**
> Por casualidad, en esa revisacion que hiciste te fijaste en cual es el Master Control de audio en la consola/Mix ?

De paso, fijate que los controles de volumen esten cerca del maximo y anda probando. No seria la primera vez que algunos sonidos no se escuchan porque el control que maneja su volumen esta al minimo o silenciado.

Guillermo, antes que nada, gracias por contestar, hace bastante que vengo con este problema y no logro solucionarlo, te comento que todos los volumenes estan al maximo, aparte como te comenté escucho mp3 y escucho los videos con el SMPlayer perfectamente seleccionando en ambos casos "OSS", no se como acceder al Master Control de la consola :P soy nuevito en esto, pero desde Preferencias->sonido puse todas las opciones y nada, incluso entre en el gstreamer-preferences y nada, saludos.

---

### Post by victor maldonado on 2009-05-21
hola: mira yo tambien soy nuevo y tengo un porblema parecido pero para entrar a la consola para ver el master debes escribir en la terminal( aplicaciones-accesorios-terminal) alsamixer y ahi ves los nivesles y los subes. te mueves con las flechas hacia los lados y subes el volumen con la flechas hacia arriba.. espero que sirva de algo

Atte

victor

---

### Post by ramiro_md on 2009-05-21
Ejecuta alsaconf. Bienvenido a Ubuntu !

---

### Post by gmunioz on 2009-05-22
Hola jmo....:

Si estas usando jaunty, es un problema de pulseaudio.

Esta compitiendo con alsa por el dispositivo de sonido.

Prueba desinstalar pulseaudio y dejar solo alsa.

Aplicaciones - Accesorios - Terminal

sudo aptitude purge pulseaudio

Sugerencia: antes de utilizar un comando con sudo, averigua

que hace con

man comando

Saludos.

---

