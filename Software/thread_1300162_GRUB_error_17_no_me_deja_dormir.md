---
title: "GRUB error 17 no me deja dormir"
date: 2009-10-24
forum: Software
---

### Post by Skavenger on 2009-10-24
Les cuento lo que paso y dejo informacion de mis discos a ver si me pueden dar una mano con esto que me esta volviendo loco. Disculpen la falta de tildes, estoy con LiveCD y no me toma la config del teclado.

Estaba por viajar y decidi quitar uno de los 3 HD que tengo que es donde guardo musica y peliculas, entre otras cosas. Resulta que cuando la prendo nuevamente luego de sacar el disco, me da el error 17 del grub y no arranca nada. Entonces, como tenia que dejar prendida la PC, necesitaba una solucion rapida asi que reinstale el MBR de XP para poder ingresar al sistema. Hasta ahi todo bien, pero cuando quise reinstalar grub nada funciono. Probe mil cosas y sigo recibiendo ese maldito error.


**El error en cuestion y lo que veo en pantalla cuando arranca la PC**

```
GRUB loading stage 1.5
GRUB loading, please wait
Error 17
```


**Tengo los discos organizados de la siguiente manera en el BIOS, son 3 en total**

```
--HD1 SATA
------ XP
------ Win7
------ Particion con archivos

--HD2 IDE (solo para Ubuntu)
------ Particion root /
------ Particion /home
------ Swap

--HD3 SATA
------ Unica particion con archivos
```


Lo primero que probe fue reinstalar GRUB...

```
ubuntu@ubuntu:~$ sudo grub

grub> find /boot/grub/stage1
 (hd2,0)

grub> root (hd2,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
```

...pero no funciono.


Baje Super Grub Disk y toque las mil y una opciones que tiene para reparar, pero nada... sigo recibiendo el error 17.

Me fui al otro extremo y pense 'bueno, si reinstalo Ubuntu tal vez pueda solucionarlo', pero no, luego de reinstalar el SO sigo recibiendo el mismo error!


**Informacion de los discos**

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x009a009a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       60800   456920730    f  W95 Ext'd (LBA)
/dev/sda5            3917        9138    41945683+   7  HPFS/NTFS
/dev/sda6            9139       60800   414974983+   7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdded9f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182401  1465136001    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb08ba66e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9730    78150743+  ee  GPT
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ clear

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x009a009a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       60800   456920730    f  W95 Ext'd (LBA)
/dev/sda5            3917        9138    41945683+   7  HPFS/NTFS
/dev/sda6            9139       60800   414974983+   7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdded9f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182401  1465136001    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb08ba66e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9730    78150743+  ee  GPT
```


**menu.lst**

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=a86504f9-2d76-4ffd-9262-abbc6f9a30b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a86504f9-2d76-4ffd-9262-abbc6f9a30b1

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a86504f9-2d76-4ffd-9262-abbc6f9a30b1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a86504f9-2d76-4ffd-9262-abbc6f9a30b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a86504f9-2d76-4ffd-9262-abbc6f9a30b1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a86504f9-2d76-4ffd-9262-abbc6f9a30b1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a86504f9-2d76-4ffd-9262-abbc6f9a30b1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

En fin, creo que son todos los datos que en general se piden, no? Cualquier cosa me avisan, y muchas gracias de antemano!

---

### Post by gmunioz on 2009-10-24
Hola ska...:

¿Dónde está Ubuntu?

Aqui NO:

Disk /dev/sda: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       60800   456920730    f  W95 Ext'd (LBA)
/dev/sda5            3917        9138    41945683+   7  HPFS/NTFS
/dev/sda6            9139       60800   414974983+   7  HPFS/NTFS

Aqui tampoco:

Disk /dev/sdb: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182401  1465136001    7  HPFS/NTFS


Y aqui tampoco:

Disk /dev/sdc: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9730    78150743+  ee  GPT

---

### Post by Skavenger on 2009-10-24
Mira, realmente no entiendo lo que dice la info q tira el fdisk -l, pero al Ubuntu lo instalé en este:

```
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
```

Muchas gracias por responder.

---

### Post by gmunioz on 2009-10-24
Hola ska...:

Pues no esta.

algo pasó con el disco y asi te lo

informan fdisk y el Grub.

error 17, la partición esta pero es desconocida.

---

### Post by Skavenger on 2009-10-24
Qué cosa rara... entonces voy a formatearla totalmente y reinstalaré de nuevo Ubuntu, a ver si así se soluciona el problema. Pregunto ya que estamos, ¿es preferible ext3 o ext4 para las particiones?

---

### Post by staar on 2009-10-24
si ese es el orden de los discos en el BIOS, te equivocaste al reinstalar grub, tendrías que haber puesto *root (hd1,0)*, porque grub empieza a contar desde cero, y toma el orden desde el BIOS...

lo que no entiendo es porqué ese disco con ubuntu tiene una GPT, si decís que la pc tiene BIOS y no EFI...

saludos

---

### Post by gmunioz on 2009-10-24
Hola ska.....:

Te sugiero ext4.

Además si vas a sacar y poner

discos, seria conveniente para 

evitar problemas, que crees una

partición ext3 de unos 384 megas

en /dev/sda y la montes como /boot

---

### Post by Skavenger on 2009-10-25
> **gmunioz said:**
> Hola ska.....:

Te sugiero ext4.

Además si vas a sacar y poner

discos, seria conveniente para 

evitar problemas, que crees una

partición ext3 de unos 384 megas

en /dev/sda y la montes como /boot

Perfecto, entonces tendría que quedar así, ¿no?

```
--HD1 SATA
------ Partición /boot (ext3)
------ XP
------ Win7
------ Partición con archivos

