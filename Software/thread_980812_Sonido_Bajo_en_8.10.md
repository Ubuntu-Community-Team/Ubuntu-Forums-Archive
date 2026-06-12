---
title: "Sonido Bajo en 8.10"
date: 2008-11-13
forum: Software
---

### Post by Estranged2 on 2008-11-13
Gente, tengo un pequeño problema con el sonido. Escucho bien, pero no al volumen normal. Tengo que poner los parlantes al máximo para escuchar lo que en Windows escucho cuando está a la mitad.
Me dijeron que tipee alsamixer en la consola, y están todos al máximo, pero sin embargo no se escucha con el volumen que debería.
Me pasa tanto en reproductores de música como con el sonido de videos...
Alguien sabe qué puede estar pasando?

---

### Post by hictio on 2008-11-13
Yo tenia un problema similar, pero solo para los audios de sistema (el de login, y logout, por ejemplo, y de las animaciones Flash); todo lo demas se escuchaba perfecto.
No se si ya lo probaste, pero, en mi caso, el problema lo solucione subiendo el volumen de 'PCM' a traves de click en el icono del parlante, y seleccionaar 'Open Volume Control'.

---

### Post by Estranged2 on 2008-11-13
Sí ya lo probé. Está todo al máximo. No sé si será un problema de codecs o de drivers de la placa... Es rarísimo, porque prácticamente todo el volúmen se reduce a la mitad de lo que reproduce cuando uso Windows...
Les juro que es lo único que me falta para que Ubuntu me funcione a la perfección y no volver a windows hasta que salga el Diablo III jajaja

---

### Post by hictio on 2008-11-13
Ok, entonces, proba lo siguiente:

"System -> Preferences -> Sound"

Selecciona el tab "Devices", y luego los diferentes eventos, hace click en "play", y fijate si tenes output.
Si no tenes, proba uno diferente, yo tuve que pasarme a los de OSS.

[URL=http://img58.imageshack.us/my.php?image=audiodemierdaqk2.png][IMG]http://img58.imageshack.us/img58/8707/audiodemierdaqk2.th.png[/IMG]
[/URL]

---

### Post by facundocorradini on 2008-11-13
Yo tengo (casi) el mismo problema. 

Tengo un arranque dual de 8.04 y 8.10, y en 8.10 el volumen es mas o menos la mitad que en 8.04....

Voy a ver si encuentro alguna diferencia en las preferencias...

---

### Post by Gpafundi on 2008-11-14
Yo tengo el mismo problema.

---

### Post by sajnox on 2008-11-17
> **Estranged2 said:**
> Gente, tengo un pequeño problema con el sonido. Escucho bien, pero no al volumen normal. Tengo que poner los parlantes al máximo para escuchar lo que en Windows escucho cuando está a la mitad.
Me dijeron que tipee alsamixer en la consola, y están todos al máximo, pero sin embargo no se escucha con el volumen que debería.
Me pasa tanto en reproductores de música como con el sonido de videos...
Alguien sabe qué puede estar pasando?

Vamos por lo basico, podes postear la salida del comando

```
asoundconf list
```

Asi vemos que placa de sonido tenes, yo tenia una problema parecido en una notebook toshiba, esto lo tuve con Gutsy

---

### Post by guillermolisi on 2008-11-17
Hasta aqui y salvo contadas pocas excepciones, los que han experimentado este sintoma lo han solucionado revisando todos los controles de volumen del mixer.

Si no se ven todos los controles, hay que hacer que se vean, activarlos y jugar con ellos para identificar cual es el que esta como master regulando el volumen general del sistema de sonido.

Una alternativa rapida es ir a consola de comandos y ejecutar alsamixer. Ahi se veran y podran probar todos los controles de la consola de audio.

---

### Post by acdm86 on 2008-11-18
Hola, a mi me pasaba lo mismo y lo solucione asi, segun una recomendacion que me dieron en la lista, click secundario en el parlantito, arriba a la derecha, abrir control de volumen y darle a todo lo que te parezca para arriba, anda probando, asi lo hice yo y funciono

---

### Post by mixed on 2008-11-24
yo tenia el mismo problema pero lo solucione mas o menos . abris las opciones de sonido .preferencias y le marque la casilla que dice external amplifier y todo lo que sea output. asi me mostraba las opciones para subir el sonido soundround etc. algo mejoro . uso alsa y mi driver de sonido es el via 8237

---

