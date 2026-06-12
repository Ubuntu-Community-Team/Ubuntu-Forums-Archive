---
title: "Los vídeos flash en youtube no andan como deberían :s"
date: 2008-04-02
forum: Software
---

### Post by chispachips on 2008-04-02
Hola muy buenas a toda la comunidad argentina ^^, soy español y vengo de la comunidad ubuntu-es en que la verdad no te hacían mucho caso... Así que deposito a partir de ahora todas mis esperanzas en argentina y en esta comunidad, que son los argentinos quienes siempre habéis estado dispuestos a ayudar y sois el país que más me gusta de sudamérica jaja ;)

Y ahora fuera de peloteos jaja, esta era mi presentación. Mi problema comienza ahora, tengo la versión 7.04 Feisty Fawn instalada y el navegador web Firefox, el problema es que los vídeos en flash como los de youtube no andan tan fluidos como deberían, si no que andan a unos 5 fotogramas por segundo, un refresco lento. He probado a desinstalar cualquier plugin que había y volverlo a instalarlo de todas las formas que he podido (desde el propio firefox, desde Synaptic, desde Añadir/Quitar programas con los Ubuntu restricted extras) pero nada, incluso probé a reinstalar todo el Firefox enterito borrando la carpeta .mozilla para que no se quedase la información; pero nada, ese refresco lento sigue ahí.

He hecho varias instalaciones de Ubuntu, pues llevo año y medio utilizándolo y nunca me pasó, incluso instalé esta versión en otras ocasiones, la 7.04, y siempre fueron bien los vídeos flash... ¿Me podrían echar un cable por favor? He buscado y no encuentro nada en ninguna comunidad :S

Muchas gracias de antemano

---

### Post by Mauro22 on 2008-04-02
Hola y bienvenido!



Que version tienes de Ubuntu la de 32bits o la de 64bits??

Probaste con otro navegador como Opera? Eso descartaria firefox.

Tienes instalado JavaRuntime? no se si tiene algo que ver pero por las dudas---


:guitar:

---

### Post by chispachips on 2008-04-02
Tengo la versión de 32 bits. No probé con Opera, pero en otras instalaciones de el mismo Ubuntu siempre me fué bien :S , no sé por qué ahora no; Java sí lo tengo instalado porque uso Frostwire como cliente P2P que lo necesita.

---

### Post by PatoDB on 2008-04-02
Mira amigo a mi me pasaba algo similiar...

Los videos no se veian bien, o muchos directamente ni cargaban.

Pero el principal sintoma que tenia era que, cuando accedia a la pagina de Megaupload y queria poner password, arriba a la derecha, en vez de aparecerme un * por cada caracter, me aparecia el caracter limpio y visible...

