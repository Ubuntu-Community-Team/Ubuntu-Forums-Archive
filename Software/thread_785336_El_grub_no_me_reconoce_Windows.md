---
title: "El grub no me reconoce Windows"
date: 2008-05-07
forum: Software
---

### Post by Luciano Cossettini on 2008-05-07
Hola.
La situación es esta:
Tenía un sólo rigido particionado, en una partición Ubuntu y en la otra Windows. Todo perfecto.
Conseguí otro rígido, y como no tenía muchas cosas en la computadora instalé windows en el nuevo rígido, con el live CD de Ubuntu formatié el rígido anterior eliminando las particiones e instalando Ubuntu (usé la opción "asisitida, usando todo el disco rígido", no la manual). 
El tema es que ahora no me da la opción de bootear con windows, y el disco está intacto porque lo veo desde Ubuntu, y lo puedo montar como disco ntfs, y veo que está windows. 
Probé desde el bios hacer que sólo bootee desde ese rígido y me dice que no encuentra archivos de booteo. 
¿qué pudo haber cambiado la instalación de Ubuntu?
¿hay manera de editar el grub?
¿es un problema de Windows?
en fin.... agradezco cualquier ayuda.

---

### Post by arist0tle on 2008-05-07
Errr.....Sorry yo no hablo espangol.....I think you are saying that you lost you grub menu by installing windows alongside an ubuntu install....try Super Grub

---

### Post by faktorqm on 2008-05-07
> **arist0tle said:**
> Errr.....Sorry yo no hablo espangol.....I think you are saying that you lost you grub menu by installing windows alongside an ubuntu install....try Super Grub

Entonces si no hablas español para que posteas en un foro donde se habla español? Postea en uno donde se hable ingles y listo ¬¬

respondiendo: Lo que tenes que hacer basicamente es detectar a donde reconoce linux el sistema con windows, y agregar unos comandos en el grub, pero primero necesitamos saber a donde "ve" linux el windows.

Para esto hacemos ```
sudo fdisk -l
``` en una terminal y postea el resultado asi te decimos exactamente que agregar en el grub. Tambien postea con que disco arrancas, si con el de linux o con el de windows.

Por ahora no uses el super grub disk, si bien no es malo, no lo veo necesario pudiendo arreglar el problema editando un archivo con la informacion correcta. Espero que te haya servido. Salu2!

---

### Post by sajnox on 2008-05-07
Es que no le notificaste al Grub del cambio.

Ejecuta lo siguiente y mandanos el contenido

```
sudo fdisk -l
```
```

cat /boot/grub/menu.lst
```

Con eso podemos ver que hay que corregir para que levante con windows tambien

Saludos

---

### Post by Luciano Cossettini on 2008-05-07
bueno, a ver...  posteo lo requerido.

La computadora arranca con el disco donde está linux, sin dar la opción de arrancar con windows.
El disco con windows está montado en /windows, lo veo, puedo incluso administrar y editar archivos, etc, pero no arrancar con windows.

Pongo en el terminal:


luciano@Alter-Ego:~$ sudo fdisk -l

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xdf97df97

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extendida
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disco /dev/sdb: 8455 MB, 8455200768 bytes
255 cabezas, 63 sectores/pista, 1027 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3ce13ce0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        1026     8241313+   7  HPFS/NTFS


luciano@Alter-Ego:~$ cat /boot/grub/menu.lst

(posteo sacando "default options")

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
luciano@Alter-Ego:~$ 

saludos

---

### Post by Mauro22 on 2008-05-07
> **Luciano Cossettini said:**
> 
Probé desde el bios hacer que sólo bootee desde ese rígido y me dice que no encuentra archivos de booteo. 



Seguro te falta el ntloader.exe


Arreglando el grub no vas a solucionar nada. Solo que aparezca la opcion de windows y que te de el mismo error.


Lo que tenes que hacer es:

Con un disco de inicio de Windows, arreglar ("formatear") el MBR

```

fdisk /mbr

```Con eso perdes el grub pero vas a poder iniciar el windows.

Una vez hecho eso, metes el livecd de ubuntu y reinstalas el grub.



PD: Ubuntu nunca te detecto el windows, porque los archivos de arranque de este no estan. Sin eso "windows" son solo datos, y grub no se da cuenta de ello.

