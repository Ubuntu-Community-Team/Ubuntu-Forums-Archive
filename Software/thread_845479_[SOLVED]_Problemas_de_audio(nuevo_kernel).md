---
title: "[SOLVED] Problemas de audio(nuevo kernel?)"
date: 2008-06-30
forum: Software
---

### Post by Vero1 on 2008-06-30
Hola,

Aparte de tener problemas con nvidia(expuesto en otro post) tambien se me presenta el problema de no tener audio de ninguna especie.

Alsa está instalado.

Probé el otro día abrir un video que es wmv y como no funcionaba me puse a buscar en Google donde leí que había que instalar el codec w32. Lo hice pero a pesar de éso cuando quiero ver ese video me sale un cartelito que dice: Failed to connect stream. Invalid argument.

No sé qué hacer.

Gracias

---

### Post by Vero1 on 2008-06-30
> **Vero1 said:**
> Hola,

Aparte de tener problemas con nvidia(expuesto en otro post) tambien se me presenta el problema de no tener audio de ninguna especie.

Alsa está instalado.

Probé el otro día abrir un video que es wmv y como no funcionaba me puse a buscar en Google donde leí que había que instalar el codec w32. Lo hice pero a pesar de éso cuando quiero ver ese video me sale un cartelito que dice: Failed to connect stream. Invalid argument.

No sé qué hacer.

Gracias

Cuando quiero probar los sonidos, me sale este cartel:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by Vero1 on 2008-07-03
> **Vero1 said:**
> Cuando quiero probar los sonidos, me sale este cartel:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Sigo sin audio. Ahora cuando quiero correr gnome-alsamixer me sale lo siguiente:

(gnome-alsamixer:8569): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Fallo de segmentación

A ver si alguien entiende qué está pasando, por favor.

Gracias

---

### Post by Mauro22 on 2008-07-03
En sistema -> preferencia -> sonido. Tenes en autodetectar?

Porque HH usa pulseaudio. bah.. al menos yo no tengo mas alsa.

---

### Post by Vero1 on 2008-07-03
Mauro,

Justo hace 10 minutos se solucionó el asunto gracias a la ayuda de erUSUL de ubuntu-es.

Agradezco tu interés.

saludos

p.d.
hubo que reinstalar los módulos.

---

