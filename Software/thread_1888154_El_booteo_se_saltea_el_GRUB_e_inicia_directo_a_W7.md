---
title: "El booteo se saltea el GRUB e inicia directo a W7"
date: 2011-11-28
forum: Software
---

### Post by Applelnx on 2011-11-28
Hola, acabo de comprar una Lenovo V570 que viene con Windows 7 y le quise instalar Ubuntu 11.10. Durante la instalacion no parece haer habido problemas, pero cuando reinicio la computadora no me inicia el GRUB, inicia directo a Windows.

Estuve leyendo bastante por internet pero no estoy seguro de lo que tengo que hacer (generalmente los errores son al reves, que no inicia Windows).

En fin, tengo entendido que esta booteando directo desde la particion de Windows. Para eso, con un live USB puse
```

sudo fdisk -l
```

y la salida fue:
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xebafd6dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   710243298   354915825+   7  HPFS/NTFS/exFAT
/dev/sda3       710244350  1434222591   361989121    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      1434222592  1465149167    15463288   12  Compaq diagnostics
/dev/sda5      1373403136  1434222591    30409728    7  HPFS/NTFS/exFAT
/dev/sda6       710244352  1360994303   325374976   83  Linux
/dev/sda7      1360996352  1373403135     6203392   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1999 MB, 1999634432 bytes
16 heads, 32 sectors/track, 7628 cylinders, total 3905536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005d8a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     3905535     1948736    6  FAT16
```

Alguno podra ayudarme para resolver este problema? Tengo varios años con instalaciones de Ubuntu pero esta es la primera vez que me pasa esto...
Saludos y gracias por anticipado!

---

### Post by guillermolisi on 2011-11-28
En que lugar del disco instalaste GRUB ?
Hiciste una actualizacion de GRUB con ```
sudo update-grub
``` ?
Si es una Lenovo, que hace ahi la particion indicada como Compaq-diagnostics ?
La particion sda3 deberia estar alineada o a un sector fisico o a un cilindro.

---

### Post by Applelnx on 2011-11-28
> **guillermolisi said:**
> En que lugar del disco instalaste GRUB ?
Hiciste una actualizacion de GRUB con ```
sudo update-grub
``` ?
Si es una Lenovo, que hace ahi la particion indicada como Compaq-diagnostics ?
La particion sda3 deberia estar alineada o a un sector fisico o a un cilindro.

Hola Guillermo, gracias por tu tiempo. Respecto de la indtalacion de GRUB, cuando instalaba Ubuntu eleji la opcion de instalarlo junto a Windows 7, no se a donde se habra instalado.

No se desde donde puedo actualizar el GRUB, ya que solo puedo iniciar Ubuntu desde un live USB.

Lo de la particion Compaq diagnostics me sorprendio a mi tambien...

---

### Post by granjero on 2011-11-28
fijate esta guía a ver si soluciona tus problemas...

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

salud!

---

### Post by guillermolisi on 2011-11-28
En general se recomienda instalar GRUB en el MBR del disco rigido, es decir para tu caso /dev/sda.

---

### Post by Applelnx on 2011-11-28
> **granjero said:**
> fijate esta guía a ver si soluciona tus problemas...

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

salud!

Probe con todas estas y ninguna funciono. Sigue cargando Windows 7 y el GRUB ni aparece...

La verdad que no se en que particion quedo instalado el GRUB. Probe cambiando la particion de booteo a la de Linux pero no funciono:

[ATTACH]208181[/ATTACH]

Tambien probe con el Boot Repair, sin resultados favorables.
[http://paste.ubuntu.com/753231/](http://paste.ubuntu.com/753231/)

---

### Post by guillermolisi on 2011-11-28
En el BIOS no habra algo en particular que produzca este efecto ?

De todas formas la particion extendida, que contiene las logicas donde esta instalado Ubuntu, no esta alineada a sector (por lo tanto tampoco a cilindro) y eso no es bueno.

Tambien me llama la atencion que esa particion extendida sea reconocida por fdisk como Win95 (LBA).

---