---

### Post by Luciano Cossettini on 2008-05-07
Ok,

---

### Post by sajnox on 2008-05-07
Tal vez me equivoco, pero me parece que si le agregas esto al archivo menu.lst te lo tendria que cargar

title		Windows 95/98/NT/2000
root		(hd1,0)
makeactive
chainloader	+1

Cargaselo al final del archivo y reinicia la maquina.

El metodo que te da Mauro funcionar, funciona...pero me parece que haces algunos pasos de mas.

Para estar seguro elegi desde el bios bootear con el segundo disco, si arranca windows segui el consejo que te doy yo.

Saludos

---

### Post by phxnd on 2008-05-07
de paso hago una preguntita:lolflag: =P

yo isntale guindows en una particion del disco, que es lo que tengo que agregar en el grub para poder bootear desde windows?

esto es lo que me tira el fdisk

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        3259    26177886    7  HPFS/NTFS
/dev/hda2            3260        9731    51986340   83  Linux
/dev/hda3            9732       10011     2249100    5  Extendida
/dev/hda4            9872       10011     1124518+  82  Linux swap / Solaris
/dev/hda5            9732        9871     1124487   82  Linux swap / Solaris



Edit:

para bootear desde linux hago

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=984472fd-5f5d-4caf-b73f-46453bbee9ea ro quiet splash locale=es_ES
initrd          /boot/initrd.img-2.6.22-14-386
quiet


(en el grub obvio)

---

### Post by Mauro22 on 2008-05-07
> **sajnox said:**
> 
title        Windows 95/98/NT/2000
root       ** (hd1,0)**
makeactive
chainloader    +1



Lo negro cambialo de acuerdo a tu caso.

---

### Post by faktorqm on 2008-05-07
luciano:

en tu menu.lst tenes que agregar esto :

```

title Esto es lo que vos ves cuando booteas
root (hdX,Y)
savedefault
makeactive
chainloader +1

```

donde X es el numero PARA grub de tu disco rigido, e Y es el numero PARA GRUB de la particion. Para el sda, X vale 0, para sdb X vale 1. Para la particion 1 Y vale 0, para la particion 2 Y vale 1. (OJO con las particiones extendidas, ver fdisk -l atentamente)

y también tenes que agregar el separador, que naturalmente no hace nada:

```

title		Otros sistemas operativos es un buen ejemplo
root

```

o sea que PARA TU CASO Y SOLO PARA TU CASO te queda asi:

```

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title		Otros sistemas operativos:
root

title		Windows XP Professional SP2
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

Aca te dejo el mio por si queres comparar:

```

faktorqm@the-edge:~$ cat /boot/grub/menu.lst
gfxmenu		/boot/grub/message.new
default		0
timeout		10

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9a4b9f99-b82a-4037-a734-f3e78ee9b8b4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9a4b9f99-b82a-4037-a734-f3e78ee9b8b4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet

title		Otros sistemas operativos:
root

title		Windows XP Professional SP2
root		(hd0,0)
savedefault
makeactive
chainloader	+1

faktorqm@the-edge:~$

```

OJO que la primera linea es solo para el booteador grafico, no te mandes macanas.
Ahora bien, si rompiste de alguna manera el arranque del windows, lo que tenes hasta aca es el grub bien para que cuando lo repares te ande perfectamente. Si vos le pones desde el grub que arranque y te dice que no puede, entonces arranco bien y el que esta tirando el error es el windows.

phxnd:

En tu caso seria agregar esto al final del menu.lst:

```

title		Otros sistemas operativos:
root

title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Espero que les haya servido a ambos. Suerte y salu2!!

---

### Post by Luciano Cossettini on 2008-05-07
Creo que ya detecté donde está el problema, pero no sé cómo solucionarlo.
El tema es que Windows no bootea desde ese rígido nuevo (no es una partición, es un rígido diferente), y ni siquiera puedo reinstalarlo porque me dice que para instalarse tiene que escribir en el disco donde está linux, y no puede porque obviamente no reconoce el sistema de archivos. 
O sea, ¿cómo puedo hacer para tener Windows y Linux en dos discos rígidos diferentes sin que Windows me pida escribir esos archivos de inicio en el disco de Linux? ¿se puede hacer una partición de booteo compatible con Windows?

