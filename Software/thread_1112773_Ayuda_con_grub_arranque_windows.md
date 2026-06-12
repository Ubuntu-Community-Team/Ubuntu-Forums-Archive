---
title: "Ayuda con grub arranque windows"
date: 2009-04-01
forum: Software
---

### Post by mcarla on 2009-04-01
hola, soy nueva en ubuntu, espero que puedan ayudarme, les cuento mi situación: Tenía Ubuntu 6.06 y Windows XP corriendo perfectamente en un disco IDE, iniciando mediante el grub, pero tuve que cambiar el disco y puse uno con Win 98, al cambiar de nuevo el disco podía iniciar Ubuntu pero no Win. Probé muchas cosas,como poner rootnoverify, pero no pude hacer nada. También probé con el Super Grub Disk, pero al iniciar Win me tira 

Error 13: "Invalid or unsupported executable format"

y busqué el error en google pero nada se asemeja a mi situación. Este es mi último recurso, tengo algunos archivos valiosos y no quiero formatear el disco, y no tengo el cd de win para recuperar el MBR. 

Les dejo mis fdisk -l y mi menu.lst a ver si me pueden guiar, ya que no se me ocurre más nada.

```

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/hda2            4257        9726    43937775   83  Linux

Disk /dev/sda: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          16        7748     1979456    e  W95 FAT16 (LBA)


```

