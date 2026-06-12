---
title: "Apagon durante aptitude update (solucionado) ¿algo mas por hacer?"
date: 2009-02-19
forum: Software
---

### Post by dhcancelo on 2009-02-19
Buenas....
Ayer sufri un corte de energia electrica y se apago la pc actualizando, mientras descargaba los paquetes mediante aptitude update.
Me salio el mensaje de abajo...
Yo puse mi clave y corri fsck /dev/sda2 y me pidio muchas ok para reparar cosas rotas de las cuales la mayoria no tenia ni idea que son. Ahora levanta bien, pero consulto si tendria que hacer algo mas para que mi Hardy 64bits quede perfecto (como estaba antes), ¿o con esto es suficiente?
Muchas gracias.
Saludos.
Wex


ckecking drive /dev/sda2: 58% (stage 1/5, 187/224)
/dev/sda2: Inodes that were part of a corrupted orphan linked list found.

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
            (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda2: 59% (stage 1/5, 191/224)

                  [FAIL]
* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root
filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the
maintenance shell and restart the system.
Give root password for maintenance (or type Control-D to continue):

---

### Post by guillermolisi on 2009-02-19
> **dhcancelo said:**
> Buenas....
Ayer sufri un corte de energia electrica y se apago la pc actualizando, mientras descargaba los paquetes mediante aptitude update.
Me salio el mensaje de abajo...
Yo puse mi clave y corri fsck /dev/sda2 y me pidio muchas ok para reparar cosas rotas de las cuales la mayoria no tenia ni idea que son. Ahora levanta bien, pero consulto si tendria que hacer algo mas para que mi Hardy 64bits quede perfecto (como estaba antes), ¿o con esto es suficiente?
Muchas gracias.
Saludos.
Wex


ckecking drive /dev/sda2: 58% (stage 1/5, 187/224)
/dev/sda2: Inodes that were part of a corrupted orphan linked list found.

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
            (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda2: 59% (stage 1/5, 191/224)

                  [FAIL]
* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root
filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the
maintenance shell and restart the system.
Give root password for maintenance (or type Control-D to continue):
En teoria deberia haber quedado tal como estaba antes gracias al accionar del fsck.

Si no notas que alguna funcion no se comporta como antes, usala tranquilo.

Volviste a probar Aptitude para verificar que no encuentra inconsistencias o te emite algun mensaje de error o advertencia ?

Tenes otros discos o ese que mencionas es el unico con Ubuntu ?

---

### Post by dhcancelo on 2009-02-19
Al parecer esta todo normal, por ahora es mi unico ubuntu, excepto un par virtualizados para probar....
Aptitude al parecer esta ok, aunque igual corri por las dudas sudo dpkg --configure -a
Muchas gracias por la respuesta.
Saludos.

---

### Post by guillermolisi on 2009-02-19
> **dhcancelo said:**
> Al parecer esta todo normal, por ahora es mi unico ubuntu, excepto un par virtualizados para probar....
Aptitude al parecer esta ok, aunque igual corri por las dudas sudo dpkg --configure -a
Muchas gracias por la respuesta.
Saludos.
Igual y luego de releer el mensaje que te dio la maquina donde dice que fsck se interrumpio y te advierte que lo corras manualmente, te sugiero que le hagas caso y procedas a correrlo (con sudo y parametros adecuados para que solucione cualquier inconsistencia que detecte).
Como para no tener sorpresas en el futuro.

---

### Post by dhcancelo on 2009-02-20
> **guillermolisi said:**
> Igual y luego de releer el mensaje que te dio la maquina donde dice que fsck se interrumpio y te advierte que lo corras manualmente, te sugiero que le hagas caso y procedas a correrlo (con sudo y parametros adecuados para que solucione cualquier inconsistencia que detecte).
Como para no tener sorpresas en el futuro.

Ok. Voy a pasar #fsck a / (ext3) y #reiserfsck a /home (reiserf).
Muchas gracias por todo.
Saludos.
Wex

---