---

### Post by Mauro22 on 2008-05-07
No importa si Windows esta en otro disco o particion. 

GRUB al instalarse lo va a encontrar. Siempre y cuando los archivos de arranque de windows esten. Por eso te dije del fdisk /mbr. Porque te falta el arranque de win2.

Las demas respuestas solo agregar las instrucciones para que GRUB lee esos archivos, que vos no tenes.

---

### Post by Luciano Cossettini on 2008-05-07
creo que el problema va por el lado de que el maldito windows notiene sus **** archivos de inicio, pero no puedo reinstalarlo booteando con el CD de windows (por lo que ya dije antes), y tampoco sé como hacer lo de fdisk /mbr. Escribo eso en el terminal y me pone "no se puede abrir /mbr".
Edité menu.lst con lo sugerido pero igual no arranca...
La verdad es que si realmente no tuviera que usar programas muy específicos de música, ni instalaría windows...

---

### Post by faktorqm on 2008-05-07
Bue, ahora cambia un poquito la cosa. 
Apaga la compu, desenchufala, sacale la tapa, desconecta el disco con linux directamente y hace asi, pone el disco de windows en ESCLAVO (quiza es como esta ahora) y prende la pc y reinstala o instala como prefieras como si nada hubiera pasado.
Apagas la compu cuando todo este ok, desenchufas, luego conectas el disco con linux, como MAESTRO, y arrancas el linux normalmente. Cambias el grub y reinicias. 
Ahi vas a ver como el grub te bootea el windows sin ningun problema con la configuracion propuesta.

Para no reinstalar: Todo igual, salvo que en vez de reinstalar el xp cuando pones el cd de xp, te vas hasta la consola de recuperacion, escribis "fixmbr", y reinicias. Tu xp deberia levantar normalmente. Si levanto, segui con lo mismo de arriba. (cambia reinstalacion por esto).

a todos: estoy harto de ver el comando fdisk /mbr. eso es para win95/98/98SE/ME no se usa mas y es absolutamente obsoleto. Que no se sienta ofendido el que lo dijo, no es contra él sino contra todos los que comunican ERRONEAMENTE. Me interesa que aprendan y comuniquen con resposabilidad cosas que estan bien, y no cosas que son del año 2000.

Si tenes dudas consulta. Salu2!

---

### Post by Mauro22 on 2008-05-07
> **faktorqm said:**
> a todos: estoy harto de ver el comando fdisk /mbr. eso es para win95/98/98SE/ME no se usa mas y es absolutamente obsoleto. **Que no se sienta ofendido el que lo dijo**, no es contra él sino contra todos los que comunican ERRONEAMENTE. Me interesa que aprendan y comuniquen con resposabilidad cosas que estan bien, y no cosas que son del año 2000!

