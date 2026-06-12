---
title: "Xubuntu muy lento."
date: 2009-01-30
forum: Software
---

### Post by Hadso on 2009-01-30
Hola tengo una notebook con 500 de ram, 40gb de disco (para el xubuntu) y un procesador AMD 1.2. Tengo el xubuntu 8.10.
Instalé esta distro porque quería probar uan verdaderamente rápida y que tenga todas las posibilidades que linux pueda ofrecer. 
No me quejo de ella, pero es mas lenta que win xp. Tarda mas en bootear, en lanzar los programas, en hacer aparecer los menúes, etc. 

Que estoy haciendo mal? Como puedo revertirlo? 

Gracias!

---

### Post by guillermolisi on 2009-01-30
> **Hadso said:**
> Hola tengo una notebook con 500 de ram, 40gb de disco (para el xubuntu) y un procesador AMD 1.2. Tengo el xubuntu 8.10.
Instalé esta distro porque quería probar uan verdaderamente rápida y que tenga todas las posibilidades que linux pueda ofrecer. 
No me quejo de ella, pero es mas lenta que win xp. Tarda mas en bootear, en lanzar los programas, en hacer aparecer los menúes, etc. 

Que estoy haciendo mal? Como puedo revertirlo? 

Gracias!
Y sobre la placa de video que podes decirnos ?

---

### Post by gmunioz on 2009-01-30
Hola had....:
Estas comparando un sistema operativo del año 2001 con otro del año 2008.
Para que la perfomance sea pareja, deberías comparar Windows XP con Debian Sarge o Xubuntu con Vista.
Ahora ese operativo de Microsoft que dices es más rápido que Xubuntu, ¿tiene corriendo antivirus, antispyware, firewall, etc. etc.?
Si quieres mejorar la perfomance de tu ordenador, reemplaza xcfce por lxde, que esta en los repositorios y solo usa 50 megas de ram o por fluxbox, con este último, que requiere bastante uso del editor de texto para configurarlo, tu ordenador no correrá volará.
O prueba la variante de puppy, gallipup que no requiere configuración manual y esta preparada tambien para hacer volar los ordenadores algo antiguos.
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu** -* 22 Mad Jaunty User*

---

### Post by sartrejp on 2009-01-31
Pero con 500 mb de ram hasta ubuntu debería andar en forma decente. Mucho más xubuntu.

---

### Post by Hadso on 2009-01-31
El win tiene un antivirus corriendo y programas nuevos, como el chrome, juegos como el NFS etc. Nunca tuve un problema. 
He probado otras disros minimalistas de Linux, pero prefiero esta a pesar de mis quejas :D.
Ademas, podría instalar un flux, pero por lo que mas dicho, no tengo los conocimientos requeridos como para configurarlo.

Como reemplado xfce por lxde? Es bueno este último? Estoy muy conforme con el xfce. Es recomendable cambiarlo?

Por ultimo, quiero agregar que el detalle de este problema es que de mis casi 500 de ram, el 65% está siendo consumido permanentemente. En el foro en ingles me dijeron que es porque tengo doble booteo.
Puede ser este el inconveniente?
Gracias!

---

### Post by Hei Ku on 2009-01-31
No, el doble booteo no tiene nada que ver.

---

### Post by Hadso on 2009-01-31
Si, es ílogico que ocupe RAM. Pero, que es lo que me hace usar el 65% de mi memoria ram y que por ende hace que funcione tan lento. Puede haber otra cosa que también haga que corra lento? Hay alguna configuración en particular?

Gracias!

---

### Post by Hei Ku on 2009-01-31
El video, la velocidad de disco y la RAM es lo mas importante.
Ahora, Linux en general consume toda la memoria que tenga disponible, para optimizar. El tema es cuanto de eso es optimizacion y cuanto es un programa que se morfa memoria de mas. Notas que escribe o lee mucho del disco rigido?

---

### Post by Hadso on 2009-01-31
Si, ahora que me doy cuenta me parece que sí.

---

