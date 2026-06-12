---
title: "Como instalar Adobe Photoshop CS2 en Ubuntu en 8 pasos!"
date: 2007-02-12
forum: Software
---

### Post by QUASAR_FREAK on 2007-02-12
Esta guía cubre la instalación de Adobe Photoshop CS2 en Ubuntu en 8 simples pasos. Este método solo fue probado en Ubuntu pero debería funcionar en cualquier otra Distro de Linux.

- Ke necesitamos?[LIST]
[*]Ubuntu =)
[*]Una instalación de Windows con Adobe Photoshop CS2 ya activado.[/LIST]- Levantemos una terminal y ejekutemos:
 **Nota: **En lugar de usar la terminal podemos buskar los paketes con synaptic.[LIST]
[*]**$ sudo apt-get update**
[*]**$ sudo apt-get install wine**
[*]**$ winecfg**     /*Para krear la estructura de directorios wine*/[/LIST]- Ahora copiamos los archivos necesarios desde la instalacion de box;[LIST]
[*]Copia toda la carpeta de Adobe de **&#8220;c:\Program Files\**&#8221; a &#8220;**/home/TUUSUARIO/.wine/drive_c/Program Files/&#8221;**[/LIST]- Ahora exportamos las llaves de Adobe del registro de Windows;[LIST]
[*]En Windows, ejecutemos **&#8220;regedit&#8221;** y exportemos **&#8220;HKEY_LOCAL_MACHINE/Software/Adobe/&#8221;** a **&#8220;adobe.reg&#8221;**.
[*]El próximo paso es copiar este archivo a Ubuntu y agregarlo al registro de wine, esto lo hacemos tipeando **&#8220;$ sudo wine regedit adobe.reg&#8221; **para importarlo a wine.
[*]Listo! ejekutemoslo con **&#8220;$ sudo wine &#8211;winver winxp &#8220;[Path del Photoshop/photoshop.exe&#8221; **o crea un acceso directo y disfruta de Adobe Photoshop CS2 en Ubuntu [IMG]http://www.prysmax.com/forum/images/smilies/set1/thumbup1.gif[/IMG][/LIST]Guía original en: [http://blog.publicidadpixelada.com/h...untu-10-steps/]("http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/")

---

### Post by BlackHero on 2007-02-12
buena quasar =) gracias por el aporte

---

### Post by DuckMan on 2007-02-12
funciona al 100% ????? =OOOOOOOOO

---

### Post by screening on 2007-02-12
Bien ahi, lo subo a mi blog (con la fuente OBVIO)
gracias!

---

### Post by MeduZa on 2007-02-12
hago un paso mas para los que tengan problemas al ejecutarlo:

en el xorg.conf tienen que quitar esto:
> Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

de lo contrario les aparecera un error cuando arranca el adobe, eso es para cualquier vercion

Saludos ;)

---

### Post by lavaramano on 2007-02-13
> **MeduZa said:**
> hago un paso mas para los que tengan problemas al ejecutarlo:

en el xorg.conf tienen que quitar esto:
de lo contrario les aparecera un error cuando arranca el adobe, eso es para cualquier vercion

Saludos ;)

buenisimo esto que aclaras.
porque yo lo intente varias veces en varias pcs y siempre me pasaba eso. una cagada.
voy a ver si lo pruebo eso hoy

---

### Post by beuno on 2007-02-13
Quasar, si funciona (aka, si lo hace funcionar Mauro) te ganaste una remera de kbglob.

---

### Post by QUASAR_FREAK on 2007-02-13
josha. a mi no me anduvo, me tira
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!

Para reencodear el adobe.reg use wine notepad adobe.reg y lo salve de nuevo.

---

### Post by MeduZa on 2007-02-13
> **beuno said:**
> Quasar, si funciona (aka, si lo hace funcionar Mauro) te ganaste una remera de kbglob.

