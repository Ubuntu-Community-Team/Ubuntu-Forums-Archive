---
title: "[SOLVED] eliminar algunas opciones de GRUB"
date: 2009-08-19
forum: Software
---

### Post by drazhe on 2009-08-19
Hay alguna manera sencilla y practica de que un usuario totalmente ignorante en el asunto, pueda eliminar algunas opciones que da a elegir el selector GRUB?

pregunto esto porque con las distintas actualizacion del kernel en ubuntu, ahora me aparecen com 6 ubuntus con diferencias minimas en los decimales del kernel y ya es como medio larga la lista...

---

### Post by josecuervo86 on 2009-08-19
Podes modificarlo desde /boot/grub/menu.lst. Necesitas permisos de root para eso, pero es bastante sencillo, aunque por las dudas te conviene hacer un back-up del archivo por si se pudre todo. De última, postea aca el contenido y te ayudamos ;)

---

### Post by infernus92 on 2009-08-19
mas facil es bajar desde synaptic, apt-get o aptitude como tengas ganas, el startup-manager
este programita es una interfaz grafica muy simple y agradable para configurar opciones como de GRUB y de usplash...
una vez instalado aparece en administracion como "Administrador de Arranque"
espero que te sirva

Saludos

---

### Post by drazhe on 2009-08-20
> **infernus92 said:**
> mas facil es bajar desde synaptic, apt-get o aptitude como tengas ganas, el startup-manager
este programita es una interfaz grafica muy simple y agradable para configurar opciones como de GRUB y de usplash...
una vez instalado aparece en administracion como "Administrador de Arranque"
espero que te sirva

Saludos

tengo el startup manager instalado, pero no me da la opcion de eliminar, sino de setear cual SO arranca por default... no me molesta y ademas uso mas ubuntu que otros SOs, pero me molesta tener 6 ubuntus con diferencias minimas en el kernel, ademas de que utilizo solo la ultima version siempre... va,siempre que ande bien.. jejeje

---

### Post by drazhe on 2009-08-20
aca pongo el contenido de mi archivo menu.lst para ver si me pueden ayudar...la opcion que esta marcada en negrita es la unica que me gustaria que apareciera de todos los ubuntus...
disculpen las caritas felices, se ve que la combinacion de simbolitos crea esas caritas... pero supongo que ustedes sabran mejor que yo que ahi va un ( un 8 y otro ) (todo junto obviamente)




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
# kopt=root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1

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

[B]title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet[/B]

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by josecuervo86 on 2009-08-20
Utilizas la que esta en verde no? Borra todo lo que esta en rojo y listo. Igual hace back-up del archivo antes



## ## End Default Options ##

[color="green"]title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro single
initrd /boot/initrd.img-2.6.28-15-generic[/color]

[COLOR="Red"]title Ubuntu 9.04, kernel 2.6.28-14-generic
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro single
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1 ro single
initrd /boot/initrd.img-2.6.28-11-generic[/color]

title Ubuntu 9.04, memtest86+
uuid c3978ff8-0b67-4ed0-b8cb-c2c9eb01a4c1
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Cajuma on 2009-08-20
Fijate bien que en el startup manager hay una opcion para poner la cantidad de Kernels que queres en el menu, a mi me paso lo mismo y lo solucione de esa manera.
Saludos.

---

### Post by drazhe on 2009-08-20
> **Cajuma said:**
> Fijate bien que en el startup manager hay una opcion para poner la cantidad de Kernels que queres en el menu, a mi me paso lo mismo y lo solucione de esa manera.
Saludos.

Tenias razon... con el startupmanager se me ocurre que es mas sencillo, consegui que solo me apareciera la ultima version del kernel con su respectivo recovery mode y el +86 no se que cuernos y el otro So nada mas.. 
muchas gracias!

---

### Post by Cajuma on 2009-08-20
De nada......:lolflag:
Pd.: Poné solved.

---

### Post by infernus92 on 2009-08-21
justo venia a decir lo q dijo Cajuma... jaja
pero te digo q por si las dudas deja 2 kernels... la otra vez con el kernel nuevo me andaba mal y tuve que iniciar con uno viejo para solucionar el problema...
tomalo como consejo...

Saludos

---

