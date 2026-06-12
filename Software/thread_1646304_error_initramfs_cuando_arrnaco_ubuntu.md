---
title: "error initramfs cuando arrnaco ubuntu"
date: 2010-12-15
forum: Software
---

### Post by sebasaade on 2010-12-15
Buenas. despues de venir usando ubuntu durante un tiempo en vmware me decidi a instalarlo.
y me encontre con este problema al arrancarlo. probe algunas posibles soluciones que aportaban en los foros pero ninguna me soluciono el problema. (poniendo exit logro ingresar a ubuntu.)
tengo ubuntu y windows en la pc (ambos de 64 bits). en windows tengo dos particiones, mas la que windows reserva para el sistema.

Save up waiting for root device. commons problems:
   -boot args (cat /proc/cmdline)
     -check rootdelay= (did the system wait long enough?)
     -check root=(did the system wait for the right device?)
   -missing modules (cat /proc/modules; ls/dev)

Alert! /dev/disc/by-uuid/4549e404-6721-4223-965b-2ebc418895e4 does not exist
dropping to a shell!!
busybox v1.13.3 (ubuntu 1:1.13.3 - 1ubuntu11) built-in shell (ash)
Enter "help for a list of built in commands

(initramfs)

saludos
espero puedan ayudarme , ya que soy prácticamente un novato en estas ramas.
sebastian

---

### Post by biale on 2010-12-15
"4549e404-6721-4223-965b-2ebc418895e4": Existe una partición con esa UUID?

Podrías contar algo de lo que te ya hiciste intentado una solución?

Porque es posible que la ubicación de las particiones haya generado un problema de visibilidad en tiempo de arranque.

---

### Post by sebasaade on 2010-12-16
> **biale said:**
> "4549e404-6721-4223-965b-2ebc418895e4": Existe una partición con esa UUID?

Podrías contar algo de lo que te ya hiciste intentado una solución?

Porque es posible que la ubicación de las particiones haya generado un problema de visibilidad en tiempo de arranque.
te paso a contar. en primer lugar, instale el ubuntu 10.10. como me salto el error intiframs, lo desinstale e instale el 10.04. la forma que lo desinstale es eliminando las particiones desde windows y despues corri el super grub disk.
al instalar el ubuntu 10.04 me surgio el mismo inconveniente asi que leyendo en unos foros hice lo siguiente:

1. Edité el grub (sudo gedit /boot/grub/grub.cfg) agregandolepci=nomsi. me dejo de tirar el error hasta que descargue el paquete de actualizaciones. como lei en un foro que eso no se debia hacer le borre el "pci=nomsi". en ese mismo foro aconsejaban modificar el fichero /etc/deaults/grub descomentando la linea "GRUB_DISABLE_UUID=true". como siguio apareciendo el error volvi a comentar la linea.

2. lo otro que hice fue: Entre a ubuntu desde el cd live. fui a gparted y corri el check o validar. tampoco se solucionó.

espero puedan ayudarme.
soy conciente de que hice cualquiera.
saludos
sebastian

---

### Post by biale on 2010-12-16
Por algún medio estas pudiendo arrancar Ubuntu? Super Grub disk, etc?

A su vez, Gparted indica tanto (1) la UUID y (2) la nomenclatura LINUX de las particiones. Podes postear ambas dos, para la partición de arranque de Ubuntu?

Y ya que estamos, en el menú de arranque, ingresa en modo comando (tecla c) y luego ingresa el comando "set". Conta que dicen los items prefix, root y locale_dir.

---

### Post by sebasaade on 2010-12-17
> **biale said:**
> Por algún medio estas pudiendo arrancar Ubuntu? Super Grub disk, etc?

A su vez, Gparted indica tanto (1) la UUID y (2) la nomenclatura LINUX de las particiones. Podes postear ambas dos, para la partición de arranque de Ubuntu?

Y ya que estamos, en el menú de arranque, ingresa en modo comando (tecla c) y luego ingresa el comando "set". Conta que dicen los items prefix, root y locale_dir.


Te paso la info. Las capturas de pantalla de Gparted desde el cdlive. 
y lo que saque desde el modo comando ( c ) y (set)

prefix=(hd0,5)/boot/grub
root=hd0,5
locale_dir=(hd0,5)/boot/grublocale

ah y si puedo entrar a ubuntu escribiendo "exit" cuando termina de aparecer el error "initramfs" 

saludos
gracias

---

### Post by biale on 2010-12-18
Los datos que pasaste parecen estar bien. Y con un simple "exit" Ubuntu arranca: hay visibilidad.

Lo que puede estar sucediendo es un bloqueo de disco, y por eso "GRUB_DISABLE_UUID=true no funciona, no encuentra una partición root. Y luego si la encuentra, y arranca!

Una prueba interesante sería intentar arrancar con el Super Grub Disk, como para ver que pasa. Ahora siguen mis ideas...

(1) Supongo que has actualizado a Lucid, y sino habria que instalar las actualizaciones.

(2) Podes editar en grub la sentencia de arranque (ingresar una "e") y borrar "quiet splash". Que indique algo mas, si algo le cuesta o interfiere, etc. USB? Y tambien luego del arranque ver los logs que encuentres en /var/log

(3) Tambien se puede agregar un rootdelay agrandado a 60 o 90 en las sentencias de arranque de grub. Quedaría algo así:

... root=UUID=4549e404-6721-4223-965b-2ebc418895e4 ro rootdelay=90

(Ojo: todo en la misma linea)

(4) Ingresar al bios y tratar de fijar emulacion IDE para los discos SATA. Incluso retirar alguna opción "enhanced" que hubiera. 

(5) Supongo que el grub los has intalado en el mbr (sda) y no en la partición (sda5)?

Espero que tengas exito, pero de cualquier manera contanos como te fué.

---

### Post by biale on 2010-12-22
No tuve tiempo se leerlo, pero suena on-topic:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/672964](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/672964)

y si es esto se arregla con las ultimas actualizaciones de las libs de udev.

---