El /dev/sda es porque tengo un pendrive conectado

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-51-server
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-server root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-server
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-server (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-server root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-51-server
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Perdón si se hizo muy largo, pero estoy casi rendida. Gracias y espero que  el problema tenga arreglo.

---

### Post by staar on 2009-04-01
una pregunta... cuando volviste a poner el disco, verificaste que el jumper (master o slave) estuviera seteado como antes?...
saludos

---

### Post by pablo.s on 2009-04-01
Hola: Por lo que veo de menu.lst está correcto. ¿Recordás si cuando
cerraste por última vez Windows se cerró bien? Como está en una
partición NTFS es posible que si se ha apagado sin desmontar bien
te dé errores para iniciar. ¿Desde Ubuntu podés montar la partición,
podés ver los datos? Saludos.

---

### Post by gmunioz on 2009-04-01
Hola mca....:

La lectura de tu post evidencia datos algo inconsistentes, ya que:

Dices: *"....tuve que cambiar el disco y puse uno con Win 98...."*

Y pegas la salida de tu fdisk entre cuyos datos resalta:

*"..../dev/hda1  *   1   4256  34186288+ 7  HPFS/NTFS..."*

Hasta donde se, que no es mucho, Windows 98 no reconoce el sistema de archivos ntfs.

Saludos.

---

### Post by mcarla on 2009-04-01
Hola, ante todo gracias staar y pablo.s por contestar. Explico mejor mi situación porque en ese momento estaba muuuuuy cansada y confundí algunas cosas. 
Problema 1: En realidad no cambié los discos, puse el de Win 98 junto con el que tengo win XP y Ubuntu (o sea que tuve los dos discos conectados al mismo tiempo). Yo quería iniciar Win XP y que éste me reconociera el disco de Win 98, (ya lo había hecho sin problemas) pero ésta vez directamente inició Win 98. Al ver esto cambié la conexión del disco con Win 98, inicio el equipo y selecciono en el grub Win XP, me muestra las líneas 

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

y se queda muerto. 

Problema 2: Mediante el Super Grub Disk, recuperé el MBR de Win y borró el grub, pero al iniciar también se queda muerto, no muestra nada. Luego al ingresar a Ubuntu no me reconoce la partición de Windows, que antes de ejecutar el Super Grub la reconocía sin problemas.
Recuperé el grub nuevamente y a Ubuntu lo ejecuta sin problemas, pero al seleccionar Xp me muestra el error 13.

Gracias por la paciencia y espero que me puedan ayudar:p

---

### Post by pablo.s on 2009-04-01
Hola: Evidentemente era lo que sospechaba. 
Hay dos maneras para recuperar la información de
Windows. Una es montar la partición desde Ubuntu
pero forzandola a que se monte. Fijate si tenés el
paquete ntfs-3g.
Otra manera es arrancando con el disco de instalación
de Windows, poner modo de recuperación y hacer
chkdsk /f /r.
Lo mas probable es que si lográs montar desde 
Ubuntu copies la información antes que no se pueda
acceder mas a la partición.
Saludos.

---

### Post by infernus92 on 2009-04-01
yo tuve un problema similar con 2 discos, en uno window$ y en el otro ubuntu... al final el problema era que se habia cambiado el orden de arranque de los discos desde la BIOS
basto con entrar al BIOSconfig apenas inicia la computadora y arreglar eso... y me decia lo mismo que te dice a vos cuando intentaba iniciar con window$... espero que te sirva

Saludos

---

### Post by gmunioz on 2009-04-01
Hola mca....:

Sugerencia:

1- Desconecta de la alimentación y del cable ide el disco con Windows 98 y deja solo el disco con Windoxs XP y Ubuntu enchufado en el extremo de la manguera con los jumpers seteados como master.

2- Inicia con Ubuntu e instala las ntfsprogs, a continuación ejecuta repetidas veces ntfsfix para corregir el sistema de archivos de Windows XP y por último luego de cerrar la sesión de Ubuntu intenta iniciar con Windows XP. 

3- Para el caso de que no puedas iniciar con ninguno de los dos operativos, reinstala con el Super Grub disk el Grub.

4- Una vez que esten funcionando correctamente los dos operativos, reconecta el disco de Windows 98, tomando la precaución de enchufarlo en el conector del medio del cable ide previo colocar sus jumpers seteados como slave.

5- Reinicia con Ubuntu, monta el nuevo disco, rescata tus archivos y dale un formato con un sistema de archivos Linux si solo piensas acceder a los archivos desde Ubuntu, o de Microsoft (ntfs) si los has de acceder desde Windows XP.

Saludos.

---

### Post by infernus92 on 2009-04-01
dip-switch?? ****************... pero hace mas de 10 años que no se usan los dip-switch en computacion... se usan jumpers desde que me acuerdo...
creo que vi un disco de 200Mb que ya venia con jumpers...

ah... y con desconectar la alimentacion alcanza... sin energia no se puede transferir informacion...

saludos

---

### Post by mcarla on 2009-04-03
Hola, gracias a todos por contestar.

Para pablo.s: el paquete ntfs-3g no lo tenía, pero seguí el tutorial de esta página para conseguirlo

[http://www.versvs.net/anotacion/como-instalar-ntfs-3g-en-ubuntu-y-escribir-en-particiones-windows-desde-linux](http://www.versvs.net/anotacion/como-instalar-ntfs-3g-en-ubuntu-y-escribir-en-particiones-windows-desde-linux)

y seguí los pasos que se indicaban, pero apareció este error:

mount: unknown filesystem type 'ntfs-3g'

ni idea porqué. Hacer chkdsk no puedo, no tengo el cd de instalación de Win.

Para infernus92: a qué te referís con BIOSconfig? Al setup del BIOS?O es un programa que se llama BIOSconfig?

Para gmunioz: el disco de Win 98 lo saqué hace rato, y no lo quiero poner de nuevo, sólo lo necesitaba para un momento. Igual ejecuté ntfsfix y salió el siguiente error:

Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument
Volume is corrupt. You should run chkdsk.

Espero que me puedan seguir ayudando porque estoy muy perdida.

Saludos!!!

---

### Post by gmunioz on 2009-04-04
Hola mca...:

¡Proporcionas los datos con cuentagotas! :)

Navega hasta:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Descarga este archivo:

[http://www.rloe.com/ken/xpquick.zip](http://www.rloe.com/ken/xpquick.zip)

En un disquete formateado desde cualquier Windows, 98, nt, 2000, xp
copia los archivos que se encuentran en ese zip:
boot.ini
ntdetect.com
ntldr


Inicia el ordenador con ese disquete

Cambia al disco c:

Busca el archivo chkdsk en la instalación de windows

Ejecuta chkdsk /f

En ese mismo sitio, tienes otros disquetes e isos que pueden ser de interes.

Saludos.
Gabriel.

**6666 - Más Malo Que El Diablo**

---

### Post by infernus92 on 2009-04-04
> **mcarla said:**
> 
Para infernus92: a qué te referís con BIOSconfig? Al setup del BIOS?O es un programa que se llama BIOSconfig?
Saludos!!!


es el setup de la BIOS

Saludos

---

### Post by infernus92 on 2009-04-04
googleando encontre este tutorial que te puede servir

> Recuperar GRUB

De Guía Ubuntu

Saltar a navegación, búsqueda
Uno de los problemas más comunes a lo que se enfrenta un usuario de GNU/Linux es que en caso de instalar o reinstalar un sistema operativo distinto (por ejemplo, Windows), el MBR (Master Boot Record) es reescrito por el del último sistema instalado, borrándonos el GRUB.

Hay dos maneras de recuperar el GRUB: usando Super Grub Disk, o usando una distribución Live que contenga al GRUB.

Tabla de contenidos

[esconder] [esconder]
1 Usando Super Grub Disk
2 Usando una distribución Live
2.1 Mediante el intérprete de comandos GRUB
2.1.1 Opción 1
2.1.2 Opción 2
2.2 Cambiando el origen de la carpeta raíz
3 Ver también
4 Enlaces externos
[editar]
Usando Super Grub Disk

Super Grub Disk es un restaurador del GRUB que se puede instalar en un dispositivo de almacenamiento portátil o externo (disquete, CD, DVD, USB, etc.). Incluye un manual integrado y es muy fácil de usar.

Puedes descargarlo desde el siguiente enlace:

Super Grub Disk 0.9598 (394 kB)
Es una imagen de disco ISO comprimida bajo GZip, necesitarás descomprimirla y luego copiar el contenido de la imagen a un disco externo, se recomienda un disquete de 3 1/2" por su reducido tamaño (para hacerlo en un CD o DVD, puedes usar un quemador de discos como K3b o Brasero).

Al arrancarlo, las opciones que debemos seguir son las siguientes:

Idioma: español
Sistema operativo: Linux
Tarea: Arreglar arranque de Linux (GRUB)
[editar]
Usando una distribución Live

Consiste en usar una distribución en modo LiveCD para instalar nuevamente el GRUB. Usaremos el LiveCD de Ubuntu (debe ser la versión Live o Desktop), aunque puede ser cualquier otra distribución que use GRUB como gestor de arranque y no LILO.

En modo de resumen, los pasos que hay que seguir son los siguientes:

Arrancar una distribución LiveCD
Montar la partición donde se encuentra instalado Ubuntu
Instalar el GRUB en esa partición
A continuación se explica, en unos sencillos pasos, cómo hacerlo:

Iniciamos el ordenador y arrancamos desde el CD
Arrancamos Ubuntu (o la distribución escogida) en modo LiveCD
Abrimos una terminal o consola (no es necesario si tenemos una interfaz de línea de comandos, es decir, en modo texto)
Creamos una carpeta donde montar la partición de Ubuntu (la podemos crear en /media, por ejemplo: /media/ubuntu/)
Montamos la partición donde se encuentra instalado Ubuntu, usando el comando mount.
Aquí hay dos soluciones posibles:
[editar]
Mediante el intérprete de comandos GRUB

[editar]
Opción 1

Ejecutamos los siguientes comandos:
$ sudo grub    --> ejecutamos el intérprete de comandos del GRUB
> root (hdX,Y) --> indicamos dónde está ubicada la partición de Ubuntu
> setup (hdX)  --> instalamos el GRUB en ese disco
> quit         --> salimos del intérprete de comandos del GRUB
Donde X es el número de disco rígido, y Y es el número de partición. Este sistema difiere un poco del usado para montar las particiones en GNU/Linux; ambos son un único número decimal y comienzan en 0; por ejemplo:

hd0: es el primero disco duro completo, al igual que hda o sda
hd0,0: es la primera partición del primer disco duro, al igual que hda1 o sda1
hd0,1: es la segunda partición del primer disco duro, al igual que hda2 o sda2
hd1,2: es la tercera partición del segundo disco duro, al igual que hdb3 o sdb3
El primer disco duro del GRUB es el primer disco duro maestro, el segundo es el primer disco duro esclavo, el tercero es el segundo disco duro maestro, y así sucesivamente.

[editar]
Opción 2

Desde una consola ejecutamos los siguientes comandos:
$ sudo grub                --> ejecutamos el interprete de comando de grub
> find /boot/grub/stage1   --> busca donde esta la partición de ubuntu
> root (hdX,Y)             --> poner el valor devuelto anterior
> setup (hd0)              --> instala grub en nuestro primer disco duro (hd0), 
                               que es con el que inicia la computadora
> quit                     --> salimos del interprete de comando de grub
[editar]
Cambiando el origen de la carpeta raíz

Cambiamos el origen de la carpeta raíz de nuestro sistema de archivos al directorio en el que hemos montado la partición de Ubuntu, para que al instalar GRUB interprete que la raíz del sistema está ahí.

1. Antes que nada, crear un directorio y montar allí la partición de Ubuntu:

$ sudo mkdir /media/ubuntu
$ sudo mount /dev/hda1 /media/ubuntu
2. Luego conectar el directorio dev del livecd con el de la partición Ubuntu:

$ sudo mount --bind /dev /media/ubuntu/dev
3. El comando necesario para cambiar el origen del directorio raiz es:

$ sudo chroot /media/ubuntu/
4. Ahora instalamos el GRUB en el MBR del primer disco duro, que normalmente estará configurado como Primary Master (hda):

# grub-install /dev/hda

no se si vana a ndar o no los link... pero espero que te sirva

Saludos

---

### Post by mcarla on 2009-04-05
Hola, primero, gracias a todos por sus respuestas. Les comento que pude reparar uno de mis problemas mediante el programa Testdisk, ahora Ubuntu ya reconoce la partición de Win XP y la monta al inicio; pero me queda el problema de hacerlo arrancar, ya que como expliqué, al seleccionar Win XP en el grub tira el siguiente error:

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

y se queda muerto. 

Probé con cambiar en el menu.lst a rootnoverify, pero lo único distinto que pasa es que no muestra la línea Filesystem type unknown, partition type 0x7. Podría ser un problema de mala configuración de los parámetros del disco?Digo esto ya que en Testdisk me advertía sobre que el número de cabezas era 16 pero el valor correcto podía ser 255 y no me dejaba avanzar. Cambié el num de cabezas a 255 (el programa tiene una opción para cambiarlo, pero no lo guarda) y ahí sí pude avanzar (en Testdisk). No sé como se cambian los parámetros de configuración del disco en Ubuntu.
Si necesitan más datos o tienen alguna solución o causa de mi problema, consultenmé. 
Saludos!!

---

### Post by pablo.s on 2009-04-05
Hola: La mas facil sería:

1) Hacer backup de los datos de la partición de Windows
2) Instalar Windows nuevamente (mil latigazos en mi espalda,
me los tengo merecidos, o alguna pena similar)
3)Restaurar GRUB

