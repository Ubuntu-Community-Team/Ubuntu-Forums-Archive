---
title: "pequeña &quot;irregularidad&quot; con GRUB"
date: 2009-04-29
forum: Software
---

### Post by francoarza on 2009-04-29
soy bastante novato con ubuntu (con linux en general) y hace poco instale el StartUp Manager para "optimizar" el arranque de ubuntu, luego de no encontrar ninguna opcion significativa desistale ese programa y apague la pc, al otro dia, la prendi normalmente pero me econtre con una ventana que nunca antes habia visto (el menu del GRUB donde pregunta con que kernel iniciar) el problema es que quiero hacer que se cargue automaticamente como era antes, pero no encuentro la forma, desinstale el StartUp Manager, lei el menu.lst para ver si habia algo "modificable" pero no me anime a meterle mano. 

P.S.: tambien noto que GNOME tarda incluso mas en arrancar que antes quedando la pantalla negra por severos segundos. 

otra modificacion que hice fue agregar "profile" al final de la linea del kernel que hay que editar. pero no encuentro solucion a mi problema, ni mejorias en el arranque del sistema.

desde ya muchas gracias :)

---

### Post by francoarza on 2009-04-29
por cierto, uso Ubuntu 9.04

---

### Post by sajnox on 2009-04-29
Reinstala el Startupmanager y quita la opcion del tiempo de espera

Saludos

---

### Post by francoarza on 2009-04-29
hice eso, pero nada.. sigue igual, ademas desde ahora tarda muchisimo en cargar GNOME no se si tiene algo que ver.. pero simultaneamente tengo los dos inconvenientes..

muchas gracias por tu respuesta sajnox! pero sigo igual :(

---

### Post by josecuervo86 on 2009-04-29
Podrias postear el menu.lst del grub?

---

### Post by pablo.s on 2009-04-30
Cuervo a dominar el mundooooooo

---

### Post by francoarza on 2009-04-30
tengo 2, el menu.lst y un backup. el menu.lst:

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		0

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
# kopt=root=UUID=7a111a05-800b-4fd6-89d4-98ebbdefc235 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a111a05-800b-4fd6-89d4-98ebbdefc235 ro quiet 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by francoarza on 2009-04-30
bueno ya lo solucione, encontre un backup que creo el StartUp Manager, ahora uso ese menu.lst y anda joya, pero sigo tardando siglos en arrancar GNOME y me pasa desde q instale el StartUp Manager.. tendra algo q ver?

---

### Post by pablo.s on 2009-04-30
Cuanto es exactamente, siglos?
Diez segundos, veinte, treinta?

Hay algún script que hayas
puesto para arrancar con GNOME?

Estás ejecutando Compiz?

Muchas preguntas...

---

### Post by francoarza on 2009-04-30
demasiadas! jaja 
siglos = 15 segundos.. 20
que yo sepa no hay ningun script
estaba ejecutandolo, pero lo saque para ver si se arreglaba.. pero nadia che

---

### Post by clasificado on 2009-04-30
A mi me ha pasado que despues de haberlo toqueteado tanto quedan cosas rotas que realientizan el encendido, peeeeeeeero no se ve por el splash ese de ubuntu.

cuando se lo saqué desde las opciones de grub (cambié splash por nosplash) vi que el mysql, el apache, el wesnothd, el firestarter y un par mas fallaban por timeout.

una boludez, pero me sirvio mucho para reducir el tiempo del bootup

clasificado

---

### Post by pablo.s on 2009-05-01
> **clasificado said:**
> cuando se lo saqué desde las opciones de grub (cambié splash por nosplash) vi que el mysql, el apache, **[SIZE=4]el wesnothd[/SIZE]**, el firestarter y un par mas fallaban por timeout.

El juego tiene un deamon 
al arranque?????

Oy Vey

---

