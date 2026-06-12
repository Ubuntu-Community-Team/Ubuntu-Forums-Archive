---
title: "No encuentra el directorio Home"
date: 2010-01-03
forum: Software
---

### Post by akiestudio on 2010-01-03
Cuando inicio ubuntu 9 , sale la pantalla en negro y me dice lo siguiente:

File system chek failed a long is beging saved /var/long/fsck/checkfs if that location is writable Please repair the file systmen manually 
A maintenance shell will now be started 
Control + D terminate this shell and resume system boot.
Give root password for maintenance or type Control +D to continue.

Doy a Control + D , porque no se como repararlo manualmente y sale la pantalla de usuario donde poner nombr y login 

Despues de autentificarme sale el siguiente mensaje:

Su directorio personal esta establecido a: /home/fran pero no existe desea iniciar una sesion con el directorio raiz / como personal.

En este punto como no se que hacer reinicio el ordenador

Alguna ayuda por favor.Gracias

---

### Post by gmunioz on 2010-01-03
Hola aki....:

Inicia con un live-cd
En una consola (Aplicaciones - Accesorios - Terminal)
Ejecuta (Escribes la orden y das enter)
```
sudo su
fdisk -l *(es ele minuscula)*
```
Este último comando te dará una salida similar a esta:
```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x612b85d1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          36      289138+  83  Linux
/dev/sda2              37        9729    77859022+   5  Extendida
/dev/sda5            3041        3162      979933+  82  Linux swap / Solaris
/dev/sda6            3163        9729    52749396   83  Linux
/dev/sda7              37        3040    24129567   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

```
Las particiones cuyo id es 83 son las que debes reparar
Lo haces ejecutando en esa misma consola
```
umount /dev/sda?  *(cambia ? por lo que corresponde)*
fsck -a /dev/sda?  *(cambia ? por lo que corresponde)*
reboot
```

---

### Post by akiestudio on 2010-01-06
Buenos dias  cuando hago un ; umount del disco dice que no se monta el disco , asi despues ejecuto el fsck , si despues reinicio el sigue saliendo el mismo problema que no encuentra el directorio home , 
Otra solucion , gracias.

---

### Post by akiestudio on 2010-01-07
Alguna ayuda , a nadie se le ocurre , que puedo hacer:(  por favor gracias

---

### Post by juancarlospaco on 2010-01-07
**sudo touch /forcefsck && sudo reboot**

---

### Post by akiestudio on 2010-01-08
No funciona, 

Reinicio y sale la misma pantalla en negro y donde tambien pone:

Mount dispositivo special /dev/disk-buy/***( no recuerdo mas, no me dio tiempo eran unas cifras)  no existe.....fail

Load disck apparmor module-................... fail

Donde esta el archivo de sesion , quizas si lo edito a mano  , y le doy la ruta donde se encuentra el home arranque, alguna sugerencia.

He encontrado el archivo etc/fstab que dice lo siguiente:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=158a1207-484a-4ea7-b87c-a49cb0927ba8 /home           ext3    relatime        0       2
# /windows was on /dev/sda7 during installation
UUID=0F97-262A  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=1bd0d370-2557-4bf3-a01e-f364da76a182 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


No se alguien o si esto puede ayudar , yo por si acaso no lo quiero tocar

---

### Post by juancarlospaco on 2010-01-08
Gparted LiveCD y revisar que paso, no descarto una falla de hardware...

---

### Post by akiestudio on 2010-01-08
Usando el gparted live, su terminal no es capaz de montarlo , ademas dice que no encuentra el /dev/sda2 en etc/fstab or etc/mtab:

en el mtab hay lo siguiente.

/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

Creo que si comparamos el etc/fstab y la salida de fdisk -l:

dev/sda1    id = 7 , HPTFS/NFTS
dev/sda2    id = 83 LINUX
dev/sda3    id = 5 EXTEND
dev/sda5    id = 82 LINUX/SWAP
dev/sda6    id = 5   EXTEND

Creo que puede ser hay el problema, ademas este problema me surgio ahora que recuerdo despues de usar el programa Ext2 Volumen Manager y montar el disco Home en windows para poder ver los archivos que contenia home desde linux, quizas no es este el problema y es una casualidad, pero creo que si editamos el archivo etc/fstab.

Alguien sabe si es ese el problema y como editarlo ..

Gracias

---

