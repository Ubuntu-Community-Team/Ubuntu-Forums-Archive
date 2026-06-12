---
title: "Usplash comienza bien, pero termina con líena de comandos"
date: 2009-01-10
forum: Software
---

### Post by Terraman on 2009-01-10
Hola a todos,

A una vieja notebook (ver especificaciones en firma) le he instalado el comando de línea de Ubuntu 8.04 y le he instalado software adicional que utliza pocos recursos. Le he instalado Usplash para que no aparezcan los cmonados de lines al iniciarse la computadora. Usplash comienza bien, pero al final muestra los comandos de línea. Al apagarla o reiniciarla, Usplash muestra la barra de finalización correctamente.

¿Alguien tiene alguna idea de qué puede estar pasando?

Desde ya muchas gracias,

---

### Post by Hei Ku on 2009-01-10
postea tu archivo /boot/grub/menu.lst

---

### Post by Terraman on 2009-01-10
> **Hei Ku said:**
> postea tu archivo /boot/grub/menu.lst
Hei Ku,

# menu.lst

default   0
timeout   3
hiddenmenu

title     Ubuntu 8.04.1, kernel 2.6.24-19-generic
root      (hd0,4)
kernel    /boot/vmlinuz-2.6.24-19-generic root=UUID=1bd1dd50-83b-4cf6-b590-bdff4c83d446
ro quiet splash
initrd    /boot/initrd.img-2.6.24-19-generic
quiet

title     Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root      (hd0,4)
kernel    /boot/vmlinuz-2.6.24-19-generic root=uuid=1bd1dd50-83b-4cf6-b590-bdff4c83d446
ro single
initrd    /boot/initrd.img-2.6.24-19-generic

tile      Ubuntu 8.04.1, memtests86+
root      (hd0,4)
kernel    /boot/memtest86+
quiet

---

### Post by Hei Ku on 2009-01-11
En principio pareciera que está bien, pero para estar seguro necesito el archivo COMPLETO. En este archivo, las partes comentadas son importantes.

---

### Post by Terraman on 2009-01-11
> **Hei Ku said:**
> En principio pareciera que está bien, pero para estar seguro necesito el archivo COMPLETO. En este archivo, las partes comentadas son importantes.
Hei Ku,

Ok! Ahi va:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=1bd1dd50-835b-4cf6-b590-dbff4c83d446 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1bd1dd50-835b-4cf6-b590-dbff4c83d446 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1bd1dd50-835b-4cf6-b590-dbff4c83d446 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by Hei Ku on 2009-01-11
Pareciera estar bien, no debería mostrarte la línea de comando, salvo en algun caso particular que chequee el disco o algo así.
Qué es lo que te muestra?

---

### Post by mikey.duhhh on 2009-01-11
Install StartUp-Manager.

System>Administration>StartUp-Manager

Uncheck the box that says "Show text during boot"

---

### Post by Terraman on 2009-01-11
> **Hei Ku said:**
> Pareciera estar bien, no debería mostrarte la línea de comando, salvo en algun caso particular que chequee el disco o algo así.
Qué es lo que te muestra?
Hei KU, 
La primera linea de comandos que aparece es la siguiente:
> 
Reading files needed to boot....

La última es antes de iniciar Slim:> 
Kinit: No resume image, doing normal boot...

---

### Post by Terraman on 2009-01-11
> **Hei Ku said:**
> Pareciera estar bien, no debería mostrarte la línea de comando, salvo en algun caso particular que chequee el disco o algo así.
Qué es lo que te muestra?
Hei KU, 
La primera linea de comandos que aparece es la siguiente:
> 
Reading files needed to boot....

La última es antes de iniciar Slim:> 
Kinit: No resume image, doing normal boot...

---

### Post by Terraman on 2009-01-11
> **mikey.duhhh said:**
> Install StartUp-Manager.

System>Administration>StartUp-Manager

Uncheck the box that says "Show text during boot"
mickey.duhhh,

It is already unchecked.

---

