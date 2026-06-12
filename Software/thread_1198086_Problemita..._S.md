---
title: "Problemita... :S"
date: 2009-06-27
forum: Software
---

### Post by okitos on 2009-06-27
Buenas, tengo un pequeños problema con el ·#|@·$ grub..

El tema es el siguiente, estuve meses tratando de solucionar el "Error 2" q no me deja iniciar los so, nunca le hallé solución, solamente formateando y volviendo a instalar, con esto se arregló el problema, pero queria poner el grub grafico, y en una aprte me surgieron problemas, por ejemplo, cuando entro al menu del grub al poner "find /boot/grub/stage1" me dice "error 15 no se puede encontrar el archivo", Sin emabrgo el archivo sí está y está en esa carpeta..
Lo busqué por todos lados y no encontré solución, dsp dejé de lad eso y me dispuse a instalar de cualquier manera el grub grafico, y cuando va a instalar me dice.. /boot/grub/stage1 not read correctly" y no me deja instalar :@

Que puede ser? el ubuntu esta recien instalado, version 9.04.

Y otra preguntita más.. según tengo entendido, si uno tiene disco duro IDE ubuntu, grub, lo identifica hda no? y luego algo tipo /dev/hd1 etc, pues yo tengo disco IDE y mis particiones son sda, /dev/sda1 tendrá algo que ver? Dejo el fdisk por las dudas tmb.

Saludos y gracias.

Dejo el menu.lst, fstab, por las dudas..

Fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ae40e05d-bace-4bea-a989-74f90f3570c1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=46c7b9cb-490a-4d8d-9eec-dc012ab60cc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ae40e05d-bace-4bea-a989-74f90f3570c1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae40e05d-bace-4bea-a989-74f90f3570c1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        ae40e05d-bace-4bea-a989-74f90f3570c1
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ae40e05d-bace-4bea-a989-74f90f3570c1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ae40e05d-bace-4bea-a989-74f90f3570c1
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ae40e05d-bace-4bea-a989-74f90f3570c1 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        ae40e05d-bace-4bea-a989-74f90f3570c1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ae40e05d-bace-4bea-a989-74f90f3570c1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        ae40e05d-bace-4bea-a989-74f90f3570c1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ae40e05d-bace-4bea-a989-74f90f3570c1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        ae40e05d-bace-4bea-a989-74f90f3570c1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

Disco Ide eh..
```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4e764e75

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6542    52548583+   7  HPFS/NTFS
/dev/sda2            6543        9729    25599577+   f  W95 Ext'd (LBA)
/dev/sda5   *        6543        9460    23438803+  83  Linux
/dev/sda6            9461        9729     2160711   82  Linux swap / Solaris
```

---

### Post by staar on 2009-06-27
desde hace un tiempo (medio largo ya) los discos ide se identifican con /dev/sda, /dev/sdb, etc, fue por un cambio en el driver que trae el kernel...

lo de tu problema, ya lo he visto, y creo que es un tema de alguna incompatibilidad a nivel mother, con alguna cosa rara que tenga en el manejo de los ide, y la verdad, no creo que se arregle fácil, por lo menos con la versión 1 de grub, que ya no se desarrolla más, solo se le corrigen bugs, hasta que esté listo grub2 (en la proxima versión de ubuntu va a venir este último instalado), en grub2 cambia todo, y trae soporte para temas (mucho mejores que los de gfxboot) nativamente, asi que te recomendaría que esperes hasta la proxima versión de ubuntu...

saludos

---

### Post by okitos on 2009-06-27
Ah bien de bien por la info staar, impecable, espero hasta la nueva entonces, gracias.. y el problema.. bue.. formatearé otra vez, :/

Saludos y muchas gracias por la respuesta.

---

### Post by alfplayer on 2009-06-27
No se cómo se solucionan los problemas de okitos, pero se puede probar usar grub2 en Jaunty.

---

### Post by gmunioz on 2009-06-27
Hola oki....:

Algunas veces, los problemas de incompatibilidades

entre el Grub, las bios y los rígidos se resuelven

creando una partición primaria, activa, sistema de

archivos ext3, de unos 380 megas, punto de montaje 

/boot

---

