---
title: "RadioGUI:Radios Argentinas,programa para escuchar la Radio creado por mi"
date: 2009-05-17
forum: Software
---

### Post by juancarlospaco on 2009-05-17
[CENTER][COLOR="Sienna"]**[SIZE="6"]RadioGUI : Radios Argentinas[/SIZE]**
*programa para escuchar la Radio creado por mi*[/COLOR]

[IMG]http://www.terra.es/personal5/jpayuso/MUSEO_VIRTUAL/radio_antigua_de_valvulas.jpg[/IMG]
[/CENTER]
[B]
Programa con Interface Grafica para escuchar Radios de toda Argentina[/B]
[LIST]
[*]Mas de 170 radios en un Click
[*]Incluye Radios del Interior del Pais
[*]Cache ajustable por el usuario segun el Ancho de Banda
[*]Integracion con el Sistema de Notificaciones de Ubuntu
[*]Debug User Friendly en Espanol en la Terminal
[*]1 solo Archivo
[*]Solo 13 Kb *(13.474 bytes)*
[*]Usa MPlayer de Back-End
[*]Licencia GPL
[*]Crea Acceso Directo en el Menu
[*]Interfaz Grafica sencilla y minimalista consume pocos recursos
[*]Cache Optimizado para Todos los Anchos de banda
[*]No requiere reconexion por Timeout
[*]Se instala con Doble Click
[/LIST]

[CENTER][IMG]http://www.barcelonamultimedia.com/images/fondo-radio-online.jpg[/IMG][/CENTER]


**[SIZE="5"][COLOR="Sienna"]Screenshots :[/COLOR][/SIZE]**

[CENTER][IMG]http://img198.imageshack.us/img198/4152/radiogui.gif[/IMG]


[IMG]http://img269.imageshack.us/img269/6033/radioguinotify.gif[/IMG]
[/CENTER]


**[SIZE="5"][COLOR="Sienna"]Descarga:[/COLOR][/SIZE]**

```
[CENTER][SIZE="3"]**[Bajar RadioGUI : Radios Argentinas]("http://tecnicoslinux.com.ar/livecd/RadioGUI_1.6_all.deb")**[/SIZE][/CENTER]
```

**SE AGRADECE EL HOSTING DEL ARCHIVO A [TECNICOSLINUX.COM.AR]("http://tecnicoslinux.com.ar/"), SI TE GUSTO EL PROGRAMA PASA POR LA WEB.**

***************************************************************************

**[COLOR="Sienna"][SIZE="6"]KRadioGUI: Version de RadioGUI para KDE[/SIZE][/COLOR]**
*Basado en la misma idea de RadioGUI.*

KRadioGUI *(estable y lo básico andando). *
Se pueden agregar radios sin problema alguno.