Saludos.

---

### Post by mcarla on 2009-04-05
Hola, sí, sería lo ideal, el tema es que no tengo el cd de instalación, no hay otra forma?

---

### Post by guidito73 on 2009-04-05
EDIT: Ahhhh claro, podés buscar entre tu ropero por el original (no olvides el numero de licencia) e instalarlo. O apostar por el software libre.

---

### Post by Hei Ku on 2009-04-05
Seguramente quisiste decir que puede buscar el original e instalar de acuerdo a los terminos de la licencia, no?
De otra manera, esa sugerencia violaría el Codigo de Conducta de estos foros. ;)

Podés apretar en edit y reformular tu sugerencia. :)

---

### Post by pablo.s on 2009-04-05
Felicitaciones por el post N° 1600!!!

---

### Post by Hei Ku on 2009-04-05
> **pablo.s said:**
> Felicitaciones por el post N° 1600!!!

Off-topic :lolflag:

---

### Post by mcarla on 2009-04-06
Viendo la discusión que se generó por lo legal e ilegal, procedo a aclarar. Yo lo único que quiero es que arranque el Win XP que tengo, vino en la PC ya instalado cuando la compré y no me dieron el CD de instalación. No hay una solución para mi problema sin tener que reinstalar otra vez el SO? Ah, y estoy apostando por el software libre, ya que quiero los 2 SO, es más, mi versión de Ubuntu (6.06 Server) parece que ya es obsoleta y voy a actualizar.

