---
title: "Problema urgente: Error 22 y Falta NTLDR"
date: 2008-02-21
forum: Software
---

### Post by emiliano_raso on 2008-02-21
Gente... tengo un problema. Instale en la PC de un amigo Ubuntu de la misma manera que lo instale en mi compu, pero cuando termino de instalar reinicio y no aparecia el grub, y booteaba directamente XP.
     Por lo tanto procedi a reparar el grub con el programa que nos da la guia Ubuntu "Super Grub Disk 0.9598" ([http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Usando_Super_Grub_Disk](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Usando_Super_Grub_Disk)).

     Entonces aca viene lo mas raro: ahora aparece el grub, pero cuando quiero ejecutar Ubuntu me dice:

     "Error 22: No such partition"

y cuando quiero bootear XP me dice lo siguiente:

     "Falta NTLDR. Ctrl+Alt+Supr para reiniciar"

Sinceramente no se que pasa, estoy buscando de paso y leo y leo pero no encuentro la solucion.

     Lo unico uqe se me ocurre pueda ser es lo siguiente: en mi casa tengo un Sata2, a otro amigo se lo intale sin problemas y tenia un IDE, y la PC con la que tengo el problema tiene un SATA1, podra ser eso? No creo... pero bue... lo aclaro por las dudas.

     Desde ya muchas gracias y traten de responderme rapido porque tengo en mi casa la PC de mi amigo y no se la puedo retener mucho tiempo xD

    Chauchas

---

### Post by spg76 on 2008-02-21
Según averigüé, pudo haber pasado que GRUB haya guardado mal el order de las particiones.
[En este thread]("http://ubuntuforums.org/showthread.php?t=414205") lo arreglaron iniciando con el LiveCD y cambiando (hd1,2) por (hd0,2) en el archivo /boot/grub/menu.lst. , aunque quizás este no sea tu caso.
Si queres copia el contenido de tu /boot/grub/menu.lst, para ver si te podemos dar una mano.
El otro error,  "Falta NTLDR. Ctrl+Alt+Supr para reiniciar", es un problema de Windows. Según parece te falta un archivo (NTLDR, obvio) para que inicie correctamente.
Una posible solución la encontré en [http://es.answers.yahoo.com/question/index?qid=20070510112939AA7tJh4](http://es.answers.yahoo.com/question/index?qid=20070510112939AA7tJh4)
Copio y pegó:
> Para solucionar el problema de Falta el archivo NTLDR hay seguir el procedimiento siguiente:

1.- Arrancar el pc con el disco de Windows XP metido.
2.- Cuando nos salga el asistente de instalación de Windows Xp elegir la opción de Reparar Sistema.
(En caso de que no salga el asistente significa que el sistema no ha podido arrancar desde el CD. Prueba a ponerlo en otra unidad y volver a arrancar.
Si sigue igual, entra en la BIOS y comprueba que la primera unidad en la secuencia de arranque es alguna de tus unidades de CD/DVD.
3.- Teclear 1 de 1 C:windows
4.- Una vez que estemos en c:Windows teclear FIXMBR (y pulsar intro).
5.- El sistema nos advierte de que si queremos continuar y ponemos S y pulsamos en intro.
6.- Tras el proceso teclear EXIT.
Sacamos el CD del XP, reiniciamos y arrancamos.

Si todo sale bien debería de funcionar, si lo comentado no da resultado prueba con esto otro.

Una vez que estamos en el punto 4, tenemos que copiar dos archivos, debido que en dicha pérdida se arrastra también otro que es el ntdetect, por lo tanto sería, seguir los pasos anteriores del tutorial y en vez de escribir FIXMBR sería copiar ntldr y ntdetect.

Una vez en el punto 4, escribiremos:
copy d:\i386\ntldr c:\
copy d:\i386\ntdetect.com c:\
(donde d: sería la unidad lectora donde se encuentra el cd de Windows XP).

Si todo sale bien debería de funcionar.

---

### Post by emiliano_raso on 2008-02-21
EL MENU.LST ME TIRA TODO ESTO:

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
# kopt=root=UUID=c375c5db-b863-48e5-aaaa-cb883f4b34aa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=quiet splash locale=es_ES

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c375c5db-b863-48e5-aaaa-cb883f4b34aa ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c375c5db-b863-48e5-aaaa-cb883f4b34aa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Mauro22 on 2008-02-21
NTLDR es el LOADER DE NT. Seguro que el grub se escribio en la particion y no en el mbr.


Creo que tenes que hacer:

fdisk /mbr desde un disco de inicio de win xp para poder cargar el xp y luego reinstalar el grub usando el live cd

---

### Post by faktorqm on 2008-02-21
hola, me molesta de sobremanera que pongan "urgente" en los titulos, o sea, si es urgente llamas a un amigo o pedis help por msn, o booteas con el live cd de ubuntu o booteas con las 15000 distros live que tiene gnu/linux o booteas con el windows PE si estas ultra desesperado... ¬¬

A mi ya me paso el error ese, y decidi que era inarreglable leyendo la documentacion del grub y demas yerbas. Asi que aca te adjunto un .zip (no se lo merece....) con 3 cosas, (te aclaro desde ya que las 3 son para windows, dado que en mi casa la compu de mis viejos tiene xp y recupere la mia desde esa):

1) fixntldr.exe: Este es un exe que te crea un diskette para solucionar el problema del ntldr (NT loader) y te devuelve el windows. Una vez que lo pones, revisas que arranque el windows sin problemas. Cuando tenes el windows andando, le mandas un "fixmbr", asi te aseguras de que este todo bien.

2) carpeta rawwritewin-0.7: ejecutas el archivo rawwritewin.exe y apretas el boton con los 3 puntitos que te aparece al lado de "image" y elegis el tercer archivo "super_grub_disk_castellano_floppy_0.9672.img" y le das a write.