### Post by Hei Ku on 2009-01-31
Pone en una terminal top, y fijate que programa es el mas pesadito.

No usaras Firefox con Flash por casualidad?

---

### Post by gmunioz on 2009-01-31
Hola had...:
Lxde, esta en los repositorios, simplemente lo marcas desde synaptic y te marcará todo lo necesario.
Luego al reiniciar, antes de ingresar tu nombre de usuario, pulsas en la pantalla abajo a la izquierda opciones y en sesión eliges lxde.

Respecto de fluxbox, solo requiere tiempo y paciencia.
Aqui hay un tutorial muy bueno:
[http://foros.ubuntu-cl.org/viewtopic.php?t=3171](http://foros.ubuntu-cl.org/viewtopic.php?t=3171)

El hecho de tener instalados, xfce, lxde, fluxbox, etc. etc. no influyen en el rendimiento del ordenador, solo ocupan espacio, muy poco espacio en el caso de lxde y fluxbox.

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu **-* 22 Mad Jaunty User*

---

### Post by guillermolisi on 2009-01-31
Coincido en que la salida del Top hara que se pueda trabajar sobre datos concretos, no en el aire.

Y aun falta algun dato tecnico sobre la placa de video, pero solo como algo complementario.

---

### Post by Hadso on 2009-01-31
Si, uso Firefox y es lo mas pesado que me aparece en cuanto a ram. En cuanto a uso de la PC, es el Xorg. 
Conviene cambiar a otro navegador?

Aún así todo el booteo tarda mucho y ademas, ver imágenes, abrir el dophin, la consola o lo que sea tarda mas que en WinXP.

Gracias

---

### Post by Hadso on 2009-01-31
Hola. Voy a probar el tutorial que me has sugerido. De todas maneras, no puedo entrar a synaptic porque me dice que necesito privilegios de sudo. El tema es que es la unica aplicacion que me hace problema con eso, porque  las demas, me piden la contraseña y listo. En cambio synaptic dice que todos los cambios que haga no surtiran efectos. 

Nuevamente, gracias por el consejo. Trataré de aprender el flux, como debo hacer para bajarlo a mi notebook? Es decir, pasar este problema con el synaptic.
Gracias!!

---

### Post by Hei Ku on 2009-01-31
cuando abris synaptic te pide tu contraseña, para elevar los privilegios. Pone tu contraseña y ya esta.

---

### Post by Hadso on 2009-01-31
No me la pide. Me dice:

Starting without administrative privileges

You will not be able to apply any changes. But you can still export the marked changes or create a download script for them.


Pero de ahí no paso. En cambio con los demas programas si, me la piden y listo. Como tengo que hacer?

---

### Post by sartrejp on 2009-01-31
presioná Alt+F2 y ahí poné sudo synaptic
o desde la consola poné lo mismo.
que raro que no pida la contraseña...

---

### Post by Hadso on 2009-01-31
Gracias. Desde la consola pude abrir el synaptic sin problemas, nisiquiera me pidio la contraseña. 
Ahora bien, una vez seleccionados los archivos que quise instalar, luego de tratar de bajarlos infructuosamente, apareció este mensaje repetido como error en cada archivo:

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/universe/a/alltray/alltray_0.69-1ubuntu2_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/universe/a/alltray/alltray_0.69-1ubuntu2_i386.deb)
  Could not connect to es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

Gracias.

PD: También tengo problemas para bajar unos dirvers de video desde la consola. Gracias.

---

### Post by Hei Ku on 2009-01-31
Esta fallando el repositorio .es de ubuntu.

Lo más facil para seguir sería cambiar los repositorios al internacional, pero depende de la confianza que te tengas.

sudo nano /etc/apt/sources.list

todo lo que dice es.archive. (etc)
tenes que cambiarlo a en.archive

grabar, enjuagar y repetir. :D

---

### Post by Hadso on 2009-01-31
Edité como dijiste, pero cuando entro a synaptic no me abre el archivo. Como lo puedo hacer?

Gracias!

---

