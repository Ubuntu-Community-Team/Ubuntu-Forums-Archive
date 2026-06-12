---
title: "problemas con KDE kubuntu y Urban terror"
date: 2009-07-01
forum: Software
---

### Post by r@fitiiixxx on 2009-07-01
Hola a todos!,

recientemente me pasé de GNOME a KDE para probar que tal estaba, la verdad me llevé una gran desilución al ver que no entendía nada y nada de lo que puedo acceder fasilmente es de mi interes,
muchas son mis dudas y no puedo postearlas todas en un thread, solamente voy a preguntar las mas preocupantes por ahora;

Donde esta mi "Añadir y/o Quitar Progrmas"?

tengo otro problema, quiero crear un lanzador personalizado de Urban Terror 4.1 pero no puedo porque no se como hacerlo, tube que ejecutarlo desde consola para poder jugar,

yo lo instalé siguiendo estas instrucciones
[http://www.lisfera.es/2008/06/14/instalar-urban-terror-41-en-gnulinux/]("http://www.lisfera.es/2008/06/14/instalar-urban-terror-41-en-gnulinux/")

no existe el gksu ni el gedit en KDE, o por lo menos no por defecto

me dicen como crear el lanzador en el menú favoritos con su icono respectivo?

otra cosa, como cambio mi imagen para mostrar en Kopete?

salu2, ):P

r@fitiiixxx

---

### Post by Barasuishou on 2009-07-01
bien mirá te diría que tranqui, no es tampoco tanto, lo que tiene kde es que casi todas sus aplicaciónes si vas a herramientas tiene para configurar accesos directos y el programa en si, yo generalmente lo hacía especialmente el konqueror y el amarok, para que me queden los controles tipo firefox y tipo winamp, pero eso es cuestión de gustos.

ahí, en kde (por lo que tengo entendido debido a lectura y vivencia) todo está formado por algo llamado plasma, desde los widgets, osea todas las cosas que ves tiradas en el escritorio, incluido el panel, si querés podes poner 2 paneles tipo gnome, y el menu podés ponerlo tipo tradicional

el añadir o quitar programas, se llama kpackage, es como el añadir y quitar programas junto con el synaptic, será un poco raro o incomodo al principio pero te acostumbras fácil y está en applicaciones->systema, si no me equivoco, de última usa el buscador en al boton "inicio"

para crear un lanzador a mi por lo menos no se me hizo muuuy jodido aunque no lo hize de 0, pero depende donde lo querés crear, aunque supongo será lo mismo,

el gksu(no recuerdo que es), el gedit si no existe, pero en cambio tenés el kate, que es un editor de texto que también puede usarse para programar, así que si querés abrir .txt o lo que abrías con gedit, ahora hacelo con kate

para crear en el menú favoritos el lanzador, dale click derecho sobre el lanzador, y no se si era configurar lanzador o editar, una de esas dos, ahí te va a mostrar como en el editor de menús de gnome el "árbolito", y ahí era básicamente igual si mal no recuerdo, 

yo adoro y quiero usar kde, pero con ubuntu A MI, por lo menos me vive crasheando, probé en opensuse y es un lujo pero es algo diferente a ubuntu esa distro, mientras te ande bien, te guste y estés comodo quedate con kde que está re bueno, yo espero salga la 4.3 para volver a probar a ver si es más estable

espero te sirva la ayuda, cualquier otra consulta avisa, si son muchas tus dudas de última te paso mi mail si querés y veo si te puedo ayudar

suerte, aguante kde!!!, chauu

---

### Post by Hei Ku on 2009-07-01
Como todo lo nuevo, cuesta acostumbrarse. Tranquilo :lolflag:

Creo que no esta, pero el equivalente a Synaptics es KPackageKit. No es tan poderoso, pero es simple de usar.

Si el Urban Terror lo instalaste desde un .deb, deberia haberte instalado el lanzador. Proba buscandolo en el menu. Si no, le das click derecho sobre el icono del Menu en el panel, y apreta Editor de Menu. Ahi podes crear un lanzador.

