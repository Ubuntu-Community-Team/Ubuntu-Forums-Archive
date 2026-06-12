---
title: "Instalar ubunto 8.04 con raid 0"
date: 2008-09-12
forum: Software
---

### Post by josejs on 2008-09-12
Pues tengo windows xp y he decidido pasarme a linux de una vez, y tengo este equipo:
ASUS M2N-SLI DELUXE - AM2 6400 BLACK EDITION - 2 X 1 GB DDR2 800 DHX CORSAIR DOMINATOR - 2 X 500 GB WD RAID 0 - SAPPHIRE HD 3870 SINGLE SLOT

y claro mi problema es el raid 0, quiero mantenerlo, pero cuando empiezo a instalar, y llego a la parte de las particiones, el raid 0 que tengo que en windows xp me muestra 960 GB en la instalacion de linux me muestra cada disco por su parte, osea los 2 discos separados, entonces no puedo instarlar, porque si instalo en uno de los 2 discos supongo que el raid se me jodera.

Que puedo hacer, gracias.

---

### Post by gmunioz on 2008-09-12
Hola jos...:
he aqui un procedimiento:
Es conveniente que crees las particiones donde instalaras Ubuntu desde Windows.
Iniciado el live-cd de Ubuntu pulsa:
Sistema > Administración > Gestor de paquetes Synaptic
En el pulsa Configuración > Repositorios
Activad los repositorios Universe
Haz una búsqueda por la palabra "dmraid" e instala la aplicación.
Cuando finalice cierra Synaptic. 
Pulsa Aplicaciones > Acesorios > Terminal
En la consola ejecuta:
sudo dmraid -ay
Te dará una salida, segun la motherboard y su chipset, similar a:
RAID set "via_chdfjhgecb" already active
RAID set "via_chdfjhgecb1" already active
RAID set "via_chdfjhgecb5" already active
RAID set "via_chdfjhgecb6" already active
RAID set "via_chdfjhgecb7" already active
RAID set "via_chdfjhgecb8" already active

Supongamos que sean más o menos así:

via_chdfjhgecb -- the raw raid volumen , el volumen raid
via_chdfjhgecb1 -- Partición primaria, instación del Windows XP
via_chdfjhgecb5 -- Partición Extendida, NTFS
via_chdfjhgecb6 -- Partición Extendida, NTFS
via_chdfjhgecb7 -- Partición Extendida, Ubuntu para /
via_chdfjhgecb8 -- Partición Extendida, Ubuntu para swap


El orden de las particiones es el mismo de windows

Se deben formatear las particiones donde se instalará Ubuntu para / y para swap
En la consola ejecutas:

sudo mkfs.ext3 /dev/mapper/via_chdfjhgecb7
sudo mkswap /dev/mapper/via_chdfjhgecb8
sudo swapon /dev/mapper/via_chdfjhgecb8

Obviamente, cambia los datos por los tuyos y si cambias el sistema de archivos por ejemplo ext3 por reiserfs, el que recomiendo, reemplazas ext3 por reiserfs, tambien es aconsejable tener a /boot y /home en particiones separadas, /boot en ext3 y /home en reiserfs.

Una vez terminado el particionamiento y formateo, a la instalación:

Debes crear en primer lugar el directorio donde montaras la partición y donde instalaras el sistema
Ejecutas en consola:

sudo mkdir /target
sudo mount -t ext3 /dev/mapper/via_chdfjhgecb7 /target
sudo mkdir /target/boot
sudo mkdir /target/dev
sudo mount --bind /dev /target/dev
sudo mkdir /target/proc
sudo mount -t proc proc /target/proc
sudo mkdir /target/sys
sudo mount -t sysfs sysfs /target/sys
cd /target
sudo apt-get install debootstrap
sudo debootstrap dapper /target
sudo cp /etc/apt/sources.list /target/etc/apt
sudo cp /etc/resolv.conf /target/etc
sudo cp /etc/hosts /target/etc
sudo mount --bind /dev /target/dev
sudo mount -t proc proc /target/proc
sudo mount -t sysfs sysfs /target/sys
sudo chroot /target
apt-get update
apt-get install language-pack-es
apt-get install dmraid
apt-get install grub
apt-get install linux-686
apt-get install ubuntu-base
apt-get install ubuntu-desktop
adduser <usuario>
visudo

