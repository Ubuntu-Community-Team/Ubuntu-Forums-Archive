---
title: "Ha ocurrido un un error al iniciar el demonio del Administrador de Preferencias de Gn"
date: 2008-12-18
forum: Software
---

### Post by granjero on 2008-12-18
hola amigos desde que agregue las líneas uid=1000,gid=1000 a mi fstab para que funcione la papelera en los discos ntfs y fat cada 4 o 5 inicios me sale este "hermoso" cartelito...

les dejo mi fstab 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=b01ccf79-9744-4644-8043-8988c56092e9	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=5EA4903FA4901C19	/home/jm/disco\0402	ntfs-3g	defaults,locale=es_AR.UTF-8,uid=1000,gid=1000	0	0
#Entry for /dev/sda2 :
UUID=488B-C681	/home/jm/porqueria	vfat	defaults,utf8,umask=0,uid=1000,gid=1000	0	2
#Entry for /dev/sda4 :
UUID=d746e2b7-b979-43bb-9e9b-d8a641134f72	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



no noto que pase nada malo cuando aparece ese cartelito más que mal humor.... que se pasa despues de poner aceptar... pero queria saber que puede ser....


salud!

---

### Post by c4d0rn4 on 2008-12-18
la verdad no se, no me suena muy concordante lo del fstab y el error ese.

te diría que probaras de dejar el fstab como antes y te fijes si continua.

Off: la papelera de reciclaje me irrita... odio tener que hacer shift delete siempre xD. Igual debe ser cosa mia que tengo un hd diminuto.

---

### Post by granjero on 2008-12-22
el cartelito sigue saliendo... alguien sabe que puede ser?


gracias!

---

