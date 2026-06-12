---
title: "Apreciación de Karmic Koala pre release"
date: 2009-07-23
forum: Software
---

### Post by pablo.s on 2009-07-23
Por lo pronto lo que puedo apreciar
de diferente:

-No hay Usplash (bootea en 20
 segundos o menos: reales)
-El GDM es más lindo, más
modelo 2009.
- Adiós Pidgin y gracias por el pescado!
Reemplazado por Empathy.
- La versión actualizada de OO reconoce
TODAS las fuentes!
- Se nota que anda todo mucho mas 
rápido, más rapido que Jaunty.
-EXT4 como FS por defecto en instalaciones
nuevas.
- Ubuntu One por defecto!
- Muy estable, noto casi ningún problema.
- Un tema nuevo, Ubuntu Evolution.

---

### Post by aledruetta on 2009-07-23
Yo tengo ese problema de que al eliminar archivos de la papelera el sistema se tilda. En algún lugar del foro comentaron que es un bug relacionado con EXT4. ¿Se solucionó ese tema en Karmic o tendría que instalarlo con EXT3 si quiero probar la Alpha 3?

Gracias,
Alejandro.

---

### Post by pablo.s on 2009-07-23
No creo que esté relacionado a
la Alpha 3 porque probé borrar
un archivo a la papelera y luego
eliminarlo. No se cuelga el sistema.
Si te animás a probar con la
actualización, adelante.

---

### Post by staar on 2009-07-23
el problema con el nuevo GDM es que está reescrito completamente, y todavía no hay una herramienta de configuración...

otra cosa, 20 segundos en qué hardware?

saludos

---

### Post by pablo.s on 2009-07-23
> **staar said:**
> otra cosa, 20 segundos en qué hardware?

Core2Duo 4300
1 GB RAM
Disco SATA

El objetivo que se han planteado
es que el lanzamiento final llegue
a 10/15 segundos e incluso con
un disco SSD a 8 segundos.

---

### Post by staar on 2009-07-23
interesante, me picó la curiosidad, me parece que voy a actualizar para ver cuanto logra con mi celeroneta :-D

saludos

---

### Post by pablo.s on 2009-07-23
No te ibas a pasar a un
Phenom super loco vos?

---

### Post by aledruetta on 2009-07-23
> **pablo.s said:**
> No creo que esté relacionado a
la Alpha 3 porque probé borrar
un archivo a la papelera y luego
eliminarlo. No se cuelga el sistema.
Si te animás a probar con la
actualización, adelante.

Sí, me expresé mal. El problema lo tengo en Jaunty. Por eso pregunté si sabían cómo funcionaba EXT4 en Karmic, si se había solucionado, ya que va a venir como predeterminado.

---

### Post by pablo.s on 2009-07-23
> **aledruetta said:**
> Por eso pregunté si sabían cómo funcionaba EXT4 en Karmic, si se había solucionado, ya que va a venir como predeterminado.

No olvidemos que esta es una
version Alpha y obligadamente
algunos bugs trae. A lo que te
referis vos, supongo que si se
ha pasado a EXT4 por defecto
debe ser mucho mas estable
que en Jaunty. Yo por mi parte
recien ahora estoy probando
EXT4, dado que hace muchisimos
años que vengo utilizando ReiserFS
y le rezo todos los dias a
Santa Teresita para que se
incorpore BRTFS a Karmic, pero
se ve que se ha dado cuenta que
no soy catolico, asi que nada.

---

### Post by staar on 2009-07-23
> **pablo.s said:**
> No te ibas a pasar a un
Phenom super loco vos?
hubo algunos 'inconvenientes' :-P y todavía estoy con la celeron, pero no pierdo las esperanzas :-D

saludos

---

### Post by z37a on 2009-07-23
20 segundos, me parece que Jaunty en mi PC inicia en menos, y tengo un procesador mas berreta, tengo un Athlon LE-1620 (unico core), lo unico con 4GB de RAM(uso 64 bits) y disco SATAII de 7,2K.

---

### Post by oktubrer on 2009-07-23
Estuve leyendo bastante al respecto pero no entendí, je, asi que te pregunto a vos que lo estas usando.
¿Karmic viene con Grub2 por defecto? Y en caso de ser afirmativa la respuesta, ¿por defecto es "gráfico" al estilo gfxboot?

Quiero saber si me pongo a tratar de resolver el problema de gfxboot con x64 o espero el lanzamiento de Karmic.

---

### Post by pablo.s on 2009-07-23
> **oktubrer said:**
> ¿Karmic viene con Grub2 por defecto?

Si, viene con GRUB2.


> **oktubrer said:**
> Y en caso de ser afirmativa la respuesta, ¿por defecto es "gráfico" al estilo gfxboot?

No, es puro texto, como el
tipico listado de GRUB pero
aqui lo han adornado un poco
más con unos tonos azules.

> **oktubrer said:**
> Quiero saber si me pongo a tratar de resolver el problema de gfxboot con x64 o espero el lanzamiento de Karmic.

No se que decirte, es una decisión
muy personal.

---

### Post by guillermolisi on 2009-07-23
> Quiero saber si me pongo a tratar de resolver el problema de gfxboot con x64 o espero el lanzamiento de Karmic.
Depende de tu grado de ansiedad, de la disponibilidad de tiempo que tengas, de las ganas de aprender y de (posiblemente) hacerte cargo de algun problema, entre otras cosas.

Se que hay diferencias estructurales entre Grub y Grub2 (alguien hizo sus comentarios por aqui no hace mucho) y, ademas, no son compatibles entre si.

Si aguantas hasta la ultima semana de Octubre, podes dedicarle tiempo y energia a algo diferente. Sino, "vai pra frente, garoto, e boa sorte".

---

### Post by harryscode on 2009-07-23
Hola a todos... una pregunta quizas descolgada y seguro me como un reto, mi primer ubuntu fue JJ, antes, ni cerca de linux, mi duda es.. cuando salga Karmic Koala, es como una actualización más (tipo synaptic, perdón por la ignorancia), o debo instalar todo desde cero?.
Gracias por iluminarme, sino.. de alguna forma me las arreglaré.. no pienso perderme el Koala.
Saludos a todos

---

### Post by pablo.s on 2009-07-23
Es completamente acertado:
hay diferencias gigantescas
entre la primera versión de
GRUB y esta, mas moderna.
Principalmente esta versión 
está diseñada como si fuera
un script de BASH, para decirlo
mal y pronto. De ahi en adelante,
uno podría lograr efectos que
ni se me ocurren, pero al ser
un bootloader que se puede
programar, pueden salir ideas
muy creativas.
El punto mas negativo lo encuentro
en que va a ser más dificil de
arreglar para el usuario de a
pie, por su semi complejidad.

---

### Post by pablo.s on 2009-07-23
> **harryscode said:**
> cuando salga Karmic Koala, es como una actualización más (tipo synaptic, perdón por la ignorancia), o debo instalar todo desde cero?.

Si, en ese aspecto no cambia.
Con el tipico

```
sudo apt-get dist-upgrade
```

se actualiza.

---

### Post by staar on 2009-07-23
> **oktubrer said:**
> Estuve leyendo bastante al respecto pero no entendí, je, asi que te pregunto a vos que lo estas usando.
¿Karmic viene con Grub2 por defecto? Y en caso de ser afirmativa la respuesta, ¿por defecto es "gráfico" al estilo gfxboot?

Quiero saber si me pongo a tratar de resolver el problema de gfxboot con x64 o espero el lanzamiento de Karmic. grub2 se puede instalar en jaunty, requiere un poco de toqueteo, pero mínimo, [acá]("http://phyx.wordpress.com/2009/06/10/como-instalar-grub2-en-ubuntu-jaunty/") hay un tutorial (atención a los comentarios, arreglar lo del uuid/root es importante)

en teoría, grub2 soporta soporta splash-screens, al igual que grub-legacy, pero de mejor calidad (fondos normales, bah), en formato png, jpeg o tga (y no xpm comprimido como el actual)

saludos

---

### Post by guillermolisi on 2009-07-23
> **harryscode said:**
> Hola a todos... una pregunta quizas descolgada y seguro me como un reto, mi primer ubuntu fue JJ, antes, ni cerca de linux, mi duda es.. cuando salga Karmic Koala, es como una actualización más (tipo synaptic, perdón por la ignorancia), o debo instalar todo desde cero?.
Gracias por iluminarme, sino.. de alguna forma me las arreglaré.. no pienso perderme el Koala.
Saludos a todos
Tal como decias, por favor no desvirtues el thread.

El tema de como actualizar desde una version a otra en Ubuntu es tan viejo como el segundo release (tal vez exagerando un poco). Asi que a usar "search this forum" tool.

---

### Post by harryscode on 2009-07-24
Sabia que no iba a tardar en llegar el reto. Trataré de ser un alumno más aplicado la próxima vez.
Gracias

---

### Post by pol666 on 2009-07-24
Uh huelo a "la forma de reparar el grub luego de una instalacion de windows va a cambiar" incluso ya con la 9.04 el  Supergrubdisk no funciona y habia que repararlo dese un livecd

---

### Post by gmunioz on 2009-07-24
Sumimasen por la intromisión Pablo.

El Grub 2 que se instala por defecto 

desde la alfa 2, que como lo uso desde la 

alfa 1, tuve que instalar en forma manual,

se repara desde un live-cd sin problemas,

de última se instala el Grub legacy y se

actualiza al Grub