yo lo hice andar mucho antes y no me gane nada :(
jajajja de todas maneras hacermela llegar te costaria mas que regalarme 10 ^_^

tambien hice nadar otros programas (juegos, adobe audition, winamp, emule plus, y varios mas)

solo hago eso para los que dicen que no me andan las cosas yo le digo.. si mira andan pero uso uno mejor que es gratis :)

---

### Post by beuno on 2007-02-13
> **MeduZa said:**
> yo lo hice andar mucho antes y no me gane nada :(
jajajja de todas maneras hacermela llegar te costaria mas que regalarme 10 ^_^

tambien hice nadar otros programas (juegos, adobe audition, winamp, emule plus, y varios mas)

solo hago eso para los que dicen que no me andan las cosas yo le digo.. si mira andan pero uso uno mejor que es gratis :)

Va para vos tambien entonces.
Lo unico que quiero son pasos repetibles en todas las PCs que lo hagan funcionar, y que tenga una performance aceptable.
Asi los diseñadores empiezan a ir a Linux tambien...

---

### Post by lavaramano on 2007-02-13
no los veo a los diseñadores en linux, y no porque los odie o algo.
sino porque tenes al flash, al dweaver, bla bla bla. la clasica excusa del usuario de windows.

ahora, si lo logras te ganaste un grano de cafe (?)
y si lo lograste por la fuerza.. yo te diria que te consigas un papa movil o algo parecido.

---

### Post by jajajavi on 2007-02-14
> **QUASAR_FREAK said:**
> 
[LIST]
[*]**$ sudo apt-get update**
[*]**$ sudo apt-get install wine**
[*]**$ winecfg**     /*Para krear la estructura de directorios wine*/[/LIST]


y resulta que:
```
javi@amd64javi:~$ winecfg
/usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)

```

hace tiempo que quiero hacer andar el wine en mi amd64 y siempre me falta algo...
igualmente le hago el aguante al gimp, mientras que inkscape y scribbus no tienen mucho que envidiarle al illustrator o quarkxpress. acá hay un diseñador gráfico migrando hacia la libertad, y como dijo r2d2 jauretche "no es cuestión de cambiar de collar, sino de dejar de ser perro"

---

