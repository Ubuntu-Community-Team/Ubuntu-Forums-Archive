---
title: "Al Fin Volvi a ubuntu... problemas...NEED BACKUP"
date: 2008-05-29
forum: Software
---

### Post by xpelaox on 2008-05-29
HOla gente, que tal? al fin, despues de que volvio mi notebook del servicio tecnico HP, recien ahora pude hacerme un tiempito para poner mi Ubuntu, ahora 8.04 =D, a punto y me surgieron un par de problemas, algunos ya arrastradoas de 7.04 otros nuevos y queria ver si me podian dar una manito :)

Primero, y mas preocupante, es medio extraño el asunto... Tengo mi Notebook Tx1030LA conectada a una Docking station HP que se conecta a un puerto raro que tiene la notebook, y ademas de ser un "portanotebook" actua como replicator o algo asi... bueno, a ese replicator tengo conectado un teclado y mouse inalambrico... todo funciona lindo lo reconoce... pero despues de un tiempo, generalmente despues de un tiempo inactivo que la notebook apaga la pantalla, cuando vuelvo el mouse funciona lento, como con un delay. 
Booteo Ubuntu con el comando noacpi, me da la sensacion de que de alguna forma en la suspancion el acpi se vuelve a activar.. puede ser? y hay alguna forma de solucionarlo?.

Segundo y menos importante: A este mismo replicator tengo conectada una salida VGA que va a mi LCD, hay algun programa que simule al de Nvidia de windows? lei una guia en innet que me parece que es medio vieja y cuando la hize rompi todo, suerte que hize backup.

Tercero: la base esta/replicator tiene unos parlantes incorporados, en windows, cuando lo conecto se deshabilitan los de la notebook y se habilitan los de la base, pero en ubuntu funcionan los de la notebook y no los de la base.

y por ahora eso es todo :) espero que me puedan dar una mano!

Saludos y si te tomaste el trabajo de leer lo que escribi, Gracias =D

---