Respecto de ext4, lo uso para / y /home

desde Jaunty alfa 2 y nunca tuve problemas

decenas de apagones mediante, aunque para

mi /home/usuario/datos aun sigo fiel a reiserfs.

---

### Post by oktubrer on 2009-07-24
Ok, gracias por las respuestas.  Me parece que voy a esperar el release, ya traté varias veces de instalar gfxboot y siempre termine restaurando el grub desde el livecd.
Cuando lo pude instalar ok, no me reconocía casi ninguna imagen (al menos no las que quería).
Tiempo al tiempo! le cambiaré un poco los colores para que se vea distinto.

---

### Post by aledruetta on 2009-07-24
> **pablo.s said:**
> Por lo pronto lo que puedo apreciar
de diferente:

-No hay Usplash (bootea en 20
 segundos o menos: reales)
-El GDM es más lindo, más
modelo 2009.
- Adiós Pidgin y gracias por el pescado!
Reemplazado por Empathy.
- La versión actualizada de OO reconoce
TODAS las fuentes!
- Se nota que anda todo mucho mas 
rápido, más rapido que Jaunty.
-EXT4 como FS por defecto en instalaciones
nuevas.
- Ubuntu One por defecto!
- Muy estable, noto casi ningún problema.
- Un tema nuevo, Ubuntu Evolution.

Otra cosa que noté, es que me avisó cuando la batería de la portátil completó la carga. En Jaunty nunca recibí ese mensaje. Es una pavadita, pero bueno, quería comentarlo.

Y en el selector de usuarios del panel superior aparece un menú para las configuraciones de Ubuntu, una especie de Panel de Control en Windows. Ya antes lo había visto, pero me parece que había que invocarlo en Terminal.

---

### Post by rubioo on 2009-07-24
Mi PC ya esta booteando en menos de 20 segundos, así que va a volar :P

 Muchas gracias por la información pablo :)

            Saludos

---

### Post by lega on 2009-07-25
A mi me pasó algo extraño, bajé la iso del livecd, la grabé y al bootear quedaba trabada en el bootloader, grabé dos cds y me pasó lo mismo, entonces bajé la iso del alternate, lo instalé, y al terminar la instalación reinicié y me pasó lo mismo que con el Livecd, se trababa mas o menos al 10% de cargar el bootloader, de casualidad me acordé que leí en algún lado, no se si acá o en algún blog, que a alguien le pasaba eso y apretando una tecla seguía cargando, así que probé con la barra espaciadora y heme aquí escribiendo estas lineas desde la alpha 3 de Karmic :) ahora instalé los drivers de Nvidia y me pide reiniciar,tengo miedo! :P

---

### Post by pablo.s on 2009-07-25
Vamos Lega, pegue el salto...

---

### Post by lega on 2009-07-25
Bueno, reinicié y pude volver a entrar, lo de la barra espaciadora fue casualidad, sin tocar nada el bootloader queda trabado en el 10% maso y después de 30 seg. arranca, o sea, a mi me tarda mas de 50 seg en arrancar el sistema :) con drivers nvidia solo me reconoce hasta 1024x768 de resolución,eso ya me pasaba con Jaunty y  con el nvidia-settings lo cambiaba, aquí no funciona aún.

No encontré el tema nuevo

---

### Post by Mauro22 on 2009-07-26
Ya lo instalé y la verdad que por ser alpha me parece mas estable que jaunty. 

Me reconoció todo y anda mucho mas rápido.


EDIT: AWN no anda (al menos a mi) y el WiFi siempre apareace desconectado al iniciar sesión, tengo que darle al botón pero veo si hago un script.

EDIT2: Tras una actualizacion perdi el clic en el touchpad (no el boton, sino apretar sobre el pad) y de vez en cuando, se apaga y se prende la pantalla :S... pero las mejoras siguen siendo mas con respecto a JJ

---

### Post by gmunioz on 2009-07-28
Algunas sugerencias:

Para los intrépidos que se arriesguen a usar karmic:

1 - Agreguen a los repositorios, algunos de jaunty, 

como por ejemplo:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

Esto es para evitar el error de dependencias incumplidas, 

que suele aparecer al intentar algunas aplicaciones que

aun no estan disponibles por completo.

2 - Solo actualicen por consola con apt-get, mejor si lo

hacen desde el modo de recuperación, opción netroot, synaptic

es altamente riesgoso y se debe descartar.

3- Si alguna actualización (apt-get upgrade) se detiene

(en modo consola) pulsando Ctrl + C se recupera el control

y mediante dpkg --reconfigure -a, se restablece la instalación

interrumpida de los paquetes.

4 - Si las resoluciones de pantalla no se obtienen por los

medios comunes, se fijan editando xorg.conf y agregando las

opciones conocidas, que aun son válidas a pesar de aparecer

el xorg.conf vacío o caso vacío.

---

### Post by tinoq3 on 2009-07-31
Instalé la Alpha 3 y seguí los pasos tal cual explicaste gmunioz para actualizar. Lo probé prácticamente nada ya que lo puse ayer a la noche. Hasta el momento lo único que pude observar fue:

- Tengo un disco con XP y otro para Ubuntu, luego de instalar no podía ver desde Grub la opción de arranque de "Ventanita". Lo pude solucionar con un "sudo update-grub2"

- Un pantallazo negro durante un seg pero luego volvió a la normalidad.

- Cada vez que inicia, monta automáticamente el disco de XP y para esto me pide password (es medio molesto).

- Al crear la conexión de Speedy me pidió una password para algo llamado "key....." no sé cuanto más (disculpen pero no acuerdo) y cada vez que conecta me la pide (también es molesto).

Y si, lo noto más rápido que JJ... supongo que será porque no tengo compiz activado :rolleyes:

---

### Post by guillermolisi on 2009-07-31
Una razon por la cual es algo mas rapido es que usa EXT4 como sistema de archivo.

---

### Post by staar on 2009-07-31
> **tinoq3 said:**
> 
- Cada vez que inicia, monta automáticamente el disco de XP y para esto me pide password (es medio molesto).

- Al crear la conexión de Speedy me pidió una password para algo llamado "key....." no sé cuanto más (disculpen pero no acuerdo) y cada vez que conecta me la pide (también es molesto).


eso es de fácil solución, podés especificar la partición NTFS en el fstab para que la monte cuando todavía no te logueaste, o cambiás los permisos para que tu usuario pueda montar discos...

para que no te pida password del keyring podés cambiarlo por uno vacio, eso se explicó en el foro, para alguien que se lo pedía al conectarse a wifi, según me acuerdo (y también se explicó para el kwallet de kubuntu)

saludos

---

### Post by Mauro22 on 2009-07-31
> **tinoq3 said:**
> - Un pantallazo negro durante un seg pero luego volvió a la normalidad.


A mi tambien me pasa, lo "solucioné" desactivando el salvapantallas... pero igual pasa... no tan seguido pero pasa.. tenes placa Intel Graphics??

> **guillermolisi said:**
> Una razon por la cual es algo mas rapido es que usa EXT4 como sistema de archivo.

Mas alla de eso, yo en JJ ya tenia ext 4 y volaba, ahora sigo con ext4 y vuela aun mas..



Lo noto mas con Virtualbox, tengo 2 monitores, en uno corriendo kk y en el otro Ventanas 7 ... y es increible la mejoria que hay corriendo los dos a la vez.


**_*Lo bueno:*_** No hay mas "lineas" raras en los videos, en esas partes rapidas que parece que tarda en refrescarse la imagen. Eso no esta mas. Las peliculas tienen un poco mas de definicion.

_***Lo malo: ***_Aun con las mejorias en los drivers Intel, Compiz se sigue colgando...

---

### Post by tinoq3 on 2009-08-02
Gracias staar, solucionado lo del keyring. Probé dándole permisos a mi usuario pero continúa pidiendo password para montar el disco con XP. Voy a tener que averiguar como modificar el fstab.

PD: Alguien pudo instalar los drivers 9.7 de Ati? No hubo forma de hacerlos andar...

---

### Post by pol666 on 2009-08-02
estaba pensando Mauro, y si probas Kwin el composite de KDE4, te dara los mismos problemas?

---

### Post by Mauro22 on 2009-08-03
Sabes que es lo que me intriga. 


Ayer encontré mi pendrive con slax que tiene Kde e instale el modulo de Compiz. E funciono de maravilla. 


Como serian los pasos? instalo kde y?



Gracias!!!

---

### Post by guillermolisi on 2009-08-03
> **Mauro22 said:**
> Sabes que es lo que me intriga. 


Ayer encontré mi pendrive con slax que tiene Kde e instale el modulo de Compiz. E funciono de maravilla. 


Como serian los pasos? instalo kde y?



Gracias!!!
Kwin con Compiz siempre resulto conflictivo, por lo menos desde KDE3 a la fecha (KDE4.3)

---

### Post by pablo.s on 2009-08-03
Si, si, hagan todo el
off-topic que quieran 
porque en diez dias se
viene post de Alpha 4...

---

### Post by sartrejp on 2009-08-03
Les hago una consulta. El tiempo de booteo, ¿desde cuando hasta cuando lo miden? En mi caso (con JJ, 32 bits, 2 nucleos y 2 gb de ram) desde que aprieto el botón de encendido, hasta que aparece el escritorio listo para usar, pasan unos 50 segundos (y eso que desactivé algunos servicios como bluetooth e impresora porque no estoy usando)

---

