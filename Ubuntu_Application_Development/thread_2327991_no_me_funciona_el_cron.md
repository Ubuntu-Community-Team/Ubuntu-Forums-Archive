---
title: "no me funciona el cron"
date: 2016-06-16
forum: Ubuntu Application Development
---

### Post by radvla2 on 2016-06-16
Hola, 


Os escribo desesperado.
En el directorio etc/cron.hourly he incluido este fichero llamado mi_cron.


Es un cron muy sencillo que incluye un solo script.


Aunque el scrip funciona fuera del cron, cuando lo incluyo no.


Tampoco que hacer para que aunque este en un fichero cron aparezcan en pantalla los echos de control.


El fichero es este, "radvla" es el usuario y "leeractualizado" el scrip


SHELL/bin/bash
PATH=/home/radvla: radvla/local/sbin/: usr/local/bin : usr/sbin :usr/bin: /bin :/sbin :bin/bash


59 21 * * * radvla export SHEL=/bin/bash; /usr/bin/bash /home/radvla/leeractualizar


¿Aklguien puede ayudarme?

No se que está pasando

---

### Post by aromo2 on 2016-06-16
dentro del directorio /etc/cron.daily solo tiene que estar el fichero ejecutable que quieres ejecutar cada hora, nada mas.  En tu caso leeractualizado (o leeractualizar?).  Por eso no te funciona.

Otra cosa, como es un programa ejecutado en "background" por el daemon crond, no hay manera de ver la salida por pantalla.  Si el script genera alguna salida, la recibiras en un correo electronico al usuario dueño del proceso.

Espero que esto te ayude.  Saludos.

---

