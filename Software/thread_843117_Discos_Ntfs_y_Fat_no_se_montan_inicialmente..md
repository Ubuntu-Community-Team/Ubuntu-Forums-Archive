---
title: "Discos Ntfs y Fat no se montan inicialmente."
date: 2008-06-28
forum: Software
---

### Post by nemodot on 2008-06-28
Buenas, sucede que desde que actualicé a Hardy los discos Ntfs y Fat que tengo donde guardo toda mi música y archivos (mi hermano usa windows en la particion ntfs) no se montan inicialmente. Lo cual no es la gran cosa, pues basta ir a lugares-> disco Gordo (mi disco FAT de 150 GB) y se monta. Sin embargo si no hago esto antes de querer reproducir algo de la música, el disco no parece existir, como si hubieran borrado los archivos. Luego de abrir el disco desde Lugares, los temas en el amarok vuelven a la vida y puedo escuchar música. Hay alguna forma de corregir esto y que los discos se monten solos al inicio como antes? (cuando no tenia este problema).

Otro problema irritante es el del flashplayer, con firefox 3 se me sigue cerrando por completo alguna que otra vez cuando quiero ver un video de youtube por ejemplo. Alguien sabe como corregirlo, si es que se puede?

Un saludo!

---

### Post by xpelaox on 2008-06-28
me pasa lo mismo!! me Uno a la pregutunta:S es bastante molesto -.-

---

### Post by Hei Ku on 2008-06-28
para problemas de discos, lo mejor es que postees el /etc/fstab para ver como lo tenes configurado.

---

### Post by xboo2 on 2008-06-28
Hola yo tenía ese mismo problema, lo que hice para resolverlo es instalar desde synaptic el paquete ntfs-config eso te proporciona una GUI desde donde podés indicar que particiones/discos querés que se monten desde el inicio. Espero que te sirva saludos.:)

---

### Post by Apipote on 2008-06-28
Postee lo mismo hace un par de días.
De hecho, me cansé de HH y volví a XP sp3.

Hardy Heron es para mí un verdadero dolor de cabeza, repleta de bugs.

Será que tengo mala suerte, pero todas las Distros que probé en estos días han sido muy frustrantes para mí. Suse, Fedora y Ubuntu en todos sus sabores.

Y lo peor...para la mayoría de la gente Xp ( y vista también ) anda cada vez mejor, sin dolores de cabeza, lo instalás y te toma todo de una.
La gente no entiende que te rompas la cabeza con un sistema operativo tan poco amigable.

Pero bueno, soy masoquista y tengo esperanzas que con el tiempo la cosa cambie.
Seguiré probando

Slds a todos.

---

### Post by Mauro22 on 2008-06-28
> **nemodot said:**
> Buenas, sucede que desde que actualicé a Hardy los discos Ntfs y Fat que tengo donde guardo toda mi música y archivos (mi hermano usa windows en la particion ntfs) no se montan inicialmente. Lo cual no es la gran cosa, pues basta ir a lugares-> disco Gordo (mi disco FAT de 150 GB) y se monta. Sin embargo si no hago esto antes de querer reproducir algo de la música, el disco no parece existir, como si hubieran borrado los archivos. Luego de abrir el disco desde Lugares, los temas en el amarok vuelven a la vida y puedo escuchar música. Hay alguna forma de corregir esto y que los discos se monten solos al inicio como antes? (cuando no tenia este problema).

Seguro que te faltan las entradas en el fstab

abri la consola y hace:

sudo gedit /etc/fstab


y agrega a ese archivo:

Si es NTFS:
/dev/discoparticion       /media/loquesea      ntfs nls=utf8,umask=0222 0 0

Si es FAT(32):
/dev/discoparticion     /media/loquesea   vfat iocharset=utf8,umask=000 0 0


Donde "discoparticion" es la unidad (podes verlo con un fdisk -l o desde el gparted). Esto seria: hda2 hdb4 sda1, etc etc etc

Donde "loquesea" es la carpeta donde se montará la unidad. Acordate de crearlas antes de montar el disco, sino de error:

sudo mkdir /media/loquesea

:lolflag:

---

### Post by nemodot on 2008-06-29
Genial, muchas gracias a todos. 

Sobre el tema del Flash Player y Firefox 3 todavía no hay ninguna solución?

---

### Post by Mauro22 on 2008-06-29
Que plugin de flash tenes?

---

### Post by nemodot on 2008-06-30
El flash Player non free evil plugin de adobe. Instalé el 10 beta pero me anda peor :(

---