### Post by pablo.s on 2009-08-03
> **sartrejp said:**
> El tiempo de booteo, ¿desde cuando hasta cuando lo miden? 

La clave del tiempo de booteo,
a mi humilde entender se define
por dos factores que no son ni el
procesador ni la memoria en si.
Lo que define es la rapidez del
disco rígido y el file system.
Por qué digo esto? Porque cuando
la máquina bootea trata de cargar
en la memoria todos los procesos
del init elegido y los corre desde
el disco. Se ha comprobado que 
con los discos SSD, que no tienen
un tiempo de giro físico el arranque
es muy superior al de un disco que
tiene que comenzar a girar y situar
los cabezales. Agregado a esto que
el file system sea más optimizado,
por ejemplo un Ext4, un ZFS, o digamos
Butter FS (la gran esperanza negra)
te dá un tiempo razonable.

Ah, me olvidaba: yo lo mido desde que
presiono el botón de Power hasta
que muestra GDM.

---

### Post by fedeavila on 2009-08-06
[FONT="Segoe UI"][SIZE="2"]¡Hola! Alguien conoce alguna pág. (oficial o no) para ver las noticias/novedades de la nueva versión de Ubuntu? O sea, las modificaciones, el día a día, las implementaciones, etc. ¡Gracias![/SIZE][/FONT]

---

### Post by pablo.s on 2009-08-06
En la [página del lanzamiento]("http://www.ubuntu.com/testing/karmic/alpha3")
de la última Alpha hay una
pequeña descripción de cada
mejora o caracteristica.

---

### Post by fedeavila on 2009-08-06
> **pablo.s said:**
> En la [página del lanzamiento]("http://www.ubuntu.com/testing/karmic/alpha3")
de la última Alpha hay una
pequeña descripción de cada
mejora o caracteristica.

[FONT="Segoe UI"][SIZE="2"]¡Genial! Buscaba algo en español más que nada xD 
Pero por lo menos pude sacar la fecha de lanzamiento...

Dentro de 3 meses(?)[/SIZE][/FONT]

---

### Post by pablo.s on 2009-08-06
> **fedeavila said:**
> [FONT=Segoe UI][SIZE=2]¡Genial! Buscaba algo en español más que nada[/SIZE][/FONT]


[En este post]("http://ubuntuforums.org/showthread.php?t=1221280") debatimos
mas o menos lo mismo
en español. En seis dias
sale la Alpha 4.

---

### Post by jap1968 on 2009-08-23
En mi blog he hecho una pequeña revisión de [Ubuntu 9.10 alfa 4]("http://ospatia.blogspot.com/2009/08/novedades-en-ubuntu-910.html"), con algunas capturas de pantalla.

Está en castellano y los comentarios son bienvenidos :popcorn:

---

### Post by fedeavila on 2009-08-23
[SIZE="2"][FONT="Segoe UI"]> **jap1968 said:**
> En mi blog he hecho una pequeña revisión de [Ubuntu 9.10 alfa 4]("http://ospatia.blogspot.com/2009/08/novedades-en-ubuntu-910.html"), con algunas capturas de pantalla.

Está en castellano y los comentarios son bienvenidos :popcorn:

Eah! Genial! Gracias! Esperemos que KaKo nos sorprenda en Octubre/Noviembre jaja :D[/FONT][/SIZE]

---

### Post by pablo.s on 2009-09-09
[IMG]http://ubuntuforums.org/images/editor/menupop.gif[/IMG][ATTACH]128041[/ATTACH]

---

### Post by pol666 on 2009-09-09
> **pablo.s said:**
> [IMG]http://ubuntuforums.org/images/editor/menupop.gif[/IMG][ATTACH]128041[/ATTACH]


Y tiene un SDD :(

> 
 En mi blog he hecho una pequeña revisión de Ubuntu 9.10 alfa 4, con algunas capturas de pantalla.

Está en castellano y los comentarios son bienvenido

EL analizador de espacio en disco si estaba, tenes que teclear baobab en consola y aparece, otra cosa, no tenes capturas del instalador que dicen que esta lindo? :popcorn:

---

### Post by juancarlospaco on 2009-09-10
Reportando novedades, 
no voy a hacer un tema nuevo por cada Alpha, ademas no se que alpha es...

Viene un programa para mantener la salud, estado, formateos, scaneos,
montar, desmontar, expulsar, desacoplar*(para HotSwap?)*,
iniciar, parar, bloquear, desbloquear, borrar,
SMART, RAID* software, y utilidades de discos *(solidos, rigidos, etc)*,
el mismo tiene un icono en el area de notificacion si hay algo mal en los discos.

[CENTER][IMG]http://img41.imageshack.us/img41/8382/palimtes.gif[/IMG][/CENTER]

El menu "**Lugares**" fue re-ordenado, ahora hay un Sub-Menu "**Marcadores**",
que contiene las carpetas :
[LIST]
[*]Documentos
[*]Musica
[*]Imagenes
[*]Videos
[*]Descargas
[*]Ubuntu One
[/LIST]

Todas las descargas van por defecto a la carpeta "**Descargas**",
que es nueva en la Carpeta Personal.

El icono de red del area de notificacion fue cambiado 
por uno que parece una foto de un RJ-45 Hembra *(cuando hay red cableada)*

Las notificaciones tienen ademas del efecto de transparencia,
se les agrego un muy elegante **efecto de Blurr** *(difuminado)*

El** indicator-applet** esta presente aunque este vacio, 
tiene el icono de una carta cerrada de papel blanco,
cualquier notificacion en el escritorio, 
luego de ser anunciada por el notify-osd va a parar ahi.
*(estoy en los creditos por traducirlo :P)*

SCiM fue reemplazado por Ibus.

Para la mensajeria esta Emphaty, aunque los SlideShow anunciaban Pidgin *(???)*

**PlayOnLinux esta en los Repos oficiales**,
al buscar *"Windows game"* en synaptic te aparece,
yo estoy jugando el Far Cry 2 original,
que vino de regalo con un mother en el laburo,
fue todo next next next next, version de Wine 1.1

**Emesene 1.5** en los Repos.

**VirtualBox 3**.0.4

Adobe Reader 9 *(wacale)* en los repos oficiales *(seccion partner)*

**Gnome-Shell **en los repos

**Quickly **en los repos *(estoy buscando un tuto para este)*

Parece haber una GUI para Quickly hecha en Quickly*(Python simplificado)*,
pero no esta en los Repos.

Algo nuevo se trae el Ubuntu One,
por que instala algunas librerias y cosas de CouchDB *(Couch data base)*



:guitar:

---

### Post by josecuervo86 on 2009-09-10
[quote=juancarlospaco]El menu "Lugares" fue re-ordenado, ahora hay un Sub-Menu "Marcadores",
que contiene las carpetas :

    * Documentos
    * Musica
    * Imagenes
    * Videos
    * Descargas
    * Ubuntu One
[/quote]

El submenu marcadores aparece cuando tenes mas de 5 directorios en lugares. Si sacas uno (por ejemplo Ubuntu One) te vuelve a quedar como antes

---

### Post by facurdo on 2009-09-11
Espero que a fines de ocutbre pueda usar la pc en 1024x768 con mi placa de video integrada intel 82865G (me tiene 800x600 jajaja)

---

### Post by juancarlospaco on 2009-09-12
**Si en las graficas Intel te brinda mas resolucion**, 
tambien en los monitores secundarios, 
yo tenia el problema mucho antes de que el limite de resolucion del secundario era igual al principal,
lo cual no esta bueno por que era una Netbook conectada a un Videoproyector.

---

### Post by guisheca on 2009-09-12
Yo sólo quería opinar que probé la ultima alpha de ubuntu y me *BEEP* de gusto. Amo ubuntu.

---

### Post by juancarlospaco on 2009-09-13
***Con ustedes el Software Store de Ubuntu: ***

[IMG]http://img269.imageshack.us/img269/2041/softstore.gif[/IMG]

El tema es uno que viene, se llama Hanso y trae iconos propios nuevos.
Al instalarlo agrega la entrada de Menu:** Sistema--->Tienda de Software de Ubuntu**

:)

---

### Post by pablo.s on 2009-09-13
Seguramente venga integrada en
la Alpha 6 que sale el 17, si no me 
equivoco. Además está previsto
que todo el tema gráfico sea renovado,
asi que preparemos la actualizacion!

---

### Post by pol666 on 2009-09-13
Uh me muero por ver el nuevo tema marron xD [/ironia]

---

### Post by pablo.s on 2009-09-13
Menos mal que no sos usuario
de Mac, que hace años que es
gris...

---

### Post by juancarlospaco on 2009-09-13
Lo impresionante es lo rapido que busca el cosito de buscar,
vas tipeando y filtra letra por letra instantaneo,
no es como el agregar y quitar que tiene un pequeño delay de unos segundos,
y tengo 28.9xx paquetes solo con los oficiales, partner y medibuntu, 
cada vez hay mas paquetes...

---

### Post by pablo.s on 2009-09-13
> **juancarlospaco said:**
> Lo impresionante es lo rapido que busca el cosito de buscar,
vas tipeando y filtra letra por letra instantaneo,

Ahí tenés para que era que
instalaba CouchDB.

---

### Post by juancarlospaco on 2009-09-13
> **pol666 said:**
> Uh me muero por ver el nuevo tema marron xD [/ironia]

[B][I]Marron...?
Donde...?[/I][/B]

