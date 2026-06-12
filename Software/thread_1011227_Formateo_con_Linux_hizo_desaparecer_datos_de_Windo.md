---
title: "Formateo con Linux hizo desaparecer datos de Windows"
date: 2008-12-14
forum: Software
---

### Post by Vero1 on 2008-12-14
Saludos a todos,

Sé que no nos gusta hablar de Windows pero como familiares lo usan...

Pasó así: Tengo un disco de 80 Gb que tenía 3 particiones. Dos ocupadas y una que quise formatear para instalar Fedora.
Instalé Fedora en esa partición pero el Grub no me mostraba ningun otro sistema operativo y entraba directamente a Fedora. Las particiones de Windows habían desaparecido.
Hice un sudo gparted y la respuesta fue que se ven dos particiones pero dice que el sistema de ficheros es desconocido. Estas particiones están desmontadas. Ahora, cuando hago click en alguna y miro Propiedades, dice que tiene sistema DOS y otros datos, o sea que no están vacías pero no puedo ingresar. Por otro lado cuando en gparted veo esas particiones dice: boot-lvm. La verdad es que necesito recuperar los datos de esas particiones.
Me sugirieron utilizar el GParted livCD que contiene un programa de recuperación llamado TestDisk o algo así.
Quisiera una opinión de ustedes a ver qué me conviene hacer.

Desde ya muchas gracias.

---

### Post by sajnox on 2008-12-14
Hola,

Para empezar deberiamos saber si efectivamente borraste la particiones de windows o solamente no estan en el grub

Podes postear la salida del comando 

```
sudo fdisk -l

```

Te aclaro que el sudo funciona en ubuntu, no se como es con fedora...calculo que tenes que estar logueado como root

---

### Post by Vero1 on 2008-12-14
Hola sajnox,

Me olvidé de aclarar que hice desaparecer Fedora porque no podía entrar ni en Ubuntu Hardy(que tenía) ni en Windows y luego instalé Intrepid Ibex,donde estoy ahora.

el comando que me diste dió este resultado.

Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4f744f74

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4811    38644326   83  Linux
/dev/sda2            4812        4998     1502077+   5  Extendida
/dev/sda5            4812        4998     1502046   82  Linux swap / Solaris

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa340a340

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1          25      200781   83  Linux
/dev/sdb2   *          26        9729    77947380   8e  Linux LVM

El disco con problemas es sdb.

Aclaro que en el Grub figura Windows, pero sin XP y cuando quiero bootear me contesta que no puede leer esa partición.

Gracias y saludos

---

### Post by gmunioz on 2008-12-15
Hola ver....:
Lamento informarte que la instalación de Fedora, se cargó tus particiones de Microsoft, además particionó con sistema lvm, es el acrónimo de logical volume management, que en español significa administración de volúmenes lógicos. Un sistema de avanzada que permite darle a las particiones un tamaño aproximado y luego irlo redimensionando por demanda pudiendo realizar éstas operaciones en caliente. El problema que acceder a esas particiones desde otro operativo requiere un trabajo importante y trabajoso. No obstante esto lo importante es que Fedora te eliminó el sistema de Microsoft y a todas luces es irrecuperable.
[B]Saludos.
Gabriel.
Solo doy soporte para Ubuntu[/B] - *Conozco muchas frases ingeniosas*, *pero no las recuerdo* - **Alzheimer.**

---

### Post by Vero1 on 2008-12-15
Hola Gabriel,

Decís que lo importante es que Fedora me eliminó Microsoft pero pasa que mis familiares SI lo usan. Personalmente creo que no eliminó nada porque en Propiedades dice que los archivos son de DOS...y lo mas probable es que estén invisibles. Es mas, en un informe, ya no recuerdo cual, decía que el ingreso a SDB1 estaba prohibido.
En fin, agradezco tus comentarios.

Saludos

---

### Post by guisheca on 2008-12-15
> **Vero1 said:**
> Hola Gabriel,

