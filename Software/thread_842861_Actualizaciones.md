---
title: "Actualizaciones"
date: 2008-06-27
forum: Software
---

### Post by vk-cdg on 2008-06-27
Hoy me bajó por tercera vez el hernel 2.6.24-19. Soy el único al que le pasa o a alguien mas le bajó mas de una vez?

No me molesta demasiado que me lo distribuya otra vez, salvo que no entiendo por que pasa. Además de eso, me rompe el menu.lst, por suerte tengo un backup y lo arreglo desde ahí.

---

### Post by Mister X on 2008-06-27
Pregunta: por que decis que te rompe el menu.lst?

---

### Post by lega on 2008-06-27
a mi me apareció por segunda vez hoy...en la notebook, en la pc de escritorio tengo configurado otro servidor y todavía no apareció, igual me pregunto que será, son correcciones o es el mismo kernel que estamos bajando de nuevo?

---

### Post by Hei Ku on 2008-06-27
No sera que modificaste el menu.lst a mano, y sin correr el sudo update-grub?
Si no, la actualizacion del kernel deberia volver a generar el menu sin problemas.

---

### Post by faktorqm on 2008-06-27
ja! a mi tambien me rompio el menu.lst, encima le habia hecho caso a hei ku y no lo habia tocado... pero habia instalado el grub grafico y parece que no le gusto ni un poquito.... todo mal con eso. encima ahora me tira un error que me traba el arranque... tengo que apretar espacio por que me dice que elegi mal la resolucion de no se que cosa.... a mi me parece la verdad que no estan pensando mucho en los usuarios "no expertos" por que actualizan tanto y se rompe tanto todo que claro, no da ganas de ponerte a ver eso cuando tenes que trabajar digamos... pero bueno. Salu2!

---

### Post by vk-cdg on 2008-06-28
> **Hei Ku said:**
> No sera que modificaste el menu.lst a mano, y sin correr el sudo update-grub?
Si no, la actualizacion del kernel deberia volver a generar el menu sin problemas.

Si, lo toqué a mano ya que primero instalé ubuntu y luego en el otro disco (desconectando el de ubuntu) instalé XP. Terminado eso conecté ambos y agregué las últimas lineas para que me tirara la opción de arrancar con el otro SO. La cosa es que cada vez que actualiza el kernel me quita las opciones de arranque con Windows. No es demasiado complicado ya que las vuelvo a menter y listo, pero me hincha un poco las guindas.

Este es mi menu.lst

```
gfxmenu /boot/grub/message.blusplash

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
timeout		15

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
# kopt=root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=quiet splash vga=775

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
boot

title		Ubuntu 8.04.1, kernel memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
quiet

title		Otros sistemas operativos:
root

title		Windows XP Professional SP3
root		(hd1,0)
#makeactive
#chainloader	+1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader 	+1 
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Mauro22 on 2008-06-28
Por aca lo mismo. 

La version 19 dos veces!!


Que bronca cuando tenes el menu.lst impecable jejej

:lolflag:

---

### Post by Hei Ku on 2008-06-28
el tema es que lo tienen que actualizar bien.

una vez que lo tocan, de la manera correcta, corren sudo update-grub
con eso, cuando se actualicen los cambios no van a tener problemas. Si no saben como tocarlo, utilicen los programas graficos que vienen para eso, como startup-manager o qgrubeditor.

---

### Post by vk-cdg on 2008-06-30
En general usaba el StartUp-Manager, pero cada vez que lo corro me reemplaza el nombre de cada entrada de "Ubuntu 8.04" a "Debian Linux no se que" y queda ESPANTOSO.
A partir de ahí empecé a editarlo a mano.

---

### Post by Hei Ku on 2008-06-30
entonces despues de editarlo corre sudo update-grub
si te elimina los cambios, es que lo editaste mal. :D

Es el mismo comando que corre la actualizacion de kernel, asi que si funciona ese, vas a estar tranquilo.

---

