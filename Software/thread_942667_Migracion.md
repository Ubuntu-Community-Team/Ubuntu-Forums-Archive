---
title: "Migracion"
date: 2008-10-09
forum: Software
---

### Post by fer493 on 2008-10-09
Buenas, soy nuevo por aca pero espero y agradeceria que puedan darme una mano.

Estoy ahora con Win XP pero la verdad es que se cuelga mucho y es muy inestable. Estaba pensando en pasarme a Ubuntu pero querria saber un par de cosas:

- Cual es la diferencia entre Ubuntu y Kubuntu?
- Seria compatible con mi modem Motorola SBG 900?
- Es compatibe con los formatos de Windows para fotos y video?
- Cuales son los requisitos minimos de hardware para correrlo?
- En el caso de ya instalado el SO (sea Ubuntu o Kubuntu), ya esta listo para usar o hay que configurar todo?

Muchas gracias de antemano!!

---

### Post by guisheca on 2008-10-09
Bienvenido al mundo linuxero!!!

> - Cual es la diferencia entre Ubuntu y Kubuntu?

La diferencia radica en el escritorio que utilizan, ubuntu viene con gnome y kubuntu con kde.

> - Seria compatible con mi modem Motorola SBG 900?

Por lo que vi así rapidito, es un modem wifi. Bueno no había problema de parte del modem, pero si de la pc que tengas con placa wifi, ya que ubuntu tiene algunos problemillas por ese lado. Lamentablemente en eso no te puedo ayudar porque nunca me tocó lidiar con ese tema, ya va a aparecer alguien por acá que te pueda ayudar con eso. De todas formas si aparte de wifi tiene conexión por puerto de red no habría ningún drama.

> - Es compatibe con los formatos de Windows para fotos y video?

Claro que si, por defecto van a haber algunos formatos que no vas a poder reproducir porque ubuntu no viene con los codecs de fábrica, pero se arregla poniendo esto en una consola: sudo aptitude install ubuntu-restricted-extras

> - Cuales son los requisitos mínimos de hardware para correrlo?

Con 512mb de ram ya podés correr ubuntu o kubuntu de manera fluida, lo del micro no tiene mucha importancia, con uno de 1ghz te sobra. Lo que podés hacer es bajarte los cds y correrlo en modo "live" si te funca de esa forma, instalado en el disco va a ir mucho mejor.

> - En el caso de ya instalado el SO (sea Ubuntu o Kubuntu), ya esta listo para usar o hay que configurar todo?

Hay que configurar alguna que otra cosilla, pero no te preocupes que te vamos a ayudar :)


Contestadas esas preguntas te comento que si querés usar ubuntu tu mejor amigo será google antes que nada. También podés ver este enlace: [http://guia-ubuntu.org/](http://guia-ubuntu.org/)

Y bueno, hay infinidad de info en la red, pero acá vamos a estar para orientarte.

Lo único que te digo es que va a ser un poco difícil en principio, pero no te desanimes que una ves que aprendas a usar este sistema no te vas a poder despegar.

Saludos y que el código te acompañe :)

---

### Post by fer493 on 2008-10-09
Ehh que velocidad de respuesta!!

Que buena onda che

Bueno, gracias por los tips y por el link, ya lo estoy investigando. Con lo del modem, te comento, tiene conexion por puerto de red (o sea mi computadora es a la que le llega el cable) pero hay otra pc que se conecta inalambrica a la mia. No se si sabras qué pasa con eso. 

Bueno, ya me estoy bajando el .iso para probarlo en modo live como dijiste.

Gracias!!

---

### Post by faktorqm on 2008-10-09
No pasa nada, la pones en ad-hoc, la del win tb y listo. Salu2!

---

### Post by WanderingKnight on 2008-10-09
> 
Hay que configurar alguna que otra cosilla, pero no te preocupes que te vamos a ayudar 

Y de hecho necesitás mucho menos trabajo de configuración que con XP, si alguna vez hiciste una instalación desde cero de ese sistema. Y luego las posibilidades de customización son tan amplias que verdaderamente carece de comparación. Ya de entrada tenés los dos escritorios más usados (GNOME y KDE), pero existen [muchísimos más](http://en.wikipedia.org/wiki/Desktop_environments#Examples_of_desktop_environments) ;)

Poco a poco te vas a ir dando cuenta que este sistema da para muchas cosas :D (tanto buenas como malas, no nos engañemos pensando que es perfecto...). Siempre que tengas ganas de aprender (fundamental! Acá no llegás a ningún lado si esperás que te sirvan las cosas en bandeja de plata) vas a llegar lejos :)

