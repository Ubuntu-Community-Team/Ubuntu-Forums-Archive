---
title: "Horrible problema en Amarok 2.2: Saltos en la reproducción"
date: 2009-11-07
forum: Software
---

### Post by pol666 on 2009-11-07
Desde que uso Amarok 2.2 que se producen pequeños cortes en la reproducción cada tantos segundos. Molestísimo. Googlie pero no encontre nada

---

### Post by guillermolisi on 2009-11-07
> **pol666 said:**
> Desde que uso Amarok 2.2 que se producen pequeños cortes en la reproducción cada tantos segundos. Molestísimo. Googlie pero no encontre nada
Raro porque desde que actualice a KK y por ahora Amarok funciona tan bien como siempre (por no decir mejor proque esta mucho mas estable que su version anterior).

---

### Post by pol666 on 2009-11-07
Es 64 bits? Por que yo culpo a eso...

---

### Post by guillermolisi on 2009-11-07
> **pol666 said:**
> Es 64 bits? Por que yo culpo a eso...
No, por ahora uso software de 32 bits.
De todas formas, se me ocurre que el problema debe estar en alguna libreria que usa Amarok que no sea igual en 64 bits que en 32.

---

### Post by pablo.s on 2009-11-08
Recuerdo que hace unos meses
hubo un  problema de PulseAudio
que se puedo solucionar cambiandole
la configuración de los fragmentos
que enviaba al servidor para reproducir.
En lugar de mandarle 10 fragmentos
de diez segundos, la solución consistió
en que enviara 20 fragmentos de cinco
segundos y asi se solucionaban los saltos.

Por supuesto que Amarok no utiliza
PulseAudio, pero en base a esta solución
se puede aplicar al servidor que tenga en
uso. ¿Cuál usa?

---

### Post by pol666 on 2009-11-08
> **pablo.s said:**
> Recuerdo que hace unos meses
hubo un  problema de PulseAudio
que se puedo solucionar cambiandole
la configuración de los fragmentos
que enviaba al servidor para reproducir.
En lugar de mandarle 10 fragmentos
de diez segundos, la solución consistió
en que enviara 20 fragmentos de cinco
segundos y asi se solucionaban los saltos.

Por supuesto que Amarok no utiliza
PulseAudio, pero en base a esta solución
se puede aplicar al servidor que tenga en
uso. ¿Cuál usa?

Phonom se llama, creo que es lo que cumple la función de pulseaudio en KDE.

---

### Post by pablo.s on 2009-11-08
> **pol666 said:**
> Phonom se llama, creo que es lo que cumple la función de pulseaudio en KDE.

Ahora me fijo si es similar y
si es asi te comento.

---

### Post by oktubrer on 2009-11-08
> **pol666 said:**
> Es 64 bits? Por que yo culpo a eso...

Yo uso la versión de 64 bits y no tiene problemas, asi que debe venir por otro lado.

---

### Post by pol666 on 2009-11-30
Hola, se acuerdan de esto? Bueno me pase a 32 bits y sigue pasando.

---

### Post by pol666 on 2009-12-06
Bump y noticias: Con Exaile no sucede, también intente usar Gstreamer en amarok pero ni siquiera reproduce.

---

