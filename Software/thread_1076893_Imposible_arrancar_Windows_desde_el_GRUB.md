---
title: "Imposible arrancar Windows desde el GRUB"
date: 2009-02-21
forum: Software
---

### Post by unsigned on 2009-02-21
Hola, que tal?
Hace poco instalé Ubuntu 8.10 en un disco rígido SATA compartido con Windows. Luego de instalar la distribución, el GRUB nunca apareció automaticamente. Arrancaba directamente Windows. Así que inicié desde el Live CD y reinstalé el gestor de arranque. De esta manera pude entrar a Ubuntu... pero no a Windows! Cada vez que intento ingresar desde el GRUB a Windows me aparece "A Kernel File Is Missing from the Disk..." 
Finalmente, (por razones laborales) opté por desinstalar el GRUB.
¿Como puedo solucionar este inconveniente?

Les dejo las especificaciones de mi computadora por si sirven de algo:
Pentium 4 3,06 Ghz
Placa Madre AsRock 775i65G
Placa de video nVidia GeForce FX 5200 256 Mb
1 Gb de RAM
1 disco SATA de 80 Gb (principal)
1 disco IDE de 80 Gb (esclavo)

Gracias.

---

### Post by kornykyano on 2009-02-22
Probaste con el **SuperGrub**?

