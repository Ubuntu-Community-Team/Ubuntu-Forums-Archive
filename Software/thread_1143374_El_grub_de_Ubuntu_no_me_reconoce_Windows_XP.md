---
title: "El grub de Ubuntu no me reconoce Windows XP"
date: 2009-04-29
forum: Software
---

### Post by cor_stellae on 2009-04-29
¡Hola!

Recién el día de hoy estoy instalando el Ubuntu en mi computadora y, como verán, he tenido varios traspiés. Aunque parece muy fácil, para los que somos un poco ignorantes de las profundidades de la programación y que nunca hemos usado Linux, siempre hay algunas cosas un poco difíciles.

El punto es que instalé Windows en una partición y Ubuntu en otra. Pero, cuando instalé el Ubuntu (la segunda vez), automáticamente me lo colocó en un disco que creó para eso de un tamaño minúsculo que no me dejaba ni siquiera actualizarme. Cuando revisé las particiones, entre procesos de instalación y desinstalación, tenía el disco particionado de la siguiente manera:

1. Partición de 25 GB, que era la originalmente destinada a Ubuntu, ahora vacía.
2. Partición de 25 GB con Windows.
3. Partición de 100 GB para datos.
4. Dos particiones de 2 GB para Grub
5. Dos particiones de 2 ó 5 GB (ya no recuerdo bien), en una de las cuales estaba el Ubuntu completo, según parecía.

Por lo tanto, decidí instalar el Ubuntu (por la tercera y última vez), pero manualmente, eliminando tanta subpartición, para que quedara un solo Grub y dándole la orden de instalar el Ubuntu en la partición grande de 25 GB.

Esto lo logré hacer, pero cuando inicio la computadora, el Grub puede ver sin problemas el Ubuntu, pero ahora no me da la opción de ver el Windows, por lo tanto, no puedo elegirlo y reiniciar con él.

Ya verifiqué el disco duro y el Windows sigue ahí, es decir, no lo borré accidentalmente.

Por lo que he estado viendo en este mismo foro, hay una manera de reprogramar el Grub para que reconozca el Windows. Si me dicen que la opción es instalarlo de nuevo, pues me armo de paciencia y lo hago, pero preferiría nada más recuperarlo...

Aunque sé que esto lo han respondido miles de veces, esta damisela desesperada pide ayuda porque voy a necesitar que me expliquen hasta lo básico para poder lograrlo, que se me hace a veces incomprensible en las respuestas que veo a otras consultas hechas antes.

Les agradezco muchísimo la ayuda y me quedo a la espera de las preguntas que necesiten para poder resolver esto.

---

### Post by josecuervo86 on 2009-04-29
Hola. Podrías responderme una pregunta? Para que hiciste una partición para el Grub?

Para empezar podrias empezar por postear el archivo menu.lst (/boot/grub/menu.lst)

---

### Post by cor_stellae on 2009-04-29
Ooops! ¿No se hacía así? Como al decirle que automáticamente instalara el Ubuntu lo hacía en la partición que el programa quería (de un tamaño muy pequeño) y no en la partición que yo quería, seguí unas instrucciones que encontré en la web para asignar la partición principal del Ubuntu y el espacio designado para utilizar como "área de intercambio", utilizando el método manual.

En cuanto a lo que me pides... soy bien ignorante... ¿cómo posteo  el archivo menu.lst (/boot/grub/menu.lst)? ¿De dónde lo saco? Como ves, esto realmente es muy nuevo para mí. ¿Te puedo pedir un poquitito de paciencia?

---

### Post by pablo.s on 2009-04-29
Pasito a pasito

1) Abris una terminal
(Aplicaciones - Accesorios-
Terminal)

2) Escribis esto:

**[COLOR=DarkGreen]sudo gedit /boot/grub/menu.lst[/COLOR]**

3) Copias y pegás el contenido
en un mensaje.

---

### Post by josecuervo86 on 2009-04-29
Ahhh, no, ya se que quisiste hacer, pero esa partición es para la swap! jeje.

