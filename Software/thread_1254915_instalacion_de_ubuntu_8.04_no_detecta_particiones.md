---
title: "instalacion de ubuntu 8.04 no detecta particiones"
date: 2009-08-31
forum: Software
---

### Post by tsueseres on 2009-08-31
hola, estoy instalando ubuntu 8.04 64bits y a la hora de seleccionar el disco le pongo manual y no me muestra masque /dev/sda.
tengo 2 particiones primarias ntfs una extendida y dentro de la extendida una particion para ubuntu otra de swap y otra ntfs.

como le ago para que la instalacion de ubuntu me las detecte

---

### Post by gmunioz on 2009-09-01
Hola tsu...:

1- Desde el operativo de Microsoft, ejecuta:

chkdsk /f y defrag, sobre ambas particiones

Luego cierra normalmente

2- Desde una sesión live de Ubuntu, ejecuta en 

consola (Aplicaciones - Accesorios - Terminal)

sudo fdisk -l    (es ele, no uno ni i)

copia y pega la salida en el post

---

### Post by tsueseres on 2009-09-01
> **gmunioz said:**
> Hola tsu...:

1- Desde el operativo de Microsoft, ejecuta:

chkdsk /f y defrag, sobre ambas particiones

Luego cierra normalmente

2- Desde una sesión live de Ubuntu, ejecuta en 

consola (Aplicaciones - Accesorios - Terminal)

sudo fdisk -l    (es ele, no uno ni i)

copia y pega la salida en el post

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa2bf227e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3300    26507218+   7  HPFS/NTFS
/dev/sda2            3301        6600    26507250    7  HPFS/NTFS
/dev/sda3            6601       60801   435369532+   5  Extendida
/dev/sda4           13102       13356     2048256   82  Linux swap / Solaris
/dev/sda5            6601       13101    52219219+  83  Linux
/dev/sda6           13357       60801   381101931    7  HPFS/NTFS

---

### Post by gmunioz on 2009-09-01
Hola Tsu....:

Pues según fdisk, tus particiones estan

perfectamente visibles.

Asi que al reintentar instalar, tendrías que

optar por particionamiento manual e instalar en

/dev/sda4 , para intercambio, swap y /dev/sda5

para root /

---

### Post by tsueseres on 2009-09-02
> **gmunioz said:**
> Hola Tsu....:

Pues según fdisk, tus particiones estan

perfectamente visibles.

Asi que al reintentar instalar, tendrías que

optar por particionamiento manual e instalar en

/dev/sda4 , para intercambio, swap y /dev/sda5

para root /

ya habia echo fdisk -l antes por que crei que se me habian borrado, pero me salio lo mismo,

ya intente todo lo que me digiste y sigue igual (sigue sin mostrarme las particiones)

---

### Post by gmunioz on 2009-09-02
Hola tsu...:

Desde la sesión live, conectado a la red, antes de

iniciar la instalación , ve si hay una nueva versión

de gparted para actualizar, si no lo hubiere baja 

el código de la ultima versión:

[http://sourceforge.net/projects/gparted/files/gparted/gparted-0.4.6/gparted-0.4.6.tar.bz2/download](http://sourceforge.net/projects/gparted/files/gparted/gparted-0.4.6/gparted-0.4.6.tar.bz2/download)

E instalalo descomprimiendo el archivo, entrando al directorio

y ejecutando en consola:

./configure
make
sudo make install

Luego reintenta la instalación.

---

### Post by tsueseres on 2009-09-02
> **gmunioz said:**
> Hola tsu...:

Desde la sesión live, conectado a la red, antes de

iniciar la instalación , ve si hay una nueva versión

de gparted para actualizar, si no lo hubiere baja 

el código de la ultima versión:

[http://sourceforge.net/projects/gparted/files/gparted/gparted-0.4.6/gparted-0.4.6.tar.bz2/download](http://sourceforge.net/projects/gparted/files/gparted/gparted-0.4.6/gparted-0.4.6.tar.bz2/download)

E instalalo descomprimiendo el archivo, entrando al directorio

y ejecutando en consola:

./configure
make
sudo make install

Luego reintenta la instalación.



la version k trae actualmente no medetecta las particiones y le intento con el paquete del link con las instrucciones que me diste y me aparece al final c compiles cannot create executables

---

### Post by gmunioz on 2009-09-02
Hola tsu....:

Esta complicado el tema...

Prueba:

En la sesión live, agrega al archivo /etc/apt/sources.list

La línea

```
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
```

Guarda el archivo y ejecuta:

```
sudo apt-get update
sudo apt-get install build-essential fakeroot 
sudo apt-get build-dep gparted
sudo apt-get -b source -t intrepid gparted
sudo dpkg -i *.deb 
```

Si esto funciona, tendrás instalado gparted versión

de Intrepid.

En instalaciones en disco duro funciona, y lo uso con

frecuencia, nunca lo he usado en sesión live.

---

### Post by tsueseres on 2009-09-03
> **gmunioz said:**
> Hola tsu....:

Esta complicado el tema...

Prueba:

En la sesión live, agrega al archivo /etc/apt/sources.list

La línea

```
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
```

Guarda el archivo y ejecuta:

```
sudo apt-get update
sudo apt-get install build-essential fakeroot 
sudo apt-get build-dep gparted
sudo apt-get -b source -t intrepid gparted
sudo dpkg -i *.deb 
```

Si esto funciona, tendrás instalado gparted versión

de Intrepid.

En instalaciones en disco duro funciona, y lo uso con

frecuencia, nunca lo he usado en sesión live.

graias por la respuesta pero
me da eroor cuando pongo la primer linea en la lista al momento de darle update no se si por que uso 8.04 pero por la otra linea de update me tardaria mucho, no tengo coneccion muy rapida a internet. no hay alguna otra manera de solucionar esto

---

### Post by gmunioz on 2009-09-03
Hola tsu...:

Prueba con otra versión, 8.10 o 9.04

---

### Post by tsueseres on 2009-09-04
> **gmunioz said:**
> Hola tsu...:

Prueba con otra versión, 8.10 o 9.04

ya probe con la version 9.04 , 8.04 y 8.10 y ninguna me detecta las particiones en el disco

---

### Post by phxnd on 2009-09-20
a mi me pasa exactamente lo mismo:
disco de 80gb
tengo una particion con W$ XP de.. nose, 20 gb creo, y tengo Ubuntu GG instalado en el resto
ahora bien, quiero instalar JJ y me pasa igual, no me reconoce las otras dos aprticiones, ni siquiera el gparted =S

edit: tal vez no fui del todo claro, lo que quiero es instalar JJ sobre GG

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitiendo la partición vacía (5)

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xdee4dee4

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3259    26177886    7  HPFS/NTFS
/dev/sda2            3260        9731    51986340   83  Linux
/dev/sda3            9732       10011     2249100    5  Extendida
/dev/sda4            9872       10011     1124518+  82  Linux swap / Solaris
/dev/sda5            9732        9871     1124487   82  Linux swap / Solaris

```
```

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8
======================
No se puede tener particiones superpuestas.

```
gparted no muestra ninguna particion, y cuando fui a la parte de soporte, dice que para poder modificar y trabajar con las particiones fat32 necesita dosfstools, y el cd live no viene con esa lib

lo importante es que me reconozca la particion de windows, que es la uqe quiero dejar intacta para que usen los simples mortales que viven conmigo(?) jaja

---

