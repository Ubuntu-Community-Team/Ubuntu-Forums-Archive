---
title: "Problema Gnome Do al iniciar y otros problemas en karmic"
date: 2009-11-21
forum: Software
---

### Post by Fisaulerod on 2009-11-21
Hola. Acabo de instalar Karmic Koala desde una instalación nueva, y resulta que gnome do no se ejecuta automaticamente al iniciar la sesión. Tengo puesto en el programa que haga eso y tambien en aplicaciones al inicio, pero igual no se inicia y debo ejecutar Gnome Do manualmente. ¿Qué puede ser?
También tengo un problema que al iniciar me sale algo como: one or more mounts /etc/fstab cannot be mounted...
No se qué es, pero me molesta un poco ver ese mensaje. Lo raro es que luego funciona todo normalmente :S.
Por ultimo, intente cambiar la imagen del grub como salía en [http://ubuntulife.wordpress.com/2009/11/01/cambiar-la-imagen-de-grub-2/]("http://ubuntulife.wordpress.com/2009/11/01/cambiar-la-imagen-de-grub-2/"), pero no pasó nada, sigue igual que antes. Lo que me parece raro es que el grub de Karmic, q entiendo es el 2, se me ve mucho más feo que el de las versiones anteriores...en fin.
Gracias de antemano.

P.D: Mi fstab es:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=04908827-713c-4950-9e47-fc013329de47 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=12780B0A780AEC73 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=51393e7e-d90a-45bf-a007-7aa9e7cdb2af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by moreback on 2009-11-22
Se le recuerda que tiene que describir un problema por tema, si no esto se desordena, como ya lo está su post.

Saludos.

---