[CENTER][IMG]http://img9.imageshack.us/img9/8702/temes.jpg[/IMG][/CENTER]

*[SIZE="1"]Ahh... en el DarkRoom[/SIZE]*
:D

---

### Post by juancarlospaco on 2009-09-13
Resulta que ahora cualquiera programa tambien :P

solo puse lo que da de ejemplo:
*"quickly create ubuntu-project test"*
y...

[CENTER][IMG]http://img177.imageshack.us/img177/5825/quickly.jpg[/IMG][/CENTER]

:D

---

### Post by pablo.s on 2009-09-13
Quickly hace que COMENZAR un
proyecto con Glade y PyGTK sea
más sencillo, pero no te enseña a
programar, no te hace programador
ni mucho menos.
Es una forma de incentivar a los
programadores que utilizan Python a
adentrarse en las aplicaciones gráficas.
El comando que invocaste lo que
hace es armarte un proyecto básico.
Pero no obstante tiene mucho potencial.

---

### Post by juancarlospaco on 2009-09-14
Coincido, ya lo se, 
pero ademas trae un lindo Tuto paso por paso sencillo *(pero en ingles)*

---

### Post by pol666 on 2009-09-14
Más allá del tema en especial. Yo creo que gnome no rinde más en lo que es visual, A no ser que gnome 3 se venga con todo, Canonical va a tener que desarollar cosas arriba, obvio si pretende competir con el escritorio de mac como habia dicho marky :)

---

### Post by guillermolisi on 2009-09-14
> **juancarlospaco said:**
> Resulta que ahora cualquiera programa tambien :P
 [CENTER][IMG]http://img177.imageshack.us/img177/5825/quickly.jpg[/IMG][/CENTER]

O codifica ? :)

---

### Post by Irwin Cespedes on 2009-09-14
Pregunto... Y Empathy? Sopprta Webcams o video conferencia :confused:

---

### Post by Hei Ku on 2009-09-14
> **pol666 said:**
> Más allá del tema en especial. Yo creo que gnome no rinde más en lo que es visual, A no ser que gnome 3 se venga con todo, Canonical va a tener que desarollar cosas arriba, obvio si pretende competir con el escritorio de mac como habia dicho marky :)

Off-topic y al borde del flamebait. :(

---

### Post by pablo.s on 2009-09-14
Pero, muchachada, este thread se
habia puesto lindo y se vienen a
pelear justo acá!
Un llamado a la coherencia.

---

### Post by staar on 2009-09-14
> **Irwin Cespedes said:**
> Pregunto... Y Empathy? Sopprta Webcams o video conferencia :confused:
depende el protocolo, pero si, hasta ahora solo en sip y xmpp/google talk, pero hace unos días se agregó soporte para la red msn...

saludos

---

### Post by juancarlospaco on 2009-09-15
Yo en los Slides de instalacion sigo viendo *"Pidgin el Cliente de IM de Ubuntu"*
CHAN!!!

---

### Post by ALEXEX on 2009-09-15
> **Mauro22 said:**
> Les dejo el mio aunque no lo pidan...
 
 
Karmic Koala actualizado al dia.
 
Screenlets: PerfectClock y Notes
Dock: Awn
Wall: Karmic Koala Unofficial
GTK: Hanso
Icons: Breathe
 
 
Hola Mauro.
 
Quizas esta pregunta no venga al tema, pero que tal esta Karmic Koala, es q en internet ya e buscado y aparece muy poca informacion, que trae de nuevo?

---

### Post by pol666 on 2009-09-15
perdon fue inevitable.:mrgreen:            [COLOR="White"]gnome s*cks[/COLOR]

---

### Post by pablo.s on 2009-09-15
En nombre del amigo Jorge Castro
les informo que:
[ATTACH]128743[/ATTACH]

Traducido al español:
Usuarios de Karmic, no ejecuten un
partial-upgrade o dist-upgrade por
el dia de hoy (Sept 15) porque los
initscripts se van a romper.

PD: Identi.ca FTW!

---

### Post by Mauro22 on 2009-09-16
> **pablo.s said:**
> En nombre del amigo Jorge Castro
les informo que:
[ATTACH]128743[/ATTACH]

Traducido al español:
Usuarios de Karmic, no ejecuten un
partial-upgrade o dist-upgrade por
el dia de hoy (Sept 15) porque los
initscripts se van a romper.

PD: Identi.ca FTW!

haberlo sabido antes.... :(

---

### Post by pablo.s on 2009-09-16
> **Mauro22 said:**
> haberlo sabido antes.... :(

Uh, te paso? Necesitamos un
sistema de rollback urgente, como
OpenSolaris... A ver dejame buscar
que en algún lado habia visto una
solución.

Mauro, fijate si [estas instrucciones]("http://roderick-greening.blogspot.com/2009/09/recover-non-booting-linux-system.html") te
son útiles.

---

### Post by Mauro22 on 2009-09-16
Me pasó y dos veces encima.. actualicé pensando que no iba a suceder....


Lo que encontré es hacer esto:

```
Once again this save me:
1)log to your account in tty1
2)sudo start dbus
3)sudo start hal
4)sudo start network-manager (i am on ADSL via ethernet)
5)sudo start gdm
```


[http://ubuntuforums.org/showpost.php?p=7958872&postcount=14](http://ubuntuforums.org/showpost.php?p=7958872&postcount=14)



Eso lo soluciona, hasta que se vuelva a actualizar. Hasta AHORA no hay update disponible.


Estoy con la alpha 1 de nuevo.

---

### Post by juancarlospaco on 2009-09-16
Pero APT y DPKG tiene Rollback :)
*Pero no la GUI*

:)

---

### Post by Mauro22 on 2009-09-16
Ya esta arreglado..


Hay que hacer un 
```

sudo apt-get dist-upgrade
```


Despues de unos largos 400mb, ta todo joya!

---

### Post by gmunioz on 2009-09-16
Hola.....:

Recomendación:

Editen el archivo /etc/default/grub

Busquen las líneas:


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0

Y cambien a:


GRUB_DEFAULT=1

Luego ejecuten update-grub

Con esto se logra que:

A por defecto, inicia en recovery mode,

ante problemas de incio, se podrá iniciar 

en consola mediante el submenu netroot

para solucionar los problemas

o

GRUB_HIDDEN_TIMEOUT=5

Luego ejecuten update-grub

Con esto se logra que:

que ante problemas del modo gráfico

al pulsar escape podamos elegir iniciar

en recovery mode, y con netroot

Una u otra opción o las dos.

---

### Post by juancarlospaco on 2009-09-17
Updates seguros *(atm)*
Nuevo XSplash en repos *(hermoooshooo)*

---

### Post by Mauro22 on 2009-09-17
> **juancarlospaco said:**
> Updates seguros *(atm)*
Nuevo XSplash en repos *(hermoooshooo)*


[IMG]http://img410.imageshack.us/img410/1224/xsplash33.png[/IMG]


:P:P

---

### Post by pol666 on 2009-09-17
Ahhhhhhhhh eso es calidad :D

---

### Post by fedeavila on 2009-09-17
> **Mauro22 said:**
> [IMG]http://img410.imageshack.us/img410/1224/xsplash33.png[/IMG]

[FONT="Segoe UI"]Ta piola ese. ¿No tenés alguna fotito del "theme" nuevo que trae con el wallpaper?[/FONT]

---

### Post by santiagoward2000 on 2009-09-20
> **juancarlospaco said:**
> ***Con ustedes el Software Store de Ubuntu: ***

El tema es uno que viene, se llama Hanso y trae iconos propios nuevos.
Al instalarlo agrega la entrada de Menu:** Sistema--->Tienda de Software de Ubuntu**

:)

Gente, estaba leyendo en [este thread]("http://ubuntuforums.org/showthread.php?p=7968677") que piensan traer este Software Store instalado en Karmic, y no Synaptic (cosa que no me convence, pero bueno, por lo menos Synaptic va a seguir en los repositorios). Mientras leía veo que alguien menciona la presencia de un **"Precio"** en la descripción de los paquetes, como se aprecia en una de las screens que puso juancarlospaco. ¿Alguien sabe de qué se trata? ¿Tienen pensado agregar software pago a los repositorios?
Saludos!

---

### Post by pablo.s on 2009-09-20
Por ahora están los dos,
personalmente NO creo que 
vayan a descartar a Synaptic.
Lo de Software Store es parte
de la "Appleificación" de Ubuntu
que se está planeando de a
poco. Si bien una tienda es por
lo general de indole comercial,
es una cuestión de nombre.
Igualmente si hubiera programas
a la venta, todo bien. Nadie debe
ser condenado por tratar de ganarse
un dinero.

---

### Post by santiagoward2000 on 2009-09-20
> **pablo.s said:**
> Por ahora están los dos,
personalmente NO creo que 
vayan a descartar a Synaptic.

En el thread que estaba leyendo, Amaranth (Ubuntu Developer) dijo:
> **Amaranth said:**
> Software Store isn't meant to replace synaptic completely, it's just supposed to provide enough functionality for regular users to not need to use synaptic. Mainly installing non-GUI apps. Synaptic will still be in the repos for you to install.
Para los que no hablen inglés, se traduce en:
> La Tienda de Software no pretende sustituir por completo synaptic, sólo debe aportar la suficiente funcionalidad para que los usuarios regulares no necesiten usar Synaptic. Principalmente la instalación de aplicaciones de interfaz no gráfica. Synaptic todavía estará en los repositorios para instalar.
La frase final me da la impresión que piensan sacar Synaptic. Igual espero que tengas razón y quede. Personalmente me parece más una alternativa a gnome-app-install (Agregar/Quitar...) que a Synaptic.

> **pablo.s said:**
> Lo de Software Store es parte
de la "Appleificación" de Ubuntu
que se está planeando de a
poco. Si bien una tienda es por
lo general de indole comercial,
es una cuestión de nombre.
Igualmente si hubiera programas
a la venta, todo bien. Nadie debe
ser condenado por tratar de ganarse
un dinero.

No estaba "condenando" a nadie. Nada más me llamó la atanción. Hoy (hasta donde yo sé) todo el software que se incluye en los repositorios es gratis, y me pareció raro que pongan en todos los programas **"Precio: gratis"**.

Saludos!

---

### Post by pablo.s on 2009-09-20
Aclaro, cuando decia que
nadie debia ser condenado, 
no me referia a que estuvieras
condenando la venta de los
programas, sino a la tradicional
confusión de "Free Software"
como "Software Gratis" y no como
lo que realmente significa:
"Software Libre", con cuatro
libertades básicas.

---

### Post by lega on 2009-09-20
A mi con las ultimas actualizaciones de la alpha 6 el Ubuntu App Store me desapareció ya no está más, a alguien más le ha pasado?

---

### Post by santiagoward2000 on 2009-09-20
> **pablo.s said:**
> Aclaro, cuando decia que
nadie debia ser condenado, 
no me referia a que estuvieras
condenando la venta de los
programas, sino a la tradicional
confusión de "Free Software"
como "Software Gratis" y no como
lo que realmente significa:
"Software Libre", con cuatro
libertades básicas.

Por mi parte no hacía falta aclarar.
[LIST=1]
[*]Ya sé que la GPL permite la venta de software.
[*]También hay que tener en cuenta que no todos los paquetes en los repositorios son libres.
[/LIST]

---

### Post by pablo.s on 2009-09-20
> **lega said:**
> A mi con las ultimas actualizaciones de la alpha 6 el Ubuntu App Store me desapareció ya no está más, a alguien más le ha pasado?

Si, ya no aparece en el
menú System.

---

### Post by juancarlospaco on 2009-09-21
El indicator-applet tiene integracion con Empathy, Evolution, 
*...y ademas Gwibber como cliente de Identi.Ca*

---

### Post by aledruetta on 2009-09-23
> **pablo.s said:**
> Si, ya no aparece en el
menú System.

Cuando instalé la alpha 6 estaba, después, al día siguiente actualizé y desapareció, pero ahora está de nuevo, donde antes estaba agregar y quitar aplicaciones.

---

### Post by aledruetta on 2009-09-23
Desde la alpha 3 hasta la última actualización de hoy de la alpha 6 no había conseguido activar los controladores de la conexión inalámbrica. Ahora, por suerte está funcionando.
Lo que sigue sin funcionar es el click en el touch pad. Es decir, el touch pad funciona, uno pasa el dedo y el cursor se murve, pero cuando golpea con el dedo no clickea, obliga a clickar con el botón.

---

### Post by Fak89 on 2009-09-24
> **Mauro22 said:**
> [IMG]http://img410.imageshack.us/img410/1224/xsplash33.png[/IMG]


:P:P

Fuaa! alguna forma de ponerlo en Jaunty?

---

### Post by lega on 2009-09-24
Diferencias entre la versión 9.04 
[ATTACH]129598[/ATTACH]

y la versión 9.10 (alpha 6 )
[ATTACH]129599[/ATTACH]

Me falta un CPU :P

---

### Post by pablo.s on 2009-09-24
Es rarísimo eso, lega.
¿Qué procesador es?

---

### Post by lega on 2009-09-24
si, raro, el procesador es un Amd64 X2 4200+ ninguna de las dos versiones instaladas es de 64bits, es la clásica versión i386, noto algo de lentitud en la alpha de karmic, pero reconozco que  puedo estar sugestionado porque descubrí esto :)