Perdon :(


Se que es obsoleto pero a veces es el unico que te saca las tostadas antes que salten.

---

### Post by faktorqm on 2008-05-07
si igual no es por vos, no te calentes. Lo vi 10000000 veces, otra figurita repetida del foro, y de muchos otros que vi por ahi. Salu2!

---

### Post by Luciano Cossettini on 2008-05-07
Creo que lentamente estoy aprendiendo cómo hacer que funcione. 
Ab&#341;i la máquina y desconecté el HD con linux, y arreglé windows.
Logré poder DESDE EL BIOS seleccionar qué rígido arranca primero, y así arranca Linux o Windows, según qué selecciono como primero en la lista de prioridad de booteo. 
O sea, los dos sistemas funcionan bien por separado.
Pero... evidentemente estoy haciendo algo mal con la configuración del grub porque no me da la opción de arrancar con windows, es como si se pasara de largo cuando arranco con el disco con linux. 
Edité menu.lst tal cual me recomendaron, pero no funciona. Es raro, de última me conformo con seleccionar desde el bios, no es que Windows lo use todo el tiempo, pero me gustaría aprender a configurar bien el grub..
Gracias por la paciencia... saludos

---

### Post by faktorqm on 2008-05-08
Bueno josha, ahora por lo menos sabemos que el problema solo reside en el grub, hace una cosa, postea la salida de estos dos comandos de vuelta a ver que esta pasando luego de los cambios.

```
sudo fdisk -l
```
```
cat /boot/grub/menu.lst
```

No lo cortes, postealo entero asi como sale, o tira los dos comandos juntos, y pone todo entero entre tags de code obvio. Salu2!

---

### Post by vk-cdg on 2008-05-08
Bueeeeenas.... permisoooo....
Bueno, nada, me meto en el thread para simplemente agradecer (agregué los thanks correspondientes) por la clara explicación, ya que en unos pocos días voy a estar en la misma situación. 
Mi disco de Windows murió así que lo saqué para ir a cambiarlo (por suerte está en garantía), la cosa es que ahí estaba mi grub por lo que me quedé sin arranque. Decidí reinstalar actualizando a Hardy (gracias por hacerme separar el /home) así que ahora solo tengo linux. 

La semana que viene cuando me den el disco de reemplazo no sabía que maniobra tenía que hacer así que este post me vino de perillas.

Mi solución será, desenchufar el disco de linux, instalar el SO de Bill, luego enchufar nuevamente a Tux y modificar el grub agregando la opción de XP para que apunte al disco nuevo.

Otra vez Faktor, Mauro y Sajnox unos capos. 
Clap clap clap.

---

### Post by sajnox on 2008-05-08
Otra cosa mas, no descarten la opcion de tener un disco para los sistemas operativos y otro para los datos. Yo lo tengo asi en mi maquina y la verdad que me siento mucho mas seguro.

Como ahora solo entro a windows para jugar un poco el disco de datos lo deje en ext3 y lo accedo desde windows con el driver, pero para los que recien empiezan lo pueden dejar en ntfs y accederlo desde Ubuntu tranquilamente.

Son distintas formas nada mas.

---

### Post by Luciano Cossettini on 2008-05-08
Bueno, acá va... es largo.

En el final de todo está agregado lo que me sugirieron pero igual se pasa de largo el menu del grub y carga Ubuntu directamente...
Espero poder solucionarlo, nuevamente gracias.
Saluts 



```
luciano@Alter-Ego:~$ sudo fdisk -l
[sudo] password for luciano: 

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xdf97df97

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extendida
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disco /dev/sdb: 8455 MB, 8455200768 bytes
255 cabezas, 63 sectores/pista, 1027 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3ce13ce0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        1026     8241313+   7  HPFS/NTFS
luciano@Alter-Ego:~$ cat /boot/grub/menu.lst
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
timeout		3

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
# kopt=root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title		Otros sistemas operativos:
root

title		Windows XP Professional SP2
root		(hd1,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
luciano@Alter-Ego:~$ 

```

---

### Post by maxkcr on 2008-05-08
hola, a ver si entendi con lo poco que pude leer de este tema:

yo tenia en mi maq un disco de 80gb particionado en 20gb para windows los restantes 60 como unidad de datos ntfs
mi intencio fue particionar esta ultima en 30 y 30 para en una de ellas instalar ubuntu pero desde que lo hice no tengo la posibilidad de volver a iniciar en windows
puse, como explicaron, en el terminal sudo fdisk -l y me aparece:

 
Disco /dev/hdc: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdc1   *           1        9541    76638051   83  Linux
/dev/hdc2            9542        9729     1510110    5  Extendida
/dev/hdc5            9542        9729     1510078+  82  Linux swap / Solaris
imaginario@imaginario-desktop:~$ 

esto quiere decir que en lugar de intalar ubuntu en una particion de 30 lo hice en todo el disoc de 80 no??? o sea que perdi todo lo que tenia en windows??? porque cuando voy a Equipo solo me aparece una unidad de disco y hasta el momento no podia saber de que capacidad

si esto es asi como supongo, que me recomiendan para lograr la configuracion que queria?
creo primero las tres particiones (dos ntfs y una ext2)? y despues que instalo primero, windows xp o ubuntu?

---

### Post by sajnox on 2008-05-08
maxkcr

Por lo que se ve, es como decis, pisaste la instalacion de Windows y escribiste encima por lo que va a ser muy dificil que recuperes algo de ahi.

Para lograr lo que queres, tener instalados los dos sistemas operativos te recomiendo que hagas lo siguiente.

1) Arranca la maquina con el Live CD
2) Arranca el programa que se llama Editor de Particiones (no recuerdo el nombre precisamente), sino lo encontras alt + f2 y escribis gparted (es muy similar al partition magic)
3) Creas dos particiones mas en formato ntfs (una para datos y otra para windows). IMPORTANTE Una de las dos particiones tiene que ser primaria y no logica, no podes instalar windows en una particion logica.
4) Apagas la maquina y instalas windows
5) Cuando reincies la maquina no vas a poder arrancar ubuntu ya que windows te va a escribir el MBR y vas a tener que reparar el grub
6) Arrancas con un Live CD y recuperar el grub siguiendo este tutorial [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB) (te indica dos formas de hacerlo, cualquiera de las dos es facil y buena)
7) Si al arrancar la maquina el Grub no tiene la opcion de arrancar windows te lees todo este thread de nuevo y editas el menu.lst agregando windows

