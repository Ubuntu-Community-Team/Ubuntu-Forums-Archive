---
title: "[SOLVED] Problema con Hardy Heron"
date: 2008-06-12
forum: Software
---

### Post by Vero1 on 2008-06-12
Hola a todos,

Despues de una pequeña batalla, he logrado instalar Hardy pero se me presentan problemas.Iré por partes.

Primero no se había actualizado el Grub, seguía figurando Gutsy. Por sugerencias del Chat, cambié los datos del .lst y ahora figura en el Grub.
Lo que pasa es que cuando intento correrlo me sale ésto:

Target file system doesn't have /sbin/init.

Entonces lo corro en modo Recovery. A veces entra y otras me sale initramfs con una serie de comandos a usar que yo no sé.

Alguien podrá indicarme qué se puede hacer?

Muchas gracias

---

### Post by Mister X on 2008-06-12
Antes de modificar el menu.lst, te daba el mensaje de error: "Target file system doesn't have /sbin/init" o te aparecio despues?

---

### Post by Vero1 on 2008-06-12
Despues Mister X. Antes no podía ingresar porque en el Grub no figuraba Ubuntu 8.04

---

### Post by Mister X on 2008-06-12
Postea las lineas que agregaste en el menu.lst. El error te dice que en el istema de archivos que montas para iniciar, no esta el proceso de inicio (init)
Probablemente el error esta en el parametro root=UUID=xxxxxxxxxxxxxxxxx

---

### Post by Vero1 on 2008-06-12
Imposible entrar en Hardy. Me sale el error comentado y tambien BusyBox(initramfs) y no hay nada que hacer, pero copié lo que sale en el Grub:

root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic
root=/dev/sdb1 ro quiet single=es_ES
initrd/boot/initrd.img-2.6.24-16-generic
savedefault
boot

---

### Post by Mister X on 2008-06-12
> **Vero1 said:**
> Imposible entrar en Hardy. Me sale el error comentado y tambien BusyBox(initramfs) y no hay nada que hacer, pero copié lo que sale en el Grub:

root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic
root=/dev/sdb1 ro quiet single=es_ES
initrd/boot/initrd.img-2.6.24-16-generic
savedefault
boot

Estás segura que instalaste hardy en /dev/sdb1 (la primer particion del SEGUNDO disco rigido?)

---

### Post by Vero1 on 2008-06-12
Bueno ahora que lo mencionás, yo tomé nota parcialmente de lo que configuré y al fijarme ahora, anoté:
Rescate fichero raiz /dev/sdb3, porque me olvidé de decirte que en un primer intento había puesto sdb1 pero no funcionó entonces reinstalé con el CD en modo de rescate y allí puse sdb3. Será ése el problema?

---

### Post by Mister X on 2008-06-13
Puede ser, inicia con un live cd y fijate donde quedó instalado

---

### Post by Vero1 on 2008-06-13
Al final me cansé y con el LiveCD formateé la partición y reinstalé(dicen que la tercera es la vencida) y en cierto modo así fue.
Esta vez se actualizó el Grub y puedo ingresar sin problemas, pero...

Ahora estoy luchando con el controlador de NVIDIA. Buscando en Google instalé el controlador mediante envy pero no lo toma y la Resolución de Pantalla es mucho menor a lo que corresponde, por lo tanto la pantalla se ve cortada y no puedo manejar las aplicaciones y tampoco me permite cambiar la resolución. 

Ya pude hacer apt-get update, por lo menos.

Voy a ver si desinstalo envy y lo vuelvo a instalar a ver si se corrige.

El otro problema es que no me funciona Evolution porque se me rechaza el pass y hay problemas con PAP. En fin, seguiré en la lucha.

Gracias.

---

