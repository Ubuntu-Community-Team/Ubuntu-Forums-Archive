---
title: "[SOLVED] Linux Headers"
date: 2008-11-02
forum: Software
---

### Post by aregnando on 2008-11-02
Hola a todos, tengo un par de temas que a pesar se haber buscado en diferentes lugares no he encontrado como resolverlos:
En principio en este momento estoy utilizando la versión del kernel 2.6.24-19 generic, aunque en una de las actualizaciones que hubo hace un par de semanas bajo un kernel más reciente (2.6.24-21) por un error mio durante la instalación preguntó si quería continuar con el que estaba usando o pasar al nuevo y le puse que siguiera con el que estaba y ahora no se como pasar al kernel 2.6.24-21. 
En fin viendo en synaptic no solo tengo instalados estos dos kernels que detallo más arriba si no que tengo desde la versión 2.6.24-16 pasando por las 17 y 18 y quisiera saber si puedo desinstalarlas sin inconvenientes.
Bueno no se si fuí claro en la explicación, apreciaría cualquier ayuda.

---

### Post by c4d0rn4 on 2008-11-02
desde el grub podés elegir que kernel bootear. Si no está en el grub el kernel más nuevo, vas a tener que meter mano ahí.

---

### Post by hictio on 2008-11-03
Podes postear una copia del archivo 'menu.lst'?
Tipea: Alt + F2, y escribi:
```

gedit /boot/grub/menu.lst (ENTER)

```

Cerralo cuando terminas, igual no lo podes modificar porque no tenes permisos.

---

### Post by fmsismo on 2008-11-03
> **aregnando said:**
> Hola a todos, tengo un par de temas que a pesar se haber buscado en diferentes lugares no he encontrado como resolverlos:
En principio en este momento estoy utilizando la versión del kernel 2.6.24-19 generic, aunque en una de las actualizaciones que hubo hace un par de semanas bajo un kernel más reciente (2.6.24-21) por un error mio durante la instalación preguntó si quería continuar con el que estaba usando o pasar al nuevo y le puse que siguiera con el que estaba y ahora no se como pasar al kernel 2.6.24-21. 
En fin viendo en synaptic no solo tengo instalados estos dos kernels que detallo más arriba si no que tengo desde la versión 2.6.24-16 pasando por las 17 y 18 y quisiera saber si puedo desinstalarlas sin inconvenientes.
Bueno no se si fuí claro en la explicación, apreciaría cualquier ayuda.

Podes desinstalar los kernels viejos, pero **_PRESTA MUCHA ATENCIÓN_** de no sacar el que estas usando.

Para ver que kernel estas usando podes hacer
[INDENT]uname -a[/INDENT]

Pega el contenido del /boot/grub/menu.lst
[INDENT]sudo cat /boot/grub/menu.lst[/INDENT]

Quizas tengamos que modificar el kernel por defecto para que te bootee con el más nuevo siempre sin que tengas que tocar nada.

Saludos

---

### Post by hictio on 2008-11-03
> 
Pega el contenido del /boot/grub/menu.lst

    sudo cat /boot/grub/menu.lst\


Una peq. correcion, no se necesita usar sudo para ver el contenido de este archivo.
Si es necesario para modificarlo.

En otras distribuciones de Linux, CentOS por ejemplo, si es necesario usar sudo para poder ver la el archivo de configuracion de grub.

---

### Post by aregnando on 2008-11-03
Hola, bueno según lo que me aconsejaba c4d0rn4 de elegir en el grub el kernel con el cual va aarrancar no lo puedo cambiar ya que el único que me muestra es el 2.6.24-19 que es el que tengo en uso pero el nuevo y más reciente según creo 2.6.24-21 no lo muestra así que no es la opción que puedo elegir.