Saludos

---

### Post by sajnox on 2008-05-08
Luciano,

Esta parte

```
title		Otros sistemas operativos:
root

title		Windows XP Professional SP2
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

Reemplazala por esto

```
title		Otros sistemas operativos:

title		Windows XP Professional SP2
root		(hd1,0)
makeactive
chainloader	+1
```

---

### Post by phxnd on 2008-05-08
> **Mauro22 said:**
> Lo negro cambialo de acuerdo a tu caso.

voy a tomar mi propio criterio y asumir que make active es para hacer la particon por default, cosa que no quiero, y el chainloader +1 ni idea,,,, pero no tengo que agrgarle una dire en el kernel? osea,
cuando booteas ubuntu le pones en root la particion, y en kernel y initrd dos direcciones, no hace falta ponerle ninguna para windows O_o

voy a intentar saludos!

---

### Post by sajnox on 2008-05-08
Si bien no tengo muy en claro que hace makeactive, te aseguro que no lo hace que sea la particion por default (yo lo tengo asi y la particion de windows no es la particion por default)

Para manejarte mejor con el grub te aconsejo que instales el administrador de arranque

```
sudo apt-get install startupmanager

```

---

### Post by faktorqm on 2008-05-08
Luciano:

```

default		0 # este es el que te va arrancar por defecto
timeout		10 # con esto le digo que tarde 10 segundos en arrancar

# esta es la entrada numero <cero> (por defecto)
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

# esta es la entrada numero <uno>
title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f5bb9da1-2bcf-41d8-a70b-b7a20622ee8c ro single
initrd /boot/initrd.img-2.6.24-16-generic

# esta es la entrada numero <dos>
title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

# esta es la entrada numero <tres>
title		Otros sistemas operativos:

# esta es la entrada numero <cuatro>
title		Windows XP Professional SP2
root		(hd1,0)
makeactive
chainloader	+1