Lo que pasa es que esas particiones te conviene hacerlas desde el instalador, ya que al ponerle que te lo instale automaticamente te lo instalo en la mas chica (ni idea por que). Para poder asignar las particiones tenes que instalarlo de forma manual.

Para abrir ese archivo pone esto en la terminal:

```
sudo gedit /boot/grub/menu.lst
```

Copia todo y pegalo aca asi lo podemos ver

EDIT: me ganaste de mano pablo

---

### Post by pablo.s on 2009-04-29
> **josecuervo86 said:**
> EDIT: me ganaste de mano pablo

Estabas posteando screenshots seguro!

---

### Post by josecuervo86 on 2009-04-29
> **pablo.s said:**
> Estabas posteando screenshots seguro!

Quiero ver el tuyo papi :D

---

### Post by cor_stellae on 2009-04-29
Pablo y José, muchas gracias por la paciencia y por la ayuda. Créanme que antes de hoy ni sabía qué era una terminal. Aquí pongo lo que salió. A ver si ustedes sí lo entienden, que para mí es una lengua ignota...


--------------------------


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
# kopt=root=UUID=9187b754-8a8b-4bce-afc6-e226f3c0c9ed ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9187b754-8a8b-4bce-afc6-e226f3c0c9ed

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
uuid        9187b754-8a8b-4bce-afc6-e226f3c0c9ed
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9187b754-8a8b-4bce-afc6-e226f3c0c9ed ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9187b754-8a8b-4bce-afc6-e226f3c0c9ed
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9187b754-8a8b-4bce-afc6-e226f3c0c9ed ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9187b754-8a8b-4bce-afc6-e226f3c0c9ed
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1b6bcf98-8822-4025-b0a1-d511f8c8ec68 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1b6bcf98-8822-4025-b0a1-d511f8c8ec68 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 9.04, memtest86+ (on /dev/sda7)
root        (hd0,6)
kernel        /boot/memtest86+.bin  
savedefault
boot

---

### Post by pablo.s on 2009-04-29
OK, una parte ya está, ahora
escribí en una terminal

**[COLOR=DarkGreen]sudo fdisk -l[/COLOR]**

(la última letra es ele)

y pegalo en un mensaje.
Con estos dos datos se
puede arreglar el grub.

---

### Post by cor_stellae on 2009-04-29
No me deja copiar y pegar... trataré de incluir la imagen.

---

### Post by pablo.s on 2009-04-29
> **cor_stellae said:**
> trataré de incluir la imagen.

Cuidado porque estás escribiendo
un 1 (uno) cuando lo indicado es
escribir l (letra ele de Lucas).

---

### Post by josecuervo86 on 2009-04-29
Pusiste sudo fdisk -1 (uno). Es una l (ele). Hace asi, copia lo que te puso pablo y en la terminal apreta boton derecho y pone pegar

EDIT: otra vez pablito!! :D

---

### Post by pablo.s on 2009-04-29
Che cuervo, no se si a vos te pasa,
pero a mi el foro se me queda
clavado, puede ser que no recargue
por la cantidad de usuarios que tiene.

---

### Post by cor_stellae on 2009-04-29
Je je je... ¡qué pena! Bueno, ya lo intenté de nuevo, pero ahora es peor: me dice en inglés primero y en español después: "commando not found" / "orden no encontrada"

---

### Post by josecuervo86 on 2009-04-29
Puede ser, lo que noto es que en estos ultimos dias esta andando bastante mas lento que de costumbre. Debe ser por la histeria de la actualización. Se esta viendo mucha gente con un solo "poroto"

---

### Post by josecuervo86 on 2009-04-29
> **cor_stellae said:**
> Je je je... ¡qué pena! Bueno, ya lo intenté de nuevo, pero ahora es peor: me dice en inglés primero y en español después: "commando not found" / "orden no encontrada"

Espera! Ponelo de vuelta, debes estar pifiandole a alguna letra:

```
sudo fdisk -l
```

(SUDO FDISK -L) Ojo, copia lo de arriba

