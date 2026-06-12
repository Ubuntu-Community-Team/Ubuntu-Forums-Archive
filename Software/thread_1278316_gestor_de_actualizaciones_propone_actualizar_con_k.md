---
title: "gestor de actualizaciones propone actualizar con kernel mas viejo"
date: 2009-09-29
forum: Software
---

### Post by sitiomatic on 2009-09-29
Hola
Yo estoy usando el kernel 2.6.31 y ahora me aparece para actualizar el kernel 2.6.28-15.
Con este kernel mi notebook anda genial, tan bien que borre win y solo uso ubuntu para todo, en cambio con el 2.6.28 tenia montones de problemas con el video intel.
Hay forma de hacer que detecte que tengo algo mas nuevo y no me proponga una actualizacion desactualizada?
Gracias

---

### Post by guillermolisi on 2009-09-29
> **sitiomatic said:**
> Hola
Yo estoy usando el kernel 2.6.31 y ahora me aparece para actualizar el kernel 2.6.28-15.
Con este kernel mi notebook anda genial, tan bien que borre win y solo uso ubuntu para todo, en cambio con el 2.6.28 tenia montones de problemas con el video intel.
Hay forma de hacer que detecte que tengo algo mas nuevo y no me proponga una actualizacion desactualizada?
Gracias
Es que el kernel 31 lo agregaste a mano y en la base de apt, en tu maquina, no esta registrada esa operacion, por eso te avisa sin haber considerado lo que realmente estas usando.

Aparecen en Synaptic los paquetes del kernel que estas usando ahora ?
Si aparecen, marcalos como bloqueados en Synaptic.

---

### Post by sitiomatic on 2009-09-29
Gracias por contestar
Estaban en synaptic
Bloquee:
linux-headers-2.6.31-020631-generic
linux-headers-2.6.31-020631
linux-image-2.6.31-020631-generic
Es correcto?

---

### Post by guillermolisi on 2009-09-29
> **sitiomatic said:**
> Gracias por contestar
Estaban en synaptic
Bloquee:
linux-headers-2.6.31-020631-generic
linux-headers-2.6.31-020631
linux-image-2.6.31-020631-generic
Es correcto?
Estaba pensando que no es necesario el bloqueo ya que apt te traera actualizaciones de los kernels, para el caso, que tengas en la maquina, sea cual sea que utilices.

Es decir, estas usando el 31 pero seguramente tambien tenes instalado y listo para poder usar, eligiendolo con el Grub, el 28.15 y es este el que quiere actualizar (posiblemente con algun parche de seguridad) dejando el 31 tal como lo instalaste hasta que pases a Karmic (que usa el 31).

---

### Post by sitiomatic on 2009-09-30
Si entendi bien, lo que vos me decis es que aunque haga la actualizacion no va a cambiar el kernel que etoy usando. Me confirmas?
Me fije y el 2.6.31 esta en synaptic.

---

### Post by guillermolisi on 2009-09-30
> **sitiomatic said:**
> Si entendi bien, lo que vos me decis es que aunque haga la actualizacion no va a cambiar el kernel que etoy usando. Me confirmas?
Me fije y el 2.6.31 esta en synaptic.
Te confirmo que es asi tal como preguntas. La actualizacion de un kernel que tengas instalado no afecta al que estes usando.

De hecho, en una maquina tengo varios, desde el 24.24 hasta el 28.15 y cuando vienen actualizaciones de kernels actualiza los que tenga, sin importar cual este usando en ese momento.

Como el 31 no esta en los repos oficiales, no se actualizara hasta que tengas instalado Karmic, porque ahi si estara en los repos, pero siempre con versiones superiores a la 31 que es, en definitiva, lo que preguntabas al principio.

---

### Post by sitiomatic on 2009-09-30
Entendido
Mil gracias
Saludos

---