### Post by sergiom99 on 2008-05-29
No estoy seguro que trae ese modelo, pero por lo de nVidia, habilita los "Restricted Drivers" o sino instalate envy que baja los ultimos drivers (pero creo que necesita recompilar algo y "se rompe" con los updates)
Por lo del sonido, capaz tenes que hacer lo que hice yo para que me deshabilite los parlantes la conectar un auricular en el front-jack.
Fijate este thread que para mi fue "la biblia" para mi Pavilion: [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
(Aclaro: tal vez no tengan el mismo hard. Leelo todo que hay bastante data a lo largo del mismo)

Suerte!

---

### Post by faktorqm on 2008-05-30
envy: ```
sudo apt-get install envyng-gtk
```

te instala el nvidia-settings que es para manejar todo ese tema de las salidas.

Lo de los restricted drivers te instala el modulo y te lo configura, nada mas, no se por que insisten con eso.... pero sobre gustos no hay nada escrito....

con respecto a lo de la suspension, lei que con eso hay unos bardos espectaculares, asi que armate de paciencia por que la mano viene heavy. Sin ir mas lejos, en el post de la epson cx algo, tienen problemas para imprimir por que magicamente les suspende el puerto. Eso es todo lo que se. Salu2!!

---

### Post by xpelaox on 2008-05-30
Hmmmm, con esto que me decis sergiom99, pienso que quizas son los drivers, yo en 7.10 instalaba unos dirvers alsa, y cuando conectaba los auriculares los parlantes se cayaban, ahora con hardy me funciona de una el sonido, asi que no instale nada.... pero no se... antes no tenia esta MAGICA docking station.

en cuanto a los de envy, faktorqm, voy a hacerlo ya mismo... y lo de la suspencion... voy a probar haciendo que no se suspenda nunca... a ver que pasa, Gracias por su ayuda!!! voy a ver que pasa, manos a la obra.

Saludos

edit: gracias faktorqm, lo de envy funciono barbaro =D

---

### Post by xpelaox on 2008-05-30
bueno, deshabilite todo desde gestion de energia, con o sin bateria, ni dejo que se ponga la pantalla en negro, despues puse a bajar envy, despues actualize... mientras se bajaban las actualizaciones, la pantalla se puso negra, y cuando movi el mouse, otra vez, todo lento... como lo pudo deshabilitar EN SERIO?

Gracias señores =D

---

### Post by xpelaox on 2008-05-30
bueno.. segui tocando.... ahora no se apaga la pantalla, pero al rato el lag vuelve... QUE HAGO?? WAAA no tiene solucion?:S

---

### Post by sergiom99 on 2008-05-30
> **faktorqm said:**
> 
con respecto a lo de la suspension, lei que con eso hay unos bardos espectaculares, asi que armate de paciencia por que la mano viene heavy. 

como es esto? Es en Hardy? porque yo pensaba hacer el upgrade de version el finde. Probe con el LiveCD y me reconocio todo (menos wireless) de una, pero no tengo ganas de reinstalar de 0 para no hacer backup de mis cosas.
Pero si hay lio con el manejo de energia mejor espero.

---

### Post by xpelaox on 2008-05-30
nono, este es un tema que ya me pasaba antes... no me acuerdo bien, pero creo que lo habia solucionado conectando directamente el mouse a un puerto USB, cuando le conectaba un usb HUB con el mouse y teclado, me pasaba esto. Ahora con la docking station se ve que es lo mismo. pero tiene que tener una solucionnn ARRAHH!!!

una coistia minima pero rara que note con hardy, es que cuando apagas que aparece la consola y empeiza a cerrar todo, se ve con rayitas azules.

pero igual no creo que te tengas que preocupar, a esta notebook todos la clasifican como Linux unfriendly :(



EDIT: Pense que habias quoteado algo mio, y conteste cualquier banana:P

---

### Post by faktorqm on 2008-05-31
lo de los problemas de manejo de energia lo arrastran desde 7.10, y todavia no lo arreglaron. fijate sobre todo las impresoras canon, que, ponele, imprimis todo bien, despues se te suspende, cuando la traes de vuelta no imprime nunca mas. por usb la conexion de la impresora claro. cosas del linux.....

---

### Post by xpelaox on 2008-05-31
> **faktorqm said:**
> lo de los problemas de manejo de energia lo arrastran desde 7.10, y todavia no lo arreglaron. fijate sobre todo las impresoras canon, que, ponele, imprimis todo bien, despues se te suspende, cuando la traes de vuelta no imprime nunca mas. por usb la conexion de la impresora claro. cosas del linux.....

Uhh si, despues de la suspencion todo lo que conectes a cualquier USB no lo reconoce... tenes que reiniciar.


buuu esto es problema de linux o de la distro?

---

### Post by xpelaox on 2008-05-31
bueh... haciendo pruebas encontre la forma de eliminar este error, si booteo sin ningun parametro extra, osea sin "noacpi" no pasa mas lo del lag del mouse... pero deja de funcionar la touchscreen -.-

---

### Post by xpelaox on 2008-06-10
BUeno señorrreeesss los molesto un poquitiiitoo mas, lo probe TODO, ya debo conocer TODAS las distro :P ubuntu, kubuntu, fedora, suse, debian, mandriva, y alguna mas... y de tanto leer, creo que encontre la forma de hacer funcionar todo en hardy, primer paso, lo logre, booteando sin ningun comando, ahora teoricamente tengo que instalar los ultimos drivers de Nvidia, mas nuevos de los que instala envy, por eso lo tube que hacer a mano, lo hize asi:
<code>
Una vez que los tengas bajados en la consola hace sudo apt-get install build-essentials cuando termine eso tene que apretar
Ctrl+Alt+F1, con eso vas a salir a modo consola
despues escribis /etc/init.d/gdm stop
cd rutadondebajasteeldriver
sudo sh nombredeldriver

Con eso te va a salir una pantalla para empezar a instalar el driver, cuando termine tenes que poner /etc/init.d/gdm start o reiniciar la pc
</code>

cuando hago esto, parece funcionar, se bootea con el logo de Nvidia, ahora bien, cuando reinicio la maquina, me aparece un error y me corre todo en baja definicion:S

alguien tiene idea de como tengo que hacer?

Graciaaaasss

---

### Post by gefarion on 2008-06-10
Hola, mira este enlace que hay algunas posibles soluciones para tu problema:

[AQUI]("http://pmartinez.wordpress.com/2008/04/26/cambiar-resolucon-de-pantalla-ubuntu-804/")

Espero que te sea util, saludos.-

---

### Post by xpelaox on 2008-06-10
no... no se por que no me toma los drivers Nvidia... alguien me explica como hacer para borrar todos los drivers, que todo vuelva a 0 y reinstalar los drivers nuevos? calculo que asi tendria que funcionar:S

---

### Post by xpelaox on 2008-06-10
logre hacerlo funcionar parcialmente, si reinicio se me desconfigura, pero en esta instancia semi configurada:P el nvidia-settings me tira en x server display configuration esto: Unable to load X Server Display Configuration page:

Failed to parse the following modeline of display device
0x00010000 'Nvidia Default Flat Panel' connected to GPU-0 'GeForce Go 6150':

source=edid :: "nvidia-auto-select"  74.900  1280 1476 1524 1536  800 805 808 812  -HSync -VSync

alguna idea?:S

---

### Post by faktorqm on 2008-06-11
Hola, por que usas EDID's? Yo los deshabilite por que tambien me traian problemas. Hay una opcion para xorg.conf que es noedid o algo asi. en la documentacion del driver de nvidia, en la seccion de apendices, aparece. Fijate si te sirve, salu2!

---

### Post by xpelaox on 2008-06-11
hmmm buscando lo que me dijiste llegue a esto, una solucion magica:P con esto parece funcionar, igual voy a seguir probando:
<code>
LANG=C nvidia-settings
</code>

---

### Post by faktorqm on 2008-06-11
Me acorde la opcion que te habia dicho, era Option "NoEdid" True en la seccion display del xorg.conf (que memoria q tengo!!) salu2!

---

### Post by xpelaox on 2008-06-11
BUenisimo, Gracias por tu ayuda!! Igual ahora logre, de alguna forma:P, hacer que funcione, asi que le voy a hacer caso a mi prof de programacion: Si Funciona, no se toca :P

Saludos y Gracias a todos por su ayuda, Chau vista, CHAU!

---

