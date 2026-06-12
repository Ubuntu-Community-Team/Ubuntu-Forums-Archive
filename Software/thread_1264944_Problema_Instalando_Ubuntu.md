---
title: "Problema Instalando Ubuntu"
date: 2009-09-12
forum: Software
---

### Post by worming on 2009-09-12
Hola! he tenido un problemita a la hora de instalar el ubuntu... Aclaro que no tengo la mas minima idea de linux, nada de nada!

Ahora paso a comentarles la situacion:

La computadora es una notebook HP, en la cual venia instalado windows vista en una particion, y en otra particion, venia una particion de recuperación... 
Como la notebook era HP y no sabia si iba a poder instalar todos los drivers de XP cree una particion y lo instale alli para probarlo... es decir tiene 3 particiones
1- win vista (160GB)
2- win xp (45GB)
3- recuperacion(win vista) (8GB)

y una 4ta particion vacia

4- particion vacia (20GB)

La idea era instalar ubuntu 9.04 en la 4ta particion, la vacia... pero cuando llego a la pantalla nº4 de la instalacion de Ubuntu (*Preparar el espacio del disco*), selecciono *"**Usar el mayor espacio continuo libre**"*, pero para mi sorpresa abajo donde te salen las particiones con sus respectivos colores, no me reconoce la particion del xp como si tubiera el xp...

Dice Esto:

**Windows Vista (loader) /dev/sda1**          **...........Windows Vista (loader) /dev/sda3**[INDENT]             160.00GB......................................................................                                                                                                                   8.00GB
[/INDENT]**/dev/sd5  [COLOR=Red]<-[/COLOR][COLOR=Red] supuesto XP[/COLOR]**...........................                                           ** Ubuntu 9.04**[INDENT]   45.00BG ................................................                                                                                                        20.00GB
[/INDENT]Lo que me llamo la atencion que no le ponga el (loader)... pero no le pase mucha importancia y continue... pero en la pantalla que te de la opcion de importar cosas desde windows, me aparecia la de windows vista y no la de xp... por lo que me preocupe y pense que tal vez me iba a pisar el arranque del XP... 

Creo que al instalar ubuntu el grub no me va a dar al opcion de iniciar con XP... por lo que mi pregunta es... 
Como puedo hacer para que Ubuntu me lo reconosca durante la instalacion?
O en todo caso, si alguien puede y me ayuda, yo lo instalo de todas formas y despues me ayudan a modificar el grub para que me reconosca el XP...

Saludos y Gracias!

PD: Perdon si esta mal posteado y no va aca, de ser asi muevanlo a donde corresponda.

---

### Post by Gonz@lo on 2009-09-12
Poné la última opción que dice "Manual" y ahí manejá las particiones a tu gusto. Tené en cuenta que ubuntu trabaja ext4 y no ntfs.

---

### Post by worming on 2009-09-12
Si... pero igualmente el arranque lo va a manejar ubuntu, por lo que si no reconoce que tengo el XP instalado a la hora de elegir con cual iniciar solamente me va a mostrar el windos Vista, y el Ubuntu...

Gracias ror responder tan rapido  :)

---

### Post by Gonz@lo on 2009-09-12
Si vos desde la configuración manual de las particiones no tocás la de windows xp y sólo te da la opción de importar configuraciones del vista no significa que se vaya a borrar la partición de xp.

---

### Post by worming on 2009-09-12
claro, si mi miedo no es que se borren los datos de la particion del xp... mi miedo es otro...
Tengo entendido que hay un solo sector de arranque que lo maneja un solo sistema operativo, independientemente de cuantos sistemas operativos tengas instalado... y ya que  ubuntu va a ser el ultimo sistema operativo que voy a instalar, va a ser ese quien lo controle, es decir me va a aparecer el grub de ubuntu dandome las opciones de en que particion iniciar y no va a ser xp, ni vista quien me deje seleccionar... pero como ubuntu no reconoce que en la particion /dev/sda5 tengo un sistema operativo instalado, obviamente no me va a ofrecer iniciar en esa particion...

---

### Post by josecuervo86 on 2009-09-12
Eso se soluciona editando el menu.lst de grub

---

### Post by worming on 2009-09-12
que grande jose cuervo... cree mi cuenta aqui porque vi como respondias con entusiasmo ja!...

Bueno entonces yo instalo y despues ante cualquier duda te consulto! puede ser?

---

### Post by josecuervo86 on 2009-09-12
Gracias worming! hace una cosa antes, habría posbilidad de que nos muetres una instantenea de lo que te aparece en el paso nº 4 para que quede mas clara la situación? Por lo que decis, xp esta en la /dev/sda5 pero en el editor de particiones del liveCD no aparece?

---

### Post by gmunioz on 2009-09-12
Sumimasen por la intromisión.

antes de instalar, sería conveniente pongas en el

post:

La salida, del comando ejecutado en consola, de una

sesión live-cd de Ubuntu:

sudo fdisk -l *(es ele no 1 ni i)*

