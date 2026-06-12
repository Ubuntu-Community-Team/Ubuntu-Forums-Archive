---
title: "Ubuntu 9.04 lento con baterias."
date: 2009-09-18
forum: Software
---

### Post by flakojaime on 2009-09-18
Asi es.

No me habia dado cuenta, ya que uso mi notebook siempre conectado con el cargador y sin la bateria.

Cuando uso el note con la bateria, se pone muy lento para su harware, incluso forzando el procesador a 2.4 Ghz. Hasta el puntero del raton se relantiza.

En un dell Xps 1730, con ubuntu 9.04 instalado. Funciona de marvilla el compiz fusion.
Las baterias estan nuevas. Ram de 4Gb, memoria de video independiente de 512 Mb y procesador Core2duo de 2,4 Ghz.

Gracias.

JJGN

---

### Post by Carlos C on 2009-09-19
¿Qué ocurre si usas el comando "top" cuando el computador se comporta de esa manera? Es posible que si lo haces veas el proceso que está exigiendo tanto a tu equipo.

Saludos.

---

### Post by flakojaime on 2009-09-19
Hola.

Esto me sale:

[[IMG]http://img17.imageshack.us/img17/509/pantallazoem.th.png[/IMG]](http://img17.imageshack.us/i/pantallazoem.png/)

---

### Post by moreback on 2009-09-19
¿Seguro que el procesador está al máximo (gobernador en "Performance")?

---

### Post by flakojaime on 2009-09-20
Si
 
El procesador esta forzado a 2.4 Ghz, los dos cores :P.
 
Saludos

---

### Post by moreback on 2009-09-20
A menos que en Windows no te pase lo mismo, se me ocurre que pueda ser algo del diseño del notebook que hace que funcione así, creo que los Macbook Air sufrían un problema similar. No se me ocurre otra cosa ya que me dices que tienes los procesadores al máximo y no veo otra cosa que pueda poner lento tu notebook.

---

### Post by Carlos C on 2009-09-20
Si miras lo que te muestra top verás que los procesos "Xorg" y "compiz.real" están exigiendo tu cpu. Podrías probar desactivando los efectos de compiz y ver si te ocurre lo mismo.

Saludos.

---

### Post by flakojaime on 2009-09-20
Bueno.

Desactive el compiz (metacity --replace)y todo vuelve a ser rápido. Incluso con el procesador On demand.

Lo que me tiene algo molesto es que con el hardware que tiene el notebook no deberia darme esos problemas. Con el adaptador de corriente no da ninguna problema (On Demand)

Corrijanme si estoy equivocado por favor.

Gracias por todo.
FLKJM

---

### Post by flakojaime on 2009-09-20
> **moreback said:**
> A menos que en Windows no te pase lo mismo, se me ocurre que pueda ser algo del diseño del notebook que hace que funcione así, creo que los Macbook Air sufrían un problema similar. No se me ocurre otra cosa ya que me dices que tienes los procesadores al máximo y no veo otra cosa que pueda poner lento tu notebook.


Con windows no me daba esos problemas, funcionaba con la misma velocidad en AC o con baterias.

Por eso me extraña su comportamiento.

El harware no es poco para que se ponga lento.:confused:

Voy a seguir investigando.

Saludos 

FLKJM

---

