---
title: "[SOLVED] grub error 17 rebelde, nada más iniciar el ordenador"
date: 2009-07-02
forum: Software
---

### Post by srsiempre on 2009-07-02
Hola,

la vida es perra.
Tenía el ubuntu escoñado, es decir, que no me funcionaba.
Instalé de cero la última versión de ubuntu.

Y otra vez, el maldito error 17 grub.

Como hace mucho tiempo que me pasó, el único recuerdo que tengo es que fue un infierno.

Antes de escribir estas lineas, me he leido cuatropientas páginas, he seguido las instrucciones cincoprentas veces, y reiniciado dospientas veces.

Cuando inicio el ordenador me aparece:

```
GRUB loading stage 1.5
GRUB loading, please wait
Error 17
```[FONT=Courier New]
[/FONT]
- No sale el menú. No se puede tecla E para editar.

A la espera de conseguir un ordenador para grabar la imagen de [http://www.supergrubdisk.org](http://www.supergrubdisk.org), que la última vez me ayudó a solucionarlo, la pregunta del millón de dolares es:

¿SE PUEDE SOLUCIONAR DESDE EL DISCO LIVECD DE UBUNTU?
(¿y se puede hacer sin consola, desde el entorno gráfico?)


Os explico mi caso, 

He hecho desde el LiveCD de ubuntu, varias probaturas.



- He comprobado que la configuración de la BIOS de los discos está en AUTO, como dice en este mensaje. 
[http://ubuntuforums.org/showpost.php?p=2650872&postcount=1](http://ubuntuforums.org/showpost.php?p=2650872&postcount=1)

- He seguido 
[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)


--------------------------------------------------
```
grub> find /boot/grub/stage1
 (hd2,0)

grub> root (hd2,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> quit
```

tambien he probado todo igual, pero con:
grub> setup (hd0,0)

--------------------------------------------------

```
$ sudo mkdir /media/ubuntu
$ sudo mount /dev/sdc1 /media/ubuntu
$ sudo mount --bind /dev /media/ubuntu/dev
$ sudo chroot /media/ubuntu/
# grub-install /dev/sda1
```no funcionó
--------------------------------------------------
tampoco
[http://oviedos.com.mx/index.php/blog/show/Error_17_en_Grub.html](http://oviedos.com.mx/index.php/blog/show/Error_17_en_Grub.html)
--------------------------------------------------

La información:


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd29a6a80

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000446ac

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

Disco /dev/sdc: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x6a54c522

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1         914     7341673+  83  Linux
/dev/sdc2             915        1045     1052257+  82  Linux swap / Solaris
/dev/sdc3            1046        3655    20964825   83  Linux
/dev/sdc4            3656       30401   214837245    b  W95 FAT32

Disco /dev/sdd: 8027 MB, 8027897856 bytes
14 cabezas, 22 sectores/pista, 50907 cilindros
Unidades = cilindros de 308 * 512 = 157696 bytes
Identificador de disco: 0x04030201

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdd1   *           8       50908     7838628    b  W95 FAT32
```--------------------------------------------------

3 discos. Los 3 SATA.

el 1o - SO windows - sda - hd0
el 2o - datos windows - sdb - hd1
el 3o - 4 particiones:
la 1a partición -- / - sdc1 - hd2,0
la 2a partición -- swap - sdc2 - hd2,1
la 3a partición -- /home - sdc3 - hd2,2
la 4a partición -- para datos para compartir con windows - sdc4 - hd2,3 

--------------------------------------------------
menu.lst

```
## ## End Default Options ##

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=2a150770-4df7-42d9-b2ac-2ce7c75ecc1c ro quiet splash locale=ca_ES
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=2a150770-4df7-42d9-b2ac-2ce7c75ecc1c ro single
initrd        /boot/initrd.img-2.6.24-19-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader    +1
boot

```Este es el menu.lst que funcionaba
antes de instalar ubuntu 9.4
y siempre me sirvió de acabar de reparar,
aunque recuerdo que no me sale el menú grub
con la cuenta atrás
así que el problema no es el menu.lst
--------------------------------------------------


Ruegos y Preguntas

- Si el error 17 es que reconoce la partición pero no puede ponerla en marcha, o si significa que linux no reconoce el orden que la BIOS da a los discos, como comprobar si esto es así.

- ¿No existe ninguna utilidad desde el entorno gráfico de ubuntu livecd para reparar estos problemas? Creo que es una gran veneno para ubuntu, ya que al instalar ubuntu, te quedas sin ordenador. Y para el que sabe algo más, tienes que invertir varias tardes...


Gracias

---

### Post by richardh9936 on 2009-07-02
Me too.  But I can't really read or write Spanish, and I don't have an answer yet.  Sorry.

---

### Post by staar on 2009-07-02
si estás usando ese menu.lst para arrancar ubuntu 9.04, con ese orden de discos, desde ya te digo que está mal, primero porque es de hardy, y segundo porque el root tendría que ser (hd2,0) y no (hd0,0)

otra cosa, no es importante, pero porqué la partición del segundo disco tiene flag de boot, si no tiene ningún SO?

lo que te recomendaría es que uses Supergrubdisk para restablecer el bootloader de windows en la MBR, y luego vuelvas a instalar grub desde cero...

y no, no existe utilidad gráfica de configuración de grub, al menos que conozca, y no creo que la haya nunca, porque la migración a grub2 ya comenzó, y el primer paso lo dió ubuntu (la proxima versión va a incluir esa versión por defecto)

saludos

---

### Post by sp33d3rs on 2009-07-02
Yo tenia el mismo problema, la única forma de solucionarlo fue instalando ubuntu de nuevo y con el qparted darle las particiones que corresponden a windows y a ubuntu.

También existe un soft que descargue (supergrub) que lo soluciona, es muy intuitivo y fácil

---

### Post by milovan1971 on 2009-07-02
Coincido con staar... parece que tenes un problema con tu archivo de configuracion del grub (menu.lst).  No parece que haga falta reinstalar.
Segun tu tabla de particion, tu ubuntu esta en sdc1 (primera particion del 3er disco duro), o sea hd2,0 para el grub. De hecho el find boot/... te lo muestra.
Usando el live cd, hace desde consola
*sudo gedit* /boot/grub/*menu*.lst
escribi el password, y edita el menu.lst, cambia "hd0,0" a "hd2,0". Guarda cambios y reinicia.
suerte

---

### Post by milovan1971 on 2009-07-02
> **richardh9936 said:**
> Me too.  But I can't really read or write Spanish, and I don't have an answer yet.  Sorry.

richardh9936, This is a spanish speaker group, but we can try helping you. Please post your menu.lst file here (only the lines at the end, without #), and the result of the command
sudo fdisk -l

Cheers

---

### Post by richardh9936 on 2009-07-03
I think I found a solution:   The issue in the thread below is that GRUB has become confused about which disk holds the /boot/grub/stage1 files.  (Matches my situation.)  

Good luck with yours.


[http://ubuntuforums.org/showpost.php?p=5315917&postcount=2]("http://ubuntuforums.org/showpost.php?p=5315917&postcount=2")

---

### Post by gmunioz on 2009-07-03
Hola srs....:

1- Inicia con un live-cd.

2- Abre una consola

3- Ejecuta:

sudo mkdir /media/ubuntu
sudo mount /dev/sdc1 /media/ubuntu
sudo mount --bind /dev /media/ubuntu/dev
sudo chroot /media/ubuntu/
cd /media/ubuntu/boot/grub
rm menu.lst
grub-install /dev/sda

---

### Post by srsiempre on 2009-07-04
Hola.

En  primer lugar **gracias a todos** por la ayuda tan rápida, un aire positivo que compensa el desasosiego de encontrarse sin ordenador, ni windows ni ubuntu.

Se me olvidó incluir estos enlaces:
Lista de errores grub: [http://www.gentoo.org/doc/es/grub-error-guide.xml#doc_chap5](http://www.gentoo.org/doc/es/grub-error-guide.xml#doc_chap5)
Una de las cosas que probé: [http://oviedos.com.mx/index.php/blog/show/Error_17_en_Grub.html](http://oviedos.com.mx/index.php/blog/show/Error_17_en_Grub.html)

Ninguna de las respuestas me dieron la clave, pero todos los mensajes me dieron ideas que me han ayudado a encontrar la solución parcial que encontré:


[LIST]
[*]Instalando de nuevo ubuntu, concretando las particiones manualmente en el entorno gráfico de instalación
[*]Y en la **BIOS **y cargué las "**Load default setting**" y funcionó.
[/LIST]

Solución parcial, porque ahora no me monta en el disco de windows y por tanto, en el grub no me hizo una opción para windows xp. Ubuntu funciona. Windows no. Ni monta el disco sda al iniciar...

Mis pasos siguientes son:

- Probar el supergrubdisk haber si lo resuelve todo.
- Buscar en el google como hacer para que monte el sda desde el inicio del sistema operativo y volver a contruir el menu.lst...

---

Mi intuición me dice que al intentar definir en la BIOS (boot order) el cd-rom como primer dispositivo de arranque, para cargar el LiveCD de ubuntu, aquí es donde modifiqué el orden de los discos y el orden de los disco para la BIOS y linux era diferente. Aunque esta teoría es vaga.


> **staar said:**
> si estás usando ese menu.lst para arrancar ubuntu 9.04, con ese orden de discos, desde ya te digo que está mal, primero porque es de hardy, y segundo porque el root tendría que ser (hd2,0) y no (hd0,0

Desde mi gran ignorancia, algo me dice que no. Mi impresión es que GRUB, es independiente del sistema operativo. Que ahora la versión de ubuntu construya el menu.lst con otra filosofía, en eso te puedo dar la razón. El menu.lst mostrado pertenece al PC que funcionaba, con ubuntu y windows a la vez. Pero ahora quizás no sirve como referencia, ya que el orden de los discos desde el punto de vista de la BIOS puede haber cambiado, al reiniciar la configuración de fábrica.

[Si alguna vez toqué la configuración de fábrica de la BIOS fue para intentar iniciar el cd-rom bootable, hacer que ubuntu se iniciara desde usb (objetivo nunca conseguido) o el tema ACPI que se encuentran en otros mensajes.]

Este es el menu.lst actual que funciona:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
#uuid        bd9a9595-e329-4882-88c8-4a13f0cda1b4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bd9a9595-e329-4882-88c8-4a13f0cda1b4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
#uuid        bd9a9595-e329-4882-88c8-4a13f0cda1b4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bd9a9595-e329-4882-88c8-4a13f0cda1b4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic
```


> **staar said:**
> otra cosa, no es importante, pero porqué la partición del segundo disco tiene flag de boot, si no tiene ningún SO?

Si es cierto, la penúltima vez que me pasó lo mismo, en la locura y desesperación ensayo error, de alguna manera, marqué la partición bootable, aunque es nfts! y solo tiene datos!. Pero no me preguntes como. Ahí se ha quedado.

> **staar said:**
> lo que te recomendaría es que uses Supergrubdisk para restablecer el bootloader de windows en la MBR, y luego vuelvas a instalar grub desde cero...

> **sp33d3rs said:**
> Yo tenia el mismo problema, la única forma de solucionarlo fue instalando ubuntu de nuevo y con el qparted darle las particiones que corresponden a windows y a ubuntu.

Si, como dije en el primer mensaje, supergrubdisk me solucionó finalmente el problema en la penúltima vez, pero en este momento no podía grabar la imagen iso en un cdrom, ya que no tenía un segundo ordenador en casa, y desde el livecd de ubuntu, no te permite sacar el cdrom para poder grabar la imagen! Sin un segundo ordenador (o sin dos cdrom una para leer el livecd de ubuntu y otra para grabar el disco de supergrub) no puedes continuar!.

El reto y la motivación de iniciar este tema, es para buscar una solución alternativa a supergrub desde el livecd de ubuntu y recopilar información para los que busquen solución a este problema tan devastador.


> **gmunioz said:**
> 
sudo mkdir /media/ubuntu
sudo mount /dev/sdc1 /media/ubuntu
sudo mount --bind /dev /media/ubuntu/dev
sudo chroot /media/ubuntu/
cd /media/ubuntu/boot/grub
rm menu.lst
grub-install /dev/sda

¿Donde está la diferencia clave del código que comento yo, que digo que no funcionó? ¿No es lo mismo?

Si, tambien lo hice, tal y como muestra el enlace Recuperar_GRUB de la guia ubuntu del principio, por supuesto cambiando del ejemplo hda por sda (ya que mis discos son SATA, y los discos hda son IDE (con el comando del terminal 'sudo fdisk -l' se puede averiguar, lo que tiene tu pc).

Yo que empecé desde el MSDOS, aún así, me siento como perdido y pertubado. Cada paso que descubro para solucionar el problema me aparecen mil preguntas más, que difurcan las dudas como ramas de un árbol. Por ejemplo, 

por que en la definición de las particiones de modo manual en la instalación gráfica de ubuntu, no me dejaba marcar sda como '/windows'? (me habré cargado MBR?)

Ya os contaré, como acaba todo!

---

### Post by staar on 2009-07-04
> **srsiempre said:**
> Solución parcial, porque ahora no me monta en el disco de windows y por tanto, en el grub no me hizo una opción para windows xp. Ubuntu funciona. Windows no. Ni monta el disco sda al iniciar...

Mis pasos siguientes son:

- Probar el supergrubdisk haber si lo resuelve todo.
- Buscar en el google como hacer para que monte el sda desde el inicio del sistema operativo y volver a contruir el menu.lst...


para agregar el Ventanas al menu.lst te podemos ayudar, no hace falta que ubuntu monte el disco al inicio para que grub pueda arrancar windos, son dos cosas diferentes, posteá la salida de un ```
sudo fdisk -l
``` actual en el ubuntu, y el contenido del archivo /boot/grub/device.map para ver como quedaron los discos en la bios y como los lee grub...

> **srsiempre said:**
> Mi intuición me dice que al intentar definir en la BIOS (boot order) el cd-rom como primer dispositivo de arranque, para cargar el LiveCD de ubuntu, aquí es donde modifiqué el orden de los discos y el orden de los disco para la BIOS y linux era diferente. Aunque esta teoría es vaga. es una teoría muy probable...

> **srsiempre said:**
> Desde mi gran ignorancia, algo me dice que no. Mi impresión es que GRUB, es independiente del sistema operativo. Que ahora la versión de ubuntu construya el menu.lst con otra filosofía, en eso te puedo dar la razón. El menu.lst mostrado pertenece al PC que funcionaba, con ubuntu y windows a la vez. Pero ahora quizás no sirve como referencia, ya que el orden de los discos desde el punto de vista de la BIOS puede haber cambiado, al reiniciar la configuración de fábrica. una parte del grub (la stage 1) es independiente de ubuntu, la otra (stage 2) no, porque los archivos de configuración están en la partición de ese SO, yo decia que ese menu.lst no servía, porque hacia referencia a un kernel (un archivo) que es de hardy, en jaunty tiene otro número, además de que el orden de los discos actual parece ser diferente...


> **srsiempre said:**
> Este es el menu.lst actual que funciona:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
#uuid        bd9a9595-e329-4882-88c8-4a13f0cda1b4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bd9a9595-e329-4882-88c8-4a13f0cda1b4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
#uuid        bd9a9595-e329-4882-88c8-4a13f0cda1b4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bd9a9595-e329-4882-88c8-4a13f0cda1b4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic
``` para poder iniciar Ventanas solo habría que agregar unas líneas similares a estas ```

title        Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader    +1
boot
``` solo que no estoy seguro de cual es el número de disco donde está dicho SO, por lo que (hd1,0) puede cambiar a (hd2,0) y el map también...


> **srsiempre said:**
> El reto y la motivación de iniciar este tema, es para buscar una solución alternativa a supergrub desde el livecd de ubuntu y recopilar información para los que busquen solución a este problema tan devastador. los pasos que describió gmunioz son la alternativa a SGD desde el livecd...

> **srsiempre said:**
> Si, tambien lo hice, tal y como muestra el enlace Recuperar_GRUB de la guia ubuntu del principio, por supuesto cambiando del ejemplo hda por sda (ya que mis discos son SATA, y los discos hda son IDE (con el comando del terminal 'sudo fdisk -l' se puede averiguar, lo que tiene tu pc). es medio off, pero los discos IDE ahora (desde el cambio del driver en el kernel) también son sda, sdb, etc...

> **srsiempre said:**
> por que en la definición de las particiones de modo manual en la instalación gráfica de ubuntu, no me dejaba marcar sda como '/windows'? (me habré cargado MBR?) no estoy seguro, pero me parece que tenés ubuntu en /dev/sda y que el disco de windos ahora se llama diferente, y la MBR está bien, sino no tendrías GRUB andando (grub se aloja allí)

saludos

---

### Post by srsiempre on 2009-07-06
Gracias a todos, especialmente a staar, que he aprendido más en sus lineas de respuesta que en muchas páginas web que me he leído. Gracias.

Lo prometido es deuda:

[SIZE=5]sudo fdisk -l[/SIZE]

```
Disc /dev/sda: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd29a6a80

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disc /dev/sdb: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000446ac

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

Disc /dev/sdc: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a54c522

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1   *           1         914     7341673+  83  Linux
/dev/sdc2             915        1045     1052257+  82  Intercanvi Linux / Solaris
/dev/sdc3            1046        3655    20964825   83  Linux
/dev/sdc4            3656       30401   214837245    b  W95 FAT32
```Parece que no ha cambiado mucho, verdad?

---------------------------------------------------------------------------

[SIZE=5]device.map[/SIZE]

```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

```Esto está como esperaba.

---------------------------------------------------------------------------

[SIZE=5]menu.lst[/SIZE]
versión que funciona ubuntu, windows todavía no.

```
splashimage (hd2,0)/boot/grub/splashimages/77942-wolf.xpm.gz
default 0
timeout 15

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
# kopt=root=UUID=344f54af-7013-4bb4-87aa-c85b319da1d5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=344f54af-7013-4bb4-87aa-c85b319da1d5

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

title Ubuntu 9.04, kernel 2.6.28-13-generic
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=344f54af-7013-4bb4-87aa-c85b319da1d5 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=344f54af-7013-4bb4-87aa-c85b319da1d5 ro  single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=344f54af-7013-4bb4-87aa-c85b319da1d5 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=344f54af-7013-4bb4-87aa-c85b319da1d5 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader    +1
boot
```Ubuntu me va bien, pero windows me sale un mensaje:

```
FALTA NTLDR
presione CTRL+ALT+SUPR
```Seguiré los consejos del enlace siguiente para correguirlo:
[http://mdug.es/2006/03/falta-ntldr/](http://mdug.es/2006/03/falta-ntldr/)


No me pude resistir a ponerle una pantalla de fondo ;.)


---------------------------------------------------------------------------

Sobre el** editor gráfico** del GRUB encontré este:
KGRUBEditor
pero no sirve de mucho, ya que finalmente tienes que ir a la consola para poner
```
sudo kcmshell4 kgrubeditor
``` y darle permisos de administrador al programa...
y por un lado, sigue sin reconocer el sda,
y por el otro en algún campo de texto no me permite escribir.... así que nada.

*... Si tuviera nivel de inglés sugeriría en launchpad.net una herramienta gráfica para solucionar este problema, los mismos pasos que estoy dando, pero automáticamente, ya que puede echar para atrás a muchos nuevos bienvenidos a ubuntu...*


---------------------------------------------------------------------------
 [SIZE=5]/etc/fstab[/SIZE]

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=344f54af-7013-4bb4-87aa-c85b319da1d5 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=9784d9c0-c0c3-4198-94d3-c4bcc5ad25fa /home           ext3    relatime        0       2
# swap was on /dev/sdc2 during installation
UUID=5ed5dc29-d56c-41c7-b775-3f4006a73cf3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```El disco con formato NFTS que si me monta, SR_DOS, no está en el archivo fstab, pero si que me aparece en el menu de ubuntu, en sitios... parece como si lo montara al hacer clic, ya que a partir de ese momento, ya me aparece en el escritorio. ¿Por que no lo monta desde un principio? Es una cosa de Jaunty.

Continuaré informando ;)

---

### Post by staar on 2009-07-06
> **srsiempre said:**
> Ubuntu me va bien, pero windows me sale un mensaje:

```
FALTA NTLDR
presione CTRL+ALT+SUPR
``` tengo la duda si realmente tenés Ventanas en (hd1,0), y no en (hd0,0), como las dos particiones son booteables explicaría parte del error (así también como los restos de una instalación anterior de Ventanas en (hd1,0)), podrías probar modificando el menu.lst para que quede así: ```

title        Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader    +1
boot
``` eso intentaría bootear windos desde el primer disco (y no desde el segundo como lo hace ahora), que es lo más lógico que se me ocurre...

> **srsiempre said:**
> El disco con formato NFTS que si me monta, SR_DOS, no está en el archivo fstab, pero si que me aparece en el menu de ubuntu, en sitios... parece como si lo montara al hacer clic, ya que a partir de ese momento, ya me aparece en el escritorio. ¿Por que no lo monta desde un principio? Es una cosa de Jaunty. por defecto, las particiones NTFS no se montan al inicio a menos que así se haya especificado en la instalación, esto ocurría también en las versiones anteriores de ubuntu, es el comportamiento normal, y si, al hacerle click el sistema monta el volumen...

para montar los volumenes al inicio es necesario agregarlos al fstab, existen varias herramientas gráficas que hacen esto, te recomendaría la más simple, ntfs-config (buscala por Synaptic, para que te deje establecer los puntos de montaje los volúmenes deben estar desmontados)

con respecto a la interfaz gráfica para configurar grub, sería un esfuerzo en vano hacerla ahora, ya que en pocos meses quedaría obsoleta, debido a que la próxima versión de ubuntu traerá grub2 por defecto, y este se configura de manera totalmente diferente al actual grub-legacy...

saludos

---

### Post by srsiempre on 2009-07-09
Hola.

Finalmente lo solucioné!
:guitar:

Cuando iniciaba windows me ponía:

```
FALTA NTLDR
presione CTRL+ALT+SUPR
```Con las instrucciones de aquí no lo pude solucionar:
[http://mdug.es/2006/03/falta-ntldr/](http://mdug.es/2006/03/falta-ntldr/)
Ya que el disco que hice desde otro pc y otra casa, no me sirvió.

Con el disco de supergrubdisk.org, pasé al error 13 de grub.

El disco de windows no lo tenía a mano, necesario para iniciar la consola de reparación.
Tenía la intuición de que habría algún modo de hacer lo mismo desde ubuntu, que alguien habría trabajado la manera de arreglar la partición NTFS de windows desde ubuntu y eureka lo encontré!:

TestDisk

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

(Lo encontré gracias a esta página que hablaba del grub error 13:
[http://members.iinet.net.au/~herman546/p15.html#13]("http://members.iinet.net.au/%7Eherman546/p15.html#13"))

Recuperé mi windows y funciona como siempre, y ahora puedo iniciar en windows y en ubuntu.

------------------------------------------------------

el menu.lst quedó finalmente así (pongo la parte:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
#map (hd0) (hd1)
#map (hd1) (hd0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader    +1
boot

```------------------------------------------------------

Espero que sirva de ayuda estas lineas, adaptando la información a su situación, ¡como mínimo que sirva de inspiración!. Me he sentido arropado por la comunidad y me siento en deuda. Esto no quedará así, espero ayudar en algún sitio! Sea ayudando a otros respondiendo mensajes, ayudando con alguna traducción, etc. Gracias a todos, no solo me ha servido como pistas para resolver el misterio, sino para sentirme apoyado. Gracias.

---

