---
title: "El sistema se cuelga a los 3 minutos de estar funcionando"
date: 2009-09-14
forum: Software
---

### Post by darkneo on 2009-09-14
Gente soy nuevo en este foro y la verdad necestio la ayuda de un grosso de ubuntu o mejor dicho de Linux.
Tengo el siguiente problema:

Tengo un AMD LE-1250 2.2GHZ, 2GB de Ram un disco de 320Gb y otro de 160Gb, la cuestion es que quise instalar cualquier version de ubuntu, desde la 7.04 hasta la 9.04 y kubuntu, xubuntu 9.04 y hasta el Fedora 11, y el problema es que se me cuelga la pc cuando inicio el sistema, me logueo perfecto, entro al sistema y a los 3 minutos se me cuelga el sistema, en terminal y en modo grafico. La verdad me volvi loco para solucionar el problema pero no le pudo encontrar solucion, probe sacandole el acpi, apic y todo eso y no anda ninguna version. La version de windows que tengo es la XP, no tendria que generar ningun problema. Yo me kiero pasar a Ubuntu y poder usar mi modem 3G de claro el cual probe el de Movistar en la version 9.04 y anduvo perfecto pero el de claro no, pero igual quiero que no se me cuelgue mas, alguno podria ser tan amable en ayudarme?? Gracias!!

---

### Post by staar on 2009-09-14
haces algo en especial antes de que se cuelgue? corriste un memtest para comprobar las memorias? en Ventanas no tenés problemas?

saludos

---

### Post by guillermolisi on 2009-09-14
Edite el asunto del thread ya que "Ayuda" no dice nada acerca del problema en si.

---

### Post by darkneo on 2009-09-15
Gracias guillermo.
 
Starr no hago nada, desde la primera vez que lo instale me hace eso, termino de instalar, me logueo y se cuelga  a los 3 minutos, no hago absolutamente nada. Puedo llegar a ser un tema de memorias?? yo tengo la que me vino con la maquina que no es que marca es y ademas yo compre una kingston de 1gb que se la puse al mes de haber comprado la maquina. Alguna idea de que puede ser??
Que es lo que pasa si le saco el ACPI el APIC y le pongo EDD=on? para que sirven??

---

### Post by guillermolisi on 2009-09-15
> **darkneo said:**
> Gracias guillermo.
 
Starr no hago nada, desde la primera vez que lo instale me hace eso, termino de instalar, me logueo y se cuelga  a los 3 minutos, no hago absolutamente nada. Puedo llegar a ser un tema de memorias?? yo tengo la que me vino con la maquina que no es que marca es y ademas yo compre una kingston de 1gb que se la puse al mes de haber comprado la maquina. Alguna idea de que puede ser??
Que es lo que pasa si le saco el ACPI el APIC y le pongo EDD=on? para que sirven??
Antes de toquetear el SO, proba de usar la maquina con una sola placa de memoria, a ver que pasa. Si no se reproduce el sintoma, estamos cerca de un problema de memoria fallada o incompatibles entre si.

Primero proba con la original que vino con la maquina y despues solo con la Kingston.
Luego comenta que tal te fue en ambos casos.

---

### Post by Hei Ku on 2009-09-15
Tambien, podes probar al arrancar la opcion de memtest, que prueba justamente las memorias. Es un test que lleva mucho tiempo, pero es muy bueno.

---

