---
title: "Mover partición"
date: 2009-09-23
forum: Software
---

### Post by leosr on 2009-09-23
Hola.
Quiero borrar la partición en la que tengo Win XP y "correr" las otras particiones. La partición a la que quiero darle el espacio ganado es al /home.
Esta es la tabla de particiones:
```
Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf8e1f8e1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1985    15944481    7  HPFS/NTFS
/dev/sda2            1986       10011    64468845    f  W95 Ext'd (LBA)
/dev/sda5            1986        3409    11438248+  83  Linux
/dev/sda6            3410        9946    52508421   83  Linux
/dev/sda7            9947       10011      522081   82  Linux swap / Solaris
leo@Semprom2600-desktop:~$ 

``` 
sda 6 es mi /home

Lo que quiero saber es si creen que voy a tener algún problema con el arranque (GRUB) después de mover las particiones.

Gracias!

---

### Post by gmunioz on 2009-09-23
Hola leo....:

Ya he posteado como mover /home.

En tu caso si no quieres complicaciones

simplemente formatea la partición a ext4

Y montala como /home/usuario/datos asi mantendrás

tus datos a salvo en futuras reinstalaciones o

cambios de versión

---

### Post by leosr on 2009-09-23
> **gmunioz said:**
> Hola leo....:

Ya he posteado como mover /home.

En tu caso si no quieres complicaciones

simplemente formatea la partición a ext4

Y montala como /home/usuario/datos asi mantendrás

tus datos a salvo en futuras reinstalaciones o

cambios de versión
De esa forma me aparece como otra unidad o sólo como una carpeta en el /home?
Pasame el link de lo que posteaste.
Ya lo encontré.

Gracias!

---

### Post by gmunioz on 2009-09-23
Hola leo....:

Como una simple carpeta dentro de /home/usuario

---

### Post by leosr on 2009-09-28
Al final lo hice desde el LiveCD con GParted, borré la partición de Win (primaria) y luego "moví" / y el espacio vacío se lo asigné a /home. No tardó mucho (supongo que por ext4) y salió todo bien, por suerte.

Gracias!

---

