---
title: "Problema con librerias despues de instalar python 2.7"
date: 2010-11-15
forum: Software
---

### Post by agustinc on 2010-11-15
El problema es mas o menos lo que dice el título, tengo ubuntu 10.10 y se me ocurrió instalar la versión 2.7 de python por lo que lo bajé de la página oficial y lo instalé, hasta ahí todo bien, el inconveniente viene cuando quiero utilizar alguna librería (gtk por ejemplo) y me dice que no existe pero está instalado.

Es más, si ejecuto python2.6 y la importo no tengo drama. Ya busqué y rebusqué y no encontré la solución ¿Cómo hago para que me las reconozca?

Ah, soy nuevo en el foro así que si rompo alguna regla pido disculpas.

---

### Post by hectorivand on 2010-11-18
> **agustinc said:**
> El problema es mas o menos lo que dice el título, tengo ubuntu 10.10 y se me ocurrió instalar la versión 2.7 de python por lo que lo bajé de la página oficial y lo instalé, hasta ahí todo bien, el inconveniente viene cuando quiero utilizar alguna librería (gtk por ejemplo) y me dice que no existe pero está instalado.

Es más, si ejecuto python2.6 y la importo no tengo drama. Ya busqué y rebusqué y no encontré la solución ¿Cómo hago para que me las reconozca?

Ah, soy nuevo en el foro así que si rompo alguna regla pido disculpas.

Hola como para tirar luz sobre el asunto. Probaste con actualizar los paquetes de las librerías, tal vez para trabajar necesita una versión nueva de las mismas.

Saludos
Nacho

---

### Post by agustinc on 2010-11-21
> **hectorivand said:**
> Hola como para tirar luz sobre el asunto. Probaste con actualizar los paquetes de las librerías, tal vez para trabajar necesita una versión nueva de las mismas.

Saludos
Nacho

De hecho, eso ya lo hice, pero según lo que veo el problema radica en que el import path de mi python2.6 es diferente al de python2.7.

Leí por ahí que tengo que escribir un archivo en cierto lugar para que python los busque, así que mi pregunta ahora sería ¿Cómo lo hago?

(Nota mental: Antes de meter dedos, preguntar cómo hacerlo)

---

### Post by Thunderfunk17 on 2010-11-29
¿Alguien ha encontrado una solución?
:D

---

### Post by agustinc on 2010-12-01
Mmm, lo que hice para "solucionar" fue usar el método poco recomendado de reinstalar ubuntu jaja. Igualmente lo dejo abierto por si alguien (Yo incluído) encuentra una solución.

Otra cosa que se puede hacer es un append a la librería sys, pero esa solución sirve sólo para lo que uno haga, no sé si me explico

---