---

### Post by pablo.s on 2009-09-24
Recién lo actualicé y
me muestra los dos
cores. Tiene GNOME
2.28 que acaba de ser
lanzado, un GDM un
poquitín más pulido,
unos fondos espaciales
y un tema de iconos
nuevo.
Network Manager trae
el nuevo rediseño.

---

### Post by xpelaox on 2009-09-24
Hola! Un detalle que descrubir y me puso muy feliz (aunque es una *): Cuando usaba mi notebook en Windows, cuando tenia sonido, el boton de "Mute" aparecia con led azul, y cuando muteaba, el led se ponia naranja. En ubuntu siempre quedaba azul hasta la llegada de KK! Magico!:D

---

### Post by juancarlospaco on 2009-09-26
**Lindos Wallpapers nuevos! **:)

[I]Me puse a investigar y 1 de las fotos es de un Parque en Chile.
Otras fueron tomadas por Mark Shuttleworth en persona, 
la verdad no sabia, cosas interesantes que nos revelan los EXIF.[/I]

---

### Post by aledruetta on 2009-09-27
Vieron que comenté que tengo un problema con el touchpad desde la alpha 3 hasta el minuto antes de escribir esto. Consigo dirigir el cursor pero no clickear cuando le pego con el dedo (es la descripción más técnica que se me ocurre) Lo extraño es que todo funciona hasta la ventana GDM, una vez que pasé de ahí, no funciona más.

Lo que me gustaría saber es si ese tipo de cosas se puede informar al equipo de desarrollo de karmic y cómo. Si es en inglés, desisto. Pero si hay otro modo, lo intentaría.

Saludos y gracias.

---

### Post by guillermolisi on 2009-09-27
> **aledruetta said:**
> Vieron que comenté que tengo un problema con el touchpad desde la alpha 3 hasta el minuto antes de escribir esto. Consigo dirigir el cursor pero no clickear cuando le pego con el dedo (es la descripción más técnica que se me ocurre) Lo extraño es que todo funciona hasta la ventana GDM, una vez que pasé de ahí, no funciona más.

Lo que me gustaría saber es si ese tipo de cosas se puede informar al equipo de desarrollo de karmic y cómo. Si es en inglés, desisto. Pero si hay otro modo, lo intentaría.

Saludos y gracias.
Para informar este sintoma como bug esperaria al lanzamiento de la version final o, en su defecto, por lo menos a la beta que esta proxima a salir.

Y si, los informes de bugs son indefectiblemente en Ingles.

---

### Post by pablo.s on 2009-09-27
Escribite el reporte de bug
en castellano que te lo traducimos
aca, asi lo presentas en Launchpad.
Eso si, vas a tener que abrir una
cuenta.

---

### Post by oktubrer on 2009-09-27
> **aledruetta said:**
> Consigo dirigir el cursor pero no clickear cuando le pego con el dedo (es la descripción más técnica que se me ocurre) Lo extraño es que todo funciona hasta la ventana GDM, una vez que pasé de ahí, no funciona más.


Probablemente ya te fijaste, pero en la configuración del mouse (o del touchpad) se puede des/habilitar el click "golpeando" el touchpad.
Más no te puedo ayudar porque actualmente estoy usando Kde.

---

### Post by aledruetta on 2009-09-28
> **oktubrer said:**
> Probablemente ya te fijaste, pero en la configuración del mouse (o del touchpad) se puede des/habilitar el click "golpeando" el touchpad.
Más no te puedo ayudar porque actualmente estoy usando Kde.

Bueno, gracias por frustrar mi primer informe de bug en launchpad. Ya había creado una cuenta y firmado el código de conducta, etc. Y resulta que era eso. En la configuración del touchpad se puede activar y desactivar la pulsación. Se ve que siempre vino activada por defecto y esta vez no.

No, fuera de broma, gracias oktubrer por la solución; y gracias a Guillermo y Pablo por lo de launchpad, otra vez será.

---

### Post by guillermolisi on 2009-09-28
> **aledruetta said:**
> Bueno, gracias por frustrar mi primer informe de bug en launchpad. Ya había creado una cuenta y firmado el código de conducta, etc. Y resulta que era eso. En la configuración del touchpad se puede activar y desactivar la pulsación. Se ve que siempre vino activada por defecto y esta vez no.

No, fuera de broma, gracias oktubrer por la solución; y gracias a Guillermo y Pablo por lo de launchpad, otra vez será.
Bueno, digamos que ahora no lo vas a usar pero seguramente no faltara oportunidad de que lo estrenes :)

Eso se llama ser previsor.

---

### Post by gmunioz on 2009-09-30
Gnome-shell

gnome-shell, por defecto ya en los repositorios esta

funcionando muy bien, traducido, muy rápido y vistoso.

Se ubica en Accesorios  oculto, basta editar el menu

activarlo y cambiar la orden de inicio de gnome-shell a

gnome-shell --replace, para poder usarlo.

---

### Post by aledruetta on 2009-09-30
> **gmunioz said:**
> Gnome-shell

gnome-shell, por defecto ya en los repositorios esta

funcionando muy bien, traducido, muy rápido y vistoso.

Se ubica en Accesorios  oculto, basta editar el menu

activarlo y cambiar la orden de inicio de gnome-shell a

gnome-shell --replace, para poder usarlo.

La he estado probando y me parece una dirección interesante para el escritorio Gnome (a pesar de que se leen muchas críticas en blogs y demás yerbas) 
El buscador que incorpora en "Actividades" funciona como un gnome-do. Encuentro muy prácticos los espacios de trabajo y cómo se mueven las cosas entre ellos. Todavía le falta pulido, pero creo que es un concepto interesante de escritorio.

