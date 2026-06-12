---
title: "3 discos para particionar"
date: 2008-07-25
forum: Software
---

### Post by crosssover on 2008-07-25
Hola gente les cuento cual es la duda que me aqueja..
  
 Actualmente tengo 3 discos rigidos:
 Sata 400Gb
 Ide 40Gb
 Ide 20Gb

Mi duda es que clase de esquema de particiones me convendria hacer para dejar instalado ubuntu hardy (hasta que salga Debian Lenny) como sistema principal y XP para jugar y no desaprovechar la placa de video :)

Anteriormente tenia algo asi con un disco de 320 Gb que un misteriosos problema con XP mal cerrado y "BSOD" de por medio se encargo de destruir junto con todos mis datos :-({|=

Sda1: 40 Gb [XP] en NTFS
Sda5: 280 Gb [Datos] en NTFS (Para compartir con Ubuntu)
Sdb1: 20 GB [/] en Ext3
Sdc1: 2 Gb [Swap]
Sdc2: 38 Gb [/home]

Muy contento con esto hasta que paso el percanse del que les hable mas arriba.

En fin. tengo pensado dejar de lado NTFS y su falso "journaling" y sacrificar la particion compartida de datos y dejar XP lo mas aislado posible asi el loco Bill no mete la corbata donde no debe.

Tambien me gustaria cambiar el sistema de archivos, Ahora estoy probando ReiserFS que va bastante bien pero se nota un poco su lentitud para trabajar con archivos pesados (ISOS, peliculas).
Es recomendable XFS ?

y una ultima cosita, como soy de adnar metiendo mano bastante seguido, y por ahi quiera instalar alguna otra distro, u otro SO como Solaris y no me llevo muy bien  con el GRUB, ¿es recomendable tener una particion separada para el /boot?

Acepto cualquier sugerncia o ejemplo de como tienen sus particiones

Saludos !

---

### Post by juanman on 2008-07-26
Solo un par de cosas: 
- la particion swap la haría en el disco sata q es mas rapido...
- XFS es recomendable con archivos grandes, yo lo uso sin problemas. Podes hacer una particion para peliculas, musica e ISOs...
- Reiserfs es recomendable con archivos chicos (muy chicos). Yo uso reiserfs en las particiones de sistema. Ext3 es otra buena opcion para la particion del sistema.
- ext3, aunq es mas lento, tiene mas opciones de montaje y herramientas (por ej, para recuperar archivos borrados). Se puede usar desde windows tambien, hay un driver, aunq creo q lo monta como ext2, por lo q perdes las caracteristicas de ext3 como el journaling... Y es el mas compatible si lo vas a usar con otros sistemas operativos como solaris o algun bsd...
- Hacer una particion con /boot es interesante, hacela en el primer disco al principio. Primero para evitar el problema en algunas bios q no logran ver mas alla del sector 1024 (no creo q sea tu caso) y segundo, en las actualizaciones del sistema, para q se actualice el grub desde cualquier sistema (si tenes un /boot en cada sistema, actualizan solo "su" grub)
- La cuestion del tamaño de cada una de las particiones, depende de los usos q le des. Si con ese esquema no tenian problemas, usa uno parecido...

Bueno, terminaron siendo mas q un par de cositas :P
Saludos

---

### Post by pol666 on 2008-07-26
yo te recomiendo que hagas una particion  grande para /home  en ext3 siemplemente eso :)

---

### Post by crosssover on 2008-07-28
gracias por la data gente, despues de particionar e instlar todo me quedo asi:


Disco /dev/sda: 400.0 GB


sda1     100Mb [Ext2] /boot
sda2     40Gb  [XFS]  /
sda3     315Gb [ReiserFS] /home
sda4           Extendida
sda5     15GB  [ReiserFFs]  /para instalar alguna otra distro    
sda6     2Gb   Linux swap 


Disco /dev/sdb: 40
sdb1  40Gb    [NTFS] win Xp


Disco /dev/sdc: 20Gb
/dev/sdc1   20Gb    [FAT32] intercambio

ah e instale XP en el disco esclabvo asi no jode el Grub que instale aparte en el disco Sata con Ubuntu.

---

