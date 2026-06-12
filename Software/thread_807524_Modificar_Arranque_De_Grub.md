---
title: "Modificar Arranque De Grub"
date: 2008-05-25
forum: Software
---

### Post by h9005 on 2008-05-25
Esto me aparece cuando quiero modificar el orden de arranque. Ahora arranca linux, pero quiero q por defecto lo haga xp.

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=2526b331-b4f0-4693-b48f-7dc3dbc09378 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=2526b331-b4f0-4693-b48f-7dc3dbc09378 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=2526b331-b4f0-4693-b48f-7dc3dbc09378 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sajnox on 2008-05-25
La forma mas facil de hacer es con el administrador de arranque

Lo instalas con

```
sudo apt-get install startupmanager
```

Desde ahi manejas todas las opciones del grub en forma grafica

Saludos

---

### Post by faktorqm on 2008-05-25
La otra es cambiar al "default 0" por "default 4". Hay un thread que yo explico un monton de cosas dando vueltas por ahi sobre grub. Salu2!

---

### Post by llove on 2008-05-27
hola, solucionaste tu problema?? tal vez podrias probar con qgurbeditor. saludos

---

### Post by h9005 on 2008-05-28
Hola no. nadie sabe como modificar los valores que postee para arrancar con xp con defecto? No pueso instalar el modo grafico. me aparece este error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by h9005 on 2008-05-28
Cambio default 0 por default 3 o 4? xq en la lista me aparecen tres opciones de linux y una de win, x lo que serian de 0 a 3. Y no hay que modificar mas nada?

---

### Post by sajnox on 2008-05-28
Las tres opciones de Linux que te aparecen son 

1) La sesion normal
2) Sesion de recuperacion (solo en modo texto)
3) Testeo de la memoria

---

### Post by atatiducken on 2008-05-29
Pone **default 4**, ese menu funciona asi:

**Ubuntu 7.10, kernel 2.6.22-14**  ..............................  default 0
**Ubuntu 7.10, kernel 2.6.22-14 Recovery mode**..............  default 1
**Memtest** ..........................................................  default 2
**Otros sistemas operativos** ....................................  default 3
**Windows** .........................................................  default 4

---

### Post by h9005 on 2008-05-29
Ok gracias ya lo estoy probando.

---