Decís que lo importante es que Fedora me eliminó Microsoft pero pasa que mis familiares SI lo usan. Personalmente creo que no eliminó nada porque en Propiedades dice que los archivos son de DOS...y lo mas probable es que estén invisibles. Es mas, en un informe, ya no recuerdo cual, decía que el ingreso a SDB1 estaba prohibido.
En fin, agradezco tus comentarios.

Saludos

A lo que se refiere Gabriel es que el punto es que perdiste tu partición de win y no la explicación sobre LVM que te dió. No es que se alegre porque hayas perdido tus particiones, de hecho creo que nadie crea conveniente una perdida de datos de ningún tipo.
Y concuerdo con el en que lamentablemente el problema es que se borró todo lo que había en la partición de win. Aunque sería de mucha ayuda para saber lo que pasó, que nos digas exactamente que pasos seguiste para instalar fedora en tu disco.
Saludos.

---

### Post by nicolastroche on 2008-12-15
Hola Vero ... no soy experto en linux, de hecho, no hay nada que se aleje más de la realidad ... pero por experiencia propia, puede ser que el sdb no esté montado ... algo que me há pasado por ejemplo con ubuntu 8.04. Fijate si te dice que precisas iniciar sesión desde root o algo similar. Por cierto, te recomendaría que trates de sacar todo de Fedora (hacer backup) y meter Ubuntu, formateando la partición de Fedora. Por ahí de esa forma podes acceder de nuevo y se te acomoda todo, ya que el formato es ext3, y además, te toma las particiones ntfs.
Si te sirve de algo, me alegro ... yo tuve problemas con ubuntu, y la única forma de solucionarlo fue reinstalando desde dapper drake, y actualizandolo nuevamente (Al menos, fue lo primero que se me ocurrió, y lo acomodé).

---

### Post by Vero1 on 2008-12-15
Hola nicolas,
Efectivamente SDB figura como NO montado.
En cuanto a Fedora, todo esto pasó cuando formateé la partición donde estaba Fedora.
En el Grub aparece Windows pero cuando le pido boot contesta que es desconocido...
Gracias por tu comentario.

saludos

p.d. me pregunto si me atrevo a tratar de montar esas particiones a ver qué pasa y si me deja jaj

---

### Post by Vero1 on 2008-12-15
Hola guisheca,

En ningun momento pensé que Gabriel se hubiera alegrado de lo que me pasó.
No perdí las particiones pues gparted las muestra pero con un signo de advertencia y el recuadro para ajustar es negro.
En otro post me dicen que pueden estar desmontadas y es cierto.

Lo que pasó fue que instalé Fedora en el disco donde está win, en una partición vacía. 
Como despues Fedora se apropió del Grub, al bootear directamente iba a Fedora y no me daba posibilidad de entrar en Ubuntu ni Windows, entonces decidí eliminar Fedora formateando esa partición, pero aparentemente se formateó todo el disco.

No creo que los datos estén perdidos ya que cuando marco una partición y miro en Propiedades dice que sus archivos son de DOS y muestra que está ocupada esa partición.

Sería cuestión de intentar montarlas a ver qué pasa?

saludos y gracias

---

### Post by sajnox on 2008-12-15
Vero,

El tema es que el sistema no muestra ninguna particion NTFS o VFAT y ahi solamente podes instalar windows. Por las dudas te aclaro que esto lo ves con las particiones montadas o no montadas.

Por favor postea la salida del comando 

```
cat /boot/grub/menu.lst
```

---

### Post by Vero1 on 2008-12-15
Hola sajnox,
No quiero instalar Windows. Lo que quisiera es recuperar esas particiones con sus datos :-)
No sé si leiste lo que comenté antes sobre las propiedades de estas particiones.

Aquí pego el resultado del comando:

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
# kopt=root=UUID=1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf

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
uuid		1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1bf6c4dd-fa7e-4fb1-a381-d6a11899a7cf
kernel		/boot/memtest86+.bin
quiet

title Windows
rootnoverify (hd1,1)
makeactive
chainloader +1



### END DEBIAN AUTOMAGIC KERNELS LIST

gracias por tus molestias.

saludos

---

