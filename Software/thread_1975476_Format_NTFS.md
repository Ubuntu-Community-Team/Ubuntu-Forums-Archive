---
title: "Format NTFS"
date: 2012-05-07
forum: Software
---

### Post by Lio56 on 2012-05-07
Hola Muchachos!!!
Estos son mis primeros pasos, y ya surgieron dudas.
Tengo un disco de 500GB. Primero instalé W7 en una particion de 101GB. Despues instalé Ubuntu 12.04 en el modo "algo mas" o personalizado: cree una partición de 102GB ext4 punto de montaje "/", despues cree una partición de 277GB de DATOS (estos datos quiero que esten en NTFS y sean vistos por W7 y Ubuntu) XFS con punto de montaje "/home/DATOS" y finalmente 20GB de SWAP (tengo 4gb de RAM).

Cuando cree la partición de DATOS el sistema de archivos podia ser ext4, ext3, JFS, XFS y otros pero no encontré NTFS (terminé eligiendo XFS). 
Se puede formtear NTFS desde el CD de UBUNTU 12.04, si es asi donde puedo encontrar dicha opción. 
O debo hacerlo con el cd de W7?

Volver a formatear solo DATOS con el cd de W7, generará algun problema en la configuración de UBUNTU tales como punto de montaje u otras que desconozca?

Gracias
Saludos
Lio

---

### Post by papibe on 2012-05-07
Hola Lio56. Bienvenido a los foros.

Siempre y cuando tu directorio home (/home/youruser) sea ext4, ext3, JFS, o XFS, no veo ningún problema.

Toma nota que tendreas que editar el archivo /etc/fstab para actualizar el tipo de la partición que estás montando en /home/DATOS

Espero que te sirva y avísanos si necesitas más ayuda.
Saludos.

---

### Post by Lio56 on 2012-05-08
Hola papibe

Mira ayer hice toda la reinstalacion de nuevo y desde cero... Creo que no se puede formatear en NTFS desde el Cd de instalacion de UBUNTU 12.04 o mejor dicho al menos yo no pude.

Una vez que terminé de instalar, instalé el gparted y formatee en NTFS la partición  de datos. 

Lei un tutorial de como montar la partición y WALA magia funcionó.

Obviamente  sigo sin saber qué puse  con "ntfs-3g"  en el fstab. Ni se que es el -3g pero paso a paso lo importante es que funcionó.

Honestamente estoy muy contento. No entendía mucho que era esa barra al costado que no se movía y hasta ahora me resulta un poco molesta pero con este artículo me situé un poco mejor donde estaba parado y porque
si quieren pueden leerlo 
[http://www.lanacion.com.ar/1470121-ubuntu-1204-o-la-persistencia-de-unityarieltorres](http://www.lanacion.com.ar/1470121-ubuntu-1204-o-la-persistencia-de-unityarieltorres)

Gracias
Saludos 
Leandro

PD: AHH perdón por poner el post en un lugar que no correspondía

---