[Descarga](https://launchpad.net/kradiogui/trunk/0.5).

O sino compilando con qmake-qt4 desde el código fuente:

```
bzr checkout lp:kradiogui
```

*Creado por WanderingKnight.*



:D

---

### Post by andy_91 on 2009-05-17
¿Cuales son las dependencias y requisitos del programa del programa?

OFFtopic: esa es la nueva vercion de phyton, ¿Se puede instalar en Hardy?

---

### Post by sergiom99 on 2009-05-17
yo lo instale en Kubuntu HH sin problemas (en la instalacion).
Al tratar de ejecutarlo desde el acceso directo en Kmenu\Multimedia, no pasa nada.
desde Konsola:
```
$ RadioGUI

 RadioGUI Radios Argentinas.

 Se recomienda 256MB de ram minimo, este sistema Linux kubuntu 2.6.24-24-generic tiene :
              total       used       free     shared    buffers     cached
Mem:          1899       1120        778          0         27        813
Swap:          988         37        950

 Programa bajo Licencia GPL
mplayer: ningún proceso eliminado
 Comprobando dependencias...

ii  kmplayer-base                              1:0.10.0c-0ubuntu3                    Base files for KMPlayer
ii  kmplayer-konq-plugins                      1:0.10.0c-0ubuntu3                    KMPlayer plugin for KHTML/Konqueror
ii  mozilla-mplayer                            3.50-1ubuntu2.1                       MPlayer-Plugin for Mozilla
ii  mplayer                                    2:1.0~rc2-0ubuntu13.1+medibuntu1      The Ultimate Movie Player For Linux - Medibu
ii  mplayer-skins                              2-7                                   Skins for the Ubuntu mplayer Package
ii  smplayer                                   0.6.0~rc2-1                           complete front-end for MPlayer
ii  smplayer-translations                      0.6.0~rc2-1                           complete front-end for MPlayer - translation

 Sistema listo para RadioGUI Radios Argentinas...

/usr/bin/RadioGUI: line 223: zenity: orden no encontrada

Uso: sh /home/sergio/radio
        Radio Mitre AM792               ( Radio Mitre 792 AM )
        Rock & Pop FM           ( Rock and Pop )
(...)

```

Asi que no pasa nada.

PS: Puede ser que te falte FM Kabul 107.9??

---

### Post by josecuervo86 on 2009-05-17
Muy bueno! ya lo estoy bajando

Pd: te falto am 1010 de Rio Cuarto, Cordoba :P (para la proxima versión)

---

### Post by pablo.s on 2009-05-17
No hace falta Python...
JuanCarlosPaco integró muy
interesantemente un script
de bash con Zenity.

---

### Post by andy_91 on 2009-05-17
> **sergiom99 said:**
> yo lo instale en Kubuntu HH sin problemas (en la instalacion).
Al tratar de ejecutarlo desde el acceso directo en Kmenu\Multimedia, no pasa nada.

Asi que no pasa nada.

PS: Puede ser que te falte FM Kabul 107.9??

ami me paso algo paresido lo instale sin problemas en Linux Mint Elysa XFCE (Deribado de HH), lo pudo ejecutar sin mayores problemas pero al momento de escuchar la radio se cierra

```
andy@andy-desktop:~$ RadioGUI

 RadioGUI Radios Argentinas. 

 Se recomienda 256MB de ram minimo, este sistema Linux andy-desktop 2.6.24-24-generic tiene : 
              total       used       free     shared    buffers     cached
Mem:           217        196         21          0          4         84
Swap:          627        106        520 

 Programa bajo Licencia GPL 
mplayer: ningún proceso eliminado
 Comprobando dependencias... 

ii  mozilla-mplayer                            3.55-1ubuntu1~hardy1                    MPlayer-Plugin for Mozilla
ii  mplayer                                    2:1.0~rc2-0ubuntu13.1+medibuntu1        The Ultimate Movie Player For Linux - Medibuntu packag
ii  mplayer-skins                              2-7                                     Skins for the Ubuntu mplayer Package

 Sistema listo para RadioGUI Radios Argentinas... 

 Sintonizando Los 40 Principales FM  ... 
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Couldn't resolve name for AF_INET6: 66.175.96.10
Couldn't resolve name for AF_INET6: 66.175.96.10
Server returned 503:Service Unavailable
Failed to parse header.
Failed, exiting.
Couldn't resolve name for AF_INET6: 66.175.96.10
mplayer: ningún proceso eliminado

```

a te dejo tres radios para que agreges a tu programa si queres 

[RED 92]("mms://wmusic.iplatense.com.ar/radio92") (de la plata)
[URL="mms://radiodisney.telecomdatacenter.com.ar/radioDisney/radiodisney.asx"]
Radio Disney[/URL] (CF)

[Cielo FM]("http://200.26.114.34:8000/cielofm.ogg") (utiliza software libre :p)

PD: Para mas radios de Argentina entra [aca]("http://sradio.tv/country/Argentina")

---

### Post by juancarlospaco on 2009-05-17
Hola de nuevo, que bueno que hallan recibido bien el programa;
**el programa es Bash Scripting y usa [Zenity]("apt:/zenity"), [Mplayer]("apt:/mplayer") y LibNotify, no usa Python.**

Igual estos requeridos deberia resolverselos, por lo menos a mi en Jaunty con Gdebi lo hizo.
Libnotify es para el nuevo sistema de notificaciones de Jaunty o version posterior, 
no requerido pero **MUY recomendado**, se instala con:

```
**sudo apt-get install libnotify***
```

Se que hay mas Radios, pero muchas usan tecnologias no muy amigables con Linux,
encontre inclusive un par de radios que te quieren instalar ActiveX,
para hacer Streaming, cosa completamente innecesaria,
las radios del Interior** algunas no estan 24x7x365**, tienen un horario.

El Script **esta diseñado para Ubuntu**, y puede resolver el solo sus propias dependencias.
Pero no en otros derivados como Kubuntu por ejemplo.

Como dice pablo.s no es mas que un humilde script de bash ;)
Contenido del .deb :

**usr/bin/RadioGUI** *---> Script de bash*
usr/share/pixmaps/multimedia-player.svg *---> Icono*
usr/share/applications/RadioGUI.desktop *---> Entrada de Menu*

andy_91: te dice que el Servidor no esta disponible, probablemente saturado, o caido.


Voy a agregar todos los Flujos Stream que posteen.
*Necesito link directo al Stream, nombre completo, ciudad y provincia de la radio.*

---

### Post by josecuervo86 on 2009-05-18
AM 1010 Radio Rio Cuarto, Rio Cuarto (Cordoba), [Link al stream]("http://www.lv16.com/r4/vivo_am.php")

Fm 93.9 Ranquel Stereo, Rio Cuarto (Cordoba), [Link al stream]("http://www.lv16.com/r4/vivo_fm.php")

Yo estuve tratando de agregarlas a un script que habian puesto hace unos dias, pero la verdad es que no lo pude hacer, seguramnete porque no entiendo demasiado :D

---

### Post by juancarlospaco on 2009-05-18
Agregados todos los Stream Posteados.
*Nueva Version a futuro.*

---

### Post by totolinux on 2009-05-18
me gusta mucho el programa, buen trabajo. usandooo

---

### Post by pablo.s on 2009-05-18
> **juancarlospaco said:**
> Como dice pablo.s no es mas que un humilde script de bash ;)

