---
title: "Kubuntu no bootea, se queda en initramfs"
date: 2009-12-04
forum: Software
---

### Post by autusgo on 2009-12-04
Necesito ayuda. Tengo el siguiente problema:
Anoche dejé la PC prendida bajando cosas con varios programas abiertos; había habido un update del sistema y me aparecía el ícono de reiniciar para aplicar los cambios en la barra de tareas (creo que fue eso lo que provocó el problema). Cuando hoy me despierto la PC estaba apagada (puede haber habido un pequeño corte de electricidad que hizo que se apagara), pero cuando la voy a encender **llega hasta el logo de Kubuntu** (ese que está antes de que la barrita de abajo se empiece a llenar) **y después queda toda la pantalla negra**, si se presiona una tecla (cualquiera) aparece una pantalla negra con letras blancas que dice entre otras cosas **(initramfs)** y ahí queda....

Buscando en la web encontré otras personas con el mismo problema y aparentemente la única solución es reinstalar (lo que quiero tratar de evitar). De todas formas, como para prepararme, puse el live CD para poder entrar al disco y hacer un backup de las cosas que no quiero perder; pero ni siquiera puedo acceder al disco!! Acá pongo una descripción de lo que me aparece cuando quiero acceder con Dolphin:
```
An error ocurred while accessing 'Volume (ext4)', the system responded: org.
freedesktop.Hal.Device.Volume.UnknownFailure: mount: wrong fs type, bad option,
bad superblock on /dev/sda1, missing codepage or helper program, or other error
In some cases useful info is found in syslog -try dmesg tail or so
```

Agradeceré cualquier ayuda sobretodo con respecto al primer tema; pero si no consigo hacerlo funcionar me conformo (desgraciadamente) con hacer el backup accediendo al disco desde el live cd y guardando las cosas en un disco NTFS que tengo.

Ahh uso Kubuntu 9.10

Gracias de antemano!

---

### Post by Mauro22 on 2009-12-04
En esa particion (/dev/sda1) que tenes instalado?? Calculo que es el sistema en si.


Como si tuviera un fallo en el formato. Podes acceder mediante liveCd a esa particion y leer/escribir con normalidad??

---

### Post by autusgo on 2009-12-05
> **Mauro22 said:**
> En esa particion (/dev/sda1) que tenes instalado?? Calculo que es el sistema en si.


Como si tuviera un fallo en el formato. Podes acceder mediante liveCd a esa particion y leer/escribir con normalidad??

En sda1 tengo el sistema, todo el disco físico está para Linux.
Y no, desde el Live CD veo el disco, pero no puedo ingresar, me dice lo que pegué en el primer post.

Creo que el problema en general se debe a que no puede montar el disco. estoy intentando entrar por consola, pero parece que tampoco se puede... Como que ya no hay forma de montar el disco.

Si a alguien se le ocurre como puedo hacer un backup, se lo voy a agradecer. Después reinstalo el sistema y listo.

Gracias!

---

### Post by alfplayer on 2009-12-05
Y realizando un chequeo de integridad a sda1 con fsck ?

---

### Post by nico089 on 2009-12-05
A mi me pasó lo mismo creo: recien se actualizo el sistema al kernell linux 2.6.31-16-generic y cuando intenta bootear dice esto y ahi queda:
 
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
Mount of filesystem failed.
A maintenance shell will now be started.
Control-D will terminate this shell and retry.
root@nicolas:~#
 
si alguien me puede ayudar se lo agradesco...
 
PS: uso ubuntu 9.10

---

### Post by nico089 on 2009-12-05
> **alfplayer said:**
> Y realizando un chequeo de integridad a sda1 con fsck ?


Funcionó perfecto con fsck, muchas gracias!!

---

### Post by alfplayer on 2009-12-05
> **nico089 said:**
> Funcionó perfecto con fsck, muchas gracias!!

OK. Ahora a esperar que el error no se repita.

---

### Post by D.Diego on 2009-12-05
No sé si es el mismo problema, pero desde la última actualización no bootea Ubuntu. Me lleva a GNU GRUB, y de ahí no sé como seguir...

---

### Post by emiliano_raso on 2009-12-06
Dirias las caracteristicas de hardware de tu maquina? Porque a mi me pasó varias veces con el LIVE CD y era falta de RAM.

---

### Post by D.Diego on 2009-12-06
emiliano, al final decidí reinstalar todo. Como todavía estoy probando Ubuntu (llevo más de 12 años con Windows, así que recién estoy aprendiendo). Lo que hice fue darle unos GB más de partición del HD a Ubuntu y recomenzar. Ah, tengo una Dell con 2,5 Gb de RAM y procesador Intel Core 2 Duo T5450

---

### Post by D.Diego on 2010-01-08
Eso, instalé unas actualizaciones hace un rato y no arranca. Me tira al GNU.GRUB con el consabido mensaje "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions"
Al darle TAB, me tira todos los posibles comandos y al darle boot me devuelve el mensaje: "no loaded kernel"
Es la segunda vez que me pasa. La vez anterior (explicado en este post: [http://ubuntuforums.org/showthread.php?t=1345784](http://ubuntuforums.org/showthread.php?t=1345784) ), instalé todo de nuevo. ¿Cómo hago para no reinstalar?

---

