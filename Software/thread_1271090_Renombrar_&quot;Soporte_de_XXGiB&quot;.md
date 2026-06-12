---
title: "Renombrar &quot;Soporte de XXGiB&quot;"
date: 2009-09-20
forum: Software
---

### Post by Alvaro_SG on 2009-09-20
Hola, soy nuevo en esto de Ubuntu y lo acabo de instalar. He instalado Ubuntu 9.04 en una partición y en la otra tengo Windows 7. Pues me gustaría renombrar "**Soporte de 473,6 GiB**" (es el nombre que tiene actualmente) a "**Windows 7**", para diferenciarlo mejor. Si lo quiero hacer manualmente me sale el siguiente error: "**No se ha podido renombrar <Soporte de 473,6 GiB> a <Windows 7>. El backend no soporta la operación.**"

Saludos y gracias.

Solucionado. ([aquí]("http://ubuntuforums.org/showpost.php?p=7985152&postcount=22"))

---

### Post by pablo.s on 2009-09-20
Contanos el método que estás
usando para renombrar el disco.

Y además posteá el contenido
de /etc/fstab.

---

### Post by Alvaro_SG on 2009-09-20
> **pablo.s said:**
> Contanos el método que estás
usando para renombrar el disco.

Y además posteá el contenido
de /etc/fstab.

Hola.

Pues para cambiar el nombre intento hacer lo siguiente.

Lugares > Equipo > Click derecho sobre el icono > Renombrar

Y aquí lo que contiene el archivo

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=7031eaf2-2b35-4776-917b-dae5f0b9173e /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d35ecca-4667-47e4-83b4-534f6d9164ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by pablo.s on 2009-09-20
No veo ninguna partición
NTFS en el archivo.
¿Ese es todo el contenido?

---

### Post by Alvaro_SG on 2009-09-20
> **pablo.s said:**
> No veo ninguna partición
NTFS en el archivo.
¿Ese es todo el contenido?

Sí, ahí está todo.

---

### Post by pablo.s on 2009-09-20
Bueno, muy rapidamente,
antes que todo UbuntuForums
se dé cuenta que se me acaban
de quemar los papeles, instalá
en Synaptic el paquete pysdm.
Cuando lo tengas listo te digo
cómo continuamos.

---

### Post by Alvaro_SG on 2009-09-20
Instalado.

---

### Post by pablo.s on 2009-09-20
Paso 1:
En una terminal escribí

```
sudo pysdm
```

Se va abrir el programa. Este
tiene una columnita a la izquierda
que te muestra los discos como
sda, sdb. Si hacés click en el
pequeño triangulo al lado del 
nombre se depliega una lista 
de particiones.
Ahora decime cuales aparecen
y fijate si una de ellas dice
```
Type    ntfs
```

---

### Post by Alvaro_SG on 2009-09-20
No, no pone nfts, solo sda4 y sda5.

---

### Post by josecuervo86 on 2009-09-20
En una termianl pone:

```
sudo fdisk -l
``` y mostranos el resultado

---

### Post by pablo.s on 2009-09-20
OK. En el menú de GNOME,
donde dice Lugares (o Places)
fijate donde dice "Computadora"
te salen todos los discos montados.
En el que dice "Soporte de 473,6"
haz click derecho y luego click
en Propiedades. En la última
solapa dice "Volumen".
Fijate que datos dice y copialos 
en un post.

---

### Post by Alvaro_SG on 2009-09-20
> **josecuervo86 said:**
> En una termianl pone:

```
sudo fdisk -l
``` y mostranos el resultado

```
Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000248ac

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2              13       57592   462501888    7  HPFS/NTFS
/dev/sda3           57593       58245     5245222+   5  Extendida
/dev/sda4           58246       77825   157276350   83  Linux
/dev/sda5           57593       58245     5245191   82  Linux swap / Solaris

```

---

### Post by pablo.s on 2009-09-20
Todo precioso con fdisk -l
pero todavia hace falta el UUID
de la partición para poder
hacer la integración en /etc/fstab.

---

### Post by EnriqueK on 2009-09-20
1.- Instalá Gparted (sudo apt-get install gparted)
2.- Desmontá la partición NTFS que querés cambiarle la ETIQUETA
3.- Ejecutá Gparted (sudo gparted), click secundario sobre la partición NTFS --> Etiqueta,  allí vas a tener la opción de cambiaele la etiqueta o el nombre de la partición.

---

### Post by Alvaro_SG on 2009-09-20
> **pablo.s said:**
> Todo precioso con fdisk -l
pero todavia hace falta el UUID
de la partición para poder
hacer la integración en /etc/fstab.