Y mañana se viene la Beta de Karmic!!!

Otra cosa que estuve experimentando hoy es la beta 14 de LUBUNTU. La instalé en un pendrive de 1 GB, usando una partición de 500 Mb, y como si fuera un LiveCD (me queda la otra mitad para llevar datos). Lo hice con la misma herramienta que tiene Jaunty para crear discos USB de inicio, desde una imagen que bajé de 350 Mb, más o menos. Realmente interesante para tener un sistema GNU/Linux liviano, para llevar en un pendrive o para usar en una maquina modesta. Anda volando.

El que la quiera probar la encuentra aquí: [http://download.lxde.org/lubuntu-9.10/](http://download.lxde.org/lubuntu-9.10/)

---

### Post by juancarlospaco on 2009-10-01
Che pero hay una GUI para configurar eso del touchpad, yo la vi, 
no recuerdo el nombre, busca en Synaptic o el Software Center...

---

### Post by aledruetta on 2009-10-01
> **juancarlospaco said:**
> Che pero hay una GUI para configurar eso del touchpad, yo la vi, 
no recuerdo el nombre, busca en Synaptic o el Software Center...

Gracias, Juan Carlos, ya lo resolví con el consejo de Oktuber. La configuración del touchpad está en "Sistema-->Preferencias-->Ratón-->Touchpad-->Activar pulsaciones del ratón con el touchpad".

---

### Post by aledruetta on 2009-10-01
Estoy bajando, por descarga directa, la imágen de la la Beta de Karmic. La conexión está muy lenta, debería bajar a 350 Kb y está bajando a 15 Kb. 
Entonces, cuando intento bajar el torrent con Transmission, para ver si de esa forma va más rápido, me arroja un error:
```
Request download is not authorized for use with this tracker - inactivo
```
¿Cuál puede ser el motivo?

---

### Post by aledruetta on 2009-10-01
Instalé Deluge y da el mismo error.

---

### Post by santiagoward2000 on 2009-10-01
> **aledruetta said:**
> Estoy bajando, por descarga directa, la imágen de la la Beta de Karmic. La conexión está muy lenta, debería bajar a 350 Kb y está bajando a 15 Kb. 
Entonces, cuando intento bajar el torrent con Transmission, para ver si de esa forma va más rápido, me arroja un error:
```
Request download is not authorized for use with this tracker - inactivo
```
¿Cuál puede ser el motivo?

A mí me hace lo mismo, pero solo el de Ubuntu. Xubuntu y Kubuntu se están bajando sin problemas por torrent. No sé qué podrá ser.

---

### Post by oktubrer on 2009-10-01
> **santiagoward2000 said:**
> A mí me hace lo mismo, pero solo el de Ubuntu. Xubuntu y Kubuntu se están bajando sin problemas por torrent. No sé qué podrá ser.

Same here!

---

### Post by juancarlospaco on 2009-10-01
Che vieron que bueno cuando clickeas una fuente de texto.
Instala fuente automatico, aunque me gusta mas que la fuente venga en .deb, sino pa sacarla despues.

---

### Post by aledruetta on 2009-10-02
> **juancarlospaco said:**
> Che vieron que bueno cuando clickeas una fuente de texto.
Instala fuente automatico, aunque me gusta mas que la fuente venga en .deb, sino pa sacarla despues.
¿Cómo es eso? No entendí.

---

### Post by rubioo on 2009-10-02
Supongo que debe ser que cuando no tenes una fuente instalada, y hay un texto que la esta usando. Al hacer clic se te instala la fuente.

---

### Post by pablo.s on 2009-10-02
No, si tenés una carpeta con 
fuentes y le hacés doble clic
a la fuente para visualizar, sale
un botón de "instalar fuente".

---

### Post by goldenfox on 2009-10-02
umm me recomiendan actualizar mi ubuntu 9.4 a la ultima de 9.10? o espero a que salga la final (me muero de ganas por probarlo xD)

---

### Post by pablo.s on 2009-10-02
Si esperaste hasta ahora,
te recomiendo que esperes
a que salga el 29 de Octubre.

---

### Post by santiagoward2000 on 2009-10-03
Qué bueno que está el nuevo tema de Xubuntu! :P

---

### Post by aledruetta on 2009-10-03
> **santiagoward2000 said:**
> Qué bueno que está el nuevo tema de Xubuntu! :P

Se agradece una captura ;)

---

### Post by santiagoward2000 on 2009-10-03
> **aledruetta said:**
> Se agradece una captura ;)

El tema se llama **Albatross** y los íconos **Elementary Xubuntu**. :)

---

### Post by aledruetta on 2009-10-03
> **santiagoward2000 said:**
> El tema se llama **Albatross** y los íconos **Elementary Xubuntu**. :)
Sí, muy lindo, realmente. Gracias Santiago.

---

### Post by santiagoward2000 on 2009-10-03
> **aledruetta said:**
> Sí, muy lindo, realmente. Gracias Santiago.

De nada :KS

---

### Post by juancarlospaco on 2009-10-06
Sincronizacion de Post-It Virtuales en la Nube del Koala.
Tomboy
:)

---

### Post by losoollenos on 2009-10-10
Bueno, sólo comentar que estoy probando en una partición, la versión beta de Karmic Koala 9.10, y me parece que al igual que la Intrepid 8.10, viene "sedienta de RAM". No puedo decir que esto sea malo en sí mismo, además quizás no sea así la versión final, pero.....me parece que voy a seguir con mi ranking: 1) Hardy 8.04 y 2) Jaunty 9.04.

Saludos para tod@s !!!!

---

### Post by fedeavila on 2009-10-10
[FONT="Segoe UI"][SIZE="2"]Pero contá algo más... A mi por ejemplo me dio mucha impresión que no haya encontrado drivers para mi Epson TX115 con tan sólo 1 día de vida jaja[/SIZE][/FONT]

:(

---

### Post by aledruetta on 2009-10-10
Edité el comentario absurdo que hice. No sé en qué estaba pensando...

---

### Post by pablo.s on 2009-10-10
> **fedeavila said:**
> Pero contá algo más... A mi por ejemplo me dio mucha impresión que no haya encontrado drivers para mi Epson TX115 con tan sólo 1 día de vida jaja

Por una parte no creo que sea
una [falencia]("http://buscon.rae.es/draeI/SrvltConsulta?TIPO_BUS=3&LEMA=falencia") de Ubuntu Karmic,
sino que se trata de la desidia de
los fabricantes de impresoras
para desarrollar drivers de sus 
propios productos para GNU/Linux.
Parece el cuento del huevo y la
gallina. En el año 2009 y con un
aproximado de 8 millones de 
usuarios de Ubuntu Linux, es 
tiempo que los señores fabricantes 
tomen decisiones estrategicas.

---

### Post by aledruetta on 2009-10-10
Hasta ahora, estéticamente hablando, fue Xubuntu el que más me gustó en su evolución de Jaunty a Karmic. Ubuntu Gnome en ese sentido no cambia demasiado, creo; y Kubuntu, sigue lindo como siempre, pero no lo conozco tanto como para saber si hubo un gran cambio.

---

### Post by andy_91 on 2009-10-10
si xubuntu cambio mucho en su apariencia por lo que vi en las capturas de santiago (yo actualize pero desde el apt, por eso mi xubuntu quedo con el tema que tenia en intrepid)
de  todas maneras le falta corregir unos problemillas con el bluetooth applet y con el sonido(cada vez que la apago se me pone en mute el mezclador).
Fuera de eso karamic esta mucho mejor que intrepid

---

### Post by aledruetta on 2009-10-10
Incluso me gustó más la splash de xubuntu que la de ubuntu -que es mucho más linda que la anterior-. Es una especie de big bang en miniatura.

---

### Post by fedeavila on 2009-10-10
[FONT="Monospace"]Quiero hacer otra impresión personal:
1) Ubuntu Software Center
2) Añadir y quitar aplicaciones
3) [s]Gestor de paquetes Synaptic[/s]
Lo veo como repetitivo. Lo raro es que en Ubuntu Software Center, de 100 aplicaciones sólo 1 tengo disponible xa instalar (estadística exagerada). Sólo las "Canonical-Maintained Applications" Evidentemente hay algo que no estoy comprendiendo; o estoy haciendo mal.

PD: En ningún momento dije o hice ver que, el hecho de que no existieran drivers para mi impresora, fuera una falencia de Ubuntu, creo que el tema de los drivers ya quedó bastante claro. El CD viene con los drivers para Windows 2000, XP, XP x64, Vista, OS X (10.3.9, 10.4.x, & 10.5.x) ¿Qué te cuesta hacer uno xa GNU/Linux? xD

Saludos[/FONT]

---

### Post by pablo.s on 2009-10-10
> **fedeavila said:**
> [FONT=Monospace]Quiero hacer otra impresión personal:
1) Ubuntu Software Center
2) Añadir y quitar aplicaciones
3) [s]Gestor de paquetes Synaptic[/s]
Lo veo como repetitivo. [/FONT]
[FONT=Monospace]
[/FONT]Añadir y quitar aplicaciones no 
existe más. Fué reemplazado desde
la Alpha 5 por Ubuntu Software Store,
ahora renombrado a Ubuntu Software 
Center. Por lo tanto quedan dos
front-end de apt-get que son el antes
mencionado y Synaptic, para la gente
que quiera una interfaz mas compleja.[FONT=Monospace]


