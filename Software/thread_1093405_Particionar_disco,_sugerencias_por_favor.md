---
title: "Particionar disco, sugerencias por favor"
date: 2009-03-11
forum: Software
---

### Post by euzkoarima on 2009-03-11
Después de mil problemas, finalmente logre armar una pc nueva, y ahora tengo que particionar e instalar.

El disco es enorme 1TB (según gparted 931 Gb), voy a instalar 8.10 64 bits (Tengo 4 Gb de ram). Voy a tener mi usuario y por lo menos 4 más, sin permisos de administrador. Mi idea en principio es la siguiente (todo en Gb):

Swap 2
/  30
/home 40
/boot -> vale la pena partición aparte ???

Y después la idea es dejar unos 150 para pruebas, me refiero a instalar otros OS y la mayor parte (700 aprox) como un "depósito" para todos, ahí irían a parar fotos, música, videos. Que cada usuario tenga sus preferencias en su home pero los "datos reales" en el partición compartida.

Sugerencias y consejos bienvenidos.

Saludos,
Eduardo

---

### Post by ramiro_md on 2009-03-11
Hola euzkoarima. Bueno, bastante grande tu disco jeje..veamos lo de las particiones: 

> Swap 2
No hay nada para decir. Es el tamaño que corresponde.
> / 30
Sinceramente me parece algo exagerado sabiendo que con 5 o 6 gb te alcanza para instalarte un sistema GNU/Linux, pero tenés para tirar manteca al techo jaja.
> /home 40
Yo no realicé partición "/home". Los datos de programas y configuraciones están dentro de la partición donde está instalado mi sistema. Yo no ví la necesidad de hacer dicha partición porque conservo mis archivos en otra partición aparte de 100 gb :$.
Si vos decís de 40 gb por los 4 usuarios, no te hagas drama, cada usuario va atener su carpeta /home/usuario con sus configs, y no creo que ocupen 10 gb en configuraciones y datos de programas je.
> /boot
No la conozco je.

Y con el resto no hay mucho para decir. Lo único que te recomiendo es que a la partición mayor (donde almacenas los datos) la hagas como extendida, así adentro podés utilizar 4 particiones más (1 para datos y 3 para tus pruebas).

Bueno espero haberte guiado, un saludo..y suerte :D

---

### Post by luks911 on 2009-03-11
A mí también me parece excesivo el / de 30gb, la otra vez en el irc decían que todos los repositorios de Intrepid ocupan 25gb. Es cierto que sería sin descomprimir, pero aun así... de todos modos, siempre podés cambiarlas  después con gparted.

---

### Post by guillermolisi on 2009-03-12
Si cada user tiene la posibilidad de instalar o estan pensando usar utilitarios, aplicaciones y servicios y /var y /opt estaran incluidos en la particion /, dejala tal como la pensaste en 30Gb (y no se si hasta le daria algo mas, como para que no tengas que toquetearla para darle mas lugar llegado el caso de que instalen cosas que requieran mucho espacio - y aqui vienen la parte de donde pones los datos que se explotan con esos servicios/aplicaciones, que con el tiempo suelen ocupar mas lugar que el software mismo).

Todo esto considerando que podrian tener instaladas VMs, mailserver, webserver, MySQL, etc., etc.

Considera, llegado el caso de que ocupen una buena parte de la particion "deposito" como van a hacer backup de eso.

En las maquinas que uso con RedHat/Centos, generalmente marco una particion para /boot pequeña (creo, porque no estoy en la oficina aun, que algo asi de 8Mb).

---

### Post by euzkoarima on 2009-03-12
Cuento un poco más, los usuarios "en principio" no van a instalar nada raro. Igual mi idea de darle 30 al root tiene que ver también con tener una /tmp que se la banque, por ejemplo si haces algo como armar un dvd con devede, compactar con dvd95 o cosas por el estilo.

Si, ya sé que se puede indicar que use otro directorio para los temporales, pero me resulta cómodo así.

del /boot había leído que con un 1gb alcanza, lo que no me queda claro es la ventaja de hacerlo, a diferencia de tener / y /home separado que si.

Backup: de poco, en cd antes, dvd hoy día, rehaciéndolos después de algunos años, porque todos terminan palmando con el tiempo.

Esta pc no va a bootear sistemas opertivos propietarios, y salvo que sea el único modo de evitar que me linchen tampoco va a tener máquinas virtuales con sistemas propietarios.
Si va a tener wine, lo que quieran instalar y les funcione bien, lo que no, mala suerte.
Y con respecto a esto, creo (pero si alguno sabe que no es así que avise) que puedo poner los discos (C: etc) en cualquier lado sin problemas (o sea la partición "depósito").

---