---

### Post by cor_stellae on 2009-04-29
Ahora ya lo logré... esto de espacios y guiones me está volviendo loquita...

---

### Post by pablo.s on 2009-04-29
Pasito a pasito

El comando es ***[COLOR=Black]fdisk[/COLOR]***
(asi, en minusculas)

Lo que hace este comando es
manejar las particiones. En este
caso, lo que le preguntas con
el parámetro ***[COLOR=Black]-l[/COLOR]*** (menos ele) 
es ¿cuales son las particiones
que tengo en cada disco? asi
podemos identificar en cual
partición está instalado Windows.

Entonces, vamos otra vez:

**[COLOR=Green]sudo fdisk -l[/COLOR]**

(hay un espacio entre la palabra
sudo y fdisk, otro entre fdisk y
menos ele)

---

### Post by cor_stellae on 2009-04-29
Creo que ya estaba en la imagen que acabo de subir, ¿o lo hago otra vez? :( Mejor pongo buena cara... por lo menos estoy aprendiendo mucho...  :KS

---

### Post by pablo.s on 2009-04-29
Ahora haces lo mismo del principio
(lo del sudo gedit /boot/grub/menu.lst)

Y pegas este texto de aqui pero
al final de todo lo que ya está escrito



### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,6)
savedefault
makeactive
chainloader    +1

---

### Post by cor_stellae on 2009-04-29
Perfecto. Ya lo pegué... ¿Cómo lo guardo? ¿Se guarda solo? :confused:

---

### Post by cor_stellae on 2009-04-29
En realidad la pregunta era si todo lo que tengo que hacer es guardar y reiniciar para ver si funciona. ¿Es así? En ese caso, regresaré en un ratito solo para terminar de dar las gracias y contar cómo me fue... :lolflag:

---

### Post by pablo.s on 2009-04-29
Si, guardas el archivo y reinicias.

---

### Post by josecuervo86 on 2009-04-29
> **cor_stellae said:**
> Perfecto. Ya lo pegué... ¿Cómo lo guardo? ¿Se guarda solo? :confused:

No te aparece una opción guardar? Anda a **Archivo > Guardar** o apreta Ctrl + s

---

### Post by cor_stellae on 2009-04-29
Ya volví. Al reiniciar, al menos sí aparecía la opción de Windows, pero al solicitarla me dio el mensaje "Invalid device requested" :(

---

### Post by pablo.s on 2009-04-29
Me debo haber equivocado yo con
el conteo de las particiones.
Podés hacer el paso anterior y 
modificar en esta parte que pongo
abajo, pero en lugar de (hd0,6)

reemplazalo por **[COLOR=DarkGreen](hd0,5)[/COLOR]** 


> **pablo.s said:**
>  
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,6)
savedefault
makeactive
chainloader    +1

---

### Post by josecuervo86 on 2009-04-29
Me parece que es la 5 (hd0,5). Igual nena, tenes un quilombo de particiones :D

---

### Post by cor_stellae on 2009-04-29
Bien, voy a reiniciar y te aviso.

---

### Post by pablo.s on 2009-04-29
> **josecuervo86 said:**
> Me parece que es la 5 (hd0,5).

Si, conté mal porque empieza
con (hd0,0) y tiene las particiones
extendidas por lo que hay que 
agregarle una mas...

---

### Post by cor_stellae on 2009-04-29
Bueno... con 0,5 no funcionó... ¿Y ahora qué hago? 

Sobre las particiones, la idea era tener tres: dos sistemas operativos y una de datos... lo demás se salió de mis manos y mi experiencia... :(

---

### Post by cor_stellae on 2009-04-29
Mmmm... ¿no será la número 4? Estoy revisando la lista de particiones, y la que supuestamente tendría el Windows, la que se llama sda5, bueno... antes de 5 viene 3, o sea que es la número 4, a pesar del número que tiene...

---

### Post by josecuervo86 on 2009-04-29
Dale, vamos a probar con el 4, romper no se va a romper y de paso aprendes :D

---

### Post by pablo.s on 2009-04-29
Momentito!

Vamos a ver las posibilidades:

Aparecen tres discos
sda, sdb y sdc

Tenés dos discos y un pendrive?

---

### Post by cor_stellae on 2009-04-29
Ehhh.... "pendrive" qué es??? ¿Memoria flash, usb o maya? No, del todo.

Tengo tres discos duros físicos: dos de 160 GB y uno de 250 GB. Al menos esa es la idea... No tengo llaves maya pegadas ni nada parecido, únicamente la unidad lectora/escritora de CD/DVD.

Viendo el conteo, si contamos desde 0, el número sería 3 y no 4...

---

### Post by josecuervo86 on 2009-04-29
Me parece que tiene 3 discos: uno de 250 y dos de 160. Es asi?

Igual sigo pensando que es el hd0,5 si te fijas a la particion con linux la tiene en hd0,6 segun grub y es la inmediatamente continua a la de Win

EDIT: sigo llegando tarde, tengo un lag en la cabeza!!


Y probaste con hd0,4?

---

### Post by pablo.s on 2009-04-29
Me parece que está en el
segundo disco Windows,
entonces seria hd(1,0)

Discos maya? Donde estás?

---

### Post by josecuervo86 on 2009-04-29
Otra pregunta: que tenes en los demas discos??

---

### Post by cor_stellae on 2009-04-29
No, no he probado el 4... allá voy... y luego con los demás a ver cómo me va... En un rato les cuento.

"Llaves maya", Costa Rica. No sé por qué se llaman así ni dónde se originó el nombre...

---

### Post by josecuervo86 on 2009-04-29
Bueno, proba con 4 y despues contanos. Entonces en los otros discos no tenes nada?

EDIT: Googlié "llaves maya" y me aparecieron "pendrives" :P. Mira que tienen nombres, pero llaves maya no la habia sentido nunca!

---

### Post by cor_stellae on 2009-04-29
Se ha vuelto loco el archivo del grub... no me deja guardar cambios, no me da permiso, no me pide mi clave... ¿Qué pasó?

---

### Post by cor_stellae on 2009-04-29
Perdón, no respondí... los otros discos están completamente llenos de datos: toda mi colección de fotos, para empezar (las mías, tomadas por mí, no bajadas de internet) y no quiero perder absolutamente nada...

---

### Post by josecuervo86 on 2009-04-29
estas poniendo "sudo" antes de gedit....?

---

### Post by cor_stellae on 2009-04-29
¡Qué vergüenza! No.... se ve que es a mí a la que ya se me acaba la paciencia... :-k

---

### Post by pablo.s on 2009-04-29
Siempre que vayas a editar partes
importantes del sistema te va a
pedir que lo hagas con permisos
de "administrador", por lo que cada
comando importante por una
cuestión de seguridad se ejecuta con
"sudo" que permite hacer tareas
reservadas.

Puede ser que estés llamando
a gedit sin poner antes sudo...

A proposito, los pendrives los 
inventaron en un lugar donde 
yo vivia hace unos años...

---

### Post by josecuervo86 on 2009-04-29
Yo estoy "swapeando" mal! en cualquier momento vuelco

---

### Post by pablo.s on 2009-04-29
A mi el retraso de recargar la
página me hizo perder la delantera...

---

### Post by cor_stellae on 2009-04-30
Ya volví. Estos son los resultados:

0,4: invalid device requested
1,0: starting up

Y se queda en starting up, indefinidamente... Tuve que apagarla con el botón del CPU.

Mientras encendía de vuelta con el Ubuntu, vi que estaba cargando el disco 0,0. ¿Eso nos da alguna pista?

Y muchas gracias por explicarme lo del sudo, con esto espero no olvidarlo. :cool:

---

### Post by pablo.s on 2009-04-30
El 0,0 es el de Linux.

Creo que vas a tener que aplicar
la receta del doctor Live...

Tenés el cd de instalación?
Es Live CD?

---

### Post by josecuervo86 on 2009-04-30
Ya no se que decirte, pero por las dudas proba con el 3. Mirando tu fdisk con cariño me parece que puede llegar a ser ese.

---

### Post by staar on 2009-04-30
chee, según su fdisk -l, la primera partición del tercer disco tiene el flag de boot, así que tiene que poner (hd2,0) en el menu.lst...

saludos

---

### Post by pablo.s on 2009-04-30
Cierto, staar, ya estamos hechos
bolsa a esta hora!

---

### Post by josecuervo86 on 2009-04-30
Pero en ese disco no es que tenia datos nomas??

EDIT: Chicos, los dejo a ustedes que a mi el marote no me da para mas ;)

---

### Post by cor_stellae on 2009-04-30
Okay, voy a intentar con las dos opciones que me dan. Respuesta: sí, tengo el disco, si te refieres al que se utiliza para instalar el Ubuntu, es v. 9.04.

---

### Post by pablo.s on 2009-04-30
hd(2,0) sería entonces.

---

### Post by cor_stellae on 2009-04-30
No... 2,0 tampoco funcionó...
Chicos, muchas gracias por la ayuda, pero si ya nada funciona... ¿ahora qué?

---

### Post by pablo.s on 2009-04-30
Yo me decantaría por el metodo
de rescate de grub desde Live CD,
que tendriamos que haber probado
primero.

[Aquí]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB") está explicado. Son la 1:25 en
Argentina, es tarde, sino te lo explicaba
mas paso a paso yo.
Saludos.

---

### Post by cor_stellae on 2009-04-30
Gracias, Pablo, y a José también, por estar tantas horas conmigo tratando de solucionar el problema. Ve a dormir y descansa. En Costa Rica son las 10:25 pm, así que puedo quedarme un rato más tratando de arreglar el problemita.

Cuando lo logre, pondré el post de victoria. ¡Dulces sueños!

---

### Post by cor_stellae on 2009-04-30
Actualización de la situación: utilicé el Super Grub Disk y no funcionó... Traté de seguir las instrucciones para crear el Grub desde el Live Disk, pero estoy ya muy cansada y no entiendo bien. Bueno, mañana será otro día.

Saludos y buenas noches, muchas gracias por su ayuda... :KS

---

### Post by josecuervo86 on 2009-04-30
Genia! Muy bien, felicitaciones!!

---

### Post by cor_stellae on 2009-04-30
Ehh.... no entiendo muy bien las felicitaciones :confused:. Ni siquiera el Super Grub Disk fue capaz de instalar el archivo Grub, o sea, estoy exactamente igual que ayer, pero peor, porque ya lo intenté todo.

Más bien, ahora que ya me he levantado de nuevo, y visto que realmente necesito tener Windows para algunas cosas aunque no quiera, quería pedir consejo nuevamente.

Excepto por la pérdida miserable de tiempo, no tengo problema con borrar todo el disco y empezar de nuevo, porque tengo respaldo íntegro de los datos en otro disco duro físico diferente.

¿Cómo hago para instalar Ubuntu en una partición, Windows en otra y evitar que esto vuelva a suceder? ¿Se instala el Ubuntu primero y el Windows después? ¿Debo tener la partición de Ubuntu formateada en el formato favorito de Ubuntu antes de comenzar? En fin... que estoy varada...

Muchas gracias por la ayuda, realmente aprendí mucho de todo esto, pero todavía necesito encontrar la manera de poner mi computadora a funcionar bien.

---

### Post by pablo.s on 2009-04-30
> **cor_stellae said:**
> estoy exactamente igual que ayer, pero peor, porque ya lo intenté todo.

Yo diria que sabes mucho más
que ayer!


> **cor_stellae said:**
> Más bien, ahora que ya me he levantado de nuevo, y visto que realmente necesito tener Windows para algunas cosas aunque no quiera, quería pedir consejo nuevamente.

Excepto por la pérdida miserable de tiempo, no tengo problema con borrar todo el disco y empezar de nuevo, porque tengo respaldo íntegro de los datos en otro disco duro físico diferente.

Regla muy importante, aunque más
importante es grabar los datos en
un DVD. La prudencia es buena, la
paranoia es mejor.

> **cor_stellae said:**
> ¿Cómo hago para instalar Ubuntu en una partición, Windows en otra y evitar que esto vuelva a suceder? ¿Se instala el Ubuntu primero y el Windows después? ¿Debo tener la partición de Ubuntu formateada en el formato favorito de Ubuntu antes de comenzar? En fin... que estoy varada...

Podés volver al punto de partida y
hacer las cosas mejor. Sabés como
entrar a un disco de rescate de Windows
y hacer [COLOR="DarkGreen"]**fdisk /MBR**[/COLOR] ?

---

### Post by josecuervo86 on 2009-04-30
Ja, entendi mal, me creia que lo habias hecho funcionar. Perdón.

En cuanto a instalar todo de nuevo no es la mejor opción. Intentaste probar hd0,4?

Si vas a instalar todo de nuevo, SIEMPRE instala windows primero

---

### Post by cor_stellae on 2009-04-30
Je je je..., Pablo, sí, ahora sé mucho más que ayer, eso sin duda alguna, y muchas gracias por tu ayuda en todo esto. Acabo de crear un thread nuevo con todas mis preguntas puntuales sobre la instalación, porque me parece que esto ya dejó de ser una pregunta sobre el Grub.

Lo que me dices de fdisk /MBR es totalmente nuevo para mí. He estado utilizando un disco de instalación de Windows que se carga solito y no deja hacer ninguna otra cosa que instalar Windows. Como ex usuaria de Mac, recuerdo los buenos tiempos en que uno utilizaba un CD de arranque de sistema operativo, exactamente igual que el Live CD de Ubuntu; por lo tanto, esas estrategias de instalación de Microsoft me parecen trogloditas y primitivas y el Ubuntu logró enamorarme "a primera vista del Live CD". ¡Qué puedo decir!

Bueno, si no te molesta, nos vemos en el otro thread, a ver si cuando haga todo de nuevo esta vez lo logro hacer bien.

¡Un millón!

---

### Post by cor_stellae on 2009-04-30
Hola José:

Acabo de ver tu respuesta. Sí, intenté 0,4 y otras cuantas alternativas. En cuanto a instalar Windows primero, gracias por la respuesta. Voy a hacerlo así.

---

### Post by sajnox on 2009-04-30
Uy dio' que post mas largo.

Una cosa, windows no arranca desde una particion que sea #5 ya que con ese numero es una particion extendida y windows necesita una primaria y no una logica

---

### Post by pablo.s on 2009-04-30
Costó pero salió! Un trabajo
conjunto del Cuervo y mi
con la colaboración de staar
en el post mas largo del 2009...

---

### Post by josecuervo86 on 2009-04-30
De una, y fue todo en un ratito! Tambien, asi me quedo la cabeza! Ayer soñe con el Grub, y no eran cosas muy lindas :P

---

### Post by pablo.s on 2009-04-30
Estás estresado loco, leete un
libro antes de ir a dormir...

---

### Post by josecuervo86 on 2009-04-30
Jaja, voy a leerme el manual de python que esta en la mesita de luz :D

---

### Post by pablo.s on 2009-04-30
Después vas a soñar con defs
y prints... Leete la Patoruzito
digo, algo que no te haga soñar.

---

### Post by josecuervo86 on 2009-04-30
print "zzzz"

Na, fuera de joda. Mas vale me tomo un fernet (como buen cordobes que soy) y me voy a dormir tranquiliiiito

---

### Post by cor_stellae on 2009-04-30
¡Dulces sueños, chicos! Se los merecen por tenerme tanta paciencia y tanta buena disposición de ayudar. Lamento que el hilo fuera tan largo, pero esa explicación de la partición número 5 me suena muy razonable, sobre todo después de estar manipulando las particiones y ver lo enredadas que estaban...

Un abrazo enorme!!!!!!

---

