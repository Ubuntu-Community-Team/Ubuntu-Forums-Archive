---
title: "problema con códecs (supongo)"
date: 2008-10-15
forum: Software
---

### Post by benjamin_linux on 2008-10-15
Hola!!

para reproducir video tengo instalados Totem y VLC...
En T se me ve el video entrecortado, obviamente sin sonido... en VLC el video se reproduce bien, pero sin sonido... leí que es común que haya un problema de VLC con pulse audio, intenté un par de soluciones que encontré (modificar una opción dentro de preferencias del prog) pero nada... y con respecto al Totem, la verdad que no sé por qué pasa eso, el asunto es que estoy entrando a Win para ver unos míseros ánimes y no me gusta ni medio hacerlo, pero ya no sé qué hacer. Ahh y encima después de que ejecuto el Totem pierdo completamente el sonido, no puedo escuchar ni un mp3 ni un sonido en una página, nada, tengo que reiniciar para volver a escuchar cualquier cosa.
Probé de reinstalar códecs, y nada... Calculo que será un tema de codecs, pero no sé si será algún conflicto con pulse o alsa...
Saben qué puedo hacer?

Mil gracias por adelantado.

---

### Post by santiagoward2000 on 2008-10-15
Hola!
¿Esto te pasa con algún formato en particular o con cualquier video que pongas?

---

### Post by benjamin_linux on 2008-10-15
Con cualquier formato, recién recién he probado con .avi, .mp4 y .mkv

---

### Post by vampichoke on 2008-10-15
tenes instalados los extras restrictivos? (para ver esos formatos de video)
o tenes activado compiz?

---

### Post by benjamin_linux on 2008-10-15
Ahora los tengo instalados (los extras restrictivos), el problema lo tenía de antes, digo no me cambió nada (pensaba que podía ser eso) y sí, tengo activado Compiz. ¿Puede tener algo que ver!?

---

### Post by faktorqm on 2008-10-16
ehh Compiz no...
A mi me pasa si MIENTRAS veo un video en youtube, abro el vlc, no se escucha nada. Tengo que cerrar si o si la pagina, o poner algo en pausa.
Yo tengo todo en alsa, y entre programas (por ejemplo si abro vlc y totem no pasa nada, andan los dos, o sea, mezclan)
Proba por donde esta saliendo cada uno... o en el peor caso empeza a probar de a un programa por vez a ver que pasa. Salu2!

---

### Post by benjamin_linux on 2008-10-16
Vi que es común, que haya problemas con Youtube y reproductores, al mismo tiempo... pero en mi caso, ya he probado de un programa a la vez, reiniciando y ejecutando sea Totem o VLC de una. Y nada de nada.

---

### Post by pol666 on 2008-10-16
abri un totem desde consola y fijate que te dice cuando abris un video

---

### Post by benjamin_linux on 2008-10-16
Gracias a la ayuda de todos, pero

reinstalé uno por uno los codecs y todos los paquetes de gstreamer, la reinicié y voalá, primero probé con el avi, después el mkv y por último el mp4 y el Totem me reproduce perfecto todos. Ya había reinstalado pero los paquetes principales, no todos y lo hice desde Synaptic, no desde consola.

Disculpen pero lo hice de terco nomás y funcionó.

Gracias de nuevo!!

---

### Post by majatu on 2008-10-16
le instalaste codecs al sistema? porque de ultima no los tenes, si no te reprodice mp3 mp4 o similar.

instalate los paquetes gstreamer aver si te va

saludos

---

### Post by benjamin_linux on 2008-10-16
Perdón si no se entendió lo que dije más arriba, estoy con sarampión en cama y estoy ligeramente -tonto-, pero reinstalando todos los codecs y paquetes uno por uno logré que se me reproduzcan bien todos los formatos de video. Gracias!!

---

### Post by kowal on 2008-10-18
Kaffeine + xine. Lo mejor.

---

