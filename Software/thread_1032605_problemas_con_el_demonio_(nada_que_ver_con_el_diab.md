---
title: "problemas con el demonio (nada que ver con el diablo jaja)"
date: 2009-01-06
forum: Software
---

### Post by lucasfava on 2009-01-06
El problema apareció cuando puse que ingresara automáticamente. Es el mismo cartelito, que me aparecía, cuando usaba el sistema desde el live cd, alguna forma de arreglarlo hay :popcorn:. Uso Hardy, por si las moscar :D

---

### Post by lucasfava on 2009-01-06
El cartelito no aparecía cuando metía el usuario y contraseña, solo apareció cuando me aburrí de clickearlo y hacerlo automático.
Acá dejo un post de alguien que le ocurrió lo mismo y dejo la foto del cartelito
[http://ubuntuforums.org/showthread.php?t=1015440&highlight=demonio]("http://ubuntuforums.org/showthread.php?t=1015440&highlight=demonio")
Yo también no veo problema alguno, solo pareciese que esta medio al p..o :popcorn:

P.D: como entro al archivo fstab,

---

### Post by NickCis on 2009-01-07
desde consola, "sudo gedit /etc/fstab" (sin comillas). Es para Ubuntu, sino reemplaza gedit, por el editor de textos que tengas, o usa los que venienen por consola: "nano" o "vi".

Saludos.

---

### Post by lucasfava on 2009-01-07
Aca dejo lo que aparece en fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

quepuede ser:confused:

---

