---
title: "Raid1+lvm"
date: 2011-08-09
forum: Software
---

### Post by PoNcHo87 on 2011-08-09
Buenas,
En el dia de ayer instalé un Ubuntu Server 11.04, con RAID1 y LVM en la siguiente configuración:

*(Copy & paste de la impresion de pantalla en el momento de finalizar el particionado)*

```
LVM VG mirrorVG, LV homeLV - 100 GB Linux device-mapper (linear)
#1                100.0 GB        f        ext4        /home
LVM VG mirrorVG, LV rootLV - 100 GB Linux device-mapper (linear)
#1                 15.0 GB        f        ext4        /
LVM VG mirrorVG, LV homeLV - 100 GB Linux device-mapper (linear)
#1                 10.0 GB        f        ext4        /torrent

Dispositivo RAID1 #0 - 98.6 MB unkown
#1                98.6 MB         F        ext4        /boot
Dispositivo RAID1 #1 - 1.0 GB unkown
#1                1.0 GB          F        intercambio
Dispositivo RAID1 #2 - 198.0 GB Dispositivo RAID por Software
#1                497.9 GB        K        lvm
                   57.9 kB                 inutil

SCSI3 (0,0,0) (sda) - 500.0 GB ATA WD.....
#1        primary  98.6 MB B       K        raid
#2        primary   1.0 GB         K        raid
#3        primary 497.9 GB         K        raid


SCSI4 (0,0,0) (sdb) - 500.0 GB ATA WD.....
#1        primary  98.6 MB B       K        raid
#2        primary   1.0 GB         K        raid
#3        primary 497.9 GB         K        raid
```Instalo el sistema base, sin problemas.
Pero no bootea.
Hace las comprobaciones de los 3 LVs, y luego se queda en
```
*init*: *ureadahead*-*other main process* (xxx) *terminated with status 4*
```Reinstale sobre las particiones ya creadas, reinstalé borrando las particiones y lv's, y las generé nuevamente, pero sigue sin funcionar.

Modifique el grub y quité la opcion "quiet".
Y luego de eso me muestra como que no puede iniciar con el raid degradado (a pesar de que haya habilitado esa opcion).
Inicié con Live CD, instale mdamd y lvm2,
Hice que detecte los 3 RAID1, y que detecte y active el VG y los LV's.
Me lo levanta bien (por eso pude modificar el grub), pero no puedo hacer que inicie normalmente.-

Alguien tiene alguna idea de porqué sucede esto?
Gracias

PoNcHo87

---

