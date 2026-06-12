---
title: "Necesito mas espacio !!"
date: 2009-05-01
forum: Software
---

### Post by FB91 on 2009-05-01
Hola de nuevo :P !

Tengo un problemita que es el siguiente:

En mi computadora nueva le instalé desde 0 Windows XP e hice 2 particiones (200GB para W) (120GB para ubuntu) entonces una vez que instalé el XP en su partición coloco el LiveCd de ubuntu y en la sección que da a elegir en que partición se instalará creo que ahi le erré porque seleccioné la primer opción que no me acuerdo bien que decia :S la cosa es voy a mi carpeta personal, o al administrador de archivos y tengo unos 2 MB de espacio libre !! ](*,)

Entonces mi pregunta es... tengo que volver a instalar ubuntu corrijiendo el paso de la instalación en el que tengo q especificar en dodne se instalará? o simplemente puedo decirle a Ubuntu de alguna manera que "use" ese espacio que me quedó libre. (que son unos 100GB)


Mil gracias !  :)

---

### Post by staar on 2009-05-01
posteate la salida del comando ```
sudo fdisk -l
``` para saber como son tus particiones, asi te podemos ayudar mejor...

saludos

---

### Post by FB91 on 2009-05-02
**fb91@FB91:~$ sudo fdisk -l**

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x06550655

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       25170   202177993+   7  HPFS/NTFS
/dev/sda2           25171       38912   110382615    f  W95 Ext'd (LBA)
/dev/sda5           25497       38912   107763988+   e  W95 FAT16 (LBA)
/dev/sda6           25171       25474     2441817   83  Linux
/dev/sda7           25475       25496      176683+  82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

:)

---

### Post by staar on 2009-05-02
y si, quedaron bien chiquitas las particiones de ubuntu :-P, se podría pasar tu ubuntu a otra partición, pero es un proceso complicado y peligroso, no recomendable para alguien nuevo como vos...

lo mejor sería que botees con el livecd, vayas a Sistema > Administración > Editor de particiones, y borres todas las particiones (MENOS la primera, con formato NTFS, que es donde está Win), una donde está ubuntu, una de intercambio de linux (para borrarla tenés que desactivarla antes, click derecho > desactivar ;-) ) y una extendida que te quedó ahi sin usar (primero se borra la partición de 'adentro' de la extendida, y después el 'marco', osea la extendida propiamente dicha), y dejes el espacio libre resultante en el disco...

despues volvés a instalar, y en el paso del particionado seleccionas 'Usar el espacio libre' (o algo así, creo que es la segunda opción), para que ubuntu te cree las particiones solito en el espacio libre que dejaste...

si mal no recuerdo, la primera opción lo que hace es hacerse un 'huequito' en el disco e instalarse ahí, sin joder a las otras particiones, por eso es que te quedo así...

saludos

---

### Post by FB91 on 2009-05-03
Muchas gracias staar ! Todo salio 10 puntos :D !!!!

---