Cuando le di clic con el derecho en la barra me aparecian opciones de Gnash (mas info aca [http://es.wikipedia.org/wiki/Gnash]("http://es.wikipedia.org/wiki/Gnash")

Fijate si al hacer click con el Derecho, te aparece el menu de Gnash, sobre los videos de YouTube, o sobre este lugar en la pagina de Megaupload que te comente (puedes hacer la prueba)

Si te aparece el menu de Gnash, entonces prueba desinstalarlo.

Yo lo desinstale... Realmente no recuerdo como, soy bastante novato en Ubuntu, pero creo que fue desde el Gestor de Paquetes de Synaptic. Una vez que lo logre desinstalar, mi maquina volvio a la normalidad


Fijate si es viable esta opcion, la verdad no estoy muy calificado para dar una respuesta, porque no conozco mucho, pero yo solucione mi problema de esa manera...


Espero que te sirva de algo

Exitos!!!

---

### Post by facundocorradini on 2008-04-02
Probablemente hayas instalado Gnash en lugar de Flash.

Gnash es un esfuerzo de GNU por hacer un plugin de flash libre, pero aún está medio verde como para poder con el streaming de video flash.

Te recomiendo desinstalas Gnash e instalar Flash.

---

### Post by User21 on 2008-04-03
**AUN MAS:** Te recomiendo incluso usar el FLASH desde la pagina de [Adobe]("http://www.adobe.com")! 
En mi caso particular, me funciona mucho mejor. 

**DISCLAIMER:** Todos aquellos que **odien** FLASH, favor de abstenerse de hacer comentarios! ¬_¬

---

### Post by chispachips on 2008-04-03
Carai, me parece impresionante la velocidad con la que me respondéis, os doi las gracias en ese aspecto ;) .

No tengo instalado Gnash, además de que me descargué el de Adobe tanto directamente desde el navegador (cuando entras dentro de una página y te dice que faltan plugins), como desde Synaptic a parte (reinstalándolo), o una vez más quitándolo e instalando uno bajado manualmente por mi desde Adobe, sin embargo desde un sitio u otro siempre da el mismo resultado.... no tengo ni idea de qué pasa xD

---

### Post by Hei Ku on 2008-04-03
podes probar arrancar el firefox desde consola, y fijarte si tira algun error en la consola cuando intentas ver los videos

---

### Post by chispachips on 2008-04-03
Tienes razón, voy a verlo, cuando lo tenga os lo digo ;)

**_Edito_**

Aquí traigo el nuevo informe jaja, al parecer no da ningún problema, simplemente al cargar la página de Youtube ya me aparece esto:

chispachips@mario-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

Eso desde que escribo [http://www.youtube.com](http://www.youtube.com) y entra, he probado con otras páginas web y mientras tanto todo permanece en blanco, no sé si será algún indicio.

**_Edito 2_**

Ya descubrí dónde está el problema, yo sabía que todo estaba bien instalado y en teoría debería de funcionar, pensé que no podía ser otra cosa que algo del refresco o bien del monitor o algo con la Nvidia, así que hice un sudo dpkg-reconfigure xserver-xorg y elegí el driver vesa, con toda la configuración de refresco de monitor como viene por defecto dándole a Aceptar a todo; y desde entonces los vídeos en Youtube ya iban fluidos y estupendos; así que pensé: alomejor cuando instalé el driver Nvidia se modificó el xorg, porque si no recuerdo mal me decía algo de que cambiaría su estructura. Así que volví a hacer un sudo dpkg-reconfigure xserver-xorg eligiendo Nvidia y con la misma tasa de refresco del monitor para comprobar si el fallo era del refresco o de la gráfica; y como comprobé los vídeos volvieron a lo mismo, teniendo el mismo refresco. El fallo está en la Nvidia entonces, pero lo que no entiendo aún es por qué en otras instalaciones de Ubuntu con la misma compilación de drivers y demás sí me funcionaba, pero ahora que recuerdo me parece que la otra vez lo hice por Envy, y esta vez los he instalado yo a mano con un archivo .run, así que voy a bajarme Envy y voy a instalar la Nvidia mediante dicho programa a ver qué sucede; el caso es dejar todo en las mismas condiciones que la otra vez.

**_Edito 3_**

Nada, ya lo hice por Envy y todo sigue igual... buff xD ¿Alguna idea tenéis? Jaja

---

### Post by faktorqm on 2008-04-04
hola, postea tu xorg.conf (entre tag de code por favor) asi lo vemos y analizamos que se puede cambiar. yo no tengo ese problema y creo que nadie de los que usa nvidia, sino nadie la usaria :P
y aparte de eso no te olvides de poner marca y modelo de tu monitor. salu2!

---

### Post by chispachips on 2008-04-04
Ah estupendo, es que no sabía lo de la opción del código ;) , pues ahí va:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Tarjeta de vídeo genérica"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"Monitor genérico"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Eso es, mi monitor es un Impression 7V , es un poco viejo ya y es de tubo, no lo veo ya en la página de Impression  y no encuentro su frecuencia de refresco para modificarla.. en fin, a ver si vosotros tenéis idea :KS

---

