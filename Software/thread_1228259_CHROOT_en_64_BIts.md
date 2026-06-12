---
title: "CHROOT en 64 BIts"
date: 2009-07-31
forum: Software
---

### Post by El Rengo on 2009-07-31
Hola!!!

Me gustaría saber si alguno sabe explicar :P Como es que funciona el CHROOT. Se que su funcion es la de poder ejecutar aplicaciones de 32 en equipos corriendo 64 bits.
Pero no logro comprender como es que funciona :S

Muchas gracias!!!

---

### Post by staar on 2009-07-31
esa no es específicamente la función de chroot, sino la de correr programas (o una shell) con un directorio raiz especial...

si se usa para ejecutar aplicaciones de 32 bits en equipos corriendo 64 bits, lo que se hace es instalar un pequeño sistema de 32 desde (o dentro de) el de 64, con lo mínimo para que pueda instalar paquetes, y, después de instalada la aplicación que solo funciona en 32 bits, se hace chroot y se la corre, nada más, la aplicación cree que está en un entorno 32 bits porque de hecho lo está...

saludos

---

### Post by Hei Ku on 2009-07-31
Yo lo uso en mi linux de 64 bits para correr otro chroot de 64 bits, pero que tiene instalado otras librerias de desarrollo. O sea, con mi sistema principal desarrollo en KDE3 y con el chroot desarrollo para KDE4.

Lo podes usar tambien para correr versiones anteriores de Ubuntu. Tener un Hardy dentro de Jaunty, por ejemplo. La gente que hace los paquetes de instalacion lo usa mucho para testear que funcionen bien en todas las versiones.

---

### Post by staar on 2009-07-31
si, se puede usar desde un livecd también, para reparar un sistema que no bootea, es muy útil y muy poderoso ese comando...

saludos

---

### Post by El Rengo on 2009-08-01
Existe algun documento que explique bien a fondo el funcionamiento de CHROOT?
Muchas gracias por las respuestas!!! :D

---

### Post by Hei Ku on 2009-08-01
man chroot

ó

[http://es.wikipedia.org/wiki/Chroot](http://es.wikipedia.org/wiki/Chroot)

---

### Post by staar on 2009-08-01
```
info coreutils chroot
``` ;-)

---

### Post by guillermolisi on 2009-08-01
> **Hei Ku said:**
> man chroot

ó

[http://es.wikipedia.org/wiki/Chroot](http://es.wikipedia.org/wiki/Chroot)
El man de chroot deja bastante que desear. Es para alguien que ya lo sabe usar y no recuerda algun detalle.

---

### Post by clasificado on 2009-08-02
El chroot es una herramienta que puede tener demasiados usos específicos

te diria que mas que preguntar en general, busques en google como se usa chroot para llegar a un fin específico

Por ejemplo: [Google: chroot 32 bits]("http://www.google.com.ar/search?q=chroot+32+bits")

porque si buscas chroot solamente, es un bondi que te puede dejar en cualquier parada

clasificado

---