[/FONT]> **fedeavila said:**
> [FONT=Monospace]Lo raro es que en Ubuntu Software Center, de 100 aplicaciones sólo 1 tengo disponible xa instalar (estadística exagerada). Sólo las "Canonical-Maintained Applications" Evidentemente hay algo que no estoy comprendiendo; o estoy haciendo mal.[/FONT]

Fijate si tenés chequeado esto:
[IMG]http://i.imagehost.org/0348/1_19.png[/IMG]
[FONT=Monospace] 
[/FONT]
> **fedeavila said:**
> [FONT=Monospace]PD: En ningún momento dije o hice ver que, el hecho de que no existieran drivers para mi impresora, fuera una falencia de Ubuntu, creo que el tema de los drivers ya quedó bastante claro. El CD viene con los drivers para Windows 2000, XP, XP x64, Vista, OS X (10.3.9, 10.4.x, & 10.5.x) ¿Qué te cuesta hacer uno xa GNU/Linux? xD

Saludos[/FONT]

OK. A veces escribo respuestas para
clarificar conceptos que pueden ser
motivo de comentarios malintencionados
por parte de terceros (o sea ni vos ni yo)
sobre las falencias de Ubuntu.
Todo bien, no lo tomes como ofensa.

---

### Post by santiagoward2000 on 2009-10-10
> **pablo.s said:**
> Añadir y quitar aplicaciones no 
existe más. Fué reemplazado desde
la Alpha 5 por Ubuntu Software Store,
ahora renombrado a Ubuntu Software 
Center. Por lo tanto quedan dos
front-end de apt-get que son el antes
mencionado y Synaptic, para la gente
que quiera una interfaz mas compleja.

Me parece que **Añadir y quitar aplicaciones** (gnome-app-install) sí sigue existiendo. En la Beta, está instalado (por lo menos está en mi LiveCD).
Y supongo que va a seguir siendo mantenido por un tiempo (sino en Ubuntu, por lo menos por Xubuntu, que no parece que vaya a traer el **Software Store** por ahora).
Como nota de color, le agregaron al **Añadir y quitar** la opción para ver screens de los programas.
Saludos!

---

### Post by pablo.s on 2009-10-10
> **santiagoward2000 said:**
> Me parece que **Añadir y quitar aplicaciones** (gnome-app-install) sí sigue existiendo. En la Beta, está instalado 

Tenés razón.
Me llamo a silencio por unos
treinta minutos como penitencia
y vuelvo.

---

### Post by mama21mama on 2009-10-10
Los de la encriptacion que es lo nuevo e interesante; los de peritos informáticos, podran descriptar la home?

---

### Post by pablo.s on 2009-10-10
> **mama21mama said:**
> Los de la encriptacion que es lo nuevo e interesante; los de peritos informáticos, podran descriptar la home?

No. Y si te olvidás la contraseña,
vos tampoco.
Lo del cifrado ya estaba desde
Jaunty, si mal no recuerdo.

---

### Post by fedeavila on 2009-10-10
> **pablo.s said:**
> Fijate si tenés chequeado esto:
[IMG]http://i.imagehost.org/0348/1_19.png[/IMG]

[FONT="Fixedsys"]NOO!! Justamente.. No entiendo el significado de ese "menú" Si no me va a permitir instalar algunas aplicaciones (la muy gran mayoría) directamente que no me las muestre.. O me estoy equivocando y sí me tendría que permitir instalarlas? Capaz que una vez, después de añadir los repositorios de "X" aplicación, sí me va a permitir instalarlo, verdad?[/FONT]

---

### Post by pablo.s on 2009-10-10
> **fedeavila said:**
> NOO!! Justamente.. No entiendo el significado de ese "menú" Si no me va a permitir instalar algunas aplicaciones (la muy gran mayoría) directamente que no me las muestre.. 

Creo que separa entre las aplicaciones
que mantiene Canonical del resto por
un tema de soporte. Canonical ofrece
un servicio de soporte y asistencia técnica
paga. Los clientes de este servicio deben
saber cuales aplicaciones son las que
entran dentro del tema. Por otra parte,
los paquetes de Universe y Multiverse
no entran entre los que Canonical soporta.
Pero no significa que no te deja instalar
los programas.

> **fedeavila said:**
> O me estoy equivocando y sí me tendría que permitir instalarlas? Capaz que una vez, después de añadir los repositorios de "X" aplicación, sí me va a permitir instalarlo, verdad?[/FONT]

Eso es otra cosa. Si la aplicación depende
de añadir un PPA, entonces no va a estar
en la lista magicamente. Una vez que hayas
agregado la fuente de software, te lo muestra
e incluso lo podés instalar.

---

### Post by fedeavila on 2009-10-10
> **pablo.s said:**
> Por otra parte,
los paquetes de Universe y Multiverse
no entran entre los que Canonical soporta.

[FONT="Fixedsys"]Listooo! Estaba destildado y por eso no me aparecía el botoncito de Install en "USC"
](*,)[/FONT]

---

### Post by aledruetta on 2009-10-11
En los repositorios de karmic figura el paquete "lubuntu-desktop".
No sé si en Jaunty estaba, pero es una buena opción para probar ese nuevo sabor.

...

Y, cosa extraña. Las dos últimas veces que actualicé, el gestor actualizó el kernel de la versión 2.6.31-12 a la 2.6.31-13. Sin embargo, en el grub sigue apareciendo la versión 2.6.31-12.

...

---

### Post by pablo.s on 2009-10-12
> **aledruetta said:**
> Y, cosa extraña. Las dos últimas veces que actualicé, el gestor actualizó el kernel de la versión 2.6.31-12 a la 2.6.31-13. Sin embargo, en el grub sigue apareciendo la versión 2.6.31-12.

Es muy probable que el lanzamiento
final lleve el núcleo 2.6.31-13. Veo
en Synaptic que se están preparando
las variantes del núcleo con esa versión.
Entre otras novedades hubo una versión
de grub2 para amd64 que estaba haciendo
estragos en el arranque... [COLOR=Red]Por las dudas
los que tengan 64bits no actualicen grub
por ahora (o bloqueen el paquete en Synaptic)[SIZE=4]&#9888;[/SIZE][/COLOR]

---

### Post by santiagoward2000 on 2009-10-13
Hola!
Ahora que instalé Karmic me encontré con un bug medio molesto, y les aviso por las dudas a los que quieran probar Xubuntu. Cuando lo instalan, si dejan que se instalen los paquetes de idioma, terminan instalando todo el OpenOffice. Es un bug ya reportado, así que por ahora hay que esperar.
Saludos!

---

### Post by gmunioz on 2009-10-14
Hola ale....:

Inicia synaptic

Controla que no este instalado el Grub

Si lo esta, instala el Grub2, me ocurrió

no se porque, bueno en realidad porque es

beta, que no se actualizaba el Grub2 que

era el que iniciaba el sistema, y resultó ser

que se habia desinstalado el paquete del sistema

no del mbr y se habia instalado el Grub.

Reinstalado el Grub2, se desinstaló el Grub, y se

actualizó al nuevo kernel.

---

### Post by gmunioz on 2009-10-14
**Atención Atención usuarios karmic**

El kernel 2.6.31-14 en modo gráfico no funciona.

Iniciar con el kernel anterior y esperar su actualización

para usarlo.

Edito---------------

Solucionado con la instalacion de los linux -headers

---

### Post by oktubrer on 2009-10-14
> **gmunioz said:**
> **Atención Atención usuarios karmic**

El kernel 2.6.31-14 en modo gráfico no funciona.

Iniciar con el kernel anterior y esperar su actualización

para usarlo.

Lamento disentir, pero acabo de actualizar y reiniciar e ingresé en modo gráfico sin inconvenientes.  ¿Será un tema puntual con ciertas tarjetas gráficas? Yo tengo una ATI HD3200 y con todos los problemas de ATI inicio sin problemas y con efectos 3D ok.

---

### Post by gmunioz on 2009-10-14
Solucionado.

Ya estan disponibles los linux-headers

que instale posteriormente y permitieron

que las gráficas funcionaran

---

### Post by juancarlospaco on 2009-10-15
Yo estoy sincronizando en todas mis PC sin problema:
-Las Post It virtuales
-Los contactos de Evolution
-Los Archivos
-Los compartidos



:)

---

### Post by aledruetta on 2009-10-15
> **juancarlospaco said:**
> Yo estoy sincronizando en todas mis PC sin problema:
-Las Post It virtuales
-Los contactos de Evolution
-Los Archivos
-Los compartidos



:)

¿Eso lo hacés todo con Ubuntu One?

Yo quise activar el servicio, pero cuando hago login con mi cuenta de launchpad no pasa nada...

---

### Post by aledruetta on 2009-10-15
Por fin!!!!!!!!!!!
Google Earth funcionando como la gente!!!!!!!
en Ubuntu Karmic y con Compiz activado, algo que hasta ahora nunca me había sucedido.


Instalé en Synaptic:
```
googleearth-package
```
Bajé el bin de la página oficial.
Le di permisos de ejecución.
Lo ejecuté.
Se instaló,
y funciona de maravillas!!!

---

### Post by fedeavila on 2009-10-15
> **aledruetta said:**
> Por fin!!!!!!!!!!!
Google Earth funcionando como la gente!!!!!!!
en Ubuntu Karmic y con Compiz activado, algo que hasta ahora nunca me había sucedido

