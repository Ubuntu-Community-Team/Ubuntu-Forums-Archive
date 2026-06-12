---
title: "[SOLVED] Problema con audio (no funciona stereo)"
date: 2009-07-11
forum: Software
---

### Post by ketzelleshelle on 2009-07-11
Instalé Ubuntu 9.04 en una Dell Inspiron 1525 y se me presenta el problema de que en cualquiera de las dos entradas frontales para auriculares el sonido se oye por un solo lado. Solo se oye por los dos cuando dejo el plug del auricular por la mitad...

Alguna ayuda o sugerencia para empezar a ver por donde viene el problema?
Muchas Gracias!

---

### Post by guillermolisi on 2009-07-11
En los parlantes incorporados se oye bien por los dos y con el efecto stereo o solo mono ?

---

### Post by ketzelleshelle on 2009-07-11
Por los parlantes (que de por sí son bastante pobrecitos, no suenan muy bien que digamos) pareciera que el estetreo funciona bien...
Gracias por la respuesta.

---

### Post by guillermolisi on 2009-07-11
Ahora que pienso, por que mencionas "dos entradas frontales" ?
Es una para cada auricular ?

No hay una sola que contemple los dos canales stereo ?

---

### Post by ketzelleshelle on 2009-07-11
No. La Dell vino con dos entradas para dos auriculares, ambas stereo.
Con windows funcionan sin problemas.

---

### Post by guillermolisi on 2009-07-11
Si con Win funcionan perfecto con los mismos auriculares, decididamente es una cuestion de drivers de audio o de configuracion de la placa (o ambas cosas).

---

### Post by ketzelleshelle on 2009-07-12
Gracias. Era configuracion de la placa y las opciones de la misma.
Luego de buscar y buscar (recomiendo ampliamente Uboontu) dí con la solución precisa.

Tema cerrado!

---

### Post by Hei Ku on 2009-07-12
Podes dar detalles de cómo fue el arreglo, para alguien que tenga tu mismo problema? Gracias!

---

### Post by ketzelleshelle on 2009-07-17
Porsupuesto y pido disculpas no haberlo hecho.
En una terminal escribí "Alsamixer" con lo cual se me abrieron los controles de audio y configuré todo desde ahí, tenía un canal deshabilitado.
Y además subí el volumen general de los parlantes frontales que estaban bastante bajos.

---

