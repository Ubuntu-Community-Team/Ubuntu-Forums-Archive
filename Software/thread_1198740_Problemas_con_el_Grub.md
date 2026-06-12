---
title: "Problemas con el Grub"
date: 2009-06-27
forum: Software
---

### Post by losoollenos on 2009-06-27
Hola que tal !!!
Les comento este problemita a ver si me pueden tirar una mano, como siempre.
Bueno tengo nueve paticiones, de izquierda a derecha en el Gparted se ven así:
la 1, 2 y 3 primarias en ntfs; todas después son extendidas, la 4 y 5 en ext3 con "/" y "home" respectivamente de ubuntu 8.04 64 bit; 6, 7 en ext4 y 8 en ext3 con "/", "home" y "boot" en el mísmo orden con Jaunty 64 bit; finalmente la 9 es swap. El problema es que tuve que reinstalar la 8.04 y no se por que no incluyó en el grub a la 9.04, que a propósito le instalé el Boot en la partición con ext3 porque se que el grub de Hardy no la hubiese tomado en ext4. Entonces con el SupergrubDisk (también me tuve que bajar creo que la última versión para que lea ext4) puedo hacer que se agreguen bien todos los sistemas, arrancan todos bien exepto Hardy que queda un rato largo en la barrita marrón que va de un lado a otro hasta que aparece una pantalla tipo consola negra que al final dice algo de Initramfs o algo así. Pero si hago que el supergrub me agregue solo windows y hardy en el grub, ahí arranca perfecto.
Espero que no haya sido demasiado trabalenguas jejej

Bueno muchas gracias y saludos para tod@s

---

### Post by staar on 2009-06-27
con tanto lío de particiones, es preferible modificar el menu.lst a mano, para estar seguros...

posteá el contenido del archivo /boot/grub/menu.lst y la salida de ```
sudo fdisk -l
```

otra cosa, no era más fácil instalar el grub en el jaunty?

saludos

---

### Post by losoollenos on 2009-06-27
Te posteo lo que me pedís, pero si es más fácil instalar el Grub en Jaunty hacemos eso......explicame un poco cómo por favor.

_sudo fdisk -l_

ubuntu@ubuntu-desktop:~$ sudo fdisk -l
[sudo] password for ubuntu: 

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x6d697270

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        3263    15726592    7  HPFS/NTFS
/dev/sda3            3264       56885   430718715    7  HPFS/NTFS
/dev/sda4           56886       60801    31455270    5  Extendida
/dev/sda5           56886       57537     5237158+  83  Linux
/dev/sda6           57538       58712     9438156   83  Linux
/dev/sda7           58713       59365     5245191   83  Linux
/dev/sda8           59366       60475     8916043+  83  Linux
/dev/sda9           60476       60540      522081   83  Linux
/dev/sda10          60541       60801     2096451   82  Linux swap / Solaris
ubuntu@ubuntu-desktop:~$ 

_/boot/grub/menu.lst_

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
# kopt=root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=deb46b11-0b38-4591-99a2-da455f2b06c0

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		deb46b11-0b38-4591-99a2-da455f2b06c0
kernel		/vmlinuz-2.6.28-13-generic root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		deb46b11-0b38-4591-99a2-da455f2b06c0
kernel		/vmlinuz-2.6.28-13-generic root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, memtest86+
uuid		deb46b11-0b38-4591-99a2-da455f2b06c0
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=c3940e9b-8944-4176-91fb-cf14050b1c15 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=c3940e9b-8944-4176-91fb-cf14050b1c15 ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by staar on 2009-06-27
ese menu.lst es de jaunty, si reinstalaste hardy encima, la instalación de este debe haber puesto su grub, el menu.lst que tendrías que postear es el que está en la partición de hardy, por que es el que el sistema está usando...

la sugerencia de instalarlo en jaunty hubiera sido mejor si te la daba antes, ahora mejor dejalo como está...

otra cosa, que no se si estás al tanto, cuando actualizes el kernel de jaunty, vas a tener que modificar el menu.lst (a mano, porque grub está instalado en hardy, y update-grub no funciona, ya que actualiza el grub de jaunty, que no está en la MBR) para que apunte al nuevo kernel, sino la actualización no va a surgir efecto, y vas a bootear siempre con el mismo kernel...

a todo esto, y por curiosidad, porque tenés instaladas las dos versiones?

saludos

---

### Post by losoollenos on 2009-06-28
El de Hardy:

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
# kopt=root=UUID=4777c29c-3678-45f6-85c9-a1b9c54af7ef ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4777c29c-3678-45f6-85c9-a1b9c54af7ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4777c29c-3678-45f6-85c9-a1b9c54af7ef ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,6)
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