gksu -> kdesudo; gedit -> kate

En Kopete la cambias en Identidades. Configurar... Cuentas -> Modificar identidad.

---

### Post by r@fitiiixxx on 2009-07-01
> **Barasuishou said:**
> bien mirá te diría que tranqui, no es tampoco tanto, lo que tiene kde es que casi todas sus aplicaciónes si vas a herramientas tiene para configurar accesos directos y el programa en si, yo generalmente lo hacía especialmente el konqueror y el amarok, para que me queden los controles tipo firefox y tipo winamp, pero eso es cuestión de gustos.

ahí, en kde (por lo que tengo entendido debido a lectura y vivencia) todo está formado por algo llamado plasma, desde los widgets, osea todas las cosas que ves tiradas en el escritorio, incluido el panel, si querés podes poner 2 paneles tipo gnome, y el menu podés ponerlo tipo tradicional

el añadir o quitar programas, se llama kpackage, es como el añadir y quitar programas junto con el synaptic, será un poco raro o incomodo al principio pero te acostumbras fácil y está en applicaciones->systema, si no me equivoco, de última usa el buscador en al boton "inicio"

para crear un lanzador a mi por lo menos no se me hizo muuuy jodido aunque no lo hize de 0, pero depende donde lo querés crear, aunque supongo será lo mismo,

el gksu(no recuerdo que es), el gedit si no existe, pero en cambio tenés el kate, que es un editor de texto que también puede usarse para programar, así que si querés abrir .txt o lo que abrías con gedit, ahora hacelo con kate

para crear en el menú favoritos el lanzador, dale click derecho sobre el lanzador, y no se si era configurar lanzador o editar, una de esas dos, ahí te va a mostrar como en el editor de menús de gnome el "árbolito", y ahí era básicamente igual si mal no recuerdo, 

yo adoro y quiero usar kde, pero con ubuntu A MI, por lo menos me vive crasheando, probé en opensuse y es un lujo pero es algo diferente a ubuntu esa distro, mientras te ande bien, te guste y estés comodo quedate con kde que está re bueno, yo espero salga la 4.3 para volver a probar a ver si es más estable

espero te sirva la ayuda, cualquier otra consulta avisa, si son muchas tus dudas de última te paso mi mail si querés y veo si te puedo ayudar

suerte, aguante kde!!!, chauu

Muchas gracias che! me a servido bastante tu post, pero sigo sin poder hacer el lanzador, ya que yo tengo el panel como venía de stock, con el boton de "Inicio" con logo de KDE, y al hacer click me habre un menú que dice favoritos, pero ahí no puedo poner click derecho y que me diga "crear lanzador" no tengo opciones para poner directamente :S

igual he solucionado un par de cosas, pasa que de movida el echo de no entender a uno lo desespera, pero me está empezando a gustar mas :D

el echo es que para poder poner un lanzador, e arrastrado una aplicación cualquiera y click derecho > cambiar ruta y objetivo y así me a quedado, pero ese lanzador no tiene el icono del urban terror y está en el escritorio, me gustaría el icono del UT pero no se como se lo puedo poner, ademas depender de arrastrar una aplicación y modificarla no es lo mejor,

es una atadura de alambre xD, por eso nesesito saber bien como  va todo esto, che ya que sabes bastante, vos sabras como va todo esto de los efectos de escritorio? porque no he podido sacarlos, 

ahora mismo me pongo a descargar los complementos de codec de video y audio q tanto nesesito jeje

y bueno si querés pasarme tu mail ningun problema, mucho mejor ^^ avisame si querés te paso el mio por PM y arreglamos :)

que todavía tengo que saber como cambiar la fotito del Kopete para poner una personalizada y ensima no se que le pasa que se crashea cada 2 x 3 el kopete este :P

Salu2 ):P

r@fitiiixxx

---

### Post by r@fitiiixxx on 2009-07-01
> **Hei Ku said:**
> Como todo lo nuevo, cuesta acostumbrarse. Tranquilo :lolflag:

Creo que no esta, pero el equivalente a Synaptics es KPackageKit. No es tan poderoso, pero es simple de usar.

Si el Urban Terror lo instalaste desde un .deb, deberia haberte instalado el lanzador. Proba buscandolo en el menu. Si no, le das click derecho sobre el icono del Menu en el panel, y apreta Editor de Menu. Ahi podes crear un lanzador.

gksu -> kdesudo; gedit -> kate

En Kopete la cambias en Identidades. Configurar... Cuentas -> Modificar identidad.

jeje Tenés mucha razon! al principio me desesperé! que no podía hacer nada XD pero ahora entiendo un poco mas, aun así te cuento;
el UT4.1 lo instalé desde el link ese que puse en el primer post, y no es un .deb porque creo que no hay .deb's de eso, al menos yo no encontré...

ahora con el editor de menus voy a probar, jeje pasa que justo postie yo y posteaste vos un minuto antes jeje,

ahora me fijo eso, con el menu

y gracias por lo de la foto en el Kopete :)

--------------------------------------
EDIT: me fijé pero no pude, no se que pasa con el creador de submenus, solo puedo visualizar el acceso directo con el menu "al estilo clasico", no si es al estilo default que está mucho mas groso, ojalá pudiera saber donde está el icono del UT para poder ponerlo en algun lanzador tmb, ya que no se donde está!

---

### Post by staar on 2009-07-01
para crear un lanzador en el menu, es igual que en gnome, click derecho sobre el botón del kickoff (el botón de 'inicio') > Editor de menús, te vas a Juegos y agregas un nuevo elemento con los datos necesarios (le podés cambiar el ícono también), después en Aplicaciones > Juegos lo encontrás, le haces click derecho > Agregar a favoritos y listo..

si vas a usar MSN, podés probar Kmess 2, que es bastante más usable que kopete...

los efectos de escritorio podés desactivarlos con Alt + Shift + F12 (en realidad, lo que se desactiva es el compositing)

saludos

---

### Post by Hei Ku on 2009-07-01
Para modificar los efectos, anda a systemsettings, escritorio, efectos de escritorio. Son bastante similares a los de Compiz, pero con sus particularidades

---

