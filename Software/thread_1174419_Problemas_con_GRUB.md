---
title: "Problemas con GRUB"
date: 2009-05-30
forum: Software
---

### Post by RENGOdeDIA on 2009-05-30
Hola a todos, instalé ubuntu con la distribución de particiones que me recomendaron en otro post y la verdad que me gusta mucho JJ, pero tuve el siguiente problema con grub:
Tengo dos discos IDE, en el 1ro tengo win en una sola partición fat32, en el 2do tengo ubuntu en ext3 y otra partición ntfs con archivos personales. Instale GRUB en el disco con ubuntu.
Ahora bien, cuando booteo desde el 2do disco arranca el grub perfecto y me muestra para elegir entre ubuntu y win; si elijo ubuntu arranca este sin problemas, pero si elijo win me sale

```
Error 13: Invalidad or unsupported executable format
```

apretando cualquier tecla vuelvo a grub sin problemas.
Aclaro que si desde la bios booteo del 1er disco xp arranca normal.
posteo el menu-lst y el fdisk

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

timeout		5



## hiddenmenu

# Hides the menu by default (press ESC to see the menu)

#hiddenmenu



# Pretty colours

color cyan/blue white/blue



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

# kopt=root=UUID=bfebc153-95c0-4e83-9a1b-2299879e9f1e ro



## default grub root device

## e.g. groot=(hd0,0)

# groot=bfebc153-95c0-4e83-9a1b-2299879e9f1e



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

uuid		bfebc153-95c0-4e83-9a1b-2299879e9f1e

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bfebc153-95c0-4e83-9a1b-2299879e9f1e ro quiet splash 

initrd		/boot/initrd.img-2.6.28-11-generic

quiet



title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

uuid		bfebc153-95c0-4e83-9a1b-2299879e9f1e

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bfebc153-95c0-4e83-9a1b-2299879e9f1e ro  single

initrd		/boot/initrd.img-2.6.28-11-generic



title		Ubuntu 9.04, memtest86+

uuid		bfebc153-95c0-4e83-9a1b-2299879e9f1e

kernel		/boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Windows NT/2000/XP (loader)

rootnoverify	(hd0,0)

savedefault

chainloader	+1

```


```
Disco /dev/sda: 41.1 GB, 41174138880 bytes

255 cabezas, 63 sectores/pista, 5005 cilindros

Unidades = cilindros de 16065 * 512 = 8225280 bytes

Identificador de disco: 0x355d355c



Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema

/dev/sda1   *           1        5005    40202631    c  W95 FAT32 (LBA)



Disco /dev/sdb: 82.3 GB, 82348277760 bytes

255 cabezas, 63 sectores/pista, 10011 cilindros

Unidades = cilindros de 16065 * 512 = 8225280 bytes

Identificador de disco: 0xb005b005



Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema

/dev/sdb1   *           1        1982    15920383+  83  Linux

/dev/sdb2            3530       10011    52066665    7  HPFS/NTFS

/dev/sdb3            1983        2206     1799280   82  Linux swap / Solaris

/dev/sdb4            2207        3529    10626997+  83  Linux



Las entradas de la tabla de particiones no están en el orden del disco

```

**tendra algo que ver que los discos estan en el mismo puerto ide, el de win como master y el de ubuntu como slave?**

slds

---

### Post by staar on 2009-05-30
probá modificando esta línea del menu.lst ```

rootnoverify	(hd0,0)
``` dejándola así ```

rootnoverify	(hd1,0)
``` y el 'root' de acá ```

title		Other operating systems:

root
``` borralo, porque es innecesario (no estoy muy seguro de que cause problemas, pero mejor prevenir)

saludos

---

### Post by Mauro22 on 2009-05-30
Lo del rootnoverify no habria que cambiarlo porque esta bien asi, es el disco 0, particion 0.


Poné antes del rootnoverify (hd0,0):

```
map (hd0) (hd1)
map (hd1) (hd0)
```

---

### Post by staar on 2009-05-30
a ver, el agregado que propone Mauro está bien para que windos crea que está en el primer disco, por el tema de una limitación de ese SO...

pero el rootnoverify es un parámetro de GRUB, y este toma el orden de los discos desde la BIOS, siendo que RENGO tiene el disco con windos segundo en el orden de inicio, el cambio que propuse si es válido...

saludos

---

### Post by RENGOdeDIA on 2009-05-31
Bueno estuve probando y quedo perfecto, pero tuve que hacer ambas modificaciones, la de Mauro22 y la de staar, porque haciendo de a una por separado no funcionaba.
Realmente agradezco mucho por las respuestas tan rápidas.
Saludos

---