Con respecto a la cuestión del kernel entiendo más o menos lo que decís, por eso te insisto si no será mejor si es que se puede instalar el grub de Jaunty......no lo puede hacer el SuperGrubDisk?, porque cuando se actualizan los kernel siempre elimino el anterior, que va a pasar?, aparte no se cómo se modifica el menu.lst, salvo que ahora me quede claro.....

Con las dos versiones te referís a Hardy y Jaunty no?, bueno Hardy me funciona mejor en general y sobre todo en las páginas que usan Flash, juegos, etc (ya postié acá sobre lo lento que me anda Jaunty en los juegos....). Y Jaunty porque me toma bien la Webcam (0ac8:307b Z-Star Microelectronics Corp.) y puedo usar mejor aMSN y Skype, después no le veo grandes ventajas, si pudiera hacer andar la camarita en Hardy que en teoría está soportada, me quedaría con este, por lo menos hasta que se resuelva el tema del flash en Jaunty.

Un abrazo che, gracias !!!

---

### Post by staar on 2009-06-28
mirá, cuando se actualiza el kernel, se tienen que modificar dos líneas del menu.lst para poder accederlo, por ejemplo si se actualiza el kernel de la versión 2.6.28-13 a la versión 2.6.28-14 (en cada release de ubuntu se utiliza siempre la misma versión del kernel, las actualizaciones son en realidad revisiones, por eso cambian solo los dos últimos números), tendrías que modificar el menu.lst, de esto ```

title Ubuntu 9.04, kernel 2.6.28-**13**-generic
uuid deb46b11-0b38-4591-99a2-da455f2b06c0
kernel /vmlinuz-2.6.28-**13**-generic root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro quiet splash 
initrd /initrd.img-2.6.28-**13**-generic
quiet
``` a esto ```

title Ubuntu 9.04, kernel 2.6.28-**14**-generic
uuid deb46b11-0b38-4591-99a2-da455f2b06c0
kernel /vmlinuz-2.6.28-**14**-generic root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro quiet splash 
initrd /initrd.img-2.6.28-**14**-generic
quiet
``` y lo mismo en la entrada de recovery...


para el tema de arrancar jaunty desde el grub de hardy, solo tendrías que copiar las entradas para JJ del menu.lst de este, al menu.lst de HH, asi ```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4777c29c-3678-45f6-85c9-a1b9c54af7ef ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04.2, kernel 2.6.24-24-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=4777c29c-3678-45f6-85c9-a1b9c54af7ef ro quiet splash
initrd /boot/initrd.img-2.6.24-24-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=4777c29c-3678-45f6-85c9-a1b9c54af7ef ro single
initrd /boot/initrd.img-2.6.24-24-generic

title Ubuntu 8.04.2, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

## Ubuntu Jaunty

[B]title Ubuntu 9.04, kernel 2.6.28-13-generic
uuid deb46b11-0b38-4591-99a2-da455f2b06c0
kernel /vmlinuz-2.6.28-13-generic root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro quiet splash 
initrd /initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid deb46b11-0b38-4591-99a2-da455f2b06c0
kernel /vmlinuz-2.6.28-13-generic root=UUID=1d9bea4e-9808-4ad8-8a18-908219d65a61 ro single
initrd /initrd.img-2.6.28-13-generic

title Ubuntu 9.04, memtest86+
uuid deb46b11-0b38-4591-99a2-da455f2b06c0
kernel /memtest86+.bin
quiet[/B]


# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
``` el SuperGrubDisk es más una herramienta de rescate, que otra cosa, y al ser un programa que debe abarcar muchisimas posibles configuraciones distintas, puede fallar, mejor aprendé a hacerlo a mano, para minimizar los riesgos, y, en caso de falla, tengas conocimientos como para arreglarlo...

es muy raro lo que decís de flash, en teoría tendría que andar mejor en jaunty, pero me parece que podría venir por el lado de los problemas de JJ con algunas placas de video...

saludos

---

### Post by losoollenos on 2009-06-28
Ahora aparece en el grub pero no arranca JJ, sale error 15 file not found.
Es extraño también el orden, o sea, siempre me quedan una opción de Ubuntu arriba, windows al medio y el otro ubuntu abajo. Ahora quedó arriba HH, seguido abajo JJ y después abajo de todo windows.
Te lo comento por si tiene que ver.....
Che y no puedo hacer al revés, poner HH en el grub de JJ?

---

### Post by losoollenos on 2009-06-28
Ya está !!!
Probé e copiar el boot de hh en el de jj y arrancan todos.
Lo del orden dependía de dónde lo copiaba en el menu.lst.

Bueno te re agradezco tu ayuda, me sacaron del pozo una vez más !!!

Un abrazo y hasta pronto !!!

---