### Post by NickCis on 2009-07-01
Si, definitivamente es mas usable el kmess 2 qe el kopete, aca hay una guia de como instalarlo ( [http://losojosdetux.com.ar/2009/04/kmess-2-un-mensajero-msn-simple-y-completo/](http://losojosdetux.com.ar/2009/04/kmess-2-un-mensajero-msn-simple-y-completo/) ). Los repositorios de jaunty oficiales solo tienen el kmess 1, qe es muy incompleto.

Como navegador qt te recomiendo que uses el opera 10 beta (bajate el que usa qt4) de ak te lo podes bajar [ftp://ftp.rediris.es/mirror/opera/linux/1000b1/beta1/en/](ftp://ftp.rediris.es/mirror/opera/linux/1000b1/beta1/en/)

Saludos.

---

### Post by r@fitiiixxx on 2009-07-02
> **staar said:**
> para crear un lanzador en el menu, es igual que en gnome, click derecho sobre el botón del kickoff (el botón de 'inicio') > Editor de menús, te vas a Juegos y agregas un nuevo elemento con los datos necesarios (le podés cambiar el ícono también), después en Aplicaciones > Juegos lo encontrás, le haces click derecho > Agregar a favoritos y listo..

si vas a usar MSN, podés probar Kmess 2, que es bastante más usable que kopete...

los efectos de escritorio podés desactivarlos con Alt + Shift + F12 (en realidad, lo que se desactiva es el compositing)

saludos

Gracias staar! supongo que los efectos al apretar Alt + Shift + F12 devuelta vuelven a su estado original, no?

el tema con el icono es que ni idea donde esta, lo busqué en la carpeta que bajé pero no estaba ahí, ni idea, voy a seguir buscandolo...

> **Hei Ku said:**
> Para modificar los efectos, anda a systemsettings, escritorio, efectos de escritorio. Son bastante similares a los de Compiz, pero con sus particularidades

gracias Hei Ku!, jee que no lo encontraba, ahora puedo deshabilitar los efectos, ahora como es eso de que no hay compiz? si yo e visto escritorios KDE con efectos como el Aero de W2 y el cubo 3D?, hay otro gestor de ventanas parecido?

> **NickCis said:**
> Si, definitivamente es mas usable el kmess 2 qe el kopete, aca hay una guia de como instalarlo ( [http://losojosdetux.com.ar/2009/04/kmess-2-un-mensajero-msn-simple-y-completo/](http://losojosdetux.com.ar/2009/04/kmess-2-un-mensajero-msn-simple-y-completo/) ). Los repositorios de jaunty oficiales solo tienen el kmess 1, qe es muy incompleto.

Como navegador qt te recomiendo que uses el opera 10 beta (bajate el que usa qt4) de ak te lo podes bajar [ftp://ftp.rediris.es/mirror/opera/linux/1000b1/beta1/en/](ftp://ftp.rediris.es/mirror/opera/linux/1000b1/beta1/en/)

Saludos.

jee gracias :D, que raro que los repos solo tengan el kmess 1, lo voy a instalar al 2, igual tener el Kopete bien configurado y saber usarlo siempre es importante ya que uno nunca sabe que puede fallar, 
pero e visto que no se pueden ver los mensajes personales del MSN en Kopete, que desilución.

Y con respecto al Opera lo he usado en Ubuntu y es una maravilla, ahora como es el tema del qt4? donde me mandaste vos el link hay varias carpetas y varios .deb's
yo me fije en i386 pero hay varios ,deb con el opera 10 con qt dice,
me los bajo todos?

igual el Konqueror va rapido, yo que soy fana de los Navegadores y me gusta probarlos todos, el Konqueror fue una de las razones por las cuales cambié a KDE, quería probarlo, el tema es que no podes acomodar las pestañas y el MOUSE 3 no funciona para subir y bajar, para mi que rompí la ruedita del maus se me complica, pero voy a buscarle Add-ons para mejorarlo, me gustaria saber si tiene soporte para HTML 5.0

 obio que el opera lo quiero bajar tmb

mil gracias a todos! ya estoy empesando a agarrarle el gustito al KDE, tiene mucha mas elegancia que Gnome, aunque mas complejo

pd: que paso que antes en KDE venía el Seamonkey y ahora cambiaron por Konqueror? cual va mejor de esos dos?

un Salu2, ):P

r@fitiiixxx

---

### Post by Hei Ku on 2009-07-02
KWin, el gestor de ventanas de KDE, tiene sus propios efectos.

A que te referis con los mensajes personales? El subtexto que podes agregar como mensajito? Si, se ve. Lo que no tiene son mensajes off-line, me parece.

Konqueror es y será el browser de KDE, no Seamonkey. Y en cuanto a las teclas y funciones del mouse, fijate que son configurables.

---

### Post by staar on 2009-07-02
el ícono lo podés [buscar con google]("http://images.google.com.ar/images?q=urbanterror+icon&btnG=Search+Images") y del opera bajate la versión gcc4, qt4, en deb...

saludos

---

### Post by NickCis on 2009-07-02
Si, el konqueror es el navegador de Kde, esta bueno y es rapido. El problema es que muchas paginas estan hechas para IE tonces no las podes usar con konqueror, el opera es mas tolerante respecto a eso. Y la otra es instalar el firefox, pero usas las librerias Gtk.

Que es eso del seamonkey?, no es como un firefox libre?, es gtk, no?.

Saludos.

---

### Post by r@fitiiixxx on 2009-07-02
> **Hei Ku said:**
> KWin, el gestor de ventanas de KDE, tiene sus propios efectos.

A que te referis con los mensajes personales? El subtexto que podes agregar como mensajito? Si, se ve. Lo que no tiene son mensajes off-line, me parece.

Konqueror es y será el browser de KDE, no Seamonkey. Y en cuanto a las teclas y funciones del mouse, fijate que son configurables.

Ah ,así que el gestor de ventanas por defecto ya viene con los efectos?, muy comodo, mejor!
con respecto al mensaje personal de kopete, si, no se ve, no aparece ni el mio ni el de nadie mas, sea en la conversación o sea en la lista de contactos como si se veía en el pidgin, capas hay que activar una opción, me he fijado por todos lados, el tema es que a veces esas opciones no estan muy a mano,
como ayer estube descargando muchas cosas no baje el Kmess pero ahora mismo lo estoy poniendo a bajar C:
el konqueror es y será, pero según escuché o escuché mal, antes en versiones previas del KDE el Konqueror era el manejador de archivos y no el Dolphin, y el Browser por defecto era Seamonkey, igual puede que alla entendido todo mal, si es así cuentenme ya que todo lo que tenga que ver con navegadores me gusta saber

> **staar said:**
> el ícono lo podés [buscar con google]("http://images.google.com.ar/images?q=urbanterror+icon&btnG=Search+Images") y del opera bajate la versión gcc4, qt4, en deb...

saludos

NO!! no puedo creer que me alla olvidado de eso, yo que siempre buscaba los iconos en ICONSPEDIA pero por google todavía mas facil, y eso que no se me había ocurrido, que falta de imaginación :P

gracias por apuntarme con el tema del opera, ya lo estoy bajando

> **NickCis said:**
> Si, el konqueror es el navegador de Kde, esta bueno y es rapido. El problema es que muchas paginas estan hechas para IE tonces no las podes usar con konqueror, el opera es mas tolerante respecto a eso. Y la otra es instalar el firefox, pero usas las librerias Gtk.

Que es eso del seamonkey?, no es como un firefox libre?, es gtk, no?.

Saludos.

Hasta ahora no me topé con ninguna pagina echa en especial para ningun navegador, quisiera ver una porque la verdad jamás me pasó sufrir por una pagina que no es para mi navegador, el opera igual va de 10 porque es opera 10 jajajaa
y porque supuestamente saca 100 pts en el test de ACID 3, ademas de que lo puedo Syncronizar con el Opera Mini de mi nokia 5200, así que no se discute que me lo baje o no jeje,
por otro lado el firefox nativo de linux incluso en GNOME me ha resultado una desepción tremenda de lo lento que es, carga que parece que tuviera un modem por telefono, me han comentado que la versión para window$ emulada en wine funciona mas rapido, loco no?

por ultimo el navegador SeaMonkey no es un "Fork" de firefox, parte del proyecto NetScape y es la "Suite de Mozilla" que está aparte del Firefox y el Thunderbird.

 Esta suite viene con navegador seamonkey, chat irc, navegador de archivos, etc, en la actualidad Seamonkey usa muchas cosas de firefox pero muchas también son de desarrollo propio.
 
Le copió el motor de Javascript TraceMonkey al firefox, y según e visto en la web saca 92 pts en el test ACID 3, así que es un buen navegador, lastima que para moverlo se requiere GTK 2.10 para GNU/Linux y UNIX.

 Ígual estoy muy contento con el Konqueror así que no espero que lo cambien o algo así, me gusta mucho, lastima que me he fijado que no tiene muchos Add-ons para completar. 

 Asi como poder mover pestañas por lo menos dentro de la misma ventana, mejor si se pudieran sacar algunos mas, pero solo eso y como dijo Hei Ku las teclas son personalizables así que cualquier tecla que no gusta se retoca y listo C:
---------------------------------------------------
Conclusión: ya encontré mi Ícono, primero creé un Subgrupo llamado Juegos y en juegos > arcade > urban terror 4.1 . pero no aparecía así que lo borré y puse el UT4.1 en Internet > urban terror 4.1 . Si, medio atado con alambre pero al menos pude hacer el lanzador, y el icono lo bajé desde el link que me pasó staar (no puedo creer que no se me alla ocurrido todavía).

casi todo está resuelto (exepto por unos problemas que se van muy fuera de foco en la conver, porque hablar de navegadores y cositas de kopete no afecta mucho, pero para problemas con las actualizaciones mejor habro otro thread)

nomás me gustaría saber, el reemplazo para esta acción:

_Ubuntu: "$ gksu gedit /usr/share/applications/q3ut4.desktop"
>....................|........|...............................|
>....................|........|...............................|
Kubuntu: "$ ....... **kate** /usr/share/applications/q3ut4.desktop"

no más eso, y si se acuerdan de alguna opción para activar los msjes personales o los "subnicks" en kopete como para tenerlo bien configurado como segunda opción sería genial.

Mil gracias a todos uds que me están bancando justo ahora que recién empieso y no tengo a quien acudir con el tema de KDE ya que las pocas personas que conosco así de la vida que usan linux, usan GNOME, otra ves gracias por sacarme todas las dudas 

un Saludo ):P

r@fitiiixxx

---

### Post by Hei Ku on 2009-07-02
Konqueror siempre fue la navaja suiza de KDE. File manager, browser, gestor de ftp, ssh, etc. Seamonkey es gtk. No es de KDE. Lo que puede haber pasado es que alguna distro lo puso por defecto en un release, pero no es KDE.

En Kopete, anda a Configurar, lista de contacto, layout. Ahi podes configurar que mostras en tu lista de contactos. Incluso le podes configurar que a los contactos te los muestre siempre con el mismo nick, aunque ellos se lo cambien. (algo extremadamente util con individuos entre 10 y 18 años que adoran cambiarse el nick a cada rato, en vez de usar mensajes de estado) ;)

El reemplazo a gksu es kdesudo.

---

### Post by pablo.s on 2009-07-02
> **NickCis said:**
> Que es eso del seamonkey?, no es como un firefox libre?, es gtk, no?.

Es el nombre en clave de Mozilla,
el abuelo de Firefox, el clasico de
los clasicos, la reencarnacion de
Netscape Navigator...

---

### Post by r@fitiiixxx on 2009-07-02
> **Hei Ku said:**
> Konqueror siempre fue la navaja suiza de KDE. File manager, browser, gestor de ftp, ssh, etc. Seamonkey es gtk. No es de KDE. Lo que puede haber pasado es que alguna distro lo puso por defecto en un release, pero no es KDE.

En Kopete, anda a Configurar, lista de contacto, layout. Ahi podes configurar que mostras en tu lista de contactos. Incluso le podes configurar que a los contactos te los muestre siempre con el mismo nick, aunque ellos se lo cambien. (algo extremadamente util con individuos entre 10 y 18 años que adoran cambiarse el nick a cada rato, en vez de usar mensajes de estado) ;)

El reemplazo a gksu es kdesudo.

Ah, me habré equivocado yo, habré leido mal, a mi ya me parecía raro lo del Seamonkey...

y gracias por el dato de como configurar el msje personal, pero yo lo tengo en castellano y la cosa fue ir a

Configurar > [Sección] Lista de contactos > [Pestaña] Lista de contactos > (la primer opción) Estilo de lista de contactos > [modificar a] Vista Detallada.

y gracias por el consejito, tengo pocos contactos que se cambien el nick cada dos por tres, así que veo como implementarlo solo para algunos, mientras tanto estoy configurando el Kmess 2 beta, está muy bueno!

> **pablo.s said:**
> Es el nombre en clave de Mozilla,
el abuelo de Firefox, el clasico de
los clasicos, la reencarnacion de
Netscape Navigator...

O.o como es eso del "nombre en clave de Mozilla"?
y si es el abuelo del firefox, quién es el padre?
-------------------------
Gracias y Salu2 ):P

r@fitiiixxx

---

### Post by Hei Ku on 2009-07-02
El padre es Phoenix, si no me equivoco, pero tuvieron que cambiar el nombre por un tema de marca. Y de ahí salió el nombre Firefox.

---