---

### Post by valucha on 2008-10-10
> **fer493 said:**
> Buenas, soy nuevo por aca pero espero y agradeceria que puedan darme una mano.

Estoy ahora con Win XP pero la verdad es que se cuelga mucho y es muy inestable. Estaba pensando en pasarme a Ubuntu pero querria saber un par de cosas:

- Cual es la diferencia entre Ubuntu y Kubuntu?
- Seria compatible con mi modem Motorola SBG 900?
- Es compatibe con los formatos de Windows para fotos y video?
- Cuales son los requisitos minimos de hardware para correrlo?
- En el caso de ya instalado el SO (sea Ubuntu o Kubuntu), ya esta listo para usar o hay que configurar todo?

Muchas gracias de antemano!![COLOR="DarkOrchid"]


Te amplio las respuestas aunque ya te lo hayan respondido:

1. Las diferencias sí radica en el escritorio pero esto trae aparejado varias cosas a saber:
a. distintos programas, en gnome se usa el evolution para el mail, en kde se usa kmail, y asi ha y miles de programas. Todos tiene las mismas funcionalidades y todos se pueden instalar en ambos escritorios. Pero es preferible que si te gustan los de gnome, uses gnome y si te gustan los de kde uses kde y no mezcles MUCHO, porque eso hace que tengas que isntalar muchas cosas e mas y el sistema te vaya un toquesin mas lento.

b. gráficamente son muy diferentes pero ambos son igual de customizables. Para ver captuiras de panalla de las posibilidades que te da cada tipo de escritorio entrá en [www.gnome-look.org](www.gnome-look.org) y [www.kde-look.org](www.kde-look.org).

c.también está Xubuntu, que tiene xfce, otro tipo de escritorio. Es muy parecido a gnome nada más que consume muchos menos recursos y para algunos es más lindo y simple. Si tu compu está al borde con los requerimientos del sistema (256 de ram compartida con la placa de video por ejemplo) podes probarlo y vas a notar una gran diferencia en la velocidad.

2.Ese modem es uno de los que te da FIbertel? yo tengo el Motorola sb1500 y anda perfecto, no tenes que configurar nada de nada. Lo que te recomiendo es que uses un LIVE CD y ahi pruebes si anda internet y si no chiflá que te ayudamos.

3.100% compatible, Es más  los reproductores de video y audio reproducen muchos más formatos que el windows media player. Al igual que en WIndows, tenés que instalar los codecs privativos, si sos de formatiar Windows sabés a qué me refiero, de modo contrario, es alguo que alguien insaló antes de que empezaras a usar la compu para que puedas reproducir .mp3, .avi etc. En Ubuntu es tan fácil como decir "acepto", cuando querés reproducir un archivo de audio por primera vez y no tenes el codec correspondiente te pregunta si deseás instalarlo y al darle "ok" te lo instala muy rápidamente.
El OpenOffice te lee formatos de Office, de MAC, y ademas formatos abiertos. ES MAS!, te lee el formato del nuevo office 2007 .docx .xlsx, etc, que el Office 2003 para abajo no te leen. Y podés crear archivos en cualquier tipo de formato también.


4.Los minimos son
700 MHz x86 procesador
384 MB RAM
8 GB de disk duro


5.El sistema esta re listo cuando lo terminás de instalar. Vos mismo te vas a dar cuenta, tenés muchisimas aplicaciones instaladas y podés usarlo tranquilamente. Pero claro, está muy standart, podés personalizarlo y ponerlo más "lindo", sacarle las cosas que no usás, como programas, procesos y cosas más avanzadas si te animás, ponerle cosas más útiles, etc. Es decir, podés usarlo tal cual está, nisiquiera drivers tenés que instalar (a menos que tengas una tarjeta de video nvidia o ati que te pregunta si querés instalarlo, le ponés ok y lo instalas, si no querés instalar los driver podés usar igual el sistema tal cual está).

Espero que te sirva, saludossssssssss.[/COLOR]

---

### Post by User21 on 2008-10-10
En cuanto a eso de que si está listo para usar, Ubuntu desde la instalación cuenta con:

