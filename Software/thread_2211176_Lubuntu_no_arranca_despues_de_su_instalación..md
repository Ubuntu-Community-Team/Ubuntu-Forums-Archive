---
title: "Lubuntu no arranca despues de su instalación."
date: 2014-03-14
forum: Software
---

### Post by royleon on 2014-03-14
Hola amigos! soy nuevo usuario de linux, por lo tanto tengan en cuenta que talvez con la primera explicacion no sea suficiente :oops:.
Instalé lubuntu en una particion que tenia disponible, de un HDD que tiene 2 particiones, una con Windows XP y la otra obviamente adonde instalé el lubuntu. Pero cuando terminó la instalación se reinicia la PC y luego del menu de seleccion de SO me sale pantalla negra con lo siguiente:

Gave up waiting for root device. Common problems:
  -Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
  -Missing modules (cat /proc/modules; ls/dev)
Alert! /dev/disk/by-uuid/7ecfbbe4-dac0-41aa-8621-dfd486ecf438 does not exist opping to a shell!

A que se debe y que puedo hacer? [-o<
Gracias de antemano

---

### Post by euzkoarima on 2014-03-15
Dos posibilidades, grub dañado o disco dañado. Es más probable que sea el grub.

Proba:
1. Pone el cd de instalación de ubuntu, como si fueses a instalar otra vez.
2. Desde ahí podes montar y ver las particiones, con eso comprobas que no es el disco.
3. Abrís una consola, con Ctrl-Alt-T y ejecutá el comando: sudo fdisk -l
4. Copianos el resultado del comando
5. Ejecutá el comando: sudo blkid
6. Copianos el resultado del comando

Si no aparece nada raro creo que reinstalamos grub y se arregla, pero hace eso primero para ver si vamos bien.

Saludos
Eduardo

---

### Post by guillermolisi on 2014-03-15
> **royleon said:**
> Hola amigos! soy nuevo usuario de linux, por lo tanto tengan en cuenta que talvez con la primera explicacion no sea suficiente :oops:.
Instalé lubuntu en una particion que tenia disponible, de un HDD que tiene 2 particiones, una con Windows XP y la otra obviamente adonde instalé el lubuntu. Pero cuando terminó la instalación se reinicia la PC y luego del menu de seleccion de SO me sale pantalla negra con lo siguiente:

Gave up waiting for root device. Common problems:
  -Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
  -Missing modules (cat /proc/modules; ls/dev)
Alert! /dev/disk/by-uuid/7ecfbbe4-dac0-41aa-8621-dfd486ecf438 does not exist opping to a shell!

A que se debe y que puedo hacer? [-o<
Gracias de antemano

Desde que medio/soporte realizaste la instalacion ?
CD, pendrive ?

Si fue desde la ultima posibilidad, podrias iniciar tu maquina con el pendrive conectado a la PC y contarnos que resultado obtuviste ?

---