Buscando en Google he visto que si vas a /dev/disk/by-uuid aparecen.

Aquí dejo los dos UUID que hay.

4d35ecca-4667-47e4-83b4-534f6d9164ea
7031eaf2-2b35-4776-917b-dae5f0b9173e

---

### Post by pablo.s on 2009-09-20
En el menú de GNOME,
donde dice Lugares (o Places)
fijate donde dice "Computadora"
te salen todos los discos montados.
En el que dice "Soporte de 473,6"
haz click derecho y luego click
en Propiedades. En la última
solapa dice "Volumen".
Fijate que datos dice y copialos 
en un post.

---

### Post by Alvaro_SG on 2009-09-20
> **pablo.s said:**
> OK. En el menú de GNOME,
donde dice Lugares (o Places)
fijate donde dice "Computadora"
te salen todos los discos montados.
En el que dice "Soporte de 473,6"
haz click derecho y luego click
en Propiedades. En la última
solapa dice "Volumen".
Fijate que datos dice y copialos 
en un post.

```

Etiqueta:
Tamaño: 441,1 GiB
Soporte: Hard Disk
UUID: 6EBC7CE8BC7CABE9
Sistema de archivos: ntfs-3g (3.1)
Punto de montaje: /media/disk
Sistema de archivos: fuseblk
Opciones de montaje: rw nosuid nodev user_id=0 group_id=0 allow_other blksize=4096

```

---

### Post by pablo.s on 2009-09-20
Ya casi estamos.
Lo que vas a hacer ahora es
algo delicado: modificar los
puntos de montaje de las
particiones. 
En una terminal escribe:

```
sudo gedit /etc/fstab
```Se va a abrir un editor de textos.
Lo que tienes que agregar lo
destaco en color rojo.

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=7031eaf2-2b35-4776-917b-dae5f0b9173e /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d35ecca-4667-47e4-83b4-534f6d9164ea none            swap    sw              0       0
[COLOR=Red]# /media/windows7 Es la partición de Windows 7
UUID=6EBC7CE8BC7CABE9 /media/windows7  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Guardas el archivo y reinicias.
Espero que salga bien.

---

### Post by EnriqueK on 2009-09-20
Tu problema es que al crear la partición no le has puesto una etiqueta, eso se puede corregir fácilmente con lo que expliqué en mi anterior mensaje. En mi caso por ejemplo tengo una partición para un uso eventual que no monta al inicio y solo lo hace cuando entro al menú Lugares, o sea  no figura en el fstab , pero esto no impidió para que le pueda asignar un nombre representativo (etiqueta) que lo veo en el menú Lugares y en el escritorio cuando lo monto manualmente.

---

### Post by Alvaro_SG on 2009-09-21
> **pablo.s said:**
> Ya casi estamos.
Lo que vas a hacer ahora es
algo delicado: modificar los
puntos de montaje de las
particiones. 
En una terminal escribe:

```
sudo gedit /etc/fstab
```Se va a abrir un editor de textos.
Lo que tienes que agregar lo
destaco en color rojo.

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=7031eaf2-2b35-4776-917b-dae5f0b9173e /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d35ecca-4667-47e4-83b4-534f6d9164ea none            swap    sw              0       0
[COLOR=Red]# /media/windows7 Es la partición de Windows 7
UUID=6EBC7CE8BC7CABE9 /media/windows7  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Guardas el archivo y reinicias.
Espero que salga bien.

Nada, pongo eso, reinicio y sigue saliendo lo mismo.

> **EnriqueK said:**
> 1.- Instalá Gparted (sudo apt-get install gparted)
2.- Desmontá la partición NTFS que querés cambiarle la ETIQUETA
3.- Ejecutá Gparted (sudo gparted), click secundario sobre la partición NTFS --> Etiqueta,  allí vas a tener la opción de cambiaele la etiqueta o el nombre de la partición.

Cuando hago click derecho en la partición no puedo seleccionar etiqueta, porque no está activa.

---

### Post by EnriqueK on 2009-09-21
Probá con instalar **gnome-format**, una vez instalado probña nuevamente usando Gparted para ponerle la etiqueta a la partición, no uses el gnome.format para este propósito, solo hacelo con Gparted.

---

### Post by Alvaro_SG on 2009-09-21
Ya lo he cambiado. Gracias a todos, pero ninguna opción funcionó. Se cambió al cambiarlo desde Windows. Renombré Disco Duro a Windows 7 y funcionó.

---