### Post by gmunioz on 2009-01-31
Hola had...:
Este es el contenido de mi sources.list en el ordenador con Intrepid, ve que el tuyo tenga algo similar, elimina las líneas restantes.

[B]Estos son recomendables para los usuarios comunes:
[/B]
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted

Estos son riesgosos **no aconsejables** para usuarios comunes

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main multiverse restricted
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb [http://ppa.launchpad.net/lidaobing/ubuntu](http://ppa.launchpad.net/lidaobing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/lidaobing/ubuntu](http://ppa.launchpad.net/lidaobing/ubuntu) intrepid main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) intrepid main

Si no tienes Intrepid, cambia intrepid por lo que corresponda.
Saludos. 
Gabriel.
**Solo doy soporte para Ubuntu** *22 Mad Jauntu User*

---

### Post by Tobi-fp on 2009-01-31
> **Hadso said:**
> Hola tengo una notebook con 500 de ram, 40gb de disco (para el xubuntu) y un procesador AMD 1.2. Tengo el xubuntu 8.10.
Instalé esta distro porque quería probar uan verdaderamente rápida y que tenga todas las posibilidades que linux pueda ofrecer. 
No me quejo de ella, pero es mas lenta que win xp. Tarda mas en bootear, en lanzar los programas, en hacer aparecer los menúes, etc. 

Que estoy haciendo mal? Como puedo revertirlo? 

Gracias!
Usas compiz?
Unas placas de video no anda bien con compiz.

Ponga en una terminal:
~: metacity --replace

---

### Post by Hadso on 2009-01-31
Gabriel, el tema es que desde el synaptic, al seleccionar el archivo /etc/apt/sources.list no lo abrió, no hizo nada. 
Ahora tampoco puedo abrir synaptic, porque me da el siguiente error:

(synaptic:6355): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed


No puedo bajar el Flux y todo lo necesario como para ponerme a empezar.

---

### Post by sartrejp on 2009-01-31
Aunque no se decirte cual es el problema, dudo que sea el xfce o thunar, por lo que no creo que se solucione instalando fluxbox, vas a ganar espacio y velocidad, pero igual hay algo que está fallando.
No te dio ningún error en ningún momento al instalarlo?

---

### Post by Hei Ku on 2009-01-31
Vamos por partes.


En una terminal, pone:

sudo apt-get update

Despues pones tu contraseña y contame si te sale algun error.

Y dejen de marearlo, che. Vamos por partes.

---

### Post by Hadso on 2009-01-31
Gracias. Ya pude bajar el Flux. Ahora estoy tratando de condigurarlo. Pero me faltan los archivos. Estoy averiguando como resolverlos. 
Existe algun buen tutorial de Flux que me recomienden?
Gracias!

---

### Post by gmunioz on 2009-01-31
Hola had...:

Edita el archivo /etc/hosts
ejecuta en consola:

sudo leafpad /etc/hosts

Este debe tener un contenido similar al siguiente:



127.0.0.1	localhost
**127.0.1.1	hadso-desktop,redhadso**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Debes eliminar el nombre de dominio que se agrega a continuación del nombre del equipo, para que quede asi:

127.0.0.1	localhost
**127.0.1.1	hadso-desktop**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Utiliza el nombre de tu equipo, a los otros datos que se encuentran por debajo no les prestes atención, ya que en este momento estoy corriendo Jaunty y puede que se diferencien de los de tu distro.

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - Existen muchas soluciones,** *las equivocadas y la mia.*

---

### Post by gmunioz on 2009-01-31
Hola had...:

Aqui uno resumido que hace tiempo postee en ubuntu-es:

Fluxbox es un administrador de ventanas que corre sobre Xorg y se encuentra en los repositorios de Ubuntu.
Como características de importancia tiene:
- Pestañas configurables
- Barra de iconos
- Movimiento por los escritorios con la rueda del ratón
- Títulos de las ventanas configurables
- Soporte para Gnome y Kde
- Combinaciones de teclas configurables
- Disponibilidad de canal alpha (transparencias)
Para iniciar con FluxBox, una vez instalado, se reinician las X (control - alt - retroceso) y se elige -> cambiar sesión ->fluxbox

Uso

El uso de Fluxbox es muy sencillo, no existen los iconos, y se accede al menú de aplicaciones pulsando con el botón derecho en el fondo del escritorio, entonces aparece el menú de aplicaciones genérico del sistema, pulsando con el botón central aparece el menú de escritorios, donde se visualizan los escritorios activos.

Toolbar es la barra inferior o superior, lateral o central. que muestra el escritorio, las aplicaciones y un reloj. Pulsando sobre el nombre del escritorio o el reloj se accede a un menú de configuración de la barra. Si se lo hace sobre las aplicaciones se obtiene un menú contextual sobre el manejo de la ventana de la aplicación.

Las pestañas (tabs) estan integradas en el 'titlebar' de la ventana. Para agrupar dos ventanas, pulsamos con el botón del medio en el 'titlebar' de una ventana y la arrastramos hacia la que queremos agrupar. Para desagrupar, realizamos la operación inversa. Pulsando sobre el 'titlebar' obtenemos el menú contextual de la aplicación.


Configuración

En el directorio /home/usuario/ se encuentra el directorio .fluxbox, donde están los distintos archivos de configuración.

.fluxbox/menu, este archivo, contiene el menu que aparece al pulsar el botón derecho del ratón, con las aplicaciones favoritas, que se pueden ordenar en secciones y subsecciones.

El archivo a editar es /home/usuario/.fluxbox/menu

Su estructura es lineal, se ordena por secciones y subsecciones y consiste en:

[ tipo de comando]
(nombre a ver)
{comando a ejecutar y ruta}

Por ejemplo:

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[exec] (Terminal) {xfce4-terminal}
[exec] (Firefox) {firefox}
[exec] (Terminal root) {gksu xfce4-terminal}
[exec] (Ejecutar) {fbrun}
[separator]
[submenu] (Accesorios) {}
[exec] (Administrador de archivos) {thunar}
[exec] (Mousepad) {mousepad}
[exec] (Gedit) {gedit}
[exec] (Commander) {gnome-commander}
[exec] (Calculadora) {gcalctool}
[end]
[submenu] (Multimedia) {}
[exec] (Audacity) {audacity}
[exec] (Media Player) {vlc}
[exec] (RipperX) {ripperx}
[exec] (Gxine) {gxine}
[exec] (Audacious) {audacius %U}
[exec] (Nero) {nero}
[end]
[submenu] (Gráficos) {}
[exec] (Gimp) {gimp}
[exec] (Gpaint) {gpaint}
[exec] (Inkscape) {inkscape}
[exec] (GQview) {gqview}
[exec] (Draw) {oodraw}
[end]
[submenu] (Oficina) {}
[exec] (AbiWord) {abiword}
[exec] (Write) {oowriter}
[exec] (Calc) {oocalc}
[exec] (Base) {oobase}
[exec] (Impress) {ooimpress}
[exec] (Math) {oomath}
[exec] (Xchm) {xchm}
[exec] (Adobe Reader) {acroread}
[end]
[submenu] (Soft Windows) {}
[exec] (Instalar) {/home/usuario/cxoffice/bin/./cxinstallwizard}
[exec] (Ejecutar) {/home/usuario/cxoffice/bin/./cxrun}
[exec] (MS-Word) {/home/usuario/cxoffice/bin/./winword}
[exec] (MS-Excel) {/home/usuario/cxoffice/bin/./excel}
[exec] (MS-Access) {/home/usuario/cxoffice/bin/./msaccess}
[exec] (MS-P-Point) {/home/gm/cxoffice/bin/./powerpnt}
[end]
[submenu] (Internet) {}
[exec] (Gnome-PPP) {gnome-ppp}
[exec] (Firefox) {firefox}
[exec] (Thunderbird) {thunderbird}
[exec] (aMSN) {amsn}
[exec] (Gaim) {gaim}
[end]
[submenu] (Sistema) {}
[exec] (Synaptic) {gksu synaptic}
[exec] (APTonCD) {aptoncd}
[exec] (Gparted) {gksu gparted}
[end]
[submenu] (Juegos) {}
[exec] (Supertux) {supertux}
[exec] (SupertuxKart) {supertuxkart}
[exec] (PySolitaire) {pysol}
[exec] (Tuxkart) {tuxkart}
[end]
[submenu] (Fluxbox)
[config] (Configuración)
[submenu] (Estilos) {Seleccione un estilo...}
[stylesdir] (/usr/share/fluxbox/styles)
[end]
[submenu] (Estilos Personalizados) {Seleccione un estilo...}
[stylesdir] (~/.fluxbox/styles)
[end]
[submenu] (Fondos de Pantalla) {Seleccione un fondo...}
[wallpapers] (~/.fluxbox/backgrounds)
[end]
[workspaces] (Escritorios)
[submenu] (Menú) {Menú}
[exec] (Editar menu) {gedit ~/.fluxbox/menu}
[exec] (Editar init) {gedit ~/.fluxbox/init}
[exec] (Editar keys) {gedit ~/.fluxbox/keys}
[end]
[reconfig] (Recargar configuración)
[restart] (Reiniciar fluxbox)
[exec] (Acerca de...) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center}
[end]
[separator]
[exit] (Salir)
[end]