Aqui aparecerá un editor de texto. 
Vas al final del archivo, y duplicas la linea de root, y cambias la palabra root por el nombre de usuario que has creado
Guardas el archivo con [Ctrl]+[O]  Enter
Sales del editor con [Ctrl]+[X].

A continuación sigues ejecutando

mkdir /boot/grub
cp /lib/grub/i386-pc/stage1 /boot/grub/
cp /lib/grub/i386-pc/stage2 /boot/grub/
cp /lib/grub/i386-pc/e2fs_stage1_5 /boot/grub

Si no sale el i386-pc, pon el que exista.
En caso de usar el sistema reiserfs, cambiar e2fs_stage1_5 por reiserfs_stage1_5

grub

A qui entras al Grub. 
Debes informarle donde está mapeado el RAID, ejecutando:

device (hd0) /dev/mapper/via_chdfjhgecb

Cambia via_chdfjhgecb por la que corresponda

Luego debes informar donde esta tu /boot, si esta en la misma partición que /, teniendo en cuenta que el Grub cuenta desde 0, sería para el ejemplo: 

root (hd0,6)
setup (hd0)
quit
update-grub
Si (y).
Control+D
sudo gedit /target/boot/grub/menu.lst

Ser abrirá un archivo, buscar en él una línea que diga:

# kopt=root= ro

Agregar donde está mapeada la partición raiz, en el ejemplo via_chdfjhgecb7

# kopt=root=/dev/mapper/via_chdfjhgecb7 ro

Buscar la linea que diga:

# groot=(hd0,0)

Y modificadla, para indicarle donde esta la partición /root, en el ejemplo la 7, que para el Grub es la 6

# groot=(hd0,6)

Ir al final para modificar la entrada del menu, se debe indiciar la partición root donde está instalado el sistema por defecto se más o menos así:

title        Ubuntu, kernel 2.6.24-21-686
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-686 root= ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-686
savedefault
boot

title        Ubuntu, kernel 2.6.24-21-686 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-686 root= ro single
initrd        /boot/initrd.img-2.6.24-21-686
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot

Debe quedar, de acuerdo con el ejemplo asi:

title        Ubuntu, kernel 2.6.24-21-686
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-21-686 root=/dev/mapper/via_chdfjhgecb7 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-686
boot

title        Ubuntu, kernel 2.6.24-21-686 (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-21-686 root=/dev/mapper/via_chdfjhgecb7 ro single
initrd        /boot/initrd.img-2.6.24-21-686
boot

title        Ubuntu, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin 
boot

Y agregar la entrada para Windows, que quedaría así


title         Windows XP Profesional
rootnoverify     (hd0,0)
chainloader +1

Guardar el archivo.
Salir de gedit
continuar ejecutando

sudo cp /etc/hosts /target/etc/hosts
sudo cp /etc/network/interfaces /target/etc/network/interfaces
sudo gedit /etc/fstab

Se abrirá el archivo, se debe agregar la siguiente línea:

/dev/mapper/via_chdfjhgecb8    none    swap    sw    0    0

Obviamente se debe cambiar la partición via_chdfjhgecb8 del ejemplo por la correcta para swap

Guardar el archivo.
Salir de gedit.
Cerrar la sesión
Iniciar del disco rígido. 

Saludos.
Gabriel.
*Solo doy soporte para Ubuntu *- **6666 **- *Más malo que el diablo*.

---

### Post by josejs on 2008-09-13
Gracias tío, voy a probarlo todo haber si funciona, muchas gracias, ya te digo cosas.

---

### Post by fmsismo on 2008-09-13
Ojo con eso.

Porque tu controladora es una controladora sata que hace raid 0 en forma híbrida, una parte por hard y otra por soft.  Te anda en XP porque cargaste los drivers propietarios del fabricante que dan soporte a esta funconalidad.

Con linux estas haciendo raid por software.  A nivel de desempeño en los equipos actuales es practicamente lo mismo.

Hace siempre un respaldo de tus datos antes de iniciar cualquier cambio de esta índole.

Saludos

---

