---
title: "Problemas con el Grub"
date: 2008-12-20
forum: Software
---

### Post by losoollenos on 2008-12-20
Hola que tal, buenas tardes a tod@s.
Bueno el problema surgió al reinstalar windows obvio, desapareció el Grub, tengo w2000, Ubuntu y Kubuntu. Lo que pasó es que como tenía preparada una tercer partición decidí instalar Kubuntu y pensé que se iba a solucionar el problema al instalarse el grub.
Pero no se que pasó que sólo me aparece w y Kubuntu al inicio....
probé con Supergrub y sólo consigo alternar Ubuntu y Kubuntu en el grub, (no que me salgan las dos opciones juntas), para colmo en un momento inicio con Kubuntu y en la parte de configuración del sistema que hay algo de "administrador de volúmenes" le puse habilitar en el inicio la partición donde está Ubuntu pensando que se agregaría al grub, pero no.....
Ahora Kubuntu me da un error al iniciar (cuando corre la barrita azul) y Ubuntu arranca pero lo veo lento y consumiendo más recursos de lo habitual.
Necesitaría que me ayuden a deshabilitar esa partición en el inicio y lograr que aparezcan todos los sistemas en el grub, puedo hacer cosas desde Ubuntu, live-cd o supergrub.

Muchísimas gracias y saludos

---

### Post by sajnox on 2008-12-20
Si, se puede arreglar facil

Por favor postea la salida de los siguientes comandos y te pasamos como arreglarlo. Esto tenes que hacerlo desde el sistema que hayas instalado ultimo, ya sea ubuntu o kubuntu

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by losoollenos on 2008-12-21
Gracias por ayudarme sajnox.

Lo que me pediste:

ubuntu@ubuntu-desktop:~$ sudo fdisk -l
[sudo] password for ubuntu: 

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x19f1370d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306       52773   413416710    7  HPFS/NTFS
/dev/sda3           52774       60801    64484897    5  Extendida
/dev/sda5           52774       56689    31454208   83  Linux
/dev/sda6           56690       60605    31455238+  83  Linux
/dev/sda7           60606       60801     1574338+  82  Linux swap / Solaris
ubuntu@ubuntu-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=b918a1ee-177b-4104-bd5b-25dd06217cc9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b918a1ee-177b-4104-bd5b-25dd06217cc9

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		b918a1ee-177b-4104-bd5b-25dd06217cc9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b918a1ee-177b-4104-bd5b-25dd06217cc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b918a1ee-177b-4104-bd5b-25dd06217cc9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b918a1ee-177b-4104-bd5b-25dd06217cc9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		b918a1ee-177b-4104-bd5b-25dd06217cc9
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

ubuntu@ubuntu-desktop:~$ 

Del vista es un intento de instalación que me quedó en el inicio, aparece en el grub pero carga el 2000.

Gracias y saludos

---

### Post by losoollenos on 2008-12-22
Por favor, si alguien puede seguirla......muy agradecido !!!!

Saludos

---

### Post by Hei Ku on 2008-12-22
Cual es el Ubuntu y cuál el Kubuntu?

Estas pueden ser, pero para seguir necesitamos saber qué partición corresponde a qué.
```

/dev/sda5 52774 56689 31454208 83 Linux
/dev/sda6 56690 60605 31455238+ 83 Linux

```

---

### Post by losoollenos on 2008-12-22
/dev/sda5 52774 56689 31454208 83 Linux--------Kubuntu 8.04
/dev/sda6 56690 60605 31455238+ 83 Linux-------Ubuntu  8.10

Muchas gracias

---

### Post by losoollenos on 2008-12-24
Hola, me parece que no entendí, tengo que hacer algo?, les recuerdo que soy novato.....

Gracias y muy felices fiestas !!!!!

---

### Post by Hei Ku on 2008-12-24
Proba agregarle esta entrada:

```


title Kubuntu 8.10, kernel 2.6.27-9-generic
/dev/sda5
kernel /boot/vmlinuz-2.6.27-9-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet


```

la version de kernel va a depender de lo que tenías en Kubuntu. Esperemos que sea la misma que en Ubuntu.

---

