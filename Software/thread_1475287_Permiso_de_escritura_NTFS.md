---
title: "Permiso de escritura NTFS"
date: 2010-05-06
forum: Software
---

### Post by DjBuRRo on 2010-05-06
Buenas. Necesito su ayuda puesto que ya he tratado 3 días seguidos y aun no me resulta. El problema es que instale el último Ubuntu y tengo 4 particiones en NTFS. Uso Ubuntu hace varias distribuciones y siempre había conseguido montar las particiones y escribir en ellas sin ningún problema. Sin embargo, en el 10.04 me está costando más de lo que quisiera.
Instale el paquete ntfs-3g que permite usar los discos duros y que sean leídos como siempre, pero lo que sucede ahora es que sólo el root tiene permisos para escribir (no puedo pegar nada, por ejemplo). Trate usando nautilus y cambiando el permiso a mi usuario, pero una vez cambiado se regresaba a root. Trate arreglarlo metiendole mano con gedit /etc/fstab pero nada.
Estoy un tanto frustrado de no poder solucionar el problema para usar las particiones como lo hacía antes.
Ojalá pudieran ayudarme.
Les copio el  /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sdc1    /media/Chacalon    ntfs-3g    defaults,users,user,locale=es_CL.utf8    0    0
/dev/sdb1    /media/Glotón    ntfs-3g    defaults,users,user,locale=es_CL.utf8    0    0
/dev/sdc5    /media/Goloso    ntfs-3g    defaults,users,user,locale=es_CL.utf8    0    0
/dev/sdd1    /media/Padawan    ntfs-3g    defaults,users,user,locale=es_CL.utf8    0    0
/dev/sdd5    /media/Wachaca    ntfs-3g    defaults,users,user,locale=es_CL.utf8    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
/dev/sda5    /media/sda5    swap    defaults    0    0


```Me tinca que es algo simple que aún no puedo descifrar.
Saludos,

---

### Post by bichopro on 2010-05-06
Ntfs-config es un software con interfaz grafica para poder configurar todo facilmente.

Esta en el centro de software de ubuntu

---

### Post by Carlos C on 2010-05-06
Prueba modificando tu fstab según lo sugieren acá:

[http://ubuntuforums.org/showthread.php?t=1473347](http://ubuntuforums.org/showthread.php?t=1473347)

Me refiero al [#10]("http://ubuntuforums.org/showpost.php?p=9243902&postcount=10")
Recuerda hacer una copia de seguridad antes de hacer los cambios.
Saludos.

---

### Post by DjBuRRo on 2010-05-06
Muchas gracias a ambos por las respuestas. Preferí seguir la sugerencia de Carlos C puesto que lo que dijo bichopro ya lo había intentado.
Logre avanzar, pero no solucionar el problema. Ahora el propietario es el root y el grupo plugdev. Aún así, sigo sin poder pegar nada, por ende, sin escribir.
Como se extraña el manejo de los permisos de la versión pasada. Por lo menos vamos avanzando. ¿Alguna otra idea?
Muchas gracias!

---

### Post by DjBuRRo on 2010-05-07
Muchas gracias por la ayuda. Finalmente encontré la solución. Viendo que si agregaba gid:46 era posible para plugdev hacer uso de la partición, me anime y agregue uid:1000 a todas las líneas y resulto. Ahora comparto con root y soy propietario.
Finalizando, para no crear un nuevo post. Tengo la misma duda que en esta[ web]("http://www.tuxapuntes.com/drupal/node/1814"): Cuando se inicia y entra Ubuntu al escritorio, aparece una aplicación que intenta acceder al deposito de claves 'default', el cual está  bloqueado, por lo que me pide que introduzca la contraseña. ¿alguien sabe qué es? y como hacer para que no suceda todo el tiempo?
Muchas gracias de nuevo!

edit: Lamentablemente sigo teniendo un problema. Al comenzar a usar Transmission bajando un archivo y haciendo que se guarde en alguna de las particiones que ya están a mi nombre, me tira error. Creo que es por algo de escritura en las particiones. ¿Los programas necesitan permisos para usar las particiones? Por lo que tengo entendido, así no funciona Ubuntu. Sugerencias?

No sé si deba comenzar un post nuevo por el 2do problema porque se relaciona con el primero. Si es así, perdonen.

---

### Post by DjBuRRo on 2010-05-10
Up
Aún sigo sin poder solucionar el problema en transmission. Sigo recibiendo write failed on /media/Glotón...
Alguna idea? porfavor!

---

### Post by Carlos C on 2010-05-10
Prueba con este método que al parecer da mejores resultados:

[http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/](http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/)

Saludos.

---

### Post by DjBuRRo on 2010-05-11
Gracias, pero no soluciona el problema. El error: write failed sigue existiendo...

---