Es muy buen hack, no se suelen
ver adaptaciones tan vistosas de
scripts de bash :D. Felicitaciones!

No está la única [radio]("http://glz.msn.co.il/") que escucho
por streaming.

---

### Post by SLA_leandrin on 2009-05-18
Muy bueno, anda brillantemente, felicitaciones!

Para la próxima versión, incluíle Radio Salta AM840

[http://www.radiosalta.com/](http://www.radiosalta.com/)

Saludos!

---

### Post by bruno9779 on 2009-05-18
> **pablo.s said:**
> Es muy buen hack, no se suelen
ver adaptaciones tan vistosas de
scripts de bash :D. Felicitaciones!

No está la única [radio]("http://glz.msn.co.il/") que escucho
por streaming.

Es una radio Israelí.

Porque deberia aparecer una radio de oriente medio en un programa para escuchar radios Argentinas?

---

### Post by josecuervo86 on 2009-05-18
Te hago una consulta: estuve usando el programita. La verdad es que esta muy bueno, pero me dispara el uso del cpu al 90-100%. No se que podra ser, pero ya que solo es un script no deberia tener tanta incidencia en el uso del cpu

---

### Post by juancarlospaco on 2009-05-18
Simple el Codec que usan muchos es el Propietario MP3, 
que en tiempo real a calidad de 128Kb/segundo es suficiente para hacer laburar el micro,
fijate si ajustando la preferencia de cache mejora un poquito, fijate si tenes ubuntu-restricted-extras instalado.
Tenes escalamiento de frecuencia dinamico ?


Veo de incluir la radio esa, tambien hay una Emisora Argentina que trasmite desde España,
es orientada a los Argentinos que viven en españa y sus familiares locales.

---

### Post by Cisne on 2009-05-18
> **juancarlospaco said:**
> 

Veo de incluir la radio esa, tambien hay una Emisora Argentina que trasmite desde España,
es orientada a los Argentinos que viven en españa y sus familiares locales.

Buenisimo

Ya que somos una familia Italo-Argentina viajando el mundo

---

### Post by sergiom99 on 2009-05-18
instale el paquete zenicity (y otras cuantas dependencias) y ahora si funca.
Estoy escuchando "radio heavy metal" !

---

### Post by Cisne on 2009-05-18
Hay un pequeño problema con el script: termina fatal.

Si aprieto la tecla Cancelar Mplayer se rompe, rompiento todas las demas sesiones TB.

Por lo demas esta barbaro

---

### Post by juancarlospaco on 2009-05-18
> **sergiom99 said:**
> instale el paquete zenicity (y otras cuantas dependencias) y ahora si funca.
Estoy escuchando "radio heavy metal" !

Es que esta diseñado para Ubuntu, Zenity es parte de la base de las GTK
:D

---

### Post by sergiom99 on 2009-05-18
> **juancarlospaco said:**
> Es que esta diseñado para Ubuntu, Zenity es parte de la base de las GTK
:D

Igual anda muy bien, gracias por tu laburo.
En mi caso se ve asi [1] pero seguro debe ser por usar Kubuntu.

[1]

---

### Post by totolinux on 2009-05-18
mirá me di cuenta que el cpu esta al 100 % con radio rock and pop 
paré el programa y ejecute un script que uso para escuchar radios que ya fue posteado en otro tred creo que en  (script utiles etc...) y pongo la rock&pop y el cpu  esta entre 16 y 22 % 
Que sera ??

---

### Post by luks911 on 2009-05-18
> **totolinux said:**
> mirá me di cuenta que el cpu esta al 100 % con radio rock and pop 
paré el programa y ejecute un script que uso para escuchar radios que ya fue posteado en otro tred creo que en  (script utiles etc...) y pongo la rock&pop y el cpu  esta entre 16 y 22 % 
Que sera ??

¿El otro script usa mplayer también?

---

### Post by sergiom99 on 2009-05-18
el script es este [1] y si usa mplayer.
saludos.

[1] [http://ubuntuforums.org/showpost.php?p=6690485&postcount=37](http://ubuntuforums.org/showpost.php?p=6690485&postcount=37)

---

### Post by totolinux on 2009-05-19
> **luks911 said:**
> ¿El otro script usa mplayer también?

si usa mplayer y es el que posteo Sergiom99

---

### Post by sebastianabate on 2009-05-20
Muy bueno el script. Sería muy interesante que se pudiera controlar el volumen de la radio. Pero es lo único que le agregaría, me gustan las cosas simples. Una cosa rara es que a mi no me funcionaba la parte de libnotify, y la tengo funcionando porque el emesene sí la puede usar; el error que tiraba en consola era "/usr/bin/RadioGUI: line 234: notify-send: command not found", pero instalando el paquete libnotify-bin se arregló todo.

Por el tema del uso del procesador, no es mplayer el culpable, el proceso que está al 99% es 

zenity --progress --window-icon=/usr...

y continúa con un path largo. Deduzco por esto que es la ventanita que tiene la barra de progreso que va y viene constantemente la culpable.

---

### Post by elvis77 on 2009-05-20
[FONT=monospace]Frecuencia Zero FM 92.5
Mataderos, Capital Federal
[www.frecuenciazero.com.ar](www.frecuenciazero.com.ar) 
Una radio de rock donde laburo
[/FONT]

---

### Post by lega on 2009-05-20
Buenisimo el programita, se podrá agregar una opción para que uno mismo agregue radios? digo para no depender de la actualización del programa o por ejemplo si una radio cambia de proveedor de streaming, como pasó hace unos meses con Rock and Pop, Metro, Aspen, Blue y demás que creo que son todas del mismo grupo.

---

### Post by javier-2714 on 2009-05-20
Esta muy bueno funciona perfecto lo instale en ubuntu hardy sin ningún problema lo único me hace lo mismo el cpu 90 % estaría bueno corregir eso y agregarle para controlar el volumen.
Saludos

---

### Post by ombzzz on 2009-05-23
Gracias Juancarlospaco muy bueno el programa.

Tal cual algunos comentaron tambien, el top da 85% de uso de CPU para el programa zenity, mientras corre radiogui ( en un Ubuntu 9.04 recien instalado ).

Podra mejorarse eso? o es un problema del zenity?

Otro problema que tuve es que no me funcionaba el boton cancelar , en la ventana "escuchando radio". Entonces la cerre con la "cruz" ( de la barra de titulo de la ventana ) y la radio se sigue escuchando ( tanto mplayer como zenity siguen corriendo ).


Un saludo desde cordoba

         orlando

---

### Post by r@fitiiixxx on 2009-05-23
Buenaa alto reproductor! me dieron ganas de hacer algo asi yo tmb.. jeje... que buena onda... 
.le falta 1 control de volumen como bien dijeron ahi...
.ese error del cancelar que a veces no cierra asi
.poder agregar radios extras

che pero que bueno!... lo que si... intenté agregarle 1 stream mio favorito que no es de por aquí en el bash pero lo agrego en los dos lados... en la lista para seleccionar y en el stream... pero no anda che.. se corta el programa...

aver si nos enseñas a los que somos novatos a agregar radios al source ;)

suerte y salu2 ):P