~/.fluxbox/keys , este archivo nos permite configurar combinaciones de teclas para realizar las más diversas acciones
La tecla Mod1 es Alt

# cambio de escritorios
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5

#movimientos entre las pestañas.
Control right :NextTab
Control left :PrevTab

# cerrar la ventana
Control F4 :Close

# maximizar la ventana
Mod1 m :MaximizeWindow

# eliminar las decoraciones de la ventana
Mod1 n :ToggleDecor

# diversas aplicaciones
Mod1 f :ExecCommand firefox
Mod1 a :ExecCommand thunderbird

# tomar screenshots
Control s :ExecCommand import -window root -quality 85 screenshot.png
 

También se pueden controlar infinitud de opciones como
El ratón con MouseMove [+|-]xx
MouseClick 0
Mover las ventanas, Move [+|-]xx
Redimensionarlas, Resize [+|-]xx

Fluxbox con los parámetros
ShowDesktop
RootMenu
WorkspaceMenu
Reconfigure
Restart.

.fluxbox/apps, este archivo nos permite configurar como y donde se inicien determinadas aplicaciones.

[app] (galeon-bin)
[Workspace] {0}
[end]
[app] (xpmumon) # Nombre comando de la aplicación
[Workspace] {0} # zona de trabajo por defecto 0
[Dimensions] {125 125} # Regulando las dimensiones de la ventana
[Position] {17 31} # Definimos la posición
[Deco] {NONE} # Se usa para quitar decoraciones de ventana
[end]

