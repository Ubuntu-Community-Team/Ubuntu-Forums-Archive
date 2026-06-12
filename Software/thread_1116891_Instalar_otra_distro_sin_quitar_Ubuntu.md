---
title: "Instalar otra distro sin quitar Ubuntu"
date: 2009-04-05
forum: Software
---

### Post by guidito73 on 2009-04-05
Bueno gente, ya me libré de Windows, ahora quiero darle la chance a algunas distros que estuve viendo. Por lo pronto voy a ver qué onda Fedora.

La cuestión es la siguiente, imagino que puedo hacer una partición para el root y dejar el /home compartido entre las distros no?

En tal caso, sería cuestión de usar Gparted para armar la partición nueva, instalar ahí y ya quedaría en el GRUB todo bien, etc?

Gracias.

PD: La prioridad es compartir el /home.

---

### Post by josecuervo86 on 2009-04-05
Te doy otra alternativa, que es la que uso yo: emulalas con virtualbox, te evitas la tarea de particionar el disco, pero no obtenes el mismo rendimiento que corriendolo desde el disco. Pero para probar esta muy bueno

---

### Post by alberto71 on 2009-04-05
Hola. Estoy haciendo lo que querés hacer pero en una VM. Es decir, tengo Ubuntu como distro principal y le instalo otra en la misma pc virtual, reservándome la posibilidad de arrancar cualquiera de las instaladas al iniciar.

En Fedora o en cualquier distro, la instalación será como siempre, lógicamente, deberás usar la herramienta de partición de la distro para hacerle un lugar para el root (/) y (si querés), el /home; lo bueno es que podés compartir la partición de swap entre todas las distros.

Según entiendo, la única salvedad en el proceso de instalación sería **no dejar que te "pise" el grub**. En Ubuntu, cuando instalás, justo en la última pantalla antes de comenzar tenés un botón, **Avanzado**, donde podés deshabilitar la escritura de Grub en el disco rígido. No instalé Fedora (alguna vez bajaré el dvd y me sacaré las ganas), pero supongo que tendrá una posiblidad similar.

Todo esto, sirve también por si querés hacerlo en el "mundo real".

Si querés algo más profundo sobre el tema, no sé si rompo las reglas del foro (si es así pido a los mods editen el post), pero te dejo un par enlaces (externos):

* [1 solo Grub para todos tus Linux]("http://www.forat.info/2009/02/28/un-solo-grub-para-todos-tus-linux/")

* [Como instalar 145 Sistemas operativos en 1 pc]("http://www.justlinux.com/forum/showthread.php?threadid=147959")

El segundo art. está en inglés pero si te das maña, se puede entender que hizo el loco ese ;)

Espero que te sirva.
Saludos.

---

### Post by Air23 on 2009-04-05
No hay problema en compartir tu home pero usa nombres de usuario distintos en las 2 distros (algo muy similar se discutio aca: [http://ubuntuforums.org/showthread.php?t=801714](http://ubuntuforums.org/showthread.php?t=801714))

---

### Post by hictio on 2009-04-05
Tenes mucha data?
No podrias copiar a un externo/ DVD o similar la data que queres guardar?
Asi podes instalar y re-instalar cuantas veces quieras todas las distros que quieras hasta que encuentres la que te gusta, y ahi copias la data de vuelta al rigido?

Ademas, te vendria bien tener backups fuera de la propia maquina, por si las moscas :)

---

### Post by guidito73 on 2009-04-05
Muchas gracias a todos.

En cuanto a lo de virtualizar, cuento con 256 MB de RAM unicamente, asi que me temo que no va a ser posible.

Estuve leyendo los links que dejaron, son de mucha utilidad, aunque se ve un poco difícil y con chances de cagar el GRUB, jajaja.

Ya voy a ver cómo me va y les aviso.

Sigan posteando cualquier cosa, así tengo más guías.

EDIT: Tengo hecho un backup, pero como la PC la usa mi novia no quiero andar dejandola sin música por días enteros. Saben cómo es esto ;)

---

### Post by alberto71 on 2009-04-05
Hola.

Te dejo lo que tengo yo, por si te ayuda a decidirte. El grub de mi pc virtual cuando inicio queda así: [Ver Grub]("http://img87.imageshack.us/my.php?image=grub.png")

Y este es el menu.lst (que se encuentra en /boot/grub), que contiene toda la data. Lo que modifiques en este archivo define si tus distros, inician o no. Verás que no es muy difícil de entender ciertas cosas, inclusive para un papafrita como yo, que de Linux no sabe casi nada :lolflag:

A continuación te dejo entonces el contenido de menu.lst, donde lo jugoso lo encontrás cerca del final del archivo, después de **## ## End Default Options ##**

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color white/brown black/light-gray

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
# kopt=root=UUID=559f7cf3-4432-4a76-a5d0-3ceecf5156ec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=559f7cf3-4432-4a76-a5d0-3ceecf5156ec

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
# howmany=2

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		559f7cf3-4432-4a76-a5d0-3ceecf5156ec
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=559f7cf3-4432-4a76-a5d0-3ceecf5156ec ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		#! CRUNCHBANG LINUX (8.10)
uuid		616b88e9-a302-4e9b-ad69-7a6b05b87826
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=616b88e9-a302-4e9b-ad69-7a6b05b87826 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Parsix GNU/Linux 2.0
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/sdb1 ro ramdisk_size=100000 apm=power-off nomce quiet vga=791 resume=swap:/dev/sda2 
initrd		/boot/initrd.img

### END DEBIAN AUTOMAGIC KERNELS LIST

title 	SliTaz GNU/Linux (cooking)
		root (hd0,4)
		kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/hda5

title  Arch Linux 2009.2
		root   (hd0,5)
		kernel /boot/vmlinuz26 root=/dev/sda6 ro
		initrd /boot/kernel26.img
```

Con ésta forma de trabajo, todo lo que necesitás es hacer un backup de menu.lst para usar si después de instalar Fedora y hacer los cambios, tenés problemas. De ese modo, siempre podrás iniciar Ubuntu ;)

Saludos.

---

### Post by guidito73 on 2009-04-05
Ahhhh es buena esa. Es decir, si tuviera problemas, simplemente levanto el menu.lst de antes y el GRUB me quedaría tal cual lo tengo ahora. Es así?

Voy a seguir viendo porque la verdad que no me quiero arriesgar a unas puteadas de la doña :P

---

### Post by alberto71 on 2009-04-07
Exacto!

Solo tenés que asegurarte que la instalación de la nueva distro no te pise el grub pero aún en ese caso, con la copia del menu.lst, solo necesitás iniciar con un LiveCd y sobreescribir el nuevo con el tuyo.

Exitos!

---