¿Y cuál era el problema que tenías?
El mío era que cuando consultaba alguna calle, altura o dirección en el buscador, me posicionaba en Brasil o Uruguay; no recuerdo bien... Pero re-loco...

---

### Post by aledruetta on 2009-10-15
> **fedeavila said:**
> ¿Y cuál era el problema que tenías?
El mío era que cuando consultaba alguna calle, altura o dirección en el buscador, me posicionaba en Brasil o Uruguay; no recuerdo bien... Pero re-loco...

Mi problema era que con Compiz, directamente se tildaba el escritorio. Y sin compiz parecía una película cuadro a cuadro, no tenía fluidez y demoraba una eternidad en cargar la imagen. No valía la pena abrirlo.

Ahora está perfecto.

---

### Post by juancarlospaco on 2009-10-15
> **aledruetta said:**
> ¿Eso lo hacés todo con Ubuntu One?


Si, lo hace el Ubuntu One,
es muy integrado, a tal punto que casi ni lo notas, 
es una sincronizacion simple y funcional,
tambien se puede *(o se podra)* sincronizar los marcadores del firefox,
cosa que en cualquier PC que te logueas 
tenes tus marcadores, notas, contactos y archivos.

---

### Post by guisheca on 2009-10-15
> **juancarlospaco said:**
> Si, lo hace el Ubuntu One,
es muy integrado, a tal punto que casi ni lo notas, 
es una sincronizacion simple y funcional,
tambien se puede *(o se podra)* sincronizar los marcadores del firefox,
cosa que en cualquier PC que te logueas 
tenes tus marcadores, notas, contactos y archivos.

Perdón por el off, pero me da un poco de miedito eso

---

### Post by juancarlospaco on 2009-10-15
> **guisheca said:**
> Perdón por el off, pero me da un poco de miedito eso

Por que miedito?,
me parece genial, es mas seguro que DropBox*(es un agujero de seguridad)*,
y unifica muchas otras aplicaciones independientes, 
pero ya integradas en el sistema y bien soportadas.
Todo sobre SSL, que junto con SSH han probado ser seguras.

Es algo medio como el MobileMe de Apple :)

---

### Post by santiagoward2000 on 2009-10-16
> **aledruetta said:**
> Hasta ahora, estéticamente hablando, fue Xubuntu el que más me gustó en su evolución de Jaunty a Karmic. Ubuntu Gnome en ese sentido no cambia demasiado, creo; y Kubuntu, sigue lindo como siempre, pero no lo conozco tanto como para saber si hubo un gran cambio.

Hoy me di cuenta de un detalle sobre el tema Albatross (el nuevo default de Xubuntu) que no había visto antes y me llamó la atención. Está hecho con el motor Murrine que soporta transparencias! :P Cuando activamos un compositor, algunos programas muestran las ventanas con transparencias en algunas partes, mientras otras siguen completamente opacas.
Miren que lindo queda el System Monitor, con bordes, barra de menú y pestañas transparentes, pero con la lista de programas opaca y perfectamente visible!
Ahora tengo que ver qué otros programas pueden hacerlo (en algún momento creo que leí que el Exaile 0.3 trae esa opción).
Saludos!

---

### Post by staar on 2009-10-16
> **santiagoward2000 said:**
> Hoy me di cuenta de un detalle sobre el tema Albatross (el nuevo default de Xubuntu) que no había visto antes y me llamó la atención. Está hecho con el motor Murrine que soporta transparencias! :P Cuando activamos un compositor, algunos programas muestran las ventanas con transparencias en algunas partes, mientras otras siguen completamente opacas.
Miren que lindo queda el System Monitor, con bordes, barra de menú y pestañas transparentes, pero con la lista de programas opaca y perfectamente visible!
Ahora tengo que ver qué otros programas pueden hacerlo (en algún momento creo que leí que el Exaile 0.3 trae esa opción).
Saludos!

ARGB FTW! en ubuntu el tema DarkRoom que viene por defecto también esta hecho con soporte de ARGB, [acá]("http://www.cimitan.com/murrine/rgba-support/list") hay una lista de las aplicaciones en las que se puede hacer andar el chiche...

saludos

---

### Post by harryscode on 2009-10-16
Hace unos dias actualicé a 9.10 con el upgrade-manager -d... muy estable.. el xubuntu corre sin problemas.. el único detalle que encontré que no se si será por ser beta, es que no funca el salvapantallas, no se pone en negro ni agarra ninguna configuración. Fuera de eso.. un lux

---

### Post by jpmorelli on 2009-10-16
La pregunta del millón es:

Si actualizo desde 9.04 a 9.10 con dist-upgrade ( en el momento en que salga la versión final ) el GRUB se actualizará solo a GRUB2 ? el sistema de archivos me permitirá ser cambiado a ext4 ?

Salute !

---

### Post by pablo.s on 2009-10-16
> **jmorelli said:**
> Si actualizo desde 9.04 a 9.10 con dist-upgrade ( en el momento en que salga la versión final ) el GRUB se actualizará solo a GRUB2 ? 

Si.

> **jmorelli said:**
> el sistema de archivos me permitirá ser cambiado a ext4 ?

Automaticamente no.

---

### Post by jpmorelli on 2009-10-16
Muchas gracias por las aclaraciones :)

---

### Post by SLA_leandrin on 2009-10-17
Hola muchachos.

Voy a contar mis experiencias con Karmic.
Intenté actualizar mi Kubuntu Jaunty con un estrepitoso fracaso utilizando los procedimientos sugeridos en el sitio oficial de kubuntu. Resulta que me largó un error (que no recuerdo ni anoté, pero algo relacionado a phyton). Me pedía reinciar y eso hice, sin antes googlear (error mío, asumido). Por supuesto no arrancó mas no hubo caso, ni por consola ni nada. Esa noche tenía una rabia que me desperté al baño como a las 5 de la mañana y medio en sueños bajé el ubuntu karmic beta.
Al día siguiente lo instalé en un pendrive usb con un programa realmente muy muy bueno, [http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/") lo recomiendo 100%, espléndido.

Instalé sin problemas, booteando desde el pendrive en modo live me detectó que me faltaban los drivers privativos del wifi (placa broadcomm). Ál reiniciar la máuqina no me pidió mas los drivers automáticamente, así que tuve que instalarlos vía apt-get, costó un poco pero funcionó.

Algunos problemas menores con la placa de video Intel. A veces segun como arranque, tiene o no aceleración 3D, no logro detectar aún la causa.

Al margen de que todo lo demás anda bien (menos las teclas para el brillo del monitor, need help!), al intentar hacer andar el modem 3g de claro costó un poco. Resulta que en los proveedores preseteados figura Claro pero está mal la info. Manualmente en el nm-connection-editor no me toma NINGÚN cambio, ni siquiera si corro como root, incluso modifiqué los archivos de texto que genera con la configuración, pero no hay modo. Lo único que me quedó para solucionar es buscar, encontrar y editar el archivo de los proveedores, agregándole la info correcta.
El archivo que hay que editar está en:

```
/usr/share/mobile-broadband-provider-info
```

y es el:

```
serviceproviders.xml
```

en donde hay que buscar claro y poner como usuario ```
ctigprs
```, en contraseña ```
ctigprs999
``` y en APN ```
gprs.claro.com.ar
```

Luego de esto, configuré nuevamente la conexión y listo.

Sin bien no me ha resultado complicado, creo que a un novato si... espero que esto pueda ayudar a alguien con el mismo problema.

Saludos!

---

### Post by aledruetta on 2009-10-17
> **SLA_leandrin said:**
> ...bajé el ubuntu karmic beta.
Al día siguiente lo instalé en un pendrive usb con un programa realmente muy muy bueno, [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) lo recomiendo 100%, espléndido.

Sólo comentar que el creador de discos de inicio USB que traen tanto Jaunty como Karmic también funcionan muy bien. Yo instalé Lubuntu, Xubuntu, Kubuntu y Ubuntu (distintas alphas y betas) con esa herramienta y no tuve ningún problema.

Digo, para no andar instalando más cosas si las que están andan bien...

---

### Post by SLA_leandrin on 2009-10-18
> **aledruetta said:**
> Sólo comentar que el creador de discos de inicio USB que traen tanto Jaunty como Karmic también funcionan muy bien. Yo instalé Lubuntu, Xubuntu, Kubuntu y Ubuntu (distintas alphas y betas) con esa herramienta y no tuve ningún problema.

Digo, para no andar instalando más cosas si las que están andan bien...

Ah, lo que pasa es que me faltó mencionar el detalle que tuve que hacerlo al pendrive live desde la notebook de mi novia, que tiene XP...

---

### Post by aledruetta on 2009-10-20
Ahora, con Karmic, es más fácil agregar repositorios:
```
sudo add-apt-repository ppa:nombre_del_repositorio
```
Automáticamente carga la clave.

---

### Post by pablo.s on 2009-10-26
[B]Damas y Caballeros de la
Comunidad Ubuntu:[/B]
Me complace en dar por
[SOLUCIONADO] a este hilo.
A todos los que de una manera
u otra han participado, les 
agradezco mucho, y los comprometo
a participar en la Alpha de Lucid Lynx
a partir del mes de Enero.
Sin más que desearles un gran disfrute
de Ubuntu 9.10, a ser lanzado este
próximo Jueves 29, los saludo desde
aquí, su amigo Pablo.

GRACIAS POR TODO!

---

