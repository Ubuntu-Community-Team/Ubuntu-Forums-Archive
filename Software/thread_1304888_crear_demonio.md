---
title: "crear demonio"
date: 2009-10-29
forum: Software
---

### Post by fachamix on 2009-10-29
como puedo crear un demonio en debian o ubuntu ????


como hacer para que mi programa corra como un servicio, demonio,..... ???????? o mi script de bash ????

---

### Post by fachamix on 2009-10-29
como puedo programar un demonio tanto en bash como por ejemplo C.

pero lo que mas agradeceria saber, es si , teniendo un programa C o script bash ya creados .... puedo correrlos como demonios, o segundo plano, o servicios, no se ... ayuda

---

### Post by Mauro22 on 2009-10-29
Agreagalo al inicio o hacelo correr mediante cron.  O también podes agregarlo a la carpeta de servicios que se inician ( daily hourly monthly creo que se llaman )

---

### Post by fachamix on 2009-10-30
cuales son las carpetas de inicio de debian / ubuntu ????

---

### Post by Mauro22 on 2009-10-30
> Lo conseguí mediante un comando while(0) y lo do y al final done, el problema es que al arrancar el servicio se me quedaba pillado, asi que quité de los runlevel y de /etc/init.d/ y lo puse en /usr/bin y añadí la ejecucicón como sudo en /etc/rc.local así siempre se me carga al iniciar.
Muchas gracias por las ayudas.


Acá tenés el hilo completo:
[http://www.ubuntu-es.org/?q=node/26750](http://www.ubuntu-es.org/?q=node/26750)
Debe ser así...

---

### Post by rtk406 on 2010-01-11
Podrias dar un ejemplo de como resolvistes tu problema,

Pues no he podido arrancar mi aplicacion desde el inicio....

Gracias

---

### Post by juancarlospaco on 2010-01-11
Para no hacer taaaaaaaaaaantas modificaciones en el sistema instalense[ Gnome-Schedule,]("apt:/gnome-schedule")
que para lo que quieren hacer les va andar barbaro, yo se lo que les digo...
:)

---