Posteo el boot/grub/menu.lst según me sugieren hictio y fmsismo:



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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color yellow/brown white/light-gray

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=69c5f7ee-6bdc-434a-829b-a50cf045063b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash locale=es_ES vga=792

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=69c5f7ee-6bdc-434a-829b-a50cf045063b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=69c5f7ee-6bdc-434a-829b-a50cf045063b ro single
initrd		/boot/initrd.img-2.6.24-19-generic


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




También pongo una imagen del synaptic donde se ven las 2 versiones del kernel.
La pregunta que sigue es, desde Synaptic pùedo desinstalar los kernels que están fuera de uso simplemente marcando desinstalar por completo? o hay que hacer alguna otra cosa que seguramente desconozco?
Bueno desde ya muchas gracias por la ayuda.

---

### Post by c4d0rn4 on 2008-11-03
> **aregnando said:**
> 
También pongo una imagen del synaptic donde se ven las 2 versiones del kernel.
La pregunta que sigue es, desde Synaptic pùedo desinstalar los kernels que están fuera de uso simplemente marcando desinstalar por completo? o hay que hacer alguna otra cosa que seguramente desconozco?
Bueno desde ya muchas gracias por la ayuda.

mirá, como desinstalar se puede. Pero si desinstalas el unico kernel que tenés en tu grub olvidate que inicie ubuntu.

el grub es una cosa de la que tengo muy malas experiencias, asi que no voy a darte consejo alguno. No quiero que termines como yo reinstalando 4 veces Dam small linux en un día solo por el grub.

---

### Post by hictio on 2008-11-04
> 
mirá, como desinstalar se puede. Pero si desinstalas el unico kernel que tenés en tu grub olvidate que inicie ubuntu.


++

Segun el menu.lst que publicaste, no los estas usando, pero, si puedo preguntar, porque los queres desinstalar? Tenes poco espacio en el disco o algo asi?
Otra cosa, el kernel que quers, el 2.6.24-21, te lo ofrecia el "Update Manager"? No estoy seguro, pero porque no lo ejecutas manualmente a ver si tenes la opcion para instalarlo nuevamente?

---

### Post by rojojuan on 2008-11-04
> **aregnando said:**
> Hola a todos, tengo un par de temas que a pesar se haber buscado en diferentes lugares no he encontrado como resolverlos:
En principio en este momento estoy utilizando la versión del kernel 2.6.24-19 generic, aunque en una de las actualizaciones que hubo hace un par de semanas bajo un kernel más reciente (2.6.24-21) por un error mio durante la instalación preguntó si quería continuar con el que estaba usando o pasar al nuevo y le puse que siguiera con el que estaba y ahora no se como pasar al kernel 2.6.24-21. 
En fin viendo en synaptic no solo tengo instalados estos dos kernels que detallo más arriba si no que tengo desde la versión 2.6.24-16 pasando por las 17 y 18 y quisiera saber si puedo desinstalarlas sin inconvenientes.
Bueno no se si fuí claro en la explicación, apreciaría cualquier ayuda.

Tengo el mismo problema, voy a esperar el kernel nuevo para que el Grub se actualice solo. El kernel 19 anda bien, así que por ahora no tengo inconvenientes.
Esto pasó cuando estaba reinstalando HH ya que Intrepid no funciona con mi placa de video.

---

### Post by faktorqm on 2008-11-04
Yo para desinstalarlo, (me pregunto lo mismo WanderingKnight en la release party) fui a gestor de paquetes synaptic, busque todas las versiones que NO ERAN las que devolvia el comando uname -a y las desintale. Ahora, yo estoy corriendo ubuntu en un disco de 4.3gb, por lo tanto NECESITO espacio, si no lo necesitas, no lo saques!!! Salu2!

---

### Post by aregnando on 2008-11-04
Tal como vos decís Faktorqm, tengo poco espacio en el disco, me quedan solo 3,5 Gb por lo tanto trato de optimizar el espacio lo mas posible. Me parece que al igual que Rojojuan voy a esperar a la próxima actualización del kernel ya que me anda barbara la máquina y no quiero hacer nada que pueda complicarla en extremo, supongo que con la próxima actualización pasará a usar el kernel que descargue nuevo.
Muchas gracias y saludos.

