---
title: "error: Dependency is not satisfiable: libdbus-1-2"
date: 2009-01-28
forum: Software
---

### Post by AZULFRIO on 2009-01-28
Hola! antes que nada soy otro usuario nuevo, osea que instalé Ubuntu 8.10 y estoy tratando de ver como se usa, ese es todo mi conocimiento de Linux, mi problema tal vez sea simple pero la verdad es que me quedé parado ya que quise instalar un programa.. el "DVD95.DEB" y cundo lo instalo me larga un error que dice (error: Dependency is not satisfiable: libdbus-1-2) busqué en internet y creo que me faltan instalar unas librerías, o eso creo. Bueno hasta ahí llegué.
A ver si me pueden ayudar y desde ya muchas gracias

---

### Post by Air23 on 2009-01-28
Podes instalar DVD95 desde synaptic. Para ello vas a 

Sistema > Administracion > Gestor de paquetes synaptic

y buscas dvd95, luego haces doble click sobre dvd95 (o boton derecho y marcar para instalar). Por ultimo clickeas en aplicar y listo.

La otra manera es abrir una terminal y escribir:

```
sudo apt-get install dvd95
```

---

### Post by guillermolisi on 2009-01-28
Las dos alternativas que explica Air23 permiten que el propio sistema de actualizacion e instalacion de paquetes resuelva las dependencias por uno.

---

### Post by Hei Ku on 2009-01-28
ese parece un error de Synaptic, no de compilacion. Si es asi, puede ser que te falte habilitar un repositorio.

---

### Post by AZULFRIO on 2009-01-28
Bueno, una de las cosas que hice primero fué ir a aplicaciones/añadir y quitar aplicaciones, aparece como para instalarlo, lo tildo, me pide que haga recargue, lo hago y cuando recarga aparece de nuevo como no tildado, lo tildo de nuevo y me hace lo mismo. entonces lo bajo de internet como .deb le hago doble click y me aparece el error antes mencionado. Hago lo que me dice Air23, lo busco en Synaptic pero no me aparece, lo ejecuto en la trerminal y me pone que no encontró el paquete (cabe recordar que soy mas que nuevo en esto) Tal vez Hei Ku tenga razón y me falte un repositorio (sabrá Dios que es eso). Pido disculpas si soy muy incha con esto que tal vez sea una pavada, pero quiero saberlo. Mi meta es no volver más a Windows y quiero lograrlo, con la ayuda de ustedes y un poco de mi persistencia tengo que lograrlo. Obviamente que desde ya muchas gracias a todos..

---

### Post by guillermolisi on 2009-01-28
> **AZULFRIO said:**
> Bueno, una de las cosas que hice primero fué ir a aplicaciones/añadir y quitar aplicaciones, aparece como para instalarlo, lo tildo, me pide que haga recargue, lo hago y cuando recarga aparece de nuevo como no tildado, lo tildo de nuevo y me hace lo mismo. entonces lo bajo de internet como .deb le hago doble click y me aparece el error antes mencionado. Hago lo que me dice Air23, lo busco en Synaptic pero no me aparece, lo ejecuto en la trerminal y me pone que no encontró el paquete (cabe recordar que soy mas que nuevo en esto) Tal vez Hei Ku tenga razón y me falte un repositorio (sabrá Dios que es eso). Pido disculpas si soy muy incha con esto que tal vez sea una pavada, pero quiero saberlo. Mi meta es no volver más a Windows y quiero lograrlo, con la ayuda de ustedes y un poco de mi persistencia tengo que lograrlo. Obviamente que desde ya muchas gracias a todos..
Fijate en la opcion de Synaptic que te muestra que repositorios considera a la hora de bajar/actualizar, si tenes marcado el repositorio "universe" ya que esta ahi el paquete DVD95 que queres instalar.

Te adjunto screenshot de como tengo los repos en Synaptic como ejemplo

---

### Post by AZULFRIO on 2009-01-29
> **guillermolisi said:**
> Fijate en la opcion de Synaptic que te muestra que repositorios considera a la hora de bajar/actualizar, si tenes marcado el repositorio "universe" ya que esta ahi el paquete DVD95 que queres instalar.

Te adjunto screenshot de como tengo los repos en Synaptic como ejemplo

Hice lo que me dijiste y resultó ser eso... El conocimiento no tiene precio. Gracias y gracias a los demás por su interés y por molestarse en contestar.:popcorn:

---