.fluxbox/init , este archivo determina la configuración general de Fluxbox. La mayoría de estas opciones son definidas mediante el menú de configuración de Fluxbox, este es un ejemplo con comentarios:

session.titlebar.left: Stick #botones a la izquierda de las ventanas
session.titlebar.right: Minimize Maximize Close # botones a la derecha de las ventanas
session.screen0.toolbar.autoHide: false # auto-ocultar la toolbar
session.screen0.toolbar.mode: None # modo de la toolbar
session.screen0.toolbar.onTop: false # mostrar siempre encima la toolbar
session.screen0.toolbar.maxOver: false # maximizar encima de la toolbar
session.screen0.toolbar.tools: workspacename, iconbar, systemtray, clock 

# herramientas mostradas en la toolbar
session.screen0.toolbar.visible: true # mostrar u ocultar la toolbar
session.screen0.toolbar.placement: BottomCenter # posición de la toolbar
session.screen0.toolbar.height: 0 # altura de la toolbar
session.screen0.toolbar.layer: Desktop # capa en la que reside la toolbar
session.screen0.toolbar.widthPercent: 70 # anchura de la toolbar
session.screen0.toolbar.onhead: 0
session.screen0.tab.width: 64 # anchura de las pestañas
session.screen0.tab.placement: Top # posición respecto a la ventana de la pestaña
session.screen0.tab.rotatevertical: true
session.screen0.tab.height: 25 # altura de la pestaña
session.screen0.tab.alignment: Left # alineación de la pestaña
session.screen0.slit.alpha: 100 # transparencia del slit
session.screen0.slit.onTop: false # mostrar siempre encima el slit
session.screen0.slit.autoHide: false # auto-ocultar el slit
session.screen0.slit.maxOver: false # maximizar por encima del slit
session.screen0.slit.placement: CenterRight # posición del slit
session.screen0.slit.direction: Vertical # alineación del slit
session.screen0.slit.layer: Dock # capa del slit
session.screen0.slit.onHead: 0
session.screen0.slit.onhead: 0
session.screen0.iconbar.mode: Workspace
session.screen0.iconbar.alignment: Relative
session.screen0.iconbar.clientWidth: 70
session.screen0.iconbar.usePixmap: true
session.screen0.imageDither: false
session.screen0.colPlacementDirection: TopToBottom
session.screen0.windowPlacement: CascadePlacement
session.screen0.menuMode: Delay
session.screen0.fullMaximization: false # maximizar ventana por encima de todas las zonas
session.screen0.clickRaises: true # eleva la ventana al clickearla
session.screen0.focusModel: SloppyFocus # activar ventana al recibir enfoque
session.screen0.maxOverSlit: false # maximizar las ventanas por encima de la slit
session.screen0.sloppywindowgrouping: true
session.screen0.autoRaise: false # auto elevar las ventanas al recibir el enfoque
session.screen0.strftimeFormat: %R # formato de la hora de la toolbar. véase man date
session.screen0.showwindowposition: true # mostrar la posición de una ventana al moverla
session.screen0.menuDelayClose: 0 # retraso en el cierre del menú
session.screen0.workspaceNames: 1. system,2. surfing,3. comunication,4. network,5. download, # nombres de los escritorios
session.screen0.menuDelay: 0 # retraso en el cambio de una opción del menú a otra
session.screen0.antialias: true # antialiasing en la tipografía
session.screen0.resizeMode:
session.screen0.focusLastWindow: true # al cerrar la ventana activa, enfocar la última que tuvo el enfoque
session.screen0.edgeSnapThreshold: 0
session.screen0.rowPlacementDirection: LeftToRight # dirección de despliegue de las ventanas
session.screen0.opaqueMove: false # mantener opaco el fondo de una ventana mientras se mueve
session.screen0.rootCommand: # comando ejecutado al inicio
session.screen0.menuAlpha: 125 # transparencia del menú
session.screen0.workspacewarping: false # cambiar de escritorio la ventana moviéndola al lateral
session.screen0.focusNewWindows: true # enfocar nuevas ventanas
session.screen0.desktopwheeling: true # cambio de escritorios con la rueda del ratón
session.screen0.workspaces: 5 # número de escritorios
session.ignoreBorder: false
session.useMod1: true # habilitar tecla Alt para combinaciones
session.styleFile: /home/bencer/.fluxbox/styles/cthulhain_v2 # style
session.iconbar: true # habilitar iconos en la toolbar
session.groupFile: /home/bencer/.fluxbox/groups # fichero con los autogroups
session.updateDelayTime: 5
session.cacheMax: 200l
session.menuFile: /home/bencer/.fluxbox/menu # fichero con la configuración del menú
session.slitlistFile: /home/bencer/.fluxbox/slitlist # fichero con la lista del slit
session.autoRaiseDelay: 0 # retraso al mostrar un menú
session.cacheLife: 5l
session.doubleClickInterval: 250 # intervalo doble click
session.numLayers: 13 # número de capas de posicionamiento de ventanas
session.opaqueMove: false # mantener la imagen de fondo mientras se mueve una ventana
session.keyFile: /home/bencer/.fluxbox/keys # fichero de combinaciones de teclado
session.colorsPerChannel: 4
session.tabs: true # habilitar pestañas
el: 4

