---
title: "Paso a Intrepid y problemas con GKsudo"
date: 2008-12-25
forum: Software
---

### Post by z37a on 2008-12-25
Bueno gente, hoy pase todo lo de mi anterior pc a la misma pero con otro HDD, asi que aproveche y le instale intrepid, que me gustaba mas que hardy.

Si bien me tope con un problema con el nuevo network manager(que hay otro post pro esto) ahora estoy notando algo extraño. Antes con hardy utilizaba el comando gksudo delante del programa que quisiera ejecutar como root, el tema es que ahora no puedo ejecutar casi nada con el gksudo, pero si con el sudo!!!

Por ejemplo:

gksudo xterm -> Funciona OK
gksudo virt-manager -> No funciona para nada
sudo virt-manager -> Funciona de 10

Que puede ser esto? es indispensable que ejecute el virt-manager como root(por que si no lo hago no puedo agregar nics adicionales a las vms, ya probé de todo y no logro hacerlo andar para el user). Mientras podría aguantar de ejecutar sudo pero mi idea es dejar todo bien prolijo.

---

### Post by Hei Ku on 2008-12-25
te tira algun mensaje de error?
si lo ejecutas desde la consola, qué dice?

---

### Post by z37a on 2008-12-25
> **Hei Ku said:**
> te tira algun mensaje de error?
si lo ejecutas desde la consola, qué dice?

Simplemente no dice nada, solo hace como si lo ejecutara y se cerrara, no da ni un solo error.

Te comendo de paso, probe tambien con gksu.

Me falto decir, es un sistema de 64 bits, puede que tenga algo que ver?

---

### Post by Hei Ku on 2008-12-26
Incluso desde consola no dice nada?

No creo que lo de 64bits tenga algo que ver, salvo q lo hayan empaquetado muy mal.

---

### Post by z37a on 2008-12-26
> **Hei Ku said:**
> Incluso desde consola no dice nada?

No creo que lo de 64bits tenga algo que ver, salvo q lo hayan empaquetado muy mal.

La consola no dice absolutamente nada, peor lo que pude notar que es mas raro aun es que si modifico en el menu la ejecucion y la pongo como "sudo virt-manager" y ejecutar en un terminal, abre la terminal me abre el virt-manager y se cierra sola la terminal dejandome al virt-manager como root

---

