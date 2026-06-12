---
title: "Error al montar NTFS (ntfs-3g)"
date: 2011-02-26
forum: Software
---

### Post by sebasthian777 on 2011-02-26
Hola Comunidad, aplico la pregunta acá porque luego de buscar bastante este error no encontré solución que me sirva.

Tengo: 
-Ubuntu 9.10;
-Notebook DELL Inspiron 1525
-Disco Sata con dual bot entre ubuntu y windows

y cuando voy a Menu Lugares y le doy a cualquiera de las dos particiones NTFS que tengo me aparece lo siguiente

[IMG]http://s3.subirimagenes.com:81/imagen/6020411pantallazoerror.png[/IMG]
(por las dudas se caiga el server de imagenes)
[SIZE="2"]Error mounting: mount exited with exit code 11: ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
[/SIZE]

Alguna idea de esto? a alguien le apareció alguna vez??? :S

PD: no se si sirva, pero creo que esto dejo de andar, luego de instalar y configurar el usb-modeswitch para que me levante un 3g que me da el trabajo. Realmente me suena raro que sea por eso, pero si no me equivoco dejo de andar luego de que hice este cambio.

Bueno desde ya muchas gracias! Un saludo grande! =)

---

### Post by guillermolisi on 2011-02-27
Estaria bueno ver la salida completa de fdisk ```
sudo fdisk -l
```

---

### Post by sebasthian777 on 2011-02-27
> **guillermolisi said:**
> Estaria bueno ver la salida completa de fdisk ```
sudo fdisk -l
```

Perdon, me olvide de decirlo, cuando ejecuto el fdisk en la consola (con el parametro -l) no retorna nada. Lo cual me parecio raro.

---

### Post by guillermolisi on 2011-02-27
Si no antepones "sudo" no te mostrara nada.

---

### Post by sebasthian777 on 2011-02-27
> **guillermolisi said:**
> Si no antepones "sudo" no te mostrara nada.

Si lo se, pero realmente no aparece nada luego del fdisk
```

sebastiandell@sebastiandell-laptop:~$ sudo fdisk -l
[sudo] password for sebastiandell: 
sebastiandell@sebastiandell-laptop:~$ 

```

---

### Post by asterix77 on 2011-02-28
Otra alternativa a fdisk podría ser 

$sudo parted -l

para obtener información desde el disco duro desde la terminal

o en forma gráfica

$sudo gparted

Saludos

---

### Post by sebasthian777 on 2011-03-01
> **asterix77 said:**
> Otra alternativa a fdisk podría ser 

$sudo parted -l

para obtener información desde el disco duro desde la terminal

o en forma gráfica

$sudo gparted

Saludos

Hola Asterix77,
mira cuando hago el parted -l no devuelve nada y cuando ejecuto el gparted, me tira esto por consola:

```
sebastiandell@sebastiandell-laptop:~$ sudo gparted
[sudo] password for sebastiandell: 
======================
libparted : 1.8.8.1.159-1e0e
======================
No se puede hacer «stat» sobre el dispositivo /dev/sda - No existe el fichero ó directorio.
No se puede hacer «stat» sobre el dispositivo /dev/sda - No existe el fichero ó directorio.

```

y la ventana me la muestra vacia.

Alguna idea de que paso? :S, me tiene desconcertado.

---

### Post by sebasthian777 on 2011-03-01
Estuve buscando por internet y lo unico que encontre fue un error del mismo tipo que se soluciono aparentemente recompilando el Kernel, 

Sin embargo, me imagine que si actualizaba a 10.04 esto se iba a solucionar, de ser asi.

Y para mi sorpresa se soluiciono. Asi que bueno, veo de cambiar a SOLUCIONADO.

Desde ya gracias por la buena onda!
Saludos!

---

### Post by salmonete on 2013-04-27
Hola buenas, yo también tengo un problema similar me reinstale Ubuntu por un problema de red, y copie los datos, ahora cuando conecto el disco duro externo me aparece el siguiente error:

No se puede montar Ubuntu (es el nombre que le puse al disco duro)
Error mounting /dev/sdb1 at /media/guti/Ubuntu: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/guti/Ubuntu"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


¿Que puedo hacer para solucionarlo?, no quisiera formatearlo porque perdería todos los datos y hay algunos que quiero conservar.

---

### Post by gmunioz on 2013-04-27
Tienes un error en el sistema de archivos ntfs
Enchufa el disco en MsWindows y ejecuta lo que te sugieren:
run **chkdsk /f **on Windows

Si no usas MsWindows, ve a una máquina que lo tenga, corre el chkdsk,
pon a salvo tus archivos y dale formato Gnu/Linux, para evitar similares
problemas.

---

### Post by salmonete on 2013-04-28
Muchísimas gracias, enserio Ubuntu es la ostia, hasta la carpetas que Windows me elimino las he recuperado.

---