3) Arrancas con ese diskette y ahi te autodetecta (o lo podes decir vos) donde esta el windows, donde el gnu/linux, y te lo instala. Trata de hacerlo en el mbr, no en la primera particion, sino volves a volar el xp.

Tiene una especie de autoayuda el diskette ese, y esta en castellano, asi que si tenes dudas, lee la ayuda. Tambien te permite arrancar cualquier sistema operativo sin instalar nada, por las dudas si queres arrancar el ubuntu y despues instalarlo desde ahi (a mi no me sirvio).
Espero que te haya servido. Salu2!

---

### Post by emiliano_raso on 2008-02-25
GRACIAS POR TODO!

Para que linux funcione necesite reparar el grub y hacerlo arrancar si errores cambiando (hd1,2) por (hd0,1).

El tema es que arreglar el grub hace perder el NTLDR.

Las soluciones para reparar esto no funcionaron muy bien porque el hacer que windows funcione me quita el grub, y agregar el grub elimina el NTLDR.

Lo que quisiera saber es: en que directorio van los archivos NTLDR y NTDETECT??? porque los tengo en un pen drive y creo solucionarlo simplemente copiandolos al directorio al que pertecezcan, el problema es que no se donde van xD

Bueno, espero su respuesta para marcar este post como SOLVED.

Gracias...

---

### Post by faktorqm on 2008-02-25
esos archivos van en la raiz, es decir en c:\. no t sirvieron mis herramientas? a veces uno toca todo y le anda, y a veces no :( salu2!

---

### Post by Arpotrek on 2009-01-02
FactorQM, te felicito por un excelente comentario tuyo en este foro, valioso aporte de tu parte y que a mí me sirvió. Ignoro otra manera de expresar mi aprobación.
He visto que estás online en este momento, bueno, ojala veas este mensaje.
¡¡Aguante el león Estudiantes de La Plata!!
Saludos de un hincha del Ciclón.

---

### Post by euzkoarima on 2009-01-02
> **Arpotrek said:**
> FactorQM, te felicito por un excelente comentario tuyo en este foro, valioso aporte de tu parte y que a mí me sirvió. Ignoro otra manera de expresar mi aprobación.


Fácil, hace lo que pone en su firma
 > Entonces no te olvides de apretar la medallita que está abajo a la derecha del post que te sirvió

Saludos,
Eduardo

---