### Post by Vero1 on 2008-12-15
Hola sajnox de nuevo.

Te paso un ImageShack de lo que dice en Propiedades de una de las particiones en cuestión. A lo mejor te sirve de algo.

[http://img156.imageshack.us/my.php?image=pantallazo2yp6.png](http://img156.imageshack.us/my.php?image=pantallazo2yp6.png)

saludos

---

### Post by sajnox on 2008-12-15
Varo,

A donde va a buscar a windows seguro no esta, lo busca en el sdb1, y ahi claramente no esta. No se que paso en la instalacion pero por algun motivo Gparted no lo ve. Entiendo que Ubuntu esta instalado en el primer disco (el de 40gb)

Si mal no entiendo la maquina tenia ubuntu en el primer disco (41gb) y en el segundo tenias datos y windows, y ahi quisiste instalar Fedora?? Es asi??

Si fue asi, en algun momento se rompio el esquema de particiones del disco y eso hace imposible que arranque cualquier cosa.

Esperaria que alguno con un poco mas de experiencia te recomiende algun programa para recuperar particiones, y sino evaluaria que lo vea algun tecnico con experiencia, por que me parece que estas complicada.

No por nada se aconseja hacer backup antes de particionar

---

### Post by Vero1 on 2008-12-15
sajnox,

En el disco de 40 Gb desde un principio está ubuntu, exclusivamente y a ese disco no lo toqué para nada.

En el disco de 80 está Windows desde siempre y hasta que se me ocurrió instalar Fedora, tenía 3 particiones, dos ocupadas por win y la tercera libre.
En esa tercera instalé Fedora.
Pero como Fedora no permitía el acceso a ningun otro SO(porque directamente entraba en Fedora), formateé presuntamente esa partición, pero evidentemente hice algo mal y formateó todas las particiones.

En cuanto a algun programa para recuperar particiones, tengo grabado el Gparted LiveCD, donde me dijeron que había un programa llamado TestDisk o algo así que servía para ese fin, pero antes de usar el Gparted Live, quise consultar con Uds.

Ese es el panorama.

En cuanto a llamar algun técnico, hm, no me convence ya que de Linux no saben nada.

Hoy estuve mirando unos floppys que tengo y hay uno que es para arrancar windows, pero no sé podrá servir.

En fin, te agradezco tu buena voluntad y vemos si alguien mas tiene alguna sugerencia.

Saludos ):P

---

### Post by c4d0rn4 on 2008-12-15
> **Vero1 said:**
> Hola sajnox,

Me olvidé de aclarar que hice desaparecer Fedora porque no podía entrar ni en Ubuntu Hardy(que tenía) ni en Windows y luego instalé Intrepid Ibex,donde estoy ahora.

el comando que me diste dió este resultado.

Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4f744f74

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4811    38644326   83  Linux
/dev/sda2            4812        4998     1502077+   5  Extendida
/dev/sda5            4812        4998     1502046   82  Linux swap / Solaris

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa340a340

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1          25      200781   83  Linux
/dev/sdb2   *          26        9729    77947380   8e  Linux LVM

El disco con problemas es sdb.

Aclaro que en el Grub figura Windows, pero sin XP y cuando quiero bootear me contesta que no puede leer esa partición.

