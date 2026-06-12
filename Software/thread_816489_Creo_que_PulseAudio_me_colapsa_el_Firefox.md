---
title: "Creo que PulseAudio me colapsa el Firefox"
date: 2008-06-02
forum: Software
---

### Post by nemodot on 2008-06-02
Buenas, hace unos días había iniciado un post en el que buscaba una solución para un problema que tenía con el audio, lo que pasaba era que cuando reproducía flash se me colgaban los reproductores de audio. Me recomendaron que usara PulseAudio para todo y lo hice y se corrigieron todos los problemas, pero uno nuevo apareció.

Resulta que la mayoría de las veces que comienzo a ver un video en flash, o sea, la primera vez que lo hago luego de abrir el firefox, éste se cierra y tengo que volver a abrirlo, a partir de ahi ya no se cierra solo (no siempre).

Uso Ubuntu Hardy y en mi configuración de audio tengo PulseAudio para todo. Uso Firefox 3 beta 5

---

### Post by pol666 on 2008-06-02
> 
Resulta que la mayoría de las veces que comienzo a ver un video en flash, o sea, la primera vez que lo hago luego de abrir el firefox, éste se cierra y tengo que volver a abrirlo, a partir de ahi ya no se cierra solo (no siempre).


ME TIENE LOS ##### POR EL PISO!!!!!!!!!!!!! NO SE QUE HACER. 

yo pense que era de Firefox por ser beta pero parece que es de Pulceaudio :mad: me tiene cansado

---

### Post by osensei on 2008-06-02
Probá de instalar el paquete **libflashsupport** que es soporte de pulseaudio para flash, podés instalarlo desde el administrador de paquetes Synaptic, o desde la consola con el siguiente comando:

```
sudo apt-get install libflashsupport
```

---

### Post by osensei on 2008-06-02
Por otro lado, te cuento que muchos usuarios de linux experimentan una baja performance con el último flash player (9.0.124), sobre todo en la reproducción de videos. Si querés podés probar de instalarte la versión 9.0.48 que funciona mejor. En este post ya expliqué cómo conseguirla: [http://ubuntuforums.org/showthread.php?p=5000032#post5000032](http://ubuntuforums.org/showthread.php?p=5000032#post5000032)

---

### Post by pol666 on 2008-06-02
> **osensei said:**
> Probá de instalar el paquete **libflashsupport** que es soporte de pulseaudio para flash, podés instalarlo desde el administrador de paquetes Synaptic, o desde la consola con el siguiente comando:

```
sudo apt-get install libflashsupport
```



Te pensas que si no tuviera ese paquete escucharia algo?

---

### Post by marianom on 2008-06-02
Te voy a estar muy agradecido si bajas un poco el tono de tus respuestas, pol666.
Creo que todos entendemos lo irritante del problema pero si le ladras a la gente que te hace llegar su comentario, no vas a lograr otra cosa que predisponer de mala forma a quienes te podrían dar una mano.

---

### Post by nemodot on 2008-06-02
No creo que pol666 quisiera irritar a nadie con su comentario sobre el libflashsupport. De cualquier manera tiene razón, ya tengo instalado ese paquete desde antes del problema.

Pol666, si te molesta mucho, intenta cambiar de PulseAudio al anterior Alsa. El más viejo no me deja reproducir musica y flash al mismo tiempo aunque no me cierra el firefox cada vez como con el PulseAudio. 

Bueno, mi problema persiste, voy a intentar instalar una versión anterior del flash como osensei sugirió.

Saludos a todos.

---

### Post by osensei on 2008-06-03
> **pol666 said:**
> Te pensas que si no tuviera ese paquete escucharia algo?

Primero que nada, gracias Mariano por tu comentario. Segundo, pol666 mi post iba destinado a quien inició la consulta. Tercero: sí, podrías escuchar algo, porque según la experiencia que he tenido yo, sin ese paquete el sonido sale por ALSA, o al menos a mí así me pasaba en mi notebook en la cuál tengo el sonido onboard, más una placa de sonido usb, y al no tomarme el pulseaudio y salir por la usb, salía por los parlantes de la notebook mediante ALSA.

Saludos, y suerte con pulseaudio, firefox y flash!

---

### Post by pol666 on 2008-06-03
se agradece a ambos pero voy a esperar a actualizaciones y mientras maldigo a Adobe, Pulceaduio y todo el equipo de mozilla. Saludos

---

