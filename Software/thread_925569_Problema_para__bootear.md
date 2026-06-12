---
title: "Problema para  bootear"
date: 2008-09-20
forum: Software
---

### Post by pol666 on 2008-09-20
Buenas, les comento una cosita...

tengo en un disco rigido, 3 SO, Windows XP, Kubuntu, y Debian. Tenia ganas de probar la version de OsX x86 que andaba dando vuelta y como no tengo ganas de borrar ningun SO, lo voy a instalar en el otro disco.

Antes de instalar el osx instale otro debian en la segunda particion del disco rigido para ver como se comportaba el GRUB.
la cuestion es que al momento de instalar el grub, me tira un error (sin logs, solo error fatal)

Entonses, intente agregar la entrada en el Grub de Kubuntu (el que gestiona)
Entonses quedo asi (el debian que instale se llama Debian2)

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Otros Sistemas Operativos
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Debian GNU/Linux
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda3 ro quiet 
initrd		/boot/initrd.img-2.6.26-1-686
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2
title		Debian 2
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-1-686 root=/dev/sdb2 ro quiet 
initrd		/boot/initrd.img-2.6.24-1-686
savedefault
boot




Cuando elijo Debian2 al reiniciar, Me sale [B]Error 17 que no se puede montar la unidad.
[/B]

En la Bios solo me aparece para elegir el disco 1. el 2 no aparece para bootear (salvo que cambie de conector sata). Pienso que necesitare usar algun Jumper para poner como slave como pasaba con los IDE, ya que los dos discos estan sin jumper.

---

### Post by ArtPulse on 2008-09-21
Por lo que tengo entendido, el debian está instalado en el mismo disco que el resto.

En tal caso, modificás:
```

title Debian 2
**root (hd1,1)**
kernel /boot/vmlinuz-2.6.24-1-686 root=/dev/sdb2 ro quiet
initrd /boot/initrd.img-2.6.24-1-686
savedefault
boot
```

cambiando **root (hd1,1)** por:
```
root (hd0,1)
```

Probá a ver si anda =P

Saludos!

---

### Post by pol666 on 2008-09-21
eh no.. esa es la cuestion, el Debian2 esta en el segundo disco

si al grub le pongo hde0,1 bootea el debian 1 :P

---

### Post by faktorqm on 2008-09-22
postea sudo fdisk -l indicando CADA particion de que SO es, asi rearmamos el .lst del grub.

---

### Post by pol666 on 2008-09-22
Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e5d03

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS** Windows**
/dev/sda2            6528        7180     5245222+  83  Linux** Kubuntu**
/dev/sda3            7181        7833     5245222+  83  Linux Debian
/dev/sda4            7834       30401   181277460    5  Extendida
/dev/sda5            7834       30270   180225171   83  Linux** datos**
/dev/sda6           30271       30401     1052226   82  Linux **swap **/ Solaris

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04b504b5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            5223       19457   114342637+   5  Extendida 
/dev/sdb2            2612        5222    20972857+   7  HPFS/NTFS 
/dev/sdb3               1        2611    20972826    b  W95 FAT32 
/dev/sdb5            5223       19457   114342606    7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco



O_o que pása que no aparece li...

ups, bueno esperen creo que paso algo, luego les cuento

---

### Post by faktorqm on 2008-09-22
espero a que termines de postear por que no entiendo nada de lo que esta ahi... mucho desorden!

---