Styles , los estilos de fluxbox estan ubicados en /usr/local/share/fluxbox/styles/ o bien en /home/usuario/.fluxbox/styles/

Ejemplo de Style.

!Miscellaneous settings...
style.name: GS
style.author: GeeSeCillo
style.date: 20/10/03
style.credits: aLEczapKA, based upon ONE theme by <christel at geekgirl dot bz>
style.comments: Requests or questions; <aleczapka at gmx dot net>
rootCommand: bsetroot -gradient flatcrossdiagonalgradient -to \#294563 -from \#6173aa
menu.RoundCorners: BottomLeft BottomRight TopRight TopLeft
window.RoundCorners: TopRight TopLeft BottomLeft BottomRight
!Toolbar settings... o Barra de minimizar ventanas
toolbar.button: Flat Solid Horizontal
toolbar.button.color: #294563
toolbar.button.colorTo: #28455a
toolbar.button.picColor: #5a7494
toolbar.button.pressed: Flat Solid Horizontal
toolbar.button.pressed.color: #c5d3d6
toolbar.button.pressed.colorTo: #294563
toolbar.label: Flat Solid Horizontal
toolbar.label.color: #294563
toolbar.label.colorTo: #28455a
toolbar.label.textColor: #5a7494
toolbar.windowLabel: Flat Solid Horizontal
toolbar.windowLabel.color: #294563
toolbar.windowLabel.colorTo: #28455a
toolbar.windowLabel.textColor: #5a7494
toolbar.clock: Flat Solid Horizontal
toolbar.clock.color: #294563
toolbar.clock.colorTo: #28455a
toolbar.clock.textColor: #5a7494
toolbar: Flat Solid Horizontal
toolbar.color: #294563
toolbar.colorTo: #28455a
toolbar.textColor: #5a7494
toolbar.font: snap
toolbar.justify: Center
toolbar.bevelWidth: 0
toolbar.button.borderWidth: 0
toolbar.borderWidth: 0
toolbar.shaped: 0
toolbar.borderColor: #000000
 