---

### Post by bolchevique on 2009-05-23
Exelente!! Usando en Ubuntu 9.04 

ami me consume un bastante micro el proceso Zenity . va de 20 a 50%  con algún pico de 80%.

por si te sirve el dato


saludos y gracias por el programita, esta muy piola. (lo encontre en la página de tecnicos linux :) )

---

### Post by r@fitiiixxx on 2009-05-23
> **bolchevique said:**
> Exelente!! Usando en Ubuntu 9.04 

ami me consume un bastante micro el proceso Zenity . va de 20 a 50%  con algún pico de 80%.

por si te sirve el dato


saludos y gracias por el programita, esta muy piola. (lo encontre en la página de tecnicos linux :) )

a mi tmb... a todos les pasa eso... para mi es porque qda en un ciclo y no sale.. entonces es como que se traba el proceso... va eso creo, es 1 teoria... pero en realidad la pc anda bien... osea figura 99% pero yo puedo seguir habriendo ventanas q no pasa nada... asi que no se...

mal eso es de arreglo pero de urgencia...

extra: tengo 1os iconos que son 1 re masa... pero son de 64x64... si algun GIMPero los quiere extender a 256x256.. porque en la barra Gnome Do... se ve chiquito y pixelado el icono del ipod (que es de 128x128 ) que viene en el pack .deb...

 es super exelente... le da ese toque mac pro super dupper xD... considerenlo :D

los iconos son de ICONSPEDIA... ¡-pod :D ( a mi me gusta mas el azul 8))
[center]
[[IMG]http://www.iconspedia.com/uploads/119912726964664389.png[/IMG]]("http://www.iconspedia.com/icon/iradio-black---40.html")     [[IMG]http://www.iconspedia.com/uploads/1769342551099732052.png[/IMG]]("http://www.iconspedia.com/icon/iradio-red---42.html")     [[IMG]http://www.iconspedia.com/uploads/6187096711910759117.png[/IMG]]("http://www.iconspedia.com/icon/iradio-blue---41.html")
[/center]

pd: me gusto mucho el cosito que va de derecha a izq cuando la radio esta "ON" jajaja... es muy bueno... se le podrian poner varias? para molestar nomas.. xD
o uno arriba y otro abajo... ahi tiene mas onda xD

pd: te paso la radio que quiero agregar por si lo qres hacer vos... no es argentina... e, pero con pedir aca en el foro esto no le ago daño a nadie... si no no hay drama ;)      "http://www.di.fm/mp3/trance.pls"
es de esta pagina... no se si eso es lo que te tengo q pasar.. [D I G I T A L L Y - I M P O R T E D - Radio [Trance channel]]("http://www.di.fm/trance/")

---

### Post by juancarlospaco on 2009-05-23
@ombzzz:Its not a Bug, its a Feature XD ,
algunos me pidieron si se podia descartar la GUI para no tener una ventanita mas molestando,
si al fin y al cabo lo que queremos es el sonido y la musica,
para apagar la radio una vez que cerraste la ventanita de " Escuchando la radio ..."
tenes que ejecutarlo de nuevo y apreta Cancelar.


