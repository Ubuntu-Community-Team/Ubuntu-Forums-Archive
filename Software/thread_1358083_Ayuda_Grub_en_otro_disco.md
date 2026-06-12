---
title: "Ayuda: Grub en otro disco"
date: 2009-12-17
forum: Software
---

### Post by guillermon on 2009-12-17
Hola, un amigo (el cual vive lejos) está migrando a ubuntu. Luego de instalar algo no salió bien, y mis conocimientos no ayudan mucho... Aparentemente tiene dos discos físicos, uno de 80 gigas, donde planea tener ambos sistemas (con el grub para poder elegir, por supuesto), donde también puede tener su home (particionado, tal como yo le sugerí); y en el otro disco lo utilizaría para datos extras. Él me comenta que cuando enciende la pc nunca aparece el grub, iniciando directamente el Win. Si presiona F7 creo, y cambia al disco de 500 gigas, ahí sí aparece el grub... A parti de estos datos le he pedido que me envíe una captura del sistema de archivos (la cual adjunto), y de su sudo fdisk -l
```
Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x1ccc1ccb

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2d252d25

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            7295        9726    19535040    5  Extendida
/dev/sdb2   *         123         135      102400    7  HPFS/NTFS
La partición 2 no termina en un límite de cilindro.
/dev/sdb3             135        7294    57505792    7  HPFS/NTFS
/dev/sdb4               1         122      979933+  82  Linux swap / Solaris
/dev/sdb5            7295        9726    19535008+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco
ukkonen@ukkonen-desktop:~$ 
```

   Me hace dudar de una mala partición, o un error (en eso que dice"la partición 2 no termina en un límite...). Me parece que el sdb3 ha quedado perdido! En fin... ¿alguien nos ayuda? ¿cuáles son los caminos posibles? (antes que se arrepienta este pobre cristiano?
    Desde ya gracias, saludos
Guillermo

---

### Post by z37a on 2009-12-18
tendrias que hacer un "grub-install /dev/sda" o "/dev/sdb" dependiendo de como tome el disco de 80GB, y asi dejar con el grub instalado en el mbr de ambos discos.

---

### Post by granjero on 2009-12-18
eso que decís de apretar F7 me suena a que tiene que entrar en el bios y configurar en la sección de booteo con que disco bootear...

salud!

---

