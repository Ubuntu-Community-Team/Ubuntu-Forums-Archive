---
title: "La actualizacion automatica a 14.04 LTS me tira error... Que hago?"
date: 2014-05-14
forum: Software
---

### Post by fleetwood1970 on 2014-05-14
Hola a todos:

Estoy tratando de actualizar a 14.04 LTS desde 13.10 y me tira el error:

No se ha podido calcular la actualización
Ha ocurrido un problema mientras se calculaba la actualización.
Eso pudo ser causado por:
* Actualizar a una versión de Ubuntu aún no publicada
* Estar ejecutando la versión actual, aún no publicada, de Ubuntu
* Paquetes no oficiales de software no proporcionados por Ubuntu
Si nada de esto aplica, informe de este error usando la orden «ubuntu-bug ubuntu-release-upgrader-core» en una terminal.

Obviamente  que he agregado muchos PPA por mi cuenta desde que instale 13.10 (puedo  contar mas de 10 en mi lista) y ademas uso el escritorio de cinnamon ya  que me cuesta usar el que viene x defecto (Unity?).

Ahora, que  se hace para que no tire esos errores? Se deben desactivar los PPA  agregados? Se borran? Tambien tengo instalado el driver de mi tarjeta  ATI de video. Tengo que hacer algo especial con eso?

Como hago  para poder actualizar 14.04 sin errores? Me pueden ordenar un poco la  cabeza x que estoy bastante desorientada... Gracias chicos!

---

### Post by gmunioz on 2014-05-14
Descarga la imagen iso de Trusty de la misma versión (32 ó 64 bits) instalada de Saucy.
Graba una dvd ó usb.
Inicia con el dvd ó usb y carga la sesión live.
Terminada la carga de la sesión live, inicia la instalación y elige la opción actualizar el sistema.

ó

Elimina todos los ppa del sistema.
Edita el archivo /etc/apt/sources.list
Cambia todos los saucy por trusty
Y ejecuta en una terminal:

sudo su
apt-get update
apt-get dist-upgrade
dpkg --configure -a
apt-get autoremove
apt-get clean
reboot

---

### Post by fleetwood1970 on 2014-05-18
Gracias otra vez Gmunioz. Funciono bien
Muchas gracias

---