### Post by chispachips on 2008-04-06
Estoy intentando buscar a ver si encuentro el refresco de este monitor, quizás editándolo funcionase; pero debe de ser tan viejo que no lo veo por ninguna parte xD

---

### Post by Hei Ku on 2008-04-06
pregunta tonta, te fijaste en la parte de atras del monitor? los viejos traian en una etiqueta en la parte de atras los datos de refresco.

---

### Post by chispachips on 2008-04-07
jaja es verdad, traía una pegatina; lo único que ahí te dice los Hz que soporta y pone una pegatina aparte que pone August 1999 xDDD, madremía, un poco viejo ¿no? xD; en lo de los herzios pone que soporta de 50 a 60, pero no sé si eso se puede modificar en el xorg porque en Sistema>Preferencias>Resolución de la pantalla, solo me deja poner hasta 50 Hz; de todas formas no se si será lo de los herzios; yo me refería a lo de 	Horizsync 28-51 - Vertrefresh	43-60 ; eso no lo pone por detrás :S .. en fin, a ver qué opináis :) por lo menos sabemos los Hz que soporta y lo viejo que es jeje

---

### Post by faktorqm on 2008-04-07
Bueno imposible encontrar las especificaciones para tu monitor, asi que tuve que buscar otra cosa, y lo encontre, es una parte del .inf del driver para windows 98, que guarda todos los modos en el archivo de instalacion, por que usaban vxd y grp (creo) para manejar el video (por eso el virus que te daba vuelta la pantalla era tan facil de hacer) entonces copie la parte que es para tu modelo, y a partir de aca pasamos a probar a ver cual va mejor.

```

HKR,"MODES\720,400",Mode1,,"30.0-70.0,70.0,-,+"
HKR,"MODES\720,400",Mode1,,"30.0-70.0,88.0,-,-"
HKR,"MODES\640,480",Mode1,,"30.0-70.0,60.0,-,-"
HKR,"MODES\640,480",Mode1,,"30.0-70.0,67.0,-,-"
HKR,"MODES\640,480",Mode1,,"30.0-70.0,75.0,-,-"
HKR,"MODES\800,600",Mode1,,"30.0-70.0,60.0,-,-"
HKR,"MODES\800,600",Mode2,,"30.0-70.0,72.0,-,-"
HKR,"MODES\800,600",Mode2,,"30.0-70.0,75.0,+,+"
HKR,"MODES\832,624",Mode2,,"30.0-70.0,75.0,+,+"
HKR,"MODES\1024,768",Mode2,,"30.0-70.0,60.0,+,+"
HKR,"MODES\1024,768",Mode2,,"30.0-70,60.0,+,+"
HKR,"MODES\1024,768",Mode2,,"30.0-70.0,70.0,+,+"
HKR,"MODES\1024,768",Mode2,,"30.0-70.0,75.0,-,-"
HKR,"MODES\1024,768",Mode4,,"30.0-70.0,85.0,+,+"
HKR,"MODES\800,600",Mode4,,"30.0-70.0,85.0,+,+"
HKR,"MODES\1152,864",Mode4,,"30.0-70.0,75.0,-,-"
HKR,"MODES\1280,960",Mode4,,"30.0-70.0,60.0,-,-"
HKR,"MODES\1280,1024",Mode4,,"30.0-70.0,60.0,-,-"

```

Antes que nada, hacemos back-up del xorg.conf por si te desesperas y no encontras la solucion al nuevo:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_sano_y_salvo
```

Obvio que para restaurarlo tenes que escribir el mismo comando al reves ;)

Beueno, habiendo observado esto, vas a tu xorg.conf con ```
sudo gedit /etc/X11/xorg.conf
``` y en buscas la parte que te pego aca:

```

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

```

Entonces aca para probar vamos a poner donde dice Horizsync 30-70 y donde dice vertrefresh ponemos 60-90.
Ahora en la seccion "screen", en sub-seccion que dice "display" 24, agrega las resoluciones que tenias en windows, te tiene que quedar algo asi: (yo pongo de ejemplo, ojo!)

```