### Post by guillermolisi on 2009-03-12
> **euzkoarima said:**
> Si va a tener wine, lo que quieran instalar y les funcione bien, lo que no, mala suerte.
Y con respecto a esto, creo (pero si alguno sabe que no es así que avise) que puedo poner los discos (C: etc) en cualquier lado sin problemas (o sea la partición "depósito").
Si los vas a poner en cualquier lado que sea fresco y seco, para que no se arruinen mientras no los usas :D

Ahora, seriamente, a que te referis con "ponerlos en cualquier lado" ?

---

### Post by euzkoarima on 2009-03-13
> **guillermolisi said:**
> 
Ahora, seriamente, a que te referis con "ponerlos en cualquier lado" ?

A que por defecto el wine crea un directorio "drivec" (creo) dentro de $HOME/.wine pero que podes indicar en las preferencias que lo queres, p. ej en /media/deposito

A todo esto, ya particione, instalé lo básico y ahora estoy completando la isntalación.

dejo una imagen de como quedó particionado el disco.

[IMG]http://i40.tinypic.com/wjghtz.png[/IMG]

Saludos,
Eduardo

---

### Post by ramiro_md on 2009-03-15
Si entre todos esos sistemas de prueba que pensas instalar en algún momento entra window$...me parece que la partición "Depósito" no te conviene formatearla como ext. Fat o ntfs sería lo ideal en ese caso.

---

### Post by faktorqm on 2009-03-16
Edu: Menos mal que no dejaste 1gb para /boot!!! A menos que hagas cosas raras, no necesitas nunca tanto para /boot. (cosas raras significa compilar kernel y generar tu propio initrd y vmlinuz y demases)

ramiro_md: El /home se deja para hacer lo siguiente:

Vos instalas tu ubuntu feliz, y en tu disco pones / en una particion, en otra particion aparte /home y otra para swap ponele. Entonces te instalas tus programas, blabla.
Te anda todo joya, y no notas ninguna diferencia en tener la particion separada o "juntas". Ahora, por X motivo se te rompe el /, y te quedo viva /home. Simplemente, reinstalando el ubuntu, e indicandole en la instalacion que el /home lo tiene que ir a buscar a tal particion, el tipo te levanta las customizaciones que habias hecho antes automaticamente. Abris el firefox y tenes los marcadores de antes. Te instalas el copmiz y se te configura como lo tenias antes, y asi todos los programas.
Lo unico que quenes que saber para eso es que tenes que usar el mismo nombre de usuario y la misma contraseña siempre, si no no funciona xD

Saludos!

---

### Post by euzkoarima on 2009-03-17
Me parecía que lo de /boot aparte no tenía mucho sentido.
En la categoría de sistemas probar (el día que tenga tiempo) caen
arch linux
ututo
algun bsd (en ppio freebsd o dragonfly).

Irían a para al espacio que ahora está libre.

Saludos,
Eduardo

---

### Post by z37a on 2009-03-17
Yo solo pro formalidad le dejo siempre 128Megas al principio del disco como primario ara el /boot, solo pro formalidad lo hago, pero la verdad que si no compartis el sistema con windows es al dope!!!!

PD: Yo deje como 55G para el / jajaja, tengo un disco de 500 del cual el /home usa solo 30GB!!!!! El resto, videos, isos de SO's y demas al file server(600GB por NFS)

Me olvidaba, lo ideal si son discos fisicos fijos donde tenes las particiones, para hacerlo mas prolijo te recomiendo que uses el /mnt y no el /media, solo para mantener un poco la prolijidad nomas!!!!!

---

### Post by euzkoarima on 2009-03-18
La verdad usé el /media porque me "machetié" de lo que vi en otra pc que tiene un segundo disco, agregado mucho después de haber instalado ubuntu, y (no se bien como) pero terminó yendo a parar a media, así que supuse que eso estaba bien y lo mandé para ahí.
En /mnt estaba el lector de cd.

Saludos,
Eduardo

---

### Post by z37a on 2009-03-18
> **euzkoarima said:**
> La verdad usé el /media porque me "machetié" de lo que vi en otra pc que tiene un segundo disco, agregado mucho después de haber instalado ubuntu, y (no se bien como) pero terminó yendo a parar a media, así que supuse que eso estaba bien y lo mandé para ahí.
En /mnt estaba el lector de cd.

Saludos,
Eduardo

Igualmente, una gran ventaja es elegir lo que a uno le parezca mas cómodo, a mi siempre me enseñaron que los discos estáticos van en /mnt, pero ubuntu también te los monta solo en el /media, lo cual me parece raro, si no quedaría al dope el mnt(pero no va al caso). Lo que me llamo es que hallas visto el cdrom en el /mnt, era un ubuntu u otra distro?

---

### Post by euzkoarima on 2009-03-20
**z37a**: ya se por qué te llamó la atención, porque miré cualquier cosa.
En concreto, mire en mi 8.04 (desde el que escribo ahora), pero se ve que miré mal, porque acabo de mirar de nuevo y .... mnt está vacío, está todo en /media

Saludos,
Eduardo

---