!Menu settings... Opciones del menú
menu.frame: Flat Gradient Vertical
menu.frame.color: #294563
menu.frame.colorTo: #385588
menu.frame.textColor: #ffffff
menu.frame.font: snap
menu.frame.justify: Right
menu.frame.disableColor: #000000
menu.title: Flat Solid Vertical
menu.title.color: #c5d3d6
menu.title.textColor: #294563
menu.title.font: snap
menu.title.justify: Center
menu.hilite: Flat Solid
menu.hilite.color: #8eaabc
menu.hilite.textColor: #000000
menu.bullet: Triangle
menu.bullet.position: Right

!Window settings... Opciones de ventana
window.button.focus: Flat Solid PipeCross
window.button.focus.color: #294563
window.button.focus.picColor: #5a7494
window.button.unfocus: parentrelative
window.button.unfocus.color: #28455a
window.button.unfocus.picColor: #687071
window.grip.focus: Flat Gradient Vertical
window.grip.focus.color: #385588
window.grip.focus.colorTo: #294563
window.grip.unfocus: Flat Solid Horizontal
window.grip.unfocus.color: #000000
window.handle.focus: Flat Solid Vertical
window.handle.focus.color: #294563
window.handle.unfocus: Flat Solid Horizontal
window.handle.unfocus.color: #28455a
window.label.focus: Flat Gradient Vertical
window.label.focus.color: #385588
window.label.focus.colorTo: #28455a
window.label.focus.textColor: #c5d3d6
window.label.focus.font: snap
window.label.focus.justify: Center
window.font: snap
window.justify: Center
window.label.unfocus: Flat Solid CrossDiagonal
window.label.unfocus.color: #294563
window.label.unfocus.textColor: #9aa5a7
window.title.focus: Raised Bevel1 Gradient Horizontal
window.title.focus.color: #294563
window.title.focus.colorTo: #28455a
window.title.unfocus: Flat Solid Horizontal
window.title.unfocus.color: #294563
window.button.pressed: Raised Bevel1 Solid Horizontal
window.button.pressed.color: #28455a

