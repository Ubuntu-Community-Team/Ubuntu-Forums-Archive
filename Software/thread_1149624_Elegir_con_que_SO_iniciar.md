---
title: "Elegir con que SO iniciar"
date: 2009-05-05
forum: Software
---

### Post by FB91 on 2009-05-05
Les cuento mi problema,

En una particion tenía instalado Windows XP 64bits y en otra Ubuntu. Luego instalé el Windows XP de 32bits en la partición del XP de 64bits, es decir, me quedó una particion con el XP de 32bits y en otra el Ubuntu.

Una vez instalado el XP cuando prendo mi PC ya no me da a elegir entre los distintos sistemas operativos, se inicia directamente desde el XP...

Estoy seguro que la partición de Ubuntu no se borró ni nada por el estilo, estoy casi seguro que el XP tocó algo que hace que inicie directamente pero nose que es xD

Si alguien me da una mano se lo agradesco :P

---

### Post by staar on 2009-05-05
lo que pasó es que windows sobreescribió la mbr con su bootloader, borrando grub, probá con supergrubdisk: [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/") (es un cd que te permite recuperar el grub)...

saludos

---

### Post by FB91 on 2009-05-05
Descargué de [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)el archivo  [Auto for Windows]("http://www.supergrubdisk.org/index.php?pid=12") y seguí todos los pasos. Lo ejecuté, reinicié la PC, en el menú de arranque (la pantalla negra) elejí "Auto Super Grub Disk" y cuando le doy enter me sale un mensaje que me dice "This is not a bootable disk. Please insert a bootable floppy and press any key to try again."

Entonces se me dió por poner el  live cd de ubuntu pero no pasó nada... todo sigue igual :S

¿Qué hice mal?

Saludos! 
[]("http://www.supergrubdisk.org/index.php?pid=12")

---

### Post by staar on 2009-05-05
hacé una cosa, bootea con el livecd de ubuntu, abrí una terminal y corré ```
sudo fdisk -l
``` pegá la salida acá...

es para ver como son los discos y particiones de tu pc, así la podemos seguir con más datos ;-)

saludos

---

### Post by ramiro_md on 2009-05-05
A mi siempre me funcionó el método del livecd paar recuperar el GRUB. Acá te dejo el enlace [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Staar me causa intriga qué hace el comando de tu firma (sudo cat /dev/sda | aplay -fdat), pero no quiere ejecutarlo por si las dudas jeje

---

### Post by josecuervo86 on 2009-05-05
> **ramiro_md said:**
> Staar me causa intriga qué hace el comando de tu firma (sudo cat /dev/sda | aplay -fdat), pero no quiere ejecutarlo por si las dudas jeje

Ponelo!! Casi me saca las orejas!! yo tambien estaba tentado :D

---

### Post by ramiro_md on 2009-05-05
> **josecuervo86 said:**
> Ponelo!! Casi me saca las orejas!! yo tambien estaba tentado :D

Bueno, lo hago, más le vale que no pase nada xD

Edito: no paso nada grave :D que loco eso del sonido del disco :P

---

### Post by FB91 on 2009-05-05
segui los pasos que me decia el enlace q me mandaste:

[LIST=1]
[*] Idioma: español
[*] Sistema operativo: Linux
[*] Tarea: Arreglar arranque de Linux (GRUB)
[/LIST]
Una vez que hago eso me salta este mensaje de error:

ERROR 15: File not found 
:S

(mas tarde pruebo con el live cd hacer eso del 

sudo fdisk -l
Saludos!

---

### Post by staar on 2009-05-05
jajaja, es una gilada que encontré en los foros de arch :-D, ta buenísima...
pueden poner la partición que quieran, incluso otros dispositivos (recomendados: la swap y /dev/mem) :-D:-D...
es inofensivo, solo le están pasando algo a aplay para que lo reproduzca, puede ser cualquier cosa, cualquier archivo...
bueno, basta de off, vamos con el problema del amigo acá:

> **FB91 said:**
> segui los pasos que me decia el enlace q me mandaste:

[LIST=1]
[*] Idioma: español
[*] Sistema operativo: Linux
[*] Tarea: Arreglar arranque de Linux (GRUB)
[/LIST]
Una vez que hago eso me salta este mensaje de error:

ERROR 15: File not found 
:S

(mas tarde pruebo con el live cd hacer eso del 

sudo fdisk -l
Saludos!

hace lo que te pedí, que en un rato lo tenemos andando ;-)...

ah!, también postea el contenido del archivo menu.lst, que está en tu partición de ubuntu, en la carpeta /boot/grub

saludos

---

### Post by infernus92 on 2009-05-05
que raro que no anduvo con el supergrubdisk... bajaste la version que te decia la pagina??
a mi me anduvo de 10

Saludos

PD: que flashero ese comando... jajaja

---

### Post by FB91 on 2009-05-06
les cuento como me fue... 
hice lo que me dijo staar, puse sudo fdisk -l en la terminal y la salida fue la siguiente:


> ubuntu@ubuntu:~$ sudo fdisk -l
omitiendo la partición vacía (5)

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x06550655

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       25170   202177993+   7  HPFS/NTFS
/dev/sda2           25171       26415    10000462+  83  Linux
/dev/sda3           26416       38913   100390185    5  Extendida
/dev/sda4           26540       38913    99394123+  83  Linux
/dev/sda5           26416       26539      995967   82  Linux swap / Solaris

Luego fui a Lugares » Soporte 10,2GiB (que es la partición en la que está instalado Ubuntu) y el contenido de la carpeta menu-lst es este:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=18792089-696a-4a86-8901-40ac267b37e6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18792089-696a-4a86-8901-40ac267b37e6

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        18792089-696a-4a86-8901-40ac267b37e6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18792089-696a-4a86-8901-40ac267b37e6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        18792089-696a-4a86-8901-40ac267b37e6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18792089-696a-4a86-8901-40ac267b37e6 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        18792089-696a-4a86-8901-40ac267b37e6
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional x64 Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


Saludos!

---

### Post by staar on 2009-05-06
bueno, desde el livecd, abrí una Terminal y seguí estos pasos:
abrí el interprete de comandos de grub:
```
sudo grub
```
buscá donde esta la partición de ubuntu: 
```
find /boot/grub/stage1
```
ponés el valor que te devolvió, suplantando X y Y:
```
root (hdX,Y)
```
instalá grub en el primer disco duro:
```
setup (hd0)
```
salí:
```
quit
```

reinicias, y contá como fue...

saludos

---

### Post by FB91 on 2009-05-06
find /boot/grub/stage1 me da como resultado (hd0,1)

Y cuando escribo root(hd0,1) me dice "UNRECOGNIZED COMMAND" :S

Todos estos los comandos los ejecuté en una terminal de modo texto, presionando Alt+F1 (capaz que eso hice mal... aunque no creo)

Gracias por la buena onda staar :P

---

### Post by staar on 2009-05-06
es con un espacio entre root y (hd0,1) asi:
```
root (hd0,1)
```


saludos

---

### Post by FB91 on 2009-05-06
Me funcionó :D !!!!

Gracias capo !!!

---

### Post by staar on 2009-05-06
buenísimo!! me alegro...

ah, supongo que la entrada para windows quedó en el XP de 64 bits, no importa, arranca igual, si querés, editando como root el menu.lst, podés cambiarle el title...

saludos

---