Gracias.

---

### Post by pablo.s on 2009-04-06
No hubo tal discusión aunque parezca. Hay un código de
conducta que hay que seguir aunque a veces a alguna-
alguno se le chispoteen las ideas.
Creo que vas a tener que resignarte en reinstalar el
software privativo antes mencionado. Queda a tu propio
criterio la forma que lo hagas. Parece mala onda pero lo
que queremos en este foro es ver [este bug]("https://bugs.launchpad.net/ubuntu/+bug/1") solucionado.

Para todo lo demás que necesites de ayuda, desde ya
podés contar con nosotros. Saludos.

---

### Post by mcarla on 2009-04-06
Bueno, gracias igual, quería resolverlo por mí misma pero veo que no se puede. Tengo otro problema pero mejor lo pongo en otro post porque es nada que ver con esto. 

Saludos!! y Gracias!!

---

### Post by guidito73 on 2009-04-06
Claro, el tema es que si Windows te vino ya preinstalado y no te dieron el CD entonces no queda mucho que hacer lamentablemente, salvo ir a rajar unas puteadas al tipo que te vendió la máquina, que obviamente te va a querer cobrar por ponerte un Windows pirata seguramente.

Así las cosas, parece lindo momento para saltar al 9.04 o por qué no esperar a que salga Jaunty ;)

---

