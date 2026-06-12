---
title: "montar discos"
date: 2009-05-09
forum: Software
---

### Post by joseluis on 2009-05-09
Seguro que a muchos le pasó, seguro que lo dijeron miles de veces, y no termino de enganchar esta solución.
Y cuento por qué.
Tengo ubuntu 9.04 en una partición de un disco IDE, esclavo. En ese disco tengo swap y una partición fat32.
En el disco maestro tengo un disco SATA, en el que está win y en ntfs.
Y acá viene la cuestión.
El ubuntu me reconoce los discos, los muestra desde qeu arranca en el item LUGARES. Los reconoce perfecto.
Sin embargo, es como que no los monta. Tengo que hacer click sobre el icono de la lista de lugares para que pueda montarlos.
¿como hago para que los monte de primera vez?
gracias

---

### Post by Hei Ku on 2009-05-09
Fuiste al administrador de discos, o su equivalente en Gnome, y les pusiste que los monte automaticamente?
Si no, postea tu archivo /etc/fstab

---

### Post by staar on 2009-05-10
es el comportamiento por defecto de ubuntu, si querés que te los monte al inicio tenes que agregarlos al fstab...

con los NTFS, una forma fácil de hacerlo es instalando el paquete ntfs-config

saludos

---

### Post by joseluis on 2009-05-10
el fstab es:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=ed130ecb-4a5f-44f1-9b1a-dbb721948067 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=174dec12-2c26-488e-85c3-d60c15119c5e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


ahora, el fstab se presenta así luego de que hago click en los discos, desde el menú "lugares". Si no hago eso, el fstab solo me presenta el swap y sdb3 ext4 en donde están los archivos de ubuntu.

---

### Post by Mauro22 on 2009-05-10
Aca [0] hay un hilo que trata de esto... hay ejemplos y demases...



[0] [http://ubuntuforums.org/showthread.php?t=1101033&highlight=montar+disco+ntfs](http://ubuntuforums.org/showthread.php?t=1101033&highlight=montar+disco+ntfs)

---

