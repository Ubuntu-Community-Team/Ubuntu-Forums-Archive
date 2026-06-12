---
title: "[SOLVED] papelera no funciona en fat y ntfs"
date: 2008-11-30
forum: Software
---

### Post by granjero on 2008-11-30
buenas amigos, ando con un problema del cual recuerdo a medias la solución y recurro a su experiencia...

con las particiones montadas que no son nativas de ubuntu tengo el problema que en vez de mandar a la papelera quiere borrar directamente. (imagen adjunta) 

mi recuerdo y lo poco que encontré en google es que hay que agregar al fstab las opciones uid y gid pero no se bien donde...

dejo pegado mi fstab asi si alguien sabe me indica que hacer...

muchas gracias!


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=b01ccf79-9744-4644-8043-8988c56092e9	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=5EA4903FA4901C19	/home/jm/disco\0402	ntfs-3g	defaults,locale=es_AR.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=488B-C681	/home/jm/porqueria	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda4 :
UUID=d746e2b7-b979-43bb-9e9b-d8a641134f72	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


muchas gracias!

---

### Post by faktorqm on 2008-12-03
La verdad no me acuerdo como era, hace demasiado que no uso particiones fat, pero creo que tenias que usar el umask para setear el uid y el gid. Leete esto a ver si llegas a algun resultado: [http://ubuntuforums.org/showthread.php?t=952885](http://ubuntuforums.org/showthread.php?t=952885) Salu2!

---

### Post by granjero on 2008-12-06
up.

---

### Post by staar on 2008-12-06
tenia el mismo problema, y lo solucione creando, como root, una carpeta con el nombre .Trash-1000, en la raiz del disco, proba a ver si te sirve a vos

saludos

---

### Post by granjero on 2008-12-06
ya existia esa carpeta....

la borre y la cree con 

sudo mkdir .Trash-1000

pero sigue sin andar...

gracias pero no funciono!

salud!

---

### Post by granjero on 2008-12-06
solved

agregue **,uid=1000,gid=1000 ** al final de las lineas de  los discos... 

la primera vez que booteo me tiro un error del demonio de configuraciones o algo asi
ahora pareciera que anda lo mas bien...


muchas gracias...


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=b01ccf79-9744-4644-8043-8988c56092e9	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=5EA4903FA4901C19	/home/jm/disco\0402	ntfs-3g	defaults,locale=es_AR.UTF-8**,uid=1000,gid=1000**	0	0
#Entry for /dev/sda2 :
UUID=488B-C681	/home/jm/porqueria	vfat	defaults,utf8,umask=0**,uid=1000,gid=1000**	0	2
#Entry for /dev/sda4 :
UUID=d746e2b7-b979-43bb-9e9b-d8a641134f72	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


salud!

---

