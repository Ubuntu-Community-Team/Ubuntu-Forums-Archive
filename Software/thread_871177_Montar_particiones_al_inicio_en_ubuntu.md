---
title: "Montar particiones al inicio en ubuntu"
date: 2008-07-26
forum: Software
---

### Post by h9005 on 2008-07-26
Buenas como hago para que las particiones ntfs y fat 32 sean montadas automáticamente al inicio de ubuntu?

---

### Post by Mauro22 on 2008-07-26
Tenes que crear la carpeta donde queres que se monten:

Por ejemplo:

sudo mkdir /media/xp (en el ejemplo seria carpeta_que_creaste_1)
sudo mkdir /media/datos (en el ejemplo seria carpeta_que_creaste_2)


Y despues agregar al fstab

sudo gedit /etc/fstab

Si es NTFS
/dev/unidad      carpeta_que_creaste_1       ntfs nls=utf8,umask=0222 0 0

Si es FAT(32)
/dev/unidad      carpeta_que_creaste_2    vfat iocharset=utf8,umask=000 0 0


Donde unidad, es lo que corresponde a tu caso; lo podes saber haciendo:

sudo fdisk -l


Y despues:

sudo mount -a para montar todo y ver si funciono.

---

### Post by h9005 on 2008-07-27
Muchas gracias me fijo y te digo.

---

### Post by h9005 on 2008-07-28
Asi esta puesto originalmente:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6dbd51b7-1520-4481-a835-6757436ae853 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9fcbb123-a926-4910-aa2f-908a3748b4d3 /home           ext3    relatime        0       2
# /dev/sda5
UUID=fff4d1e2-0a26-4bb8-7967-fa5db73c1479 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Y asi lo modifique yo:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6dbd51b7-1520-4481-a835-6757436ae853 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9fcbb123-a926-4910-aa2f-908a3748b4d3 /home           ext3    relatime        0       2
# /dev/sda5
UUID=fff4d1e2-0a26-4bb8-7967-fa5db73c1479 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 xp ntfs nls=utf8,umask=0222 0 0
/dev/sda7 datos vfat iocharset=utf8,umask=000 0 0

No funciona, aparece esto:

@ubuntu:~$ sudo mount -a
fuse: failed to access mountpoint xp: No existe el fichero ó directorio
mount: el punto de montaje datos no existe

---

### Post by Mauro22 on 2008-07-28
> **h9005 said:**
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[B]/dev/sda1 xp ntfs nls=utf8,umask=0222 0 0
/dev/sda7 datos vfat iocharset=utf8,umask=000 0 0[/B]



xp y datos tienen que ser una ruta a una carpeta creada...

por ejemplo:

/media/xp
/media/datos

Pero tenes que crearlas antes de montarlo, por eso te devuelve que no existe el directorio

Asi es el mio:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[B]/dev/sdb1       /media/xp       ntfs nls=utf8,umask=0222 0 0
/dev/sda4       /media/datos    vfat iocharset=utf8,umask=000 0 0[/B]
```

---

### Post by luchardi on 2008-07-28
Agrego por experiencia que la carpeta que creaste le des permisos "antes de montar" de lectura / escritura, sinó te va a montar el FS en ReadOnly, al menos me pasó eso con una partición de ext3 que hice el otro día en mi equipo.

Saludos.

---

### Post by h9005 on 2009-02-22
Ok Entonces como es el procedimiento para que carguen?

---

### Post by sajnox on 2009-02-22
Una forma facil es usar mont manager

```
sudo apt-get install mountmanager
```

Depende de como uses la maquina es que te conviene saber hacerlo desde el editor de textos o ayudarte con una gui

---

### Post by fetux on 2011-03-04
No podia de ninguna manera modificar los archivos de las particiones montadas. Cambie los permisos de las carpetas antes de montar los archivos. Pero cuadno reiniciaba y montaba las particiones me volvia a cambair los permisos de las capretas.
La solucion es no usar la opcion umask, que es exactamente para cambiar los permisos.

---

### Post by guillermolisi on 2011-03-04
> **fetux said:**
> No podia de ninguna manera modificar los archivos de las particiones montadas. Cambie los permisos de las carpetas antes de montar los archivos. Pero cuadno reiniciaba y montaba las particiones me volvia a cambair los permisos de las capretas.
La solucion es no usar la opcion umask, que es exactamente para cambiar los permisos.
umask tiene distintos niveles de actuacion y generalmente se utiliza para establecer valores por defecto/esquema base para los permisos de acceso a archivos de cada particion montada.

---