[LIST]
[*]Si queres escuchar musica, podes usar [Rhythmbox]("http://www.gnome.org/projects/rhythmbox/"), y solito te va a pedir instalar los codecs necesarios para tus formatos propietarios.
[*]Si queres navegar, tenes [Firefox 3]("http://www.firefox.com"), listo y totalmente personalizable.
[*]Si necesitás crear documentos, planillas de calculo, presentaciones, [OpenOffice]("http://es.openoffice.org/") es la respuesta. Abré además los mas conocidos formatos propietarios de documentos.
[*]Necesitas descargar via torrent ? [Transmission]("http://www.transmissionbt.com/") es el cliente torrent predeterninado de Ubuntu.
[*]Algún archivo de video para pasar el rato? usás Totem y automáticamente obtienes los codecs necesarios.
[*]Los documentos PDF son facilmente accesibles via [eVince]("http://www.gnome.org/projects/evince/").
[*]Edición fotográfica para profesionales y entusiastas con [GIMP]("http://www.gimp.org/").
[*]Navega, recorre y administra colecciones de fotos con F-SPOT o el visualizador de fotos de Gnome, EOG.
[*]Administra tu correo y agenda con el poderoso [Evolution]("http://www.gnome.org/projects/evolution/").
[*]Pasa el rato con mas de una docena de jueguitos preinstalados.
[*]Extrae las pistas de un Cd con [Sound Juicer]("http://www.burtonini.com/blog/computers/sound-juicer")
[*]Graba CDs y DVDs de todo tipo con [Brasero]("http://www.gnome.org/projects/brasero/")
[*]Decenas de otras aplicaciones preinstaladas, tanto visuales como de consola.
[/LIST]
Todo esto, enmarcado en uno de los mas simples y accesibles escritorios jamás creado: [Gnome]("http://library.gnome.org/misc/release-notes/2.24/"). El mismo que MAC y otras tantas distros adoptaron. Todo eso, Desde el inicio! Que más queres? QUERÉS MAS ? Instalá cualquiera de las miles de aplicaciones libres (y no libres) disponibles para la distro más popular... 

**Qué me decis? Comprás o no comprás?** xD 

HEY! quien se esta riendo por allá atrás ???

---

### Post by WanderingKnight on 2008-10-10
> 
a. distintos programas, en gnome se usa el evolution para el mail, en kde se usa kmail, y asi ha y miles de programas. Todos tiene las mismas funcionalidades y todos se pueden instalar en ambos escritorios. Pero es preferible que si te gustan los de gnome, uses gnome y si te gustan los de kde uses kde y no mezcles MUCHO, porque eso hace que tengas que isntalar muchas cosas e mas y el sistema te vaya un toquesin mas lento.

Sino podés hacer lo que hago yo y usar Openbox con una mezcla de aplicaciones de GTK y Qt :p

Queda bárbaro y corre como los dioses :D (de todas formas sigo insistiendo que en muchas aplicaciones KDE lleva una ventaja abismal, por eso sigo usando kdeinit).

---

### Post by fer493 on 2008-10-12
Buenos muchachos muchas gracias por todas las respuestas y si, User21, me convenciste jajaj. Voy a evaluar el tema de cual poner, si Ubuntu o Xubuntu (porque mi maquina es medio vieja).

Valucha, si ese modem me lo dio Fibertel, es uno que tiene antenita para darle internet inalambrica a las otras maquinas de la casa. Pero si, voy a hacer eso del live cd a ver si funca y aviso si no anda.

Eso nomas gente, gracias por la buena onda y la rapidez!! Pronto van a contar con un nuevo usuario de linux jaja.

---