```

Ahi te modifique el menu.lst para lo que necesitas vos. Lo que tenes que hacer es, "sudo gedit /boot/grub/menu.lst" y copiar y pegar eso. El resto no sirve, son solo comentarios.

Antes no te lo mostraba por que tenias la opcion hiddenmenu sin comentar. Entonces te arranca justamente como su nombre lo dice sin mostrarte el menu para elegir el SO.

SAJNOX: 

13.3.33 savedefault
&#8212; Command: savedefault num

Save the current menu entry or num if specified as a default entry. Here is an example: 
          default saved
          timeout 10
          
          title GNU/Linux
          root (hd0,0)
          kernel /boot/vmlinuz root=/dev/sda1 vga=ext
          initrd /boot/initrd
          savedefault
          
          title FreeBSD
          root (hd0,a)
          kernel /boot/loader
          savedefault
     

With this configuration, GRUB will choose the entry booted previously as the default entry.

Que significa:

13.3.33 savedefault
- Comando: savedefault

Guarda la entrada de menu actual o un numero (si fue especificado un numero) como entrada por defecto. Ejemplo:

          default saved
          timeout 10
          
          title GNU/Linux
          root (hd0,0)
          kernel /boot/vmlinuz root=/dev/sda1 vga=ext
          initrd /boot/initrd
          savedefault
          
          title FreeBSD
          root (hd0,a)
          kernel /boot/loader
          savedefault

Con esta configuracion, GRUB elegirá la última entrada seleccionada de booteo como la entrada por defecto.

O sea, con esa configuración, si la última vez arrancaste linux, arranca solo en linux la proxima vez. Si arrancaste en otro, arrancará en ese otro la proxima.

El root abajo del title me parece que estaba de más, pero no estoy seguro. En la documentación dice que es para otra cosa, pero nunca dice que pasa cuando no le pasas ningun parámetro.

maxkcr:

Otra opinión aparte de la de sajnox, considerando que tenes ganas de instalar todo de vuelta.

1) mete el cd de windows xp, y borra todas las particiones (sino podes arranca el live de ubuntu, borra todo, aplica los cambios y reinicia)
y ponele a él una sola única de 20gb.
Termina la instalacion todo. 
2) Agarra el cd de ubuntu, y eligiendo particionado manual create una de 10gb contigua de la de windows, PRIMARIA, y montala como "/", y formateala como ext3.
Despues hacé otra contigua a esa, del resto que te quede (acordate de guardar 2gb para swap) PRIMARIA, ext3, y montala como "/home".
La última y cuarta particion, swap.
Entonces te queda:

particion 1: windows, ntfs, primaria, 20gb, montada como /media/windows
particion 2: linux, ext3, primaria, 10gb, montada como /
particion 3: datos, ext3, primaria, 48gb, montada como /home
particion 4: intercambio, primaria, 2gb, no se monta.

todo suma 80gb xD

3) Termina de instalar ubuntu como si nada hubiera pasado. Cuando reinicies vas a poder acceder a los dos sistemas. Ahora arranca en windows y visita esta pagina: [http://www.fs-driver.org/](http://www.fs-driver.org/) e instala el driver para ext2/3, y ahi vas a poder poner como una unidad (ejemplo: f: ) a tu /home de linux, o sea, a tus datos. Tambien podes poner en la g: el / de linux, pero tenes cuidado con eso. (lo viru viteh!)

Listo el pollo. Accedes dese los dos sistemas a ambos datos y particiones de datos.

phxnd: NUNCA nunca nunca asumas tu criterio. Lee la documentacion y luego si lo crees conveniente asumi tu criterio si no hay documentacion al respecto.

13.3.22 makeactive
&#8212; Command: makeactive

Set the active partition on the root disk to GRUB's root device. This command is limited to primary PC partitions on a hard disk.

Que significa: 

13.3.22 makeactive
&#8212; Comando: makeactive

Setea la particion activa del disco raiz al disco raiz del GRUB. Este comando esta limitado por las particiones primarias PC en un disco rigido.

O sea, pone la particion activa de boteo al particion que debe bootear el grub para que arranque. Lo del chain loader +1 es mucho mas complejo de explicar, asi que te lo debo por este post.

Bibliografia consultada:

Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Espero que les haya servido a todos. Espero que entiendan todo y me posteen con parrafos contentos de que todo anduvo bien. Salu2!!

p.d.: ahh me olvidaba o por si no lo vieron:
Documentacion on-line del sitio de grub: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by Hei Ku on 2008-05-08
Faktor, lo comentado es lo que usa el update-grub para rearmar el menu.lst cuando hace update de kernel. O sea, lo mas probable es que si actualiza el kernel le haga bolsa el menu.
Lo recomendable es que modifique las opciones, en la parte comentada, y despues corra el update-grub.
Es un error comun porque al aparecer comentado pareciera que no se usa, no se por que lo hicieron asi, de forma tan poco clara para editar.

---

### Post by faktorqm on 2008-05-09
ahh o sea que eso explicaria por que cada vez que hago update de kernel me aparecen los comentarios de vuelta? 

en el man update-grub dice:

update-grub is a program used to generate the menu.lst file used by the grub bootloader.  It works by looking in /boot for all files which start with "vmlinuz-". They will be treated as kernels, and grub menu entries will be created for each. It will also create the initial menu.lst if none exists, after prompting the user.

o sea: 

update-grub es un programa utilizado para generar el archivo menu.lst usado por el cargador de arranque GRUB. Éste trabaja buscando todos los archivos que comienzan con "vmlinuz-" dentro del directorio /boot.
Éstos archivos serán tomados como núcleos, y se crearan para cada uno entradas de menu de GRUB. También creará el menu.lst si éste no existe, después de preguntarle al usuario.

Ahora bien, tomando esto como valor de verdad, no me estaría poniendo como entradas en el menu de GRUB los otros sistemas operativos, es este caso no se estaría cumpliendo con el pedido aca de luciano que quiere arrancar en windows. 
Pasando en limpio, te crea un menu.lst si no existe nuevo, y si existe uno te lo actualiza agregandole el nuevo kernel digamos. 
Hei ku, vos, yo o los dos estamos equivocados :D :lolflag:

---

### Post by phxnd on 2008-05-09
> **faktorqm said:**
> 
phxnd: NUNCA nunca nunca asumas tu criterio. Lee la documentacion y luego si lo crees conveniente asumi tu criterio si no hay documentacion al respecto.


antes de creerle a siegas a alguien tomo mi propio criterio, sino seria un estupido que actuaria sin pensar....

aedmas si ponia el savedefault como decian si me la cambiaba al boot default

buen de todas formas ya me quedo lindo XD

gracias a todos por su ayuda,,, suertee

---

### Post by maxkcr on 2008-05-09
> **sajnox said:**
> maxkcr

Por lo que se ve, es como decis, pisaste la instalacion de Windows y escribiste encima por lo que va a ser muy dificil que recuperes algo de ahi.

Para lograr lo que queres, tener instalados los dos sistemas operativos te recomiendo que hagas lo siguiente.

1) Arranca la maquina con el Live CD
2) Arranca el programa que se llama Editor de Particiones (no recuerdo el nombre precisamente), sino lo encontras alt + f2 y escribis gparted (es muy similar al partition magic)
3) Creas dos particiones mas en formato ntfs (una para datos y otra para windows). IMPORTANTE Una de las dos particiones tiene que ser primaria y no logica, no podes instalar windows en una particion logica.
4) Apagas la maquina y instalas windows
5) Cuando reincies la maquina no vas a poder arrancar ubuntu ya que windows te va a escribir el MBR y vas a tener que reparar el grub
6) Arrancas con un Live CD y recuperar el grub siguiendo este tutorial [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB) (te indica dos formas de hacerlo, cualquiera de las dos es facil y buena)
7) Si al arrancar la maquina el Grub no tiene la opcion de arrancar windows te lees todo este thread de nuevo y editas el menu.lst agregando windows

Saludos

AAAHHH ok
mi gran duda era si podia reconfigurar las particiones desde ubuntu pq yo lo habia hacho con el partition magic en windows. yo estaba pensando en que capaz que tenia que iniciar el sistema con el cd de windows y ya se que con windows no voy apoder crear la particion en formato para linux 

muchas gracias!

---

### Post by faktorqm on 2008-05-09
> **phxnd said:**
> antes de creerle a siegas a alguien tomo mi propio criterio, sino seria un estupido que actuaria sin pensar....


AAAHHHH LISTOOOOOOOOO!!!

---

### Post by phxnd on 2008-05-10
> **faktorqm said:**
> AAAHHHH LISTOOOOOOOOO!!!

POBRESITO...

---

### Post by vk-cdg on 2008-05-11
Bueno, como no podía ser de otra forma, tengo un problema con esto.

Me devolvieron el disco así que procedí como decía en un post mas arriba, desconecté el HD de linux, instalé windows en el disco correspondiente y luego de terminado volví a conectar el de linux, y modifiqué el menu.ls

El fdisk-l me queda así:

```
Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3f1f3f1e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       30401   244196001    5  Extendida
/dev/sda5           30159       30401     1951866   82  Linux swap / Solaris
/dev/sda6            2433       30158   222709063+  83  Linux
/dev/sda7               1        2431    19526913   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4b8b4b8a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS
```

El cat del menú.ls es este:

```
## default num
default		0