cualquier cosa te dejo la pagina para descargarlo [http://supergrub.forjamari.linex.org/?section=home]("http://supergrub.forjamari.linex.org/?section=home") lo grabas en un pen o CD y booteas.

Viejos recuerdos cuando usaba Win$ jijij

Saludos

---

### Post by unsigned on 2009-02-22
Si, lo probé sin ningun resultado...

---

### Post by sajnox on 2009-02-22
Aca [0] tenes lo que parece ser la solucion a tu problmea (sip, esta en ingles, sino lo manejas avisa que vemos de como traducir lo que necesitas)

Saludos


[0] [http://www.linuxforums.org/forum/ubuntu-help/137075-help-cant-dual-boot-xp-ubuntu-8-10-a.html](http://www.linuxforums.org/forum/ubuntu-help/137075-help-cant-dual-boot-xp-ubuntu-8-10-a.html)

---

### Post by unsigned on 2009-02-22
Hice todas las cosas que sugerían en ese hilo sin resultado alguno... 
¿Puede ser que el "enlace" de Windows en el menu.lst apunte a cualquier lado? ¿Como es posible detectar la dirección de la particion de Windows y corregirla en el GRUB?
Gracias muchachos

---

### Post by sajnox on 2009-02-22
Poder ser...todo puede ser.

Postea el contenido de estos archivos

```
/boot/grub/menu.lst
/etc/fstab
```

Y la salida de este comando
```

sudo fdisk -l
```

---

### Post by unsigned on 2009-02-23
Ok. Aca pasa algo raro... Me falta el directorio "/grub"! Así que no voy a poder postear el contenido de menu.lst

Aca va el de 

```
sudo fdisk -l
```

```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
16 cabezas, 63 sectores/pista, 155061 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes
Identificador de disco: 0xa919a919

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1      155060    78150208+   7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x500a5009

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        6175    49600656    7  HPFS/NTFS
/dev/sdb2            6176        9729    28547505    5  Extendida
/dev/sdb5            6176        9576    27318501   83  Linux
/dev/sdb6            9577        9729     1228941   82  Linux swap / Solaris
```

Y el de /etc/fstab/

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb6 swap swap defaults 0 0
```

????

---

### Post by sajnox on 2009-02-23
Hasta donde yo se no podes no tener un directorio grub....pero evidentemente no se todo.

En un rato me fijo en casa las particiones que tiene tu maquina

Tambien te aconsejo que instales mount manager

```
sudo apt-get install mountmanager
```

---

### Post by h9005 on 2009-02-23
Con un disco ata me paso algo parecido, me anduvo Ubuntu 8.10 ii pero no win vista, meti el disco de recuperacion de vista original, elegi reparar, detectó un problema de arranque, le puse listo, reinicié y anduvo todo.

Acá cuento como resolvi el problema...

[http://ubuntuforums.org/showthread.php?t=1072400&highlight=h9005]("http://ubuntuforums.org/showthread.php?t=1072400&highlight=h9005")

---

### Post by unsigned on 2009-02-28
Uuuh, ya no sé que hacer... Formatee la partición de Ubuntu desde un programa de Windows, instalé la versión 8.04 y el GRUB sigue sin aparecer! Les comento que antes tenía un disco rígido IDE con ambos sistemas operativos y todo funcionaba a la perfección. Desde que me compré este disco SATA comenzaron los problemas... ¿Será el disco rígido?

---

### Post by sajnox on 2009-02-28
Fijate que en el bios este seteado para que el disco con el que la maquina arranque sea el que tiene instalado Ubuntu, sino nunca va a ver el bios simplemente por que en el orden de arranque no esta ese disco primero

---

### Post by infernus92 on 2009-02-28
no tengo mucha idea... pero a mi se me habia armado unos lios con el grub (por suerte ya solucionados)y no tuvo nada que ver que la bios booteara de un disco o de otro... el grub aparecia lo mismo
una preg mas o menos del caso... si yo quiero sacar el disco que tiene instalado ubuntu y dejar la computadora solo con windows... como hago para que no intente ejecutar el grub? porque probe sacando el disco pero me tira un error mas o menos que no encuentra el grub...

---

### Post by sajnox on 2009-02-28
Si bien lo que vos queres hacer esta muy mal!!!

Conseguite el Super Grub Disk, quemalo a un CD y booteas la maquina con ese CD

Segui las instrucciones y con eso recuperas el cargador de windows

---

### Post by unsigned on 2009-03-09
Ya encontré el problema! Cada vez que restauraba el GRUB, se instalaba en el disco IDE (secundario) en donde tengo archivos nada más (no hay ningun Sistema Operativo). Estaría agradecido si me dijeran como tengo que hacer para instalar el gestor de arranque en mi disco SATA (primario con Windows XP y Ubuntu).
Gracias.

---

### Post by ADICTOALMAXIMO on 2009-03-09
Instalar primero windows y luego linux

---

### Post by unsigned on 2009-03-10
> **ADICTOALMAXIMO said:**
> Instalar primero windows y luego linux

WOW vos sos Dennis Ritchie? :mrgreen:

---

### Post by faktorqm on 2009-03-11
Evidentemente no. jajajaj

Escuchame, cuando instalas en el modo grafico, en la ultima ventana, antes de que empiece la copia de archivos, hay un boton, que no me acuerdo si se llama avanzado, opciones, o algo parecido, que te deja elegir a donde vas a cargar el grub y te deja setear un proxy tambien. 

Sino tambien podes buscar en la web que hay 1500000000 tutoriales para restaurar grub (no, no exagero).

Sino tambien podes usar el super grub disk.

Sino tambien podes deshabilitar el disco sata desde el bios, instalar linux """normalmente""", poner como primero al de linux y luego metes el disco con el windows y le agregas una entrada al grub (ya andando) que bootee desde el windows y listo.

Saludos.

---

### Post by unsigned on 2009-03-11
Bueno... lo que hice fue desconectar el disco secundario IDE e instalar el GRUB en la MBR del SATA. Ahora puedo entrar en Ubuntu!!! Pero no en Windows (jeje) Cada vez que lo intento me dice "Error de lectura de disco. Presione Ctrl + Alt + Supr para reiniciar". Yo sé que el sector de arranque de Windows está impecable porque si borro el GRUB inicia perfectamente. Lo mas probable es que el root del menu.lst apunte a cualquier lado... ¿Hay alguna forma de saber en que particion tengo instalado Windows?
Aca les adjunto el menu.lst para que lo vean por las dudas

> # menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
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
# kopt=root=UUID=53de0ddb-95db-42ad-9912-fbbc1cfede95 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=53de0ddb-95db-42ad-9912-fbbc1cfede95 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=53de0ddb-95db-42ad-9912-fbbc1cfede95 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Saludos y gracias!

---

### Post by unsigned on 2009-03-20
Mucho software libre, pero nadie me ayuda...

---

### Post by pablo.s on 2009-03-20
> **unsigned said:**
> Hola, que tal?
Hace poco instalé Ubuntu 8.10 en un disco rígido SATA compartido con Windows. Luego de instalar la distribución, el GRUB nunca apareció automaticamente. Arrancaba directamente Windows. Así que inicié desde el Live CD y reinstalé el gestor de arranque. De esta manera pude entrar a Ubuntu... pero no a Windows! Cada vez que intento ingresar desde el GRUB a Windows me aparece "A Kernel File Is Missing from the Disk..." 

1 disco SATA de 80 Gb (principal)
1 disco IDE de 80 Gb (esclavo)


Un poco de teoria: en grub los discos se describen asi: 

(hd0,0) Es la primera partición del disco primario master
(hd0,1) Es la segunda partición del disco primario master
(hd0,2) Es la tercera...

(hd1,0) Es la primera partición del disco primario esclavo
(hd1,1) Esla segunda partición...

Si averiguás **en que partición de cual disco está Windows** (vamos a suponer
que está instalado en la primera partición del disco primario master) lo que 
tenés que agregar a menu.list es algo así:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

después de la linea que dice ### END DEBIAN AUTOMAGIC KERNELS LIST

Espero que te sirva. Y acordate que acá la gente ayuda de onda, nadie es 
empleado de nadie. Esta comunidad está sostenida por el trabajo solidario.
Si a veces no se encuentra una solución pronto, hay que ser paciente.

---

### Post by Mister X on 2009-03-20
> **unsigned said:**
> Mucho software libre, pero nadie me ayuda...

mis mas sinceras disculpas por parte de toda la cumunidad ya que tienen el atrevimiento de no dejar todo lo que estan haciendo para correr a ayudarte...

---

### Post by unsigned on 2009-03-20
Ok. No hacía falta contestar de forma pedante...

Gracias Pablo S. ya lo pude solucionar. Aunque desinstalé Ubuntu y me pasé a OpenSuSe.
Saludos.

---

### Post by Hei Ku on 2009-03-20
Es esperable la respuesta despues de tu comentario. Venis a un foro de software libre a pedir ayuda porque un sistema operativo privativo no te arranca, y ademas protestas de manera poco feliz.

Es como gritar "Viva el Lobo" en plena tribuna de Estudiantes. ;)

---

### Post by pablo.s on 2009-03-20
> **unsigned said:**
> Aunque desinstalé Ubuntu y me pasé a OpenSuSe.
Saludos.

Bueno, hicimos lo posible para que te quedaras con Ubuntu... snif.

---