--HD2 IDE (solo para Ubuntu)
------ Partición root / (ext4)
------ Partición /home (ext4)
------ Swap

--HD3 SATA
------ Única partición con archivos
```

Y al finalizar la config de instalación he visto que da la opción de cambiar el lugar de instalación del GRUB, en este caso, al tener esa nueva partición /boot, debería instalarlo ahí, ¿no?
Disculpen que pregunte tanto, pero no entiendo mucho. Gracias.

---

### Post by Skavenger on 2009-10-25
> **staar said:**
> si ese es el orden de los discos en el BIOS, te equivocaste al reinstalar grub, tendrías que haber puesto *root (hd1,0)*, porque grub empieza a contar desde cero, y toma el orden desde el BIOS...
Pero si le pongo (1,0) me da error (ya lo habia probado)

```
grub> root (hd1,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition
```
Formatee nuevamente, cree una vez las las particiones, pero el error sigue u.u


Asi estan mis discos ahora

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x009a009a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       60800   456920730    f  W95 Ext'd (LBA)
/dev/sda5            3917        9138    41945683+   7  HPFS/NTFS
/dev/sda6            9139       60800   414974983+   7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdded9f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a5fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3735    30001356   83  Linux
/dev/sdc2            3736        9480    46146712+  83  Linux
/dev/sdc3            9481        9729     2000092+  82  Linux swap / Solaris
```No hice lo de la particion /boot que me sugirio gmunioz porque todavia no quiero experimentar mucho con las particiones porque creo que voy a dejar un solo Windows, pero mientras tanto quiero poder instalar esto, aunque nada funciona...

---

### Post by Skavenger on 2009-11-01
Bueno... ya puedo dormir en paz (?)

Formateé el disco con Linux y le puse la última versión (Karmic) y hasta ahora funciona todo bien y arrancan los dos SO. Así es como dejé los discos:

```
--HD1 IDE (solo para Ubuntu)
------ Particion /boot
------ Particion root /
------ Particion /home
------ Swap

--HD2 SATA
------ Win7
------ Particion con archivos

--HD3 SATA
------ Unica particion con archivos
```

btw...
>  Last edited by guillermolisi; 6 Days Ago at 10:52 PM.. Reason: inapropriate language  
¿tan *inapropiado* fue para que me editen?...

---

