---
title: "Amarok deja de sonar cuando otro programa emite sonido"
date: 2009-10-29
forum: Software
---

### Post by serwwweb on 2009-10-29
Hola, tengo este problema con el sonido que como dice en el titulo del post pasa que cuando un programa comienza a sonar como por ejemplo Kopete (K3B, y cualquiera que suene) cuando da un aviso, el otro programa deja de hacerlo.
En realidad lo que mas me molesta es cuando estoy escuchando musica que Amarok deja de sonar y tengo que parar y volver a iniciar el track de audio para que vuelva a sonar.
En la configuracion de sonido tengo HDA nVidia y Pulse Audio y con cualquiera de los dos me pasa exactamente lo mismo.

Estoy usando Kubuntu Karmic RC

---

### Post by guillermolisi on 2009-10-29
> **serwwweb said:**
> Hola, tengo este problema con el sonido que como dice en el titulo del post pasa que cuando un programa comienza a sonar como por ejemplo Kopete (K3B, y cualquiera que suene) cuando da un aviso, el otro programa deja de hacerlo.
En realidad lo que mas me molesta es cuando estoy escuchando musica que Amarok deja de sonar y tengo que parar y volver a iniciar el track de audio para que vuelva a sonar.
En la configuracion de sonido tengo HDA nVidia y Pulse Audio y con cualquiera de los dos me pasa exactamente lo mismo.

Estoy usando Kubuntu Karmic RC
Si estas usando Kubuntu no se utiliza Pulse Audio.

---

### Post by pablo.s on 2009-10-29
En defensa de PulseAudio debo
decir que tiene la funciòn de mezclado.
Para explicarlo mejor, si estàs 
escuchando mùsica con Banshee por
ejemplo, y K3B te notifica con su
clàsica trompeta que termino de grabar,
suenan tanto la mùsica como el sonido
de la trompeta al mismo tiempo, aunque
baja la mùsica un poquito.

---

### Post by serwwweb on 2009-10-29
Ok, hasta ahora no estaba usando pulse, pruebo y te cuento, gracias...

---

### Post by serwwweb on 2009-10-29
Ok, acabo de probar Pulse Audio y me dice: "El dispositivo reproductor de Audio Pulse Audio no funciona. Se recurre a HDA Nvidia".
Que otra cosa podria hacer para solucionar esto?

---

### Post by Applelnx on 2009-10-29
Me pasa lo mismo. Hay como si fuese un "canal" de audio para el sistema (sonidos de sistema, amarok, dragon player, etc), y otro para los otros programas (vlc, videos de youtube). En cuanto los mezclas, ahi vienen los problemas y deja de funcionar uno de los 2.

---

### Post by pol666 on 2009-10-29
A mi me suceden pequeños cortes de menos de 1 segundo.. bastante molesto a la larga, no se que hacer.

Tal vez esos cortesitos se producen cuando el Kmess envia alguna notificación, ahí tendria más sentido.

---

### Post by serwwweb on 2009-11-19
Bueno hoy despues de navegar mucho y buscar una solucion se me ocurrio fijarme si tenia instaladas las librerias pulseaudio y no estaban instaladas aunque en la parte de multimedia de la configuracion de sistema me aparecia como seleccionable.
Lo que hice fue instalar lo siguiente y luego reiniciar previamente seleccionando como predeterminado pulseaudio:

pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio
pulseaudio-module-x11
pulseaudio-utils
pulseaudio-esound-compat

Eso fue todo, una tonteria, me siento como un idiota despues de haber dado vueltas hace casi un mes con este tema.
Espero que les sirva.
Saludos y que esten bien... ;)

---