SubSection "Display"
		Depth	24
		Modes	"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection

```

Guardas los cambios y reinicias el servidor X apretando ctrl + alt + backspace y te fijas si podes cambiar la resolucion y esas cosas. sino podes lo vemos, pensa que estamos tocando de oido. Suerte y salu2!!

---

### Post by chispachips on 2008-04-07
Ya lo probé tal cual me dijiste, puse 30 - 70 y 60 - 90 , creo recordar que sí era ese el refresco correcto; yo me acordaba de 30 - 70. Ahora me deja elegir 50 Hz, 51, 52, 53, 54, 55, 56; lo tengo en 54 porque en 56 salen unas líneas y a 55 noto ligeramente un refresco más costoso, si te fijas mucho se aprecia, aunque a simple vista no parece que fuera mal pero por si acaso lo dejé en 54. Y en cuanto a los vídeos de Youtube siguen yendo igual :(, me extraña mucho, de todas formas descartaba el refresco del monitor porque con el driver vesa a igual refresco me iban bien los vídeos, pero con driver nvidia empiezan a hacer eso aunque tuviera el mismo refresco que en vesa; tiene que ser algo del driver pero no entiendo por qué ni dónde esta el fallo....

---

### Post by faktorqm on 2008-04-08
Proba de agregar esta seccion al xorg.conf DEJANDO TODO COMO ESTA AHORA:

```

Section "ServerFlags"
Option "Xinerama" "0"
EndSection

```

Otra pregunta, en windows te llega a 60hz? sino hay que estirar un cachito mas la vertical, el horizontal dejalo asi. 50-100 podria ser un buen valor para el vertical.

Si sigue igual, sin borrar lo que te puse arriba (las modificaciones son incrementales) podes agregar esto en la seccion screen:

```

Option "AddARGBGLXVisuals" "true"
Option "DisableGLXRootClipping" "true"

```

La parte de DRI en tu xorg.conf borrala, igual que la parte del tablet pc, si no tenes sacala por que es al cohete. EN LA SECCION MODULES, borra la ilnea de DRI.

Aparte de todo esto, tambien podes agregar a la seccion monitor esto:

```
Option "UseEdidFreqs" "false"
```

Bueno algo de todo esto o todo junto deberia funcionarte, o al menos vamos descartando problemas. Salu2!!

---

### Post by chispachips on 2008-04-08
He puesto todo lo que me has dicho y he ido probando a reiniciar el entorno gráfico en cada paso y nada... los vídeos siguen con ese refresco raro, bueno, los vídeos de youtube y otros vídeos flash online, porque cualquier otro vídeo del PC va bien fluido; también puse el refresco horizontal a 50 - 100 como me dijiste; todo va estupendamente igual que antes como si no hubiera pasado nada, pero no se porque eso sigue igual.. no se.. ¿quizás se pueda tocar algo de la configuración de Nvidia? En Aplicaciones>Herramientas del sistema tengo una cosa que pone Nvidia Settings, por si hubiera que tocar algo de ahí.

Este es mi xorg.conf ahora mismo:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Tarjeta de vídeo genérica"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"Monitor genérico"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	Option "AddARGBGLXVisuals" "true"
	Option "DisableGLXRootClipping" "true"
	Option "UseEdidFreqs" "false"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
Option "Xinerama" "0"
EndSection

Aquí he subido un vídeo para que veas exactamente lo que ocurre, y ya de paso te he enseñado la opción esa de Nvidia en el menú:

[Descarga]("http://www.rumboajapon.es/Archivos/video.tar.gz")

---

### Post by faktorqm on 2008-04-08
joya que solucionaste algunos problemas. ahora con lo del refresco para mi es un tema del flash propiamente, habiendo salvado todos los problemas de video primero. Ahh me olvidaba, saca esta parte de tu xorg.conf (borrala o comentala)

```

