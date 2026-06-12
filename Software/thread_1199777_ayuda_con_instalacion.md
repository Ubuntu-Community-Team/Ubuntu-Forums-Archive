---
title: "ayuda con instalacion"
date: 2009-06-29
forum: Software
---

### Post by abdouleltobul on 2009-06-29
Hola a todos...soy nuevito por aqui....mi experiencia con linux es minima...una vez instale mandriva2006...se boot cuando queria..bueno luego hace un par de semanas consegui ubuntu 8.10.
Lo instale en un disco nuevito y funciono bastante bien.Luego tuve que utilizar el disco y ahora quise instalarlo en otro..usado pero funcionando.Realizo la instalacion pero cuando termina abre puerta del dvd dice sacar  disco y apretar enter para resetear.....no vuelve a arrancar jamas"..siemprte sale leyenda como que "no encuentra disco"
En wind utilice en hdd regenerator para revisar el disco pero dice estar ok. En partition manager reviso disco y dice tener Linux...pero no arranca----adjunto una captura de la pantalla
helps please  :guitar::guitar:

---

### Post by gmunioz on 2009-06-29
Hola abd.....:

El problema es que por alguna razón tienes equivocada o se perdió 

el uuid de la partición del disco rígido que aloja /.

Inicia con con el live-cd.

Cuando termine de iniciar abre una consola (aplicaciones - accesorios

- terminal) y ejecuta:

```
sudo fdisk -l
```

Esto te dará una salida parecida a:

```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf362f362

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1829    14691411   83  Linux
/dev/sda2            1830        9729    63456750    5  Extendida
/dev/sda5            1830        1951      979933+  82  Linux swap / Solaris
/dev/sda6            1952        3653    13671283+  83  Linux
/dev/sda7            3654        9729    48805438+  83  Linux
```

La partición que tiene el * y se identifica con id 83 sistema linux

en este caso /dev/sda1 es la de tu /

Tomando el ejemplo, de que / de GnuLinux es /dev/sda1

ejecutas en la consola el comando:

```
sudo vol_id --uuid /dev/sda1
```

Este comando te dará una salida parecida a esta:
```
d2f7f1a8-3863-438d-84cb-24a177377122
```

Es la uuid de la partición.

Anotas ambos valores, /dev/sdax y uuid

cierras la sesión, inicias del disco rígido, pulsas escape al

iniciar para ver el menu del Grub, iluminas la primer opción como

para elegir con cual línea de kernel iniciar y pulsas e de editar

te aparecerá el menu, algo asi como:


```
title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        87836804-f467-4863-8504-57d60a3ee9ea
kernel        /boot/vmlinuz-2.6.27-9-generic
root=UUID=87836804-f467-4863-8504-57d60a3ee9ea ro quiet splash
initrd        /boot/initrd.img-2.6.27-9-generic
```

Si la uuid obtenida es distinta a la escrita

te paras primero sobre la segunda línea, pulsas nuevamente e

para editar y la cambias

y luego sobre la tercera linea, pulsas e para editar y la cambias

Si la uuid fuera la correcta, te paras sobre la tercera, esa que 

comienza con kernel, pulsas e de editar y le cambias uuid por su

/dev/sdax , /dev/sda1 en el ejemplo, para que quede asi:

```
kernel        /boot/vmlinuz-2.6.27-9-generic root=/dev/sda1 ro quiet splash
```

Terminas la edicion, sales y pulsas b de bootear para iniciar con

estos valores.

Si esto te funciona y el sistema inicia, ejecuta en consola la orden

```
sudo gedit /boot/grub/menu.lst

```
y haz los cambios permanentes en sus líneas.

**PD: Este post no es para este subforo.**

---