Y un pantallazo de lo que muestra gparted

Sistema ---> Administración ---> Editor de particiones

---

### Post by worming on 2009-09-12
ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xe1615675

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       21217   170425521    7  HPFS/NTFS
/dev/sda2           21218       29262    64621462+   f  W95 Ext'd (LBA)
/dev/sda3           29263       30401     9142272    7  HPFS/NTFS
La partición 3 no termina en un límite de cilindro.
/dev/sda5           21218       26600    43233140    7  HPFS/NTFS
/dev/sda6           26601       29146    20450713+  83  Linux
/dev/sda7           29147       29262      931738+  82  Linux swap / Solaris


PD: Que particiones!!!

---

### Post by josecuervo86 on 2009-09-12
> ```
/dev/sda5 21218 26600 43233140 7 HPFS/NTFS
```

Esta seria la partición con XP. Solo faltaría el pantallazo de el editor de particiones (sitema > administración > Editor de particoines) desde el Live Cd

---

### Post by worming on 2009-09-12
ahora lo pongo! Muchas Gracias!!!!

---

### Post by worming on 2009-09-12
Ya lo instale al ubuntu... y como me lo sospeche no me tomo el xp... el windows vista si... pero no el xp que efectivamente esta en /dev/sda5

---

### Post by josecuervo86 on 2009-09-12
que chiquita la foto! no podes poner una mas grande? o por lo menos el link a la original?

Otra cosa, si estas en ubuntu abri una terminal (aplicaciones > accesorios > terminal) y escribi esto:
```
sudo gedit /boot/grub/menu.lst
```
Te va a pedir tu clave, ponela (ojo que no se va a ver, pero la escribe lo mismo) y copia el contenido en un post

---

### Post by worming on 2009-09-12
[IMG]http://www.imagenonline.com/show.php?id=182683%5D%5BIMG%5Dhttp://www.imagenonline.com/img_a182683.png[/IMG][[IMG]http://www.imagenonline.com/img_a182683.png[/IMG]]("http://www.imagenonline.com/show.php?id=182683")
[URL="http://www.imagenonline.com/show.php?id=182683%5D"]
[/URL]

---

### Post by worming on 2009-09-12
esto es lo que me tira el menu.lst
 ## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        293d9387-af84-4c6e-a0a4-100a78483f25
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=293d9387-af84-4c6e-a0a4-100a78483f25 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        293d9387-af84-4c6e-a0a4-100a78483f25
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=293d9387-af84-4c6e-a0a4-100a78483f25 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        293d9387-af84-4c6e-a0a4-100a78483f25
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

---

### Post by josecuervo86 on 2009-09-12
Bueno, hasta ahora todo bien, vos instalaste en la /dev/sda6 no? Bueno ahora falta lo ultimo que te pedi en el otro post y ya casi estamos :D

Edit: postie junto con vos, que alguien me corrija (muy recomendado :)) pero agregando esto al ultimo debería levantar la partición con XP

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title Windows XP (loader)
rootnoverify (hd0,3)
savedefault
makeactive
chainloader +1
```

---

### Post by worming on 2009-09-12
No se que mas me pedis... ya te puse la imagen del Gparted, el menu.lst... que mas necesitas ver?

segun creo... habria que agregar esto al final:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Windows XP (loader)   [COLOR=Red]Cambiar nombre[/COLOR]
rootnoverify    (hd0,4)  [COLOR=Red]Poner el numero de sda que sale en la imagen del gparted -1[/COLOR]
savedefault
makeactive
chainloader    +1

---

### Post by Hei Ku on 2009-09-12
Che, el Vista no reemplaza el loader de XP?
O sea, antes cuando tenias Vista, te habia puesto un menu donde podias elegir Vista o XP, no?

Me parece que ahora es doble el paso, desde el Grub elegis Vista, ahi te levanta el loader de Vista, y ahi elegis Vista o XP. Bah, no se, capaz le pifie mal, pero suena logico, porque si no antes no podias elegir cual arrancar.

---

### Post by worming on 2009-09-12
probe con rootnoverify    (hd0,4) y con rootnoverify    (hd0,3)... en ambos casos me aparece en el grub la opcion pero cuando selecciono windows xp me tira un error :S

---

### Post by worming on 2009-09-12
[[COLOR=#339900]**Hei Ku**[/COLOR]]("http://ubuntuforums.org/member.php?u=346209") Gracias por abrirme los ojos... si hubiese probado antes no estaria molestando todavia.. 
Perdonen y muchisimas gracias...
jose cuervo gracias por el aguante

Pero ahora quisiera saber si es posible poner todos las opciones dentro del grub asi no tengo doble selector de booteo...

---

### Post by Hei Ku on 2009-09-12
Que yo sepa, no podes, porque Vista te cambió el loader de XP.

Las instrucciones que te estaban dando serían la forma de hacerlo en un caso normal, pero ya viste que no funciona.

---

### Post by worming on 2009-09-12
Bueno... Muchisimas gracias... Tema Solucionado Entonces

---