---

### Post by c4d0rn4 on 2008-11-04
si sos de instalar cosas, fijate esto que te va a liberar bastante.

En synaptic, settings->preference->solapa Files

tilda delete y apretá delete cache.
Apply, ok y eso te libera un cacho. Otra tambien es instalar localepurge, que borra los manuales de los idiomas que no sepas leer, yo solo dejo los de ingles.

Igual debés arreglar lo del grub, pero eso te va a liberar un tanto de disco rigido.

---

### Post by aregnando on 2008-11-04
> **c4d0rn4 said:**
> si sos de instalar cosas, fijate esto que te va a liberar bastante.

En synaptic, settings->preference->solapa Files

tilda delete y apretá delete cache.
Apply, ok y eso te libera un cacho. Otra tambien es instalar localepurge, que borra los manuales de los idiomas que no sepas leer, yo solo dejo los de ingles.

Igual debés arreglar lo del grub, pero eso te va a liberar un tanto de disco rigido.

Gracias c4d0rn4, ya borré los kernels anteriores tal como me dijo Faktorqm e hice lo que me dijiste de borrar el cache, entre todo gané unos megas de espacio.
Muchas gracias y saludos.

---

### Post by hictio on 2008-11-04
Si estas desesperado, pero desperado, ya lindando en lo junkie por ganar algo de espacio de HDD, borrate el directorio '/etc/skel/Examples/', ganas 10 MB.
Obviamente, mira lo que tiene antes, pero dudo que lo necesites, en tu $HOME tenes un link a ese directorio.

Ademas, podrias revisar los temas e iconos, y borrar los que no te gustan o sabes que no vas a usar nunca, mucho espacio no liberan, pero se suma.

'/usr/share/themes/'
'/usr/share/icons/'

---

### Post by faktorqm on 2008-11-05
Yo hice igual una apretada de tornillo mas fina, si queres te digo mas o menos lo que fui haciendo. Si no estas seguro, estaria bueno que no lo hagas, por que despues aparecen algunos problemas jajaja

ayuda: la borre toda. deje el man no mas. para hacer eso borre el directorio /usr/share/doc

themes: desinstale paquete por paquete del synaptic todo lo que tenia que ver con themes, iconos, cursores, ventanas, etc.

programas en general: borre todo lo que abria menos de cada dos semanas. es decir, si no lo abro al menos una vez cada dos semanas (y eso es mucho...) lo borro. Entonces me fui buscando programas como vlc por ejemplo y borrando todo lo que tenga que ver con codecs y media players. Borre el firefox, el transmission, el deluge, la integracion con gnome, y etc y me instale opera para tener correo, torrent y navegador todo en uno.
Borre programas que vienen por defecto que no voy a usar, por ejemplo gimp, f-spot, xsane, etc.

obviamente tener el apt-get a raya con el apt-get clean, autoremove, y demases menesteres propios de la paqueteria...

kernel's: borrar los que no usas, yo tengo uno solo, y tambien borre el memtest86+, no ocupa mucho, pero todo suma!!! Lo que hago es, actualizo el kernel, ¿hay algo que no anda? no, entonces borro el viejo. si? me fijo como puedo solucionarlo, o borro el nuevo o lo arreglo, pero alguno de los dos se tiene que ir.

Salu2!!

---

### Post by aregnando on 2008-11-05
Hola Hictio y Faktorqm, estoy un poco apretado de espacio pero aún no caigo en desesperación, igual el proyecto a corto plazo es meterle un segundo HDD a mi máquina y dedicarselo integramente a Ubuntu. Ya pediré ayuda en ese momento para saber como montar el disco nuevo.
Saludos.

---