@r@fitiiixxx: Si anda el boton de Cancelar, 
todo el que quiera usar el Cancelar modifique el Lanzador de RadioGUI poniendole asi:
**[COLOR="Red"]xterm -e "RadioGUI"[/COLOR]**

El icono era originalmente un .SVG de los del tema Human, el mas apropiado que encontre, 
queria que el .DEB no lo incluya y use el que todos los Ubuntu tienen, y pese menos,
pero se ve que el .DEB lo incluye igual por si las dudas.



A futuro quiero usar el mismo Source para hacer un programa de Tragos y Bebidas,
el "Drinky" *(espero no me afanen el nombre XD )*, 
con icono personalizado y funcion de agregar tragos.

salu2

---

### Post by Mauro22 on 2009-05-23
Muy buena la recopilacion de radios, che!!


Una cosita, estuve leyendo lo del control del volumen y eso..


Hice un par de cambios (para mi):

En la linea de mplayer agregué al principio:

-gui -really-quiet

y comentar (#) los zenity que viene despues (el de la barrita y el otro)


Asi, al elegir la radio me abre una ventana del mplayer con el control del volumen y eso...

Despues al cerrar el mplayer se reincia el script dando la posibilidad de elegir otra radio o salir.

Ojala te interese, y ademas, para mejores resultados, habria que portarlo a otro lenguaje, por ejemplo python para dejar un icono en el systray...


):P

---

### Post by leonardomdq on 2009-05-27
Excelente este reproductor....muchas gracias

Una consulta se puede hacer que se vea en emesene para que salga la radio que estoy escuchando?

---

### Post by juancarlospaco on 2009-05-27
> **leonardomdq said:**
> 
Una consulta se puede hacer que se vea en emesene para que salga la radio que estoy escuchando?

Si,** si tenes algun plugin que soporte MPlayer funciona.**

Estoy preparando el lanzamiento de la Version 2, con consumo de Micro 1% :D
y las radios que pidieron.

*salu2*

---

### Post by josecuervo86 on 2009-05-27
grande juan! asi me gusta!! apenas la tengas avisa :D

---

### Post by leonardomdq on 2009-05-27
No tengo ningun plugin instalado que soporte MPlayer.

Buenisimo Juan, te felicito por el sotware.

---

### Post by hernan blau on 2009-05-27
Gracias !!!!! Con Jaunty lo instalé y comenzó a funcionar inmediatamente. Por suerte tiene clásica ! Cordialmente, HB

---

### Post by Daniel TL on 2009-05-28
Hola! Muy bueno el aporte, pero tengo un problema :(

Arranco la herramienta, sintonizo una radio (Aspen) y después de un par de minutos (2 ó 3, como máximo) el programa se cierra.

Lo arranqué desde una consola y obtuve este reporte:

[http://paste.ubuntu.com/182954/]("http://paste.ubuntu.com/182954/")

¿Qué significa? La verdad es que no me dice gran cosa...

Estoy usando Hardy de 64 bits, actualizado. El paquete .deb lo instalé con la interfaz gráfica gdebi y me indicó que no tiene probleas de dependencias.

Saludos!

---

### Post by juancarlospaco on 2009-05-28
Por defecto no tenes soporte para las Notificaciones por que cuando salio Hardy no existian,
te dice que el Servidor esta saturado, hasta el Servidor llegas, pero el Stream se corta,
tambien puede ser que te niegue algo en el medio *(ej. Proxy, Router, etc)*

Proba aumentandole la Cache al maximo.

Lo han colgado de Taringa y de un par de Blogs ya, 
nunca pense que fuera tan util un programejo tan humilde :)

*La Version 2 viene mas linda...  estoy haciendole los Skins en Gimp...*

---

### Post by josecuervo86 on 2009-05-28
> **juancarlospaco said:**
> 

*La Version 2 viene mas linda...  estoy haciendole los Skins en Gimp...*

Fecha estimada??

---

### Post by telaengancho on 2009-05-28
estaria bueno que agregaras esta radio:
FM100.5 Cordoba
mms://lv3canal1.telecomdatacenter.com.ar/lv3canal1 creo que esa la direccion de la misma

---

### Post by Daniel TL on 2009-05-30
Sigue sin funcionar :( He puesto al máximo la cache y después de unos minutos el programa se cierra...
En virtud de lo que se ha comentado, lo voy a usar en la netbook, en la que tengo JJ.
Saludos y muchas gracias por el aporte!

---

### Post by nikitux on 2009-05-30
Hola en primera instancia felicito al autor del RadioGui por tomarse semejante trabajo. Por otro lado lo estuve probando esta mañana y le quería comentar que me consumió muchos recursos de CPU , me gustaría saber si es un problema mio o a algun otro que lo usó le generó el mismo problema. Antes de probar RadioGui usaba el script echo por Buanzo y otro más que no recuerdo el nombre que tb usa Mplayer y no tengo ningun problema.

Saludos Nikitux

---

### Post by josecuervo86 on 2009-05-30
No sos el unico, a mi tambien me lo hace, pero el autor esta trabajando en ese bug y en la proxima versión "asegura" 1% de consumo de recursos :P

---

### Post by WanderingKnight on 2009-06-14
Bueno gente, sabrá perdonar juancarloscapo pero, viendo que esto está basado en Gtk, y para demostrar que los usuarios de Kubuntu no somos menos, me "subí" a su proyecto como una forma de mejorar mis habilidades con Qt (con el cual estoy haciendo otro proyecto de SL en este momento, que todavía está en pañales :)), y "porté" su aplicación a Qt/KDE. Bah, en realidad tomé la idea y armé una aplicación muy similar en Qt.

Al igual que RadioGUI, **requiere de mplayer**, pero sólo porque no pude hacer andar correctamente Phonon. En cuanto pueda ese requerimiento vuela :)