### Post by fer493 on 2008-10-12
Perdon que vuelva a molestar pero estaba viendo que onda el Xubuntu en [http://www.guia-ubuntu.org/index.php?title=Gu%C3%ADa_Xubuntu](http://www.guia-ubuntu.org/index.php?title=Gu%C3%ADa_Xubuntu) y parece que no viene con reproductor de audio, como es eso?

Tambien estaba viedno que existen otras distribuciones aparte de Xubuntu, para maquinas lentas, como UbuntuLite y Fluxbuntu, cual me recomiendan de las 3?

---

### Post by santiagoward2000 on 2008-10-12
> **fer493 said:**
> Perdon que vuelva a molestar pero estaba viendo que onda el Xubuntu en [http://www.guia-ubuntu.org/index.php?title=Gu%C3%ADa_Xubuntu](http://www.guia-ubuntu.org/index.php?title=Gu%C3%ADa_Xubuntu) y parece que no viene con reproductor de audio, como es eso?

Tambien estaba viedno que existen otras distribuciones aparte de Xubuntu, para maquinas lentas, como UbuntuLite y Fluxbuntu, cual me recomiendan de las 3?

Hola!
No, Xubuntu Hardy no viene con ningún reproductor de audio en serio, aunque podés usar Totem, que es más para videos. Pero podés instalar uno si querés, hay varios en los repositorios.
En Intrepid creo que van a poner el Audacious, que es una onda winamp.
Saludos!

_EDIT:_
Ahora cambiaron, y en el RC metieron el Listen en lugar del Audacious.

---

### Post by fer493 on 2008-10-13
> **fer493 said:**
> Perdon que vuelva a molestar pero estaba viendo que onda el Xubuntu en [http://www.guia-ubuntu.org/index.php?title=Gu%C3%ADa_Xubuntu](http://www.guia-ubuntu.org/index.php?title=Gu%C3%ADa_Xubuntu) y parece que no viene con reproductor de audio, como es eso?

**Tambien estaba viedno que existen otras distribuciones aparte de Xubuntu, para maquinas lentas, como UbuntuLite y Fluxbuntu, cual me recomiendan de las 3?**

Alguien sabe???

---

### Post by faktorqm on 2008-10-14
Si no viene con reproductor de audio te instalas VLC o similar y listo, cual es el problema?

Dependiendo del hardware de tu pc, te conviene o uno u otro, en orden del mas rapido al mas lento, viene fluxbuntu, ubuntu-lite y xubuntu. Postea que hardware tenes y vemos. Salu2!

---

### Post by fer493 on 2008-10-14
Joya, me quedo tranquilo con lo del audio entonces.

Factorqm, la maquina a la que le quiero poner linux es una AMD-K6 3D processor 427 mhz, 196 mb de ram (de los cuales siempre me aparece que tengo 183, no se por que). A esta pc la tengo con Win XP, asi que imaginate lo obscenamente lento que anda.

Gracias.

---

### Post by WanderingKnight on 2008-10-14
Dependiendo de la capacidad del disco te recomendaria que instales Ubuntu u otra distro.

Cuanto espacio de disco tiene la maquina?

---

### Post by fer493 on 2008-10-14
WanderingKnight, el disco es de 14 GB. Me gustaria alguna distro que ande rapido (pero que no sea una desgracia visual), ya me canse de esperar 30 segundos a que abra Firefox en XP.

Saludos.

---

### Post by WanderingKnight on 2008-10-14
El tema de otra distro pasa mas por el espacio. Si tenes ganas de aprender, podes hacer lo que hice yo e instalar el NetInstall de Debian (muy parecido a Ubuntu), que te tira un sistema operativo basico de consola y vas instalando los paquetes de a poco. Yo termine con una instalacion de 600~700 MB en la maquina de mi vieja que tiene 2 GB de disco, y salia con Xfce (Xubuntu) andando lo mas bien.

---

### Post by faktorqm on 2008-10-15
Si bien lo que dijo WK no esta mal, tenes que tener un mejor conocimiento de gnu/linux en general como para hacerlo, y si recien empezas no te conviene. 
Elive GEM es la distro que yo instalaria. Es un debian mas escritorio enlightment, visualmente esta buenisima y va rapido. (busca en el foro que subi a rapidshare por que el autor pide donacion...)
Salu2!!

---

### Post by fer493 on 2008-10-15
Te hice caso y me baje el Elive GEM para empezar por lo menos, pero la maquina no me arranca desde el cd. Ya le toquetee la bios y puse como 1st Boot Device al cd y como 2nd Boot Device al HD pero por alguna razon no me da bola y arranca desde el HD directamente. Que puedo hacer?

---

### Post by faktorqm on 2008-10-16
Y... te lo deberia tomar... grabaste bien el cd? Revisa eso. Salu2!

---

### Post by fer493 on 2008-10-16
Si revise el cd, pero se me ocurrio por que puede ser que no anda. Originalmente esta pc venia solo con lectora de cd (que es la unidad D:/), despues yo le agregue una grabadora (que es la unidad E:/). La D:/ dejo de leerme cds asi que ahora solo uso la E. Puede ser que yo ponga que arranque desde cd pero la maquina solo considere la D:/ y no la E:/ que es donde meto el cd de arranque??

---

### Post by faktorqm on 2008-10-16
Si puede ser eso, dependiendo que tengas como master y como esclavo, o una u otra.
Pone el cd en una, si no arranca, ponelo en la otra y volve a probar.
Te recuerdo que los dispositivos NO SE DENOMINAN CON LETRAS, eso sólo es una etiqueta que pone windows. Una lectora es una lectora, una grabadora, es una grabadora. Por ejemplo en ubuntu se podrian llamar /dev/sdc0 o /dev/sdc1 o /dev/sdb1. Salu2!!

---

### Post by fer493 on 2008-10-16
> **faktorqm said:**
> Si puede ser eso, dependiendo que tengas como master y como esclavo, o una u otra.
Pone el cd en una, si no arranca, ponelo en la otra y volve a probar.
Te recuerdo que los dispositivos NO SE DENOMINAN CON LETRAS, eso sólo es una etiqueta que pone windows. Una lectora es una lectora, una grabadora, es una grabadora. Por ejemplo en ubuntu se podrian llamar /dev/sdc0 o /dev/sdc1 o /dev/sdb1. Salu2!!

Claro claro, puse la denominacion que tengo yo. 
No puedo usar la lectora porque no anda mas, solo puedo leer cds desde la grabadora, como puedo hacer para que la maquina me reconozca esta unidad en el arranque?

---

### Post by guisheca on 2008-10-16
En donde configuras la bios para que arranque del cd tiene que haber varias opciones para arrancar con unidades opticas. Algo así como cdrom0, cdrom1, fijate a ver como te aparece en la bios.

---

### Post by fer493 on 2008-10-17
mira, las opciones que me aparecen para 1st Boot device son: ide-0, ide-1, ide-2, ide-3, cdrom, scsi (algo asi), armd-fdd, armd-hdd, network y disabled.

---

### Post by guisheca on 2008-10-17
Y vas a tener que probar lo que te dijo faktorqm tonce che. Empezá a jugar con los lugares en el cable ide y con el tema del master o esclavo. Hasta que te de, de última sacale la lectora que no anda y arrancá el livecd y después volvela a conectar.

---

### Post by chalito on 2008-10-17
Che, pero.. momento.

Si tenes una lectora de CD que no anda, porque no la sacas? no sirve de nada ahi conectada y le esta chupando jugo a la fuente al divino boton.

Yo directamente la sacaría asi de paso me aseguro que cuando en algun lado me figura "la lectora de cd", solo puede estar refiriendose a la unica que deje conectada (en este caso la grabadora)... se entiende?

---

### Post by fer493 on 2008-10-19
Ahi logre que me arranque desde el cd, tuve que toquetear un poco el tema master-esclavo pero anduvo. Ahora estoy haciendo back up de todo, asi que cuando instale (si es que lo logro jaja) les cuento como me fue. Gracias!!

---

### Post by guisheca on 2008-10-20
Excelente fer493!!! esperamos con ansias tus resultados!!
Saludos.

---

### Post by fer493 on 2008-10-21
Bueno, la verdad es que no lo pude instalar (en cualquier modo que iniciara la instalacion se me quedaba la pantalla en negro) y viendo por ahi a ver como solucionarlo, de casualidad, vi que Elive 1.0 no es compatible con placa de red Realtek (la que yo tengo), asi que no se bien que hacer.

---

### Post by fer493 on 2008-10-23
Sabe alguien por que puede ser que se me quede la pantalla en negro? Cualquier opcion que ponga (default, safe, acpi disabled, etc) pasa lo mismo: carga el kernel al 100%, despues se pone la pantalla en negro y se queda un rato leyendo el cd, luego para de leerlo y queda todo en negro. El cd esta bien grabado porque lo verifique y la iso tambien.

---

### Post by superjulin on 2008-10-23
hola fer ,por lo que comentas no estaria levantando el xserver ,puede pasar por algun tema en la placa de video,proba con alguna version anterior,en lo personal me ha pasado alguna vez y con alguna version anterior la 7.10 o 7.04 levantaba el xserver sin problema a partir de ahi actualizaba y listo la version 8.04 corria sin problema

---

### Post by fer493 on 2008-10-23
superjulin, me olvide de comentar que estaba tratando de instalar Elive 1.0, puede ser que no arranque por la misma razon (xserver)??

---

### Post by superjulin on 2008-10-24
fer,no lo conozco a elive,ahora si no levanta el entorno grafica lo mas probable es que sea por el xserver,si tenes la posibilidad de ver la consola lo que diria es hagas el comando [B]startx[B] para ver la respuesta que te da y mas o menos tener una idea de lo que pasa.

---

### Post by fer493 on 2008-10-25
Bueno, la verdad es que perdi un poco la paciencia con Elive e instale Puppy  linux, estoy escribiendo desde ahi. Por ahora va perfecto, la maquina es un jet de combate comparado con la carreta que era con Win XP. Muchas gracias a todos por la ayuda!

---

