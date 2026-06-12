---
title: "Problema con menú de grub y triple booteo"
date: 2009-04-21
forum: Software
---

### Post by Skavenger on 2009-04-21
El tema es así: instalé XP, luego Win 7 para ver qué onda y al final Ubuntu, el grub me tomó todos los SO y hasta ahí todo bien. En que en el menú de booteo me lista lo siguiente:

```
Ubuntu 8.10
Ubuntu 8.10 (recovery mode)
Ubuntu 8.10 (memtest)
=Other operating systems=
Win Vista/Loghorn (loader)
```

En lugar de listar XP y Win7 en el menú, los puso a ambos en una especie de sub menú (el loader), entonces acá surge mi problema, yo lo que quiero es **poner XP y Win7 en el menú del grub en lugar de tener que ingresar al loader de Windows**. Prefiero tener todo en un menú en lugar de dos.

Espero se entienda. Cualquier ayuda es bienvenida :D

Gracias!

---

### Post by infernus92 on 2009-04-21
no cero que sea un problema del grub esto... me parece que es como win$ te lo reconocio... grub reconoce el arranque de ubuntu y ademas el de window$...grub dice que arranque win$... pero en vez de arrancar directamente como si tuvieras 1 solo... el propio win$ te genera un menu de arranque totalmente ajeno a grub... dentro del arranque de win$ te aparece la opcion de elegir con cual de los 2 queres iniciar
no se si se va a poder cambiar eso... pero tmpoco tengo demasiada experiencia en tener 2 win$... con tener q tener 1 ya es mucho :P

Saludos

---

### Post by Skavenger on 2009-04-21
Sí, en realidad es un problema mío, no del grub =P

---

### Post by infernus92 on 2009-04-21
entonces no se si te lo van a poder solucionar... aca los que saben, engeneral saben de linux, en especial de ubuntu... eso ya es cosa de win$... si a alguno le paso eso y lo quiso y pudo solucionar.. seguro que te va a ayudar...
no es mi caso asi que yo me despido

Saludos

---

### Post by pablo.s on 2009-04-21
Copia y pegá en un mensaje nuevo
lo que aparece en /boot/grub/menu.lst

---

### Post by Skavenger on 2009-04-23
Nunca me llegó el aviso de la suscripción por email...

> **pablo.s said:**
> Copia y pegá en un mensaje nuevo
lo que aparece en /boot/grub/menu.lst

Lo posteo completo:

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
default		4

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
# kopt=root=UUID=de0125bc-7445-48d3-8d9a-9c8083331ee2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de0125bc-7445-48d3-8d9a-9c8083331ee2

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		de0125bc-7445-48d3-8d9a-9c8083331ee2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=de0125bc-7445-48d3-8d9a-9c8083331ee2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		de0125bc-7445-48d3-8d9a-9c8083331ee2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=de0125bc-7445-48d3-8d9a-9c8083331ee2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		de0125bc-7445-48d3-8d9a-9c8083331ee2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by pablo.s on 2009-04-23
Te coloco lo que tenès que agregarle
para que arranque Windows 7. Conste
que lo hago solo para que uses Ubuntu,
de ninguna forma para que uses Windows.

Fijate que no pongo todo el menu.lst
pero supongo que te daràs cuenta que parte
tenès que copiar y pegar:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

title          Windows Siete
root           (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by Skavenger on 2009-04-27
Gracias, pero no funcionó. Si entro a Win7 me tira un error:

```
Error 12: invalid device requested
```

Si entro al de XP carga nuevamente el loader. Me parece que la cosa pasa por modificar el loader de Windows en lugar de editar el grub, aunque no conozco mucho así que puede que esté equivocado.

---

### Post by pablo.s on 2009-04-27
Ok, te digo que lo armé pensando en
la lógica común de los cargadores, pero
desconozco la mecánica de los cargadores
de arranque de Vista y Seven.

---

### Post by Skavenger on 2009-04-27
> **pablo.s said:**
> Ok, te digo que lo armé pensando en
la lógica común de los cargadores, pero
desconozco la mecánica de los cargadores
de arranque de Vista y Seven.

Sí, entiendo. Por eso dije que talvez el tema pasa por modificar el loader de Windows. Voy a seguir buscando, si encuentro algo posteo por si a alguien más le hace falta.

Edit: acá se explica cómo se edita el loader de Windows para hacer lo que necesito: [http://www.ditii.com/2009/01/28/how-to-modify-windows-7-boot-loader/](http://www.ditii.com/2009/01/28/how-to-modify-windows-7-boot-loader/)

---