Section "DRI"
Mode 0666
EndSection

```

Bueno, que flash tenes? yo no se ni cual tengo :S creo que tengo el de la pagina de ellos, o sea el que te dan ellos para linux. ese lo probaste? mejora? y si no si tenes ese sacalo e instalate el

```
sudo apt-get install flashplugin-nonfree
```

ese creo que no lo use nunca. Y si incrementas el cache del firefox? probaste el firefox 3? el opera? el ie4lin? konqueror? capaz es del firefox, no se. Videos los ves bien que no sean flash? muchas preguntas perdon. salu2!!

---

### Post by chispachips on 2008-04-08
Estupendo, ya quité lo que me dijiste ;) . La versión de flash que tengo es la 9, esta me la bajé de la página oficial de Adobe; aunque he probado de mil formas, lo he hecho bajándolo "a mano", y luego metiéndolo yo en la carpeta de plugins; también lo he hecho por el mismo firefox cuando te dice que hay nuevos plugins disponibles, y también lo hice por Synaptic instalando el paquete que me has mencionado; pero nada... de una forma o de otra todo sigue igual. Todo flash que no sea un vídeo funciona muy bien, es simplemente ese refresco extraño en los vídeos flash, no solo pasa en youtube, también si quieres ver un vídeo online de Cálico Electrónico por ej o cualquier serie Flash; sin embargo cualquier vídeo que yo tenga por ahí en el ordenador funciona estupendamente. En cuanto a lo de la caché, no se ahora mismo cómo se hace lo de incrementarle, voy a mirar en las preferencias de Firefox, pero nunca se la tuve que incrementar en anteriores instalaciones :S ; probé a instalar Opera pero era un poco lioso instalar el flash; así que no le hice mucho caso... probaré con un navegador como dices o a aumentarle la caché a ver qué ocurre.

Yo deduzco que no puede ser culpa del flash, precisamente porque en el momento en que puse el driver vesa todo funcionó bien; el flash cumple su misión, pero debe de haber algo que falla... todo se cambia al activar el driver nvidia.

Por cierto, muchas gracias faktorqm, me estás ayudando muchísimo hasta ahora. Tenía muy seguro que la ayuda y el apoyo aquí la iba a encontrar, no me equivoqué ;)

---

### Post by Mauro22 on 2008-04-08
Disculpa si ya los haz contestado:

Probaste con otro S.O o con un livecd ??


:guitar:

---

### Post by chispachips on 2008-04-09
Jaja no te preocupes :p , sí, he probado porque tengo Windows XP compartido, además de que tuve en otra ocasión Ubuntu 7.10 y ese mismo también, el 7.04, lo que pasa que tuve anteriores problemas teniendo la 7.10 y me decidí por volver a la 7.04 que me parece más estable; pero siempre han ido bien los vídeos, es la primera vez que me pasa; todas las anteriores instalaciones siempre han sido en esta misma cpu y en las mismas condiciones.. no tengo ni idea de por qué ocurre entonces

---

### Post by faktorqm on 2008-04-09
Y probaste de reinstalar? o no podes? salu2!

---

### Post by chispachips on 2008-04-11
Hombre.. reinstalar es lo último que queda para todo, sea un problema grande o pequeño; a veces me da rabia que en Windows se pueda arreglar un problema sin tener que reinstalar en el 95% de los casos, en Ubuntu es más común hacerlo; pero sé que si me quito este problema reinstalando me va a salir otro peor jaja, y tal vez me quiera engañar a mi mismo de que no lo sea pero yo quiero que Ubuntu se convierta en un sistema operativo estable del que no haya que estar reinstalando una y otra vez, por eso consulto cualquier problema mínimo para saber tocarlo y así si le ocurre a una persona a la que yo le haya instalado y confiado Ubuntu yo pueda ofrecerle el soporte que necesite, que es gracias a esto lo que ayuda a crecer a usuarios de Ubuntu en número y gracias a la ayuda de cualquier persona el uso de este sistema operativo se incrementa día a día; si no, esta persona seguramente volvería a Windows; así que es mi forma de colaborar con el proyecto ;) , yo resisistiré para siempre porque Ubuntu es lo mejor con lo que me he encontrado y quiero regalárselo a todo el mundo, al igual que quiero regalarle mi ayuda y mi soporte :p .

Después de todo, este problema no es nada, y ya que tengo todo establecido y bien de nuevo en esta instalación no me gustaría reinstalar.. Como era una cosa un poco tonta no me importa quedarme con ello, pero por si acaso venía por si a alguien le ocurrió o sabía ;) .

Entonces jeje, con respecto al problema nos hemos quedado sin cartas; ya veré a ver qué se me ocurre; sin embargo digo una vez más que me ha sorprendido el modo activo de esta comunidad y siempre que necesite algo acudiré a ella porque me ha dado lo que no lo ha hecho la de España :D , estoy muy contento con todos vosotros (en la vida rellenaría un tópico con 3 páginas en Ubuntu-es xD, no te hacen ni caso...). Muchas gracias :p :guitar:

---

### Post by firepic on 2008-06-12
Saludos a todos!
En primer lugar gracias por este foro tan excelente! :)
Bueno les cuento mi problemilla, he instalado el plugin de flash non-free y todo eso... pero tampoco puedo ver los videos de youtube en el explorador mozilla... es decir, cuando le doy click a un video, sale el reproductor y pareciera que todo estuviera bien, pero el video (cualquiera) siempre se detiene a los 2 segundos (00:02)... y no hay forma de que siga con la reproducción..
Tengo tambien instalados los gstreamer ugly, bad y good, que según leí por ahí también se necesitan...
Pero nada... tienen idea de qué puede estar pasando?
Por cierto, la versión que tengo es el Ubuntu hardy heron 8.04 de 64bits.
Antes logré que se vieran perfecto los videos de youtube (ni sé cómo lo hice)... pero tuve que formatear y ahora no sé qué hacer... :confused:
Ok desde ya les agradezco su ayuda, nos leemos!

---

### Post by sebaxxxtian on 2008-06-15
> **firepic said:**
> Saludos a todos!
En primer lugar gracias por este foro tan excelente! :)
Bueno les cuento mi problemilla, he instalado el plugin de flash non-free y todo eso... pero tampoco puedo ver los videos de youtube en el explorador mozilla... es decir, cuando le doy click a un video, sale el reproductor y pareciera que todo estuviera bien, pero el video (cualquiera) siempre se detiene a los 2 segundos (00:02)... y no hay forma de que siga con la reproducción..
Tengo tambien instalados los gstreamer ugly, bad y good, que según leí por ahí también se necesitan...
Pero nada... tienen idea de qué puede estar pasando?
Por cierto, la versión que tengo es el Ubuntu hardy heron 8.04 de 64bits.
Antes logré que se vieran perfecto los videos de youtube (ni sé cómo lo hice)... pero tuve que formatear y ahora no sé qué hacer... :confused:
Ok desde ya les agradezco su ayuda, nos leemos!

a mi tambien me pasa lo mismo

:(

---

### Post by firepic on 2008-06-19
Felizmente he podido resolver mi problema, olvidé comentarlo...
Lo que hice fue desinstalar el plugin y todos los gstreamer bad, ugly good... luego volví a instalar los gstreamer... y entonces cuando me metí en la página de youtube me salío el mensaje que dice "necesita plugins adicionales para ver el contenido de esta página"... seleccioné instalar el flash y listo... cuando reinicié el explorador ya podía ver los videos bien..
Tengo que mencionar que al día siguiente volví a tener el mismo problema que antes, entonces me fuí a synaptic y en el paquete de flash-non-free le dí "reinstalar"... y se acomodó el problema.
Ok saludos, nos leemos!

---

