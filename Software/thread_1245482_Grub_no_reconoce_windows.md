---
title: "Grub no reconoce windows"
date: 2009-08-20
forum: Software
---

### Post by Pato_rinaldi on 2009-08-20
Hola a todos, soy bastante nuevo en ubuntu. Ya lo he usado hace un tiempo y ayer decidi volver a ponerlo en mi laptop. Empiezo a detallar la situacion desde el principio:
 Tenia 2 particiones en el disco una donde estaba intalado windows 7 y otra que la usaba basicamente para datos. Borre la segunda e instale ubuntu en ella. Con ubuntu ningun problema arranca y funciona de 10.
El problema esta en que cuando inicio, grub solamente me da las siguientes opciones:

```

 Ubuntu 9.04, kernel 2.6.28-11-generic
 Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
 Ubuntu 9.04, memtest86+

```Probe modificando menu.lst y agregando

```

title Windows 7
root (hd0,1)
savedefault
makeactive
chainloader +1

```pero cuando quiero bootear da Error 13: Invalid or unsupported executable format. (aclaro tambien que este error sale cuando pongo la root en (hd0,2)).

Si cambio la root a (hd0,0) o a (hd0,4) tira Error 12: Invalid device requested.

Les dejo tanto el resultado de fdisk -l como menu.lst


```

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x9af81520

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               2        5394    43319272+   f  W95 Ext'd (LBA)
/dev/sda2            5395        9592    33720435   83  Linux
/dev/sda3   *        9593        9729     1100452+  82  Linux swap / Solaris
/dev/sda5               2        5394    43319241    7  HPFS/NTFS  

``````

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=04846b84-494d-4135-9c64-c9e266c88a6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=04846b84-494d-4135-9c64-c9e266c88a6a

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        04846b84-494d-4135-9c64-c9e266c88a6a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=04846b84-494d-4135-9c64-c9e266c88a6a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        04846b84-494d-4135-9c64-c9e266c88a6a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=04846b84-494d-4135-9c64-c9e266c88a6a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        04846b84-494d-4135-9c64-c9e266c88a6a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```Desde ya gracias por su ayuda y espero haber puesto todos los datos necesarios para que me ayuden.

Saludos

Pd: Ya se que varios diran que ni me gaste y formatee windows y no lo vuelva a poner je, pero tristemente lo necesito por algunos temas...

---

### Post by staar on 2009-08-20
Ventanas está instalado en una partición extendida?? creía que no podía hacer eso, estás seguro que borraste la partición correcta? desde ubuntu podés acceder al disco con Ventanas?

saludos

---

### Post by Pato_rinaldi on 2009-08-20
Desde ubuntu puedo acceder a todos los archivos y carpetas de la particion donde esta windows.
Con respecto a la particion donde esta instalada windows, no tengo bien en claro como esta porq no la hice yo, estaba asi cuando recibi la laptop yo lo unico que hice fue poner el windows 7 en vez del xp simplemente porq estaba aburrido y queria probarlo...

Saludos

---