[Acá](https://launchpad.net/kradiogui/trunk/0.1) tienen un binario i386 que simplemente deben descomprimir, dar permisos de ejecución, y voilá.

Para 64 bits van a tener que compilar. Para bajarse el código:

```
bzr checkout lp:kradiogui/trunk/0.1
```

y después cd en el directorio y make (tienen que tener las bibliotecas de desarrollo de Qt 4 instaladas).

Ojo que todavía está muy verde. Por ejemplo, todavía no implementé nada que indique que mplayer está cargando el stream, así que cuando le den play a una radio y vean que no pasa nada, esperen un ratito a que cargue. Ah, y no viene con radios por defecto (cuando tenga tiempo añado las radios que están en la app de juancarloscapo a un archivo de configuración y lo subo).

A futuro se viene soporte para errores de mplayer y un tray icon. Y quien sabe, tal vez más adelante un plasmoid :p

Comentarios, críticas, insultos, código (:D), más que bienvenidos.

---

### Post by juancarlospaco on 2009-06-14
*Bueno me ganaste de mano *:p

**Venia a presentar [SIZE="3"]RagioGUI 1.5 [/SIZE]!!!**

[LIST]
[*]**[SIZE="3"]Bug del Uso de procesador arreglado.[/SIZE]***(Upgrade muy Recomendado!)*
[*]**Soporte para Skins.**
[*]**Todas las radios solicitadas agregadas.**
[*]**Si se sale de escuchar una Radio, se vuelve al Menu de Emisoras, por si se quiere escuchar otra, sino Cancelar se cierra.**
[*]**Zenity como paquete requerido.**
[*]**Libnotify como paquete sugerido *[SIZE="1"](necesario para la integracion con las notificaciones de Ubuntu)[/SIZE]***
[/LIST]

[CENTER]Tiene un secretito mas jejeje, 
***Skin Al Azar cuando se inicia!, Screenshot RadioGUI 1.5*** :

[IMG]http://img36.imageshack.us/img36/6054/radiogui15.gif[/IMG][/CENTER]

[LIST]
[*]*A futuro mas Skins ;P*
[/LIST]
No hace lio si RadioGUI 1.0 estaba instalado, 
no es necesario desinstalar la version 1.0, 
lo reemplaza correctamente como debe ser.


[SIZE="5"]Descarga :[/SIZE]
*[SIZE="1"]126,5 KiB (129490 bytes)[/SIZE]*
```
[CENTER]**[SIZE="3"][Descarga RadioGUI 1.5]("http://tecnicoslinux.com.ar/livecd/RadioGUI_1.6_all.deb")[/SIZE]**[/CENTER]
```

Gracias a todos por la buena onda, nunca pense que sea tan util.

Gracias al Host del .deb [http://tecnicoslinux.com.ar/](http://tecnicoslinux.com.ar/)

Gracias a WanderingKnight por la version que creo, 
se podria hacer una version combinada, 
todo en un mismo .deb instalable, que te parece...?, 
si me autorizas lo hago,
algo como GKRadioGUI y elejir en el inicio si QT o GTK.

*Bajenselo que no come el micro como el 1.0* :)

*[SIZE="1"]Si les gusto bajense[ el Bleachbit ]("http://bleachbit.sourceforge.net/download.php")que ayudo a hacer[/SIZE]*

---

### Post by josecuervo86 on 2009-06-14
Genio!! ya lo estoy bajando!! Muchas Gracias :D

---

### Post by lega on 2009-06-14
no me anda :( elijo la radio que quiero escuchar y me muestra la opcioón para el tamaño del caché, le doy aceptar y vuelve a la selección de la radio y a la selección del caché y a la selección de la radio... así hasta que me cansé y vine a reportar que no me andaba :)

---

### Post by leonardomdq on 2009-06-14
A mi me pasa lo mismo que a lega.
No me funciona, ejecuto el programa, se abre la lista de radios, carga el cache y luego aparece la lista de radios nuevamente pero no inicia.

Gracias Juan por esta nueva version.

saludos

---

### Post by WanderingKnight on 2009-06-14
> Gracias a WanderingKnight por la version que creo, 
se podria hacer una version combinada, 
todo en un mismo .deb instalable, que te parece...?, 
si me autorizas lo hago,
algo como GKRadioGUI y elejir en el inicio si QT o GTK.


Pero por su pollo! Pero igualmente dame unos días que me falta pulir varias cosas más de mi versión, cuando más o menos esté listo ahí lo hacemos.

Saludos.

---

### Post by sebastianabate on 2009-06-14
El problema es que el script llama a xview que no viene instalado por default en Ubuntu. Instalen el paquete xloadimage y listo.[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by juancarlospaco on 2009-06-14
> **lega said:**
> no me anda :( elijo la radio que quiero escuchar y me muestra la opcioón para el tamaño del caché, le doy aceptar y vuelve a la selección de la radio y a la selección del caché y a la selección de la radio... así hasta que me cansé y vine a reportar que no me andaba :)

> **leonardomdq said:**
> A mi me pasa lo mismo que a lega.
No me funciona, ejecuto el programa, se abre la lista de radios, carga el cache y luego aparece la lista de radios nuevamente pero no inicia.
Gracias Juan por esta nueva version.
saludos

Ejecutenlo en una Terminal y fijense que falla, 
algunas radios cambian codecs a algunos que no andan en Linux,
otras simplemente se saturan de a ratos.
:(

---

### Post by leonardomdq on 2009-06-14
Solucionado, instale el paquete **xloadimage** desde Sinaptic que dijo sebastianabate y funciono.

Muchas gracias

---

### Post by juancarlospaco on 2009-06-14
> **WanderingKnight said:**
> Pero por su pollo! Pero igualmente dame unos días que me falta pulir varias cosas más de mi versión, cuando más o menos esté listo ahí lo hacemos.
Saludos.

*Bueno...*, 
a lo que voy es NO hagas la lista de emisoras, 
no sabes el TIEMPO que eso me llevo...!,
te dono mi lista para tu programa tambien, y compartimos lista.
:D

---

### Post by juancarlospaco on 2009-06-14
> **sebastianabate said:**
> El problema es que el script llama a xview que no viene instalado por default en Ubuntu. Instalen el paquete xloadimage y listo.[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

> **leonardomdq said:**
> Solucionado, instale el paquete **xloadimage** desde Sinaptic que dijo sebastianabate y funciono.
Muchas gracias

Listo, solucionado, **[SIZE="3"]version 1.6 con el Hot Fix[/SIZE]** !

```
[CENTER]**[SIZE="3"][Descarga RadioGUI 1.6]("http://tecnicoslinux.com.ar/livecd/RadioGUI_1.6_all.deb")[/SIZE]**[/CENTER]
```
[I]
voy a reemplazar los otros links para que nadie se baje el viejo...[/I]

---

### Post by acdm86 on 2009-06-14
Recien lo instalé, anda perfecto, gracias, muy bueno

---

### Post by andy_91 on 2009-06-14
lo acabo de instalar esta muy weno, un 10 sin duda ;)

---

### Post by juancarlospaco on 2009-06-15
Lo probe en mi Asus eee y no consume nada de micro practicamente, Bug Free.

Los Skins tienen que ser **.jpg de 400x200Pixeles** y van en **/usr/share/RadioGUI/**
Si hacen alguno envienmelo y tal vez saldra en futuras Versiones.
:)

---

### Post by andy_91 on 2009-06-15
lo de apocalípsis no es un poco exagerado :P

---

### Post by ramiro_md on 2009-06-17
No lo he probado, pero por las imagenes te falta la FM La Redonda de La Plata 100.3..aunque son unas basuras que siempre le pegan a Gimnasia y Estudiantes son los únicos que transmiten los partidos :P (para faktorqm que no tiene el codificado jejeje)

Un abrazo

EDIT: Ahora lo probé y está bastante copado !.

---

### Post by sergiom99 on 2009-06-17
se podria incorporarle un cuadro de busqueda? todavia no pude encontrar la Metro 95.1 FM.
Gracias por tu laburo!

---

### Post by EnriqueK on 2009-06-17
Lo instalé y funcionó muy bien, pero tuve el problema de que se me desconfiguró Exaile, por lo que terminé desinstalándolo.
Lo que hago es crear un documento de textos y pongo 
[Reference]

Ref1=URL del Streaming
Por ejemplo para Radio Del Plata pongo
[Reference]

Ref1=mms://delplata.telecomdatacenter.com.ar/delplata

Y así tengo un listado personalizado y que puedo ejecutrar con mplayer o sus front ends o com VLC  Rrealmente es imposible dar gusto a todos. por lo que cualquier intento terminará en un listado muy grande que termina siendo impráctico, por lo que en mi opinión lo mejor es aprender a capturar la URL de las distintas emisiones y así conformar su radioteca personalizada.

---

### Post by WanderingKnight on 2009-06-18
Bueno, ya tengo la versión 0.5 de KRadioGUI (estable y lo básico andando). Se pueden agregar radios sin problema alguno.

Si a alguien le gustaría tener un archivo de configuración con el listado de radios que usa RadioGUI, por favor avíseme :)

[Descarga](https://launchpad.net/kradiogui/trunk/0.5).

O sino compilando con qmake-qt4 desde el código fuente:

```
bzr checkout lp:kradiogui
```

juancarlospaco:

Te molestaría editar el primer post con mi versión (el título también :))? Gracias desde ya!

---

### Post by pablo.s on 2009-06-18
Está bueno, Lucas.
Dale para adelante!

Si al archivo config que crea
cuando inicia el programa,
le ponés uno de entrada con
la base de datos del script de
juancarlos, no estaria mejor?

---

### Post by crchtiger on 2009-07-21
se podra agregar la tribu? 

[www.fmlatribu.com/](www.fmlatribu.com/)

muy copado el programa! gracias

---

### Post by guillermolisi on 2009-07-22
Que no este La Tribu es pecado capital :)

---

### Post by mama21mama on 2009-10-03
Cuando este echo el de tv me avisas :D

---

### Post by Mauro22 on 2009-10-03
No quiero hacer Spam pero como leí sobre la versión en QT, les quería comentar que yo junto a JoseCuervo86 y KondorFire estamos desarollando un fork hecho en gambas...

No he hecho mucha publicidad al respecto para no opacar el esfuerzo de JuanCarlosPaco


Les dejo la URL del proyecto por si alguien desea darle una mirada. 

[http://jarp.comxa.com](http://jarp.comxa.com)

Se que es beta, que tiene bugs y que aunque el programa en si no pesa mucho, las dependecias de gambas son varias. Actualmente estamos trabajando en otra version y he empezado la version en python gtk.

**Si alguien lo baja, y tiene la ultima version de emesene por favor NO instale el plugin para CurrentSong. Emesene cambio varias cosas dejando obsoleto el plugin.**

Gracias!

---

### Post by mama21mama on 2009-10-03
Mauro22 muy buena la aplicacion :D ... pero quiero tv please help!
Me quedo sin cable pronto [-o<

---

### Post by josecuervo86 on 2009-10-04
mama, proba este: [http://shakaran.es/blog/tivion/](http://shakaran.es/blog/tivion/)

---

### Post by mama21mama on 2009-10-04
> **josecuervo86 said:**
> mama, proba este: [http://shakaran.es/blog/tivion/](http://shakaran.es/blog/tivion/)

si ese prove y ni anda en jaunty solo es para karmic.

probé ahora bien el que dijo Mauro22 el jarp y veo tv, también tiene radio anda +10

---

### Post by Applelnx on 2009-10-04
Muy bueno, mis felicitaciones ;)

---

### Post by Mauro22 on 2009-10-05
> **Mauro22 said:**
> No quiero hacer Spam pero como leí sobre la versión en QT, les quería comentar que yo junto a JoseCuervo86 y KondorFire estamos desarollando un fork hecho en gambas...

No he hecho mucha publicidad al respecto para no opacar el esfuerzo de JuanCarlosPaco


Les dejo la URL del proyecto por si alguien desea darle una mirada. 

[http://jarp.comxa.com](http://jarp.comxa.com)

Se que es beta, que tiene bugs y que aunque el programa en si no pesa mucho, las dependecias de gambas son varias. Actualmente estamos trabajando en otra version y he empezado la version en python gtk.

**Si alguien lo baja, y tiene la ultima version de emesene por favor NO instale el plugin para CurrentSong. Emesene cambio varias cosas dejando obsoleto el plugin.**

Gracias!


Aviso nomas, que recien colgué la version 0.8 que tiene muchas mas cosas y es mas estable! Gracias!

---

### Post by Kabezon on 2009-10-05
Muy bueno el JARP!

---

### Post by juancarlospaco on 2009-10-24
[LIST]
[*]***[SIZE="3"]OPA!, que es eso...?[/SIZE]***
[/LIST]

[IMG]http://img260.imageshack.us/img260/2104/pantallazo2t.jpg[/IMG]

For fun, yo uso jarp jajajaja.
:P

---

### Post by matog on 2009-11-12
Buenisima la aplicacion.
Pregunta: Debería mostrarme alguna notificacion en el area de notificacion del sistema, o con algun cartelito por ahi? No me muestra nada...estoy con Karmic.

Sugerencia: estaria muy bueno que uno pueda agreguar radios, y que mande su lista a un servidor, y de ahi, cada uno puede actualizar las listas de du RadioGUI.

Saludos!!!

---

### Post by matitoro on 2010-03-01
;) gracias anda de 10

---

### Post by LolaMora on 2010-03-15
Buenas.:)
Llegué aquí para poder escuchar mis radios favoritas porque desde las paginas de las mismas no puedo, me sale que me faltan complementos.
Tu programa se instaló perfectamente, puedo escuchar las radios que probé, pero faltan mis radios en la lista.

Para la próxima versión, Juan, si podés agregarlas son:

AM 530 radio de las madres
AM 740 radio cooperativa
AM 750 radio Nacional Cordoba

(Como podés ver, no escucho la radio 10) je je...

---

### Post by raulito on 2010-04-08
Felicitaciones !!!
Anda muy bien

---

