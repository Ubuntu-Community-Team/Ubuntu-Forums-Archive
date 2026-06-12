---
title: "no aparace grub, lubuntu recien instalado"
date: 2010-05-26
forum: Software
---

### Post by serbesa on 2010-05-26
hola,

acabo de instalar lxde despues de una instalacion minima de ubuntu 10.04, el cd normal no me funcionó, en un computador vien viejito.

sucede que no aparece grub, y por supuesto windows, entra directamente a lubuntu.

cualquier ayuda es bien recibida
saludos

---

### Post by Carlos C on 2010-05-27
Lo más probable es que no esté actualizando el GRUB. En el terminal por favor escribe:
```
sudo update-grub
```

Probablemente con eso puedas ver windows.

---

### Post by serbesa on 2010-05-27
ya lo hice, y no me detecto windows, puede ser problema de windows al momento de particionar, lo que no entiendo, es porque no aparece grub al prender el pc...

---

### Post by Carlos C on 2010-05-27
Te sugiero escribas en el terminal:
```
sudo fdisk -l
```
para que veas cómo está distribuida tu tabla de particiones. Por favor copia acá el resultado para que tengamos una mejor idea de lo que está pasando.

Saludos.

---

### Post by serbesa on 2010-05-27
es un pc de 1 ghz, 256 de ram que tiene un disco duro de 40 G y dos más pequeños, uno de ellos no lo lee ni windows.
 lo que me sale es lo sgte con fdisk -l:

sudo fdisk -l
[sudo] password for pcviejo: 

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x2ca62ca5

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4866    18598913    5  Extendida
/dev/sda5            2551        4775    17866752   83  Linux
/dev/sda6            4775        4866      731136   82  Linux swap / Solaris

Disco /dev/sdb: 2160 MB, 2160377856 bytes
128 cabezas, 63 sectores/pista, 523 cilindros
Unidades = cilindros de 8064 * 512 = 4128768 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x77862116

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         520     2096608+   6  FAT16
/dev/sdb2             521         522        8064    5  Extendida
/dev/sdb5             521         522        8032+   1  FAT12

---

### Post by Carlos C on 2010-05-28
Se supone que grub2 no desplegará ningún menú en caso de no haber otro sistema instalado. Extrañamente pareciera no reconocer que Windows existe. Sin embargo puedo ver que tienes una partición NTFS que correspondería al sistema de Microsoft. Lo primero que se me ocurre es forzar al grub a actualizarse, es decir ejecutar:

```
sudo update-grub
```

Si eso no es suficiente prueba presionando la tecla Shift mientras se inicia el sistema, eso debiera mostrarte el menú.

Saludos.

---

### Post by serbesa on 2010-05-28
Holas, les cuento lo que paso, aburrido de este problema, deisnstale grub2 e instale grub legacy, pero seguia el mismo problema. Despues instale de nuevo grub2 y se arreglo...
saludos

---