## timeout sec
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=08549639-bc1d-4dd9-a521-92fa96276846 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

title		Otros sistemas operativos:

title		Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

La cosa es que cuando elijo la opción de Ubuntu, todo va bien, levanta lo mas bien, pero cuando elijo la opción de Windows se queda ahí, me muestra un "Loading..." pero no pasa de ahí.
Cambiando el disco predeterminado desde el BIOS, puedo levantar windows normalmente, por lo que los archivos de arranque los tiene.

Debe ser una gilada, pero lo veo y no me doy cuenta.

---

### Post by Mauro22 on 2008-05-11
Yo lo tengo asi:

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        MS Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


---

### Post by faktorqm on 2008-05-11
> **phxnd said:**
> POBRESITO...

Pobrecito va con C. Te llevaste lengua a marzo campeón? 
Igual nunca más te voy a volver a contestar un post, pero bueno.

Te cuento, para que lo sepas, que los tipos que escriben la documentación, por lo general son los propios desarrolladores, y saben muy bien lo que están poniendo. Eso de que creer a ciegas es estúpido, si bien es discutible, no aplica a GNU/Linux. Vos no los conocés a todos en el foro y sin embargo aceptas sus respuestas y las tomas como valor de verdad, asi que estás en una contradicción.

---

### Post by vk-cdg on 2008-05-11
> **Mauro22 said:**
> Yo lo tengo asi:

Mil gracias Mauro, una vez mas. Con esto funcionó.

---

### Post by vk-cdg on 2008-05-11
> **faktorqm said:**
> Pobrecito va con C. Te llevaste lengua a marzo campeón? 
Igual nunca más te voy a volver a contestar un post, pero bueno.


Un viejo conocido (o conocido viejo) siempre dice... "No gastes pólvora en chimangos, que solos por su propio peso caen"

---

### Post by euzkoarima on 2008-05-12
> **phxnd said:**
> POBRESITO...

Una de las personas que más ayudan en este foro es faktorqm, a quien tuve el agrado de conocer personalmente en la fiesta de lanzamiento del HH. Si lo que el te contesta no te sirve, ok, no lo apliques. Pero por favor no hagas comentarios que desalienten a los que ayudan (no tanto por este post tuyo que cité, más bien por el anterior). En lo personal no me parece ni productivo, ni justo.

(y para ser consistente, si lo que yo te digo no te parece, olvídalo!)

Saludos

---

### Post by ivannewell on 2009-09-04
pincha....ya te abran j****o varias veces con esto pero estoy super newbie con esto y te veo bastate empapado con esto..... marque los comandos que diste al principio del tema y me sale esto.....para mi instale mal todo pero me gustaria q me des tu diagnostico ....puede ser???????????????????????????



Disco /dev/sda: 20.4 GB, 20411080704 bytes
255 cabezas, 63 sectores/pista, 2481 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa1a4a1a4

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1338      979965   82  Linux swap / Solaris
/dev/sda3            1339        2481     9181147+  83  Linux

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00000001

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        6708    53881978+   7  HPFS/NTFS
/dev/sdb2            6709       19456   102398310    f  W95 Ext'd (LBA)
/dev/sdb5            6709       19456   102398278+   7  HPFS/NTFS





y enel.. cat /boot/grub/menu.lst


n@n-desktop:~$ cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=68d353d8-766d-41ca-a19d-d1b70e4a5593 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=68d353d8-766d-41ca-a19d-d1b70e4a5593 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=68d353d8-766d-41ca-a19d-d1b70e4a5593 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
n@n-desktop:~$ sudo fdisk-l
[sudo] password for n: 
Sorry, try again.
[sudo] password for n: 
sudo: fdisk-l: command not found
n@n-desktop:~$ sudo -l
User n may run the following commands on this host:
    (ALL) ALL
n@n-desktop:~$ n
nbash: n: orden no encontrada
n@n-desktop:~$ n
bash: n: orden no encontrada
n@n-desktop:~$ sudo fdisk -l

Disco /dev/sda: 20.4 GB, 20411080704 bytes
255 cabezas, 63 sectores/pista, 2481 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa1a4a1a4

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1338      979965   82  Linux swap / Solaris
/dev/sda3            1339        2481     9181147+  83  Linux

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00000001

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        6708    53881978+   7  HPFS/NTFS
/dev/sdb2            6709       19456   102398310    f  W95 Ext'd (LBA)
/dev/sdb5            6709       19456   102398278+   7  HPFS/NTFS
n@n-desktop:~$ 
n@n-desktop:~$ cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=68d353d8-766d-41ca-a19d-d1b70e4a5593 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=68d353d8-766d-41ca-a19d-d1b70e4a5593 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=68d353d8-766d-41ca-a19d-d1b70e4a5593 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



por favor ...preciso q me tiren un diagnostico

---