Gracias y saludos

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd252d252

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3456    27760288+   7  **HPFS/NTFS**
Partition 1 does not end on cylinder boundary.
/dev/sda2            3457        4865    11317792+   f  W95 Ext'd (LBA)
/dev/sda5            3457        3892     3500248+  83  Linux
/dev/sda6            3893        4817     7430031   83  Linux
/dev/sda7            4818        4865      385528+  82  Linux swap / Solaris
```

Tan solo con esa información que pusiste antes se ve que no hay particiones del tipo de windows. Sean las ntfs o las variantes de fat.

La solución, si es que la hay, algún programa muy especifico o algún técnico en recuperación de hd. La verdad desconozco que hayas programas así, pero lo último que se pierde es la esperanza.

por lo pronto te diría que dejes de usar el disco ese.

---

### Post by Vero1 on 2008-12-15
Hola c4,

Hay un programa que forma parte del Gparted Live-Cd, tengo entendido y ya lo tengo en mi escritorio para quemarlo en un CD, pero antes quería la opinión de ustedes.

Ese disco no lo puedo usar para nada, ya que no puedo entrar.

Agradezco tu comentario.

saludos

---

### Post by juanman on 2008-12-15
Hola Vero1, efectivamente te recomendaría que pruebes con testdisk. Es un programa libre, disponible para Linux, estable, no tan dificil de usar (hay herramientas avanzadas como autospy mas complicadas) y es ideal para recuperar particiones perdidas. Aparte se puede probar para q haga un analisis sin tocar el disco...
Si no encuentra ninguna particion, podes probar con photorec (q forma parte de testdisk tambien) y no solo sirve para recuperar fotos, sino unos cuantos tipos de archivos mas...
Testdisk esta en los repositorios asi q lo podes instalar con synaptic...
Despues lo ejecutas desde una terminal con:
- sudo testdisk
- Le das a create log.
- Elegis el disco (te moves con las flechitas del teclado y enter)
- En tipo de tabla de particion, elegis Intel
- Y vas a Analyse
- Despues Quick Search
Y tal vez te haga unas preguntas y te detecte las particiones... Si la detecta, apretando p se pueden ir viendo los archivos y copiandolos o apretando enter vas a tener la posibilidad de escribir la tabla de particiones para q se vuelvan a ver como estaban antes...

En la web de testdisk tenes algunos tutoriales [http://www.cgsecurity.org/wiki/TestDisk_ES](http://www.cgsecurity.org/wiki/TestDisk_ES)

Pregunta por cualquier cosa... Es muy probable q surjan dudas...
PD: desde q no entras al #ubuntu-ar-cafe, el canal esta re muerto (a /me se le pianta un lagrimon)

---

### Post by Vero1 on 2008-12-16
Hola ):P

Te agradezco mucho tu comentario. No sabía que TestDisk estuviera en los repos.
Tengo un montón de dudas con respecto a ésto que me pasó, porque creo que esas particiones no están vacías pero imposible entrar en Windows para usar el CD de instalación donde se puede pedir reparación, porque el formateo que usé para esa partición de Fedora era ext3 y por supuesto Windows no lo puede leer.

Bueno, pasaré por la Web de TestDisk a leer un poco lo que dice.

Gracias por las instrucciones y link que me das.

Saludos

p.d.
En lo que respecta a que no entro mas en ubuntu-ar-cafe es porque se había vuelto muy desagradable para mi, por malas palabras, etc.
y que no se te piante un lagrimón(jaj). Estás invitado al canal #supremos que es mucho mas agradable y hay unos cuantos argentinos.

---

### Post by Vero1 on 2008-12-16
Hola Juanma,

Aquí de nuevo, ya que dijiste que pregunte, pregunto :-P

Es sobre el cambio de Type.

Por ejemplo, en la partición que presuntamente debería bootear, dice *P Linux LVM. Eso habría que cambiarlo por FAT32 no? Si es así se cambia en Advanced.(según leí el asterisco significa booteo)

Yo hice la prueba y me pregunta si actualmente es 83.(eso cuando le indiqué FAT32) Me fuí a 83(que está en una lista) y dice Linux. Quiere decir que está comprobando que actualmente es Linux y me pregunta?

No creas que no leí el tutorial, pero no me siento muy segura de hacer las cosas como corresponde.

Supongo que vos has usado ya este programa no?

Bueno, espero que leas este post y me saques la duda.

):P

---

### Post by MeduZa on 2008-12-16
no perdiste nada aun, los datos estan en el plato del disco
podes recuperarlos pero vas a necesitar alguna erramienta que lea el disco

---

### Post by Vero1 on 2008-12-16
Hola Meduza,

Justamente estoy por usar un programa que se llama TestDisk pero tengo mis dudas.
Con un poco de suerte Juanman que me lo recomendó, me ayudará.

Gracias y saludos

---