### Post by lavaramano on 2007-02-14
@jajajavi: proba con 'sudo aptitude install glibc'.
y sino [http://pacogp.wordpress.com/2006/11/21/wine-para-amd64/](http://pacogp.wordpress.com/2006/11/21/wine-para-amd64/) ya esta empaquetado en un .deb

saludous

---

### Post by undiaperfecto on 2007-02-14
a mi me pasa lo mismo, pero yo tengo un intel celeron.
va en realidad no se si es lo mismo, cuando trato de instalar wine en synaptic, me sale No se pudieron instalar todos los paquetes para instalacion o actualizacion, y desde terminal me tira un error similar.
creo que el wine no quiere ser mi amigo,

---

### Post by Nemesis Teufel on 2007-02-14
> **lavaramano said:**
> no los veo a los diseñadores en linux, y no porque los odie o algo.
sino porque tenes al flash, al dweaver, bla bla bla. la clasica excusa del usuario de windows.

Tambien pueden ser diseniadores graficos o industriales que no tienen xq usar la suite d macromedia. 
Hablando de dise. industr:  me imagino que es lo mismo para Ilustrator..no?


Yo tenia un problema para hacer cargar el PS CS2, no me contraba la carpeta con el regedit.exe o algo asi.. no me acuerdo bien, en una semana podre sentir mi pc nuevamente y ahi comento que es lo que me pasa.

---

### Post by MeduZa on 2007-02-15
> **beuno said:**
> Va para vos tambien entonces.
Lo unico que quiero son pasos repetibles en todas las PCs que lo hagan funcionar, y que tenga una performance aceptable.
Asi los diseñadores empiezan a ir a Linux tambien...

el adobe 6.0 y 7.0 andan perfecto solo que cuando seleccionas un area el recuadro no se ve pero es solo cuando estas haciendo la seleccion, ya que cuando esta echa se ve bien no se que sera. Agrego algo: cuando quiten eso del xorg.conf recuerden quitar tambien el acceso en serverlayout:

> Section "ServerLayout"
	Identifier "TwinView Configuration"
	Screen 0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents" quiten esta
	InputDevice     "cursor" "SendCoreEvents" esta y
	InputDevice     "eraser" "SendCoreEvents" esta
EndSection

si no hacen eso lo mas seguro es que el X no les arranque

Saludos

---

### Post by jajajavi on 2007-02-16
> **lavaramano said:**
> @jajajavi: proba con 'sudo aptitude install glibc'.
y sino [http://pacogp.wordpress.com/2006/11/21/wine-para-amd64/](http://pacogp.wordpress.com/2006/11/21/wine-para-amd64/) ya esta empaquetado en un .deb

me dice:
[COLOR="Olive"]No se pudo encontrar el paquete "glibc". Sin embargo,
"glibc" aparece en el nombre de los siguientes paquetes:
  glibc-pic glibc-2.3.5-0ubuntu1 devhelp-book-glibc glibc-doc
No se instalará, actualizará o eliminará ningún paquete.
[/COLOR]
y también [COLOR="Olive"]You have to configure "localepurge"[/COLOR] qué es localpurge?

por otro lado, tengo una versión wine posterior al empaquetado que me sugerís, la bajé de ese mismo blog hace un tiempo.
tengo dapper 6.06. estaré haciendo algo mal? muchas gracias de todos modos (y por ahora el gimp se la rebanca...)

---

### Post by jajajavi on 2007-03-05
actualicé a edgy y anda wine, pero al intentar instalar el photoshop me pasa esto:

```
javi@amd64javi:~$ sudo wine –winver winxp “\home\javi\.wine\dive_c\Program Files\Adobe\Photoshop CS\photoshop.exe"
wine: could not load L"c:\\windows\\system32\\\00e2\0080\0093winver.exe": Module not found

```

¿qué estoy haciendo mal?

---

### Post by QUASAR_FREAK on 2007-03-05
fijate en los komentarios de la guía original, ahi dice como safar de esa del winver.

---

### Post by lucasordonez on 2008-03-19
quasar_freak una pregunta..
ya exporté al nombre adobe.reg, pero nosé donde guardarlo, lo guarde en varios lados pero me dice > regedit: File not found "adobe.reg" (2)
lo pase al home y no pasa nada me pide que tire otro comando ...
nosé a dnd mandarlo para que luego lo exporte al wine ..
y en la carpeta de adobe tengo instalado el premiere, el illus y el photoshop, será ese un problema? aunque no creo, porque todavia ni lo transferí.
gracias, igual el aporte es de 25!

---

### Post by QUASAR_FREAK on 2008-03-19
ya no deberia hacer falta esto, el thread es bastante viejo, gracias a la ayuda de google en wine ya se puede instalar el photoshop cs2 sin vueltas y se esta trabajando para el soporte del cs3.

Fijate de tener la ultima version de wine instalada y usar estos repos:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

Para info sobre adobe cs3 en wine:
[http://jonramvi.wordpress.com/2008/03/11/62/](http://jonramvi.wordpress.com/2008/03/11/62/)

Para mas info sobre wine:
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by lucasordonez on 2008-03-19
thnks

---

### Post by QUASAR_FREAK on 2008-03-19
no entiendo el " en mi opinion ni vos sabias como se hacia .." pero pasando eso por alto y que el thread es del 2006 intento explicarte nuevamente.

En lugar de hacer estos 8 pasos, si tenes la version de wine 0.9.57 (obtenes la version ejecutando en consola: wine --version) lo unico que tenes que hacer es montar el cd de adobe photoshop cs2 y hacer un wine setup.exe, seguir la instalacion como si estuvieses en windows y al final encontraras los accesos directos dentro del menu aplicaciones -> Wine -> Programas-> Adobe Photoshop CS2.

Eso que parece un ftp es el repositorio de wine para ubuntu gutsy.

Me alegro que hallas encontrado esta guia en varios idiomas, eso significa que sabes usar google =)

Ni idea porque tanto rencor man pero bue dejame decirte que si en lugar de perder el tiempo rompiendo el CoC lo invertis leyendo no solo dejaras de ser principiante sino que ademas vas a tener tu adobe photoshop`instalado.

Suerte!

---

### Post by facundocorradini on 2008-03-19
Che, actualizencé.

**Photoshop CS2 ya anda a la perfección en Wine, **sin necesidad de hacer ningun malabar. 


Doble click al instalador y listo. 


Lo mismo para Fireworks, Dreamweaver y Flash. 

Todos andan 100% bien

---

### Post by User21 on 2008-03-20
ASI ES:
Tengo Photoshop CS2 funcionando muy bien en wine-0.9.57, con un escritorio virtual.
Aunque me re acostumbré con el GIMP! xD

---

### Post by Aradnix on 2008-07-08
Hola:

   He visto que es posible añadir Photoshop CS2 y correrlo en ubuntu, peor tengo dudas al respecto. No sé si solo sea posible con esa versión, es decir, ¿con CS o CS3 no se puede? y por otra parte algo más importante, que hay si quiero trabajar no sólo con Photoshop sino con Illustrator o InDesign además, ¿es posible instalar no solo Photoshop sino la CS2 completa? ¿Alguien sabe como o lo ha intentado?

Saludos:
Aradnix

---

### Post by Dravish on 2010-01-04
> **QUASAR_FREAK said:**
> Esta guía cubre la instalación de Adobe Photoshop CS2 en Ubuntu en 8 simples pasos. Este método solo fue probado en Ubuntu pero debería funcionar en cualquier otra Distro de Linux.[U]
...[/U]

Gracias por compartir esto con todos, acabo de instalar ubuntu 9.10 y precisamente buscaba esto, lo único que me da un error curioso, al abrir el photoshop cs2 me dice:
"Falta el nombre de usuario, la organización o el número de serie de adobe photoshop, o no son validos. La aplicación no puede continuar y se cerrará".

Pero he seguido todos los pasos que explicas no sé como solucionarlo.

¿Podrían echarme una mano?, gracias.

---

### Post by Aradnix on 2010-01-04
Hoal:

Pues mira, como ves la tecnología ha avanzado y uno de los requisitos es que tengas la ultima versión de Wine. Ahora bien también depende de que versión de Photoshop estés hablando se que es la CS2 pero no se si requieras de un serial algo así. Si fueses más descriptivo en lo que hiciste sería más fácil la ayuda, decir que hiciste todo tal cual el tutorial no es muy elocuente.

Saludos y suerte:
Aradnix

---

### Post by Dravish on 2010-01-05
> **Aradnix said:**
> Hoal:

Pues mira, como ves la tecnología ha avanzado y uno de los requisitos es que tengas la ultima versión de Wine. Ahora bien también depende de que versión de Photoshop estés hablando se que es la CS2 pero no se si requieras de un serial algo así. Si fueses más descriptivo en lo que hiciste sería más fácil la ayuda, decir que hiciste todo tal cual el tutorial no es muy elocuente.

Saludos y suerte:
Aradnix

Bueno, gracias por contestar, pero al final lo pude solucionar, eliminé la carpeta que copié de la particion de windows y lo instalé de cero con el wine, la cosa funcionó como la seda, ya no hace falta hacer los 8 pasos ni tener una instalación de windows, el mismo wine ya lo recoge e instala a la perfección.

De todas formas gracias y feliz año entrante.

---

### Post by phsilver on 2010-09-27
Hola..
Les cuento lo que me paso a mi, quizas alguien sepa a que se debe..

Instale Dreamweaver 8 sin problemas y anda perfecto!
Instale el Photoshop CS2 sin problemas pero cuando lo quiero correr me dice que mi cuenta no tiene los privilegios suficientes, que ingrese desde otra cuenta con privilegios...

El tema es que hay una sola cuenta creada: la mia!!!!

Todavia no probe con illustrator y flash, con el flash va a haber lío porque si estas trabajando con CS4, los archivos no los podes abrir con versiones anteriores...
Saludos.!

---

