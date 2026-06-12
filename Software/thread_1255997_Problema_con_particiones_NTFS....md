---
title: "Problema con particiones NTFS..."
date: 2009-09-02
forum: Software
---

### Post by Patchiu on 2009-09-02
Hola gente del foro!
Les cuento lo que paso:

Tengo varias particiones NTSF y de Ubuntu en EXT4.
Todo empezo cuando yo configure el automontaje de particiones con "ntfs-config 0.5.5", y cuando me pidio que nombre las particiones, les di un nombre a cada una.

Hasta ahi, paso el tiempo y no sucedio nada. 
La cosa fue que por accidente, les puse mal el nombre a las particiones y como me confundia, las renombre en modo administrador yendo a /media y apretando **F2 + Cambiar nombre**...
 (suena reeee bestia, y asi fue finalmente).

El problema es que, a partir de ese momento, me muestra los volumenes de las particiones en "Lugares", pero solo en modo usuario, **en modo root no me las muestra**, y no me deja entrar a ninguna de ellas (de las NTSF).
Y cuando quiero entrar a una yendo a "Lugares", me da el error: 
**"Solo el usuario root puede montar la particion"**.

Y cuando ahora entro a /media tanto como usuario o como root, veo que las particiones siguen ahi, y **me toma las particiones como si fueran carpetas vacias.**

Al poner las propiedades en una particion en /media (en "Lugares" no aparece la opcion "Propiedades", pero me da la opcion "Montar", pero le das click y nada.. el mismo error de "Solo el usuario root puede montar la particion"), me aparece esto:
> Nombre: Disco C
Tipo: carpeta (inode/directory)
Contenido: Nada.
Lugar: /media.
Volumen: Desconocido.


Pero poniendo sudo fdisk -l me muestra esto:
> Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x36de36dd

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         679     5454036    7  HPFS/NTFS
/dev/sda2             680       19457   150834285    f  W95 Ext'd (LBA)
/dev/sda5             680       16203   124696498+   7  HPFS/NTFS
/dev/sda6           16204       19457    26137723+   7  HPFS/NTFS

Disco /dev/sdb: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8f4a8f4a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        8447    67850496    7  HPFS/NTFS
/dev/sdb2            8448       10011    12562830    5  Extendida
/dev/sdb5            8448        8571      995998+  82  Linux swap / Solaris
/dev/sdb6            8572       10011    11566768+  83  Linux

Probe con **sudo ntfslabel /dev/sdXX nombreX**
Pero NADA! Me aparece el nombre cambiado, pero sigue el error...
Lo curioso, es que en "Lugares" aparecen con el nombre que les di con *sudo ntfslabel /dev/sda1 SDA1* (o sea, "SDA1") y en "/media" me aparecen con el nombre que les di como root ("Disco C")..
 

Si alguien tiene alguna idea... se lo agredecere _bastante!_

---

### Post by mama21mama on 2009-09-02
Hola no desesperes amigo mira [aqui]("http://mamalibre.eshost.com.ar/?q=node/26") dice como montarlas.

Saludos

---

### Post by Patchiu on 2009-09-10
Buenisimo el Link!
Era un *BEEP* barbaro! 
Pero me re ayudo el link que me dejaste!
(Si bien tuve que acudir a otros sitios para entenderlo del todo, me re sirvio y ahora tengo todo joya!)

Muchisimas Gracias!
Salu2!

---