!doesn't work yet anyways, but good to have
window.tab.justify: Center
window.tab.label.unfocus: Flat Solid
window.tab.label.unfocus.color: #294563
window.tab.label.unfocus.textColor: #294563
window.tab.label.focus: Flat Solid
window.tab.label.focus.color: #385588
window.tab.label.focus.textColor: #c5d3d6
window.tab.borderWidth: 1
window.tab.borderColor: rgb:10/10/10
window.tab.font: nu

! Opciones del Slit ( o barra de aplicaciones )
slit: flat gradient vertical
slit.color: #385588
slit.colorTo: SlateGrey
slit.borderWidth: 0
slit.bevelWidth: 0
slit.borderColor: #000000
window.frame.focusColor: #c5d3d6
window.frame.unfocusColor: #28455a
handleWidth: 3
frameWidth: 1
bevelWidth: 0
borderWidth: 0
borderColor: #28455a

! Opciones de redondeo de esquinas
menu.roundCorners: TopRight TopLeft
window.roundCorners: TopRight TopLeft BottomLeft BottomRight

Si no se quiere trabajar con los estilos, existen infinidad de ellos en distintos sitios al respecto.


Añadir Iconos
En esencia fluxbox no tiene iconos, sin embargo se pueden agregar utilizando por ejemplo:

- Idesk
- Tkdesk

Que se encuentran en los repositorios de Ubuntu

Definir el fondo de pantalla
Fluxbox incorpora una aplicación llamada fbsetbg para configurar el fondo de pantalla.
Este programa es un wrapper, más o menos un programa que basa sus funcionalidades en otros programas.
Lo que hace fbsetbg es elegir entre todas las aplicaciones instaladas en tu sistema que permiten definir el fondo de pantalla, tales como feh, wmsetbg, xsri
Teniendo instalado alguno de esos paquetes, para definir la imagen de fondo no tenemos que hacer más que escribir:

fbsetbg -c /ruta/a/la/imagen.png

Se puede definir la imagen desde el propio menú de Fluxbox, creando el directorio ~/.fluxbox/background o un enlace a nuestra carpeta de imágenes y editando el menú.


Cuando inicia fluxbox  por primera vez, solo se ve un escritorio vacio, pero se crean los archivos de configuración, vuelve a xfce y desde una consola configuralos para el proximo inicio, puede copiar y pegar del ejemplo para hacer más rapido y luego modificarlos con tranquilidad ya desde fluxbox. lee el post de ubuntu-cl que tiene como dejarlo hecho una maravilla.

Saludos.
Gabriel.
**Solo doy Soporte para Ubuntu - 6666 Más malo que el Diablo**

---

### Post by Hadso on 2009-01-31
Gracias por la respuesta.Muy completa. Entendí casi todo, salvo la ultima parte. Y creo que es importante porque, TODOS los cambios que le hago al flux no se guardan. 

"vuelve a xfce y desde una consola configuralos para el proximo inicio, puede copiar y pegar del ejemplo para hacer más rapido y luego modificarlos con tranquilidad ya desde fluxbox. lee el post de ubuntu-cl que tiene como dejarlo hecho una maravilla"

Gracias de nuevo. 
Saludos,

---

### Post by Hei Ku on 2009-02-01
Hadso, como sigue esto? Pudiste abrir el synaptic normalmente al final?

---

### Post by gmunioz on 2009-02-01
Hola had...:
Me refiero a que como fluxbox la primera vez que aparece solo tiene un escritorio vacio que asusta, volviendo al escritorio por defecto y abiendo una consola se pueden configurar sus archivos para que en el proximo inicio fluxbox inicie con un aspecto menos intimidante.
Respecto del post de ubuntu-cl, tiene unos trucos interesantes que hace que fluxbox se vea muy bien.
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu** - *Es preferible callar y pasar por idiota, que hablar y demostrarlo.*

---

### Post by Hadso on 2009-02-03
Sisisis. Muchas gracias. 
Ahora ando muy entretinido con el Flux. 
Gracias nuevamente.

---

