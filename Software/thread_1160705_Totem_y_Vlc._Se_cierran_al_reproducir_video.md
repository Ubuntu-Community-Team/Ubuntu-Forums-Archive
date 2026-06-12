---
title: "Totem y Vlc. Se cierran al reproducir video"
date: 2009-05-15
forum: Software
---

### Post by rubioo on 2009-05-15
Hola, resulta que viendo unos videos que tengo, se me cierra solo el reproductor(sea totem o vlc), aunque esto no pasa siempre. Hay veces que los puedo ver normalmente y otras se cierran, aunque no siempre en la misma parte del video.
 
 En totem me sale esto:
> cristian@cristian-desktop:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: Error: Disconnected: Conexión terminada
pulsesink.c(451): gst_pulsesink_is_dead (): /GstPlayBin:play/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin8/GstAutoAudioSink:autoaudiosink2/GstPulseSink:autoaudiosink2-actual-sink-pulse


 Y con el VLC me sale esto:
> 
cristian@cristian-desktop:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu2~ppajaunty1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "es"
[00000001] main libvlc: Ejecutar vlc con el interfaz por defecto. Usa 'cvlc' para usar vlc sin interfaz.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000528] alsa audio output error: cannot recover from buffer underrun
[00000528] alsa audio output error: ALSA error: Error de entrada/salida
vlc: pcm_pulse.c:312: pulse_delay: Afirmación `pcm->stream' fallida.
Cancelado


  Gracias y saludos!

---

### Post by pablo.s on 2009-05-15
Es mas o menos el mismo
problema que tenia JoseCuervo.
Lo solucionó desinstalando Python,
creo. Fijate buscando por los
posts que escribió, hará cosa de
tres semanas.

---

### Post by rubioo on 2009-05-15
Como me dolio leer desinstalar python :(
 Me fijo y comento como fue
 
       Gracias pablo

---

### Post by rubioo on 2009-05-15
Entonces vos decis que si desinstalo python va a andar?
 Despues no puedo instalarlo de nuevo, para programar? porque me esta
 gustando python(por eso me dolio leer la parte de desinstalar python)

      Gracias

---

### Post by pablo.s on 2009-05-16
Si, te entiendo perfectamente, 
a mi me gusta mucho Python, es
muy lindo lenguaje.
No se exactamente que hizo José,
pero después que lo desintales,
reinstalalo porque Ubuntu no es
Ubuntu sin Python...

---

### Post by hictio on 2009-05-16
> **rubioo said:**
> Hola, resulta que viendo unos videos que tengo, se me cierra solo el reproductor(sea totem o vlc), aunque esto no pasa siempre. Hay veces que los puedo ver normalmente y otras se cierran, aunque no siempre en la misma parte del video.

  Gracias y saludos!

Una pregunta, los textos de los menúes y demás de VLC se ven bien? O se ven así:

[URL=http://img30.imageshack.us/img30/6692/vclfontproblems.jpg]
[IMG]http://img30.imageshack.us/img30/6692/vclfontproblems.th.jpg[/IMG]
[/URL]

Yo tenía un problema similar con VLC, y era debido a que uso VRGB/VBGR font hints para suavizar las fuentes, había [un bug](https://bugs.edge.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657) que no sólo ponía las fuentes mal, sino que me crasheaba el VLC también; pero los updates de Jaunty del Miércoles 13 de Mayo lo arreglaron todo.

---

### Post by pablo.s on 2009-05-16
> **hictio said:**
> había [un bug]("https://bugs.edge.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657") que no sólo ponía las fuentes mal, sino que me crasheaba el VLC también; pero los updates de Jaunty del Miércoles 13 de Mayo lo arreglaron todo.

Si, con ese bug [URL="http://ubuntuforums.org/showthread.php?t=1143033"]nos rompimos
la cabeza[/URL] para saber como hacer
un workaround. Solo afectaba a
aplicaciones de KDE.

---

### Post by rubioo on 2009-05-16
Se me ven bien:

  [IMG]http://img231.imageshack.us/img231/9564/pantallazoh.th.png[/IMG]

 Para desinstalar python que paquete es :confused: porque tengo estos:
 > 
 python
 python2.5
 python2.6
 

   Gracias y Saludos!

---

### Post by pablo.s on 2009-05-16
No sé en realidad, estoy tocando
de oido. Pero supongo que con:

[COLOR=DarkGreen]**sudo apt-get remove python**[/COLOR]

algo resultará.

---

### Post by rubioo on 2009-05-16
Jaj bueno pruebo eso y vemos, de ultima reistalo :P

---

### Post by pablo.s on 2009-05-16
No es para tanto. Todo lo que
empieza tiene un final.

---

### Post by rubioo on 2009-05-16
#-o
 Cuando puse sudo *apt-get remove python* me empeso a desinstalar un monton de paquetes, como brasero, nautilus, entre otros, hasta que lo pare.
 Hay alguna forma de saber cuales se borraron para instalarlos?](*,)

 PD: espero que sea un final feliz :)

---

### Post by pablo.s on 2009-05-16
Che, pero antes de desinstalar 
te sale la lista de programas, te
pregunta si querés continuar y
aún asi le diste Y ?

Por ejemplo:

[COLOR=DarkGreen]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl tesseract-ocr librdf0 kdebase-runtime-data-common
  libgda3-common libgfortran3 amarok-common kde-icons-oxygen libexiv2-5
  libboost-thread1.37.0 librasqal1 python2.5 libloudmouth1-0
  libtorrent-rasterbar2 libsoprano4 redland-utils kdelibs5-data libwmf-bin
  libstreamanalyzer0 libblas3gf python2.5-minimal imagemagick-doc liblapack3gf
  libgda3-bin libgda3-3 libpq5 libstreams0 imagemagick exiv2
  libboost-filesystem1.37.0 miro-data perlmagick soprano-daemon
  kdebase-runtime-data libboost-system1.37.0 libglademm-2.4-1c2a
  python-libtorrent libgdl-1-0 tesseract-ocr-deu libboost-python1.37.0
  libgdl-1-common tesseract-ocr-eng
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte alsa-utils amarok apport apport-gtk apt-xapian-index apturl at-spi
  brasero capplets-data checkbox checkbox-gtk command-not-found
  compiz-fusion-plugins-extra compiz-fusion-plugins-main computer-janitor
  computer-janitor-gtk contact-lookup-applet emesene eog evince f-spot
  fast-user-switch-applet file-roller firefox-3.0-gnome-support
  firefox-gnome-support foomatic-db-hpijs gcalctool gconf-editor gconf2 gdebi
  gdebi-core gdm gdm-guest-session gedit gimp gksu gnome-about
  gnome-app-install gnome-applets gnome-applets-data gnome-codec-install
  gnome-color-chooser gnome-control-center gnome-doc-utils gnome-games
  gnome-games-data gnome-keyring gnome-media gnome-media-common gnome-menus
  gnome-mount gnome-orca gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-settings-daemon gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-user-guide gnome-utils gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-good gucharmap hal-cups-utils hpijs hplip hplip-data
  indicator-applet indicator-messages inkscape jockey-common jockey-gtk
  kdebase-runtime kdebase-runtime-bin-kde4 kdelibs-bin kdelibs5
  kdemultimedia-kio-plugins khelpcenter4 language-selector
  language-selector-common launchpad-integration libbonoboui2-0
  libgail-gnome-module libgksu2-0 libgnome-media0 libgnome-pilot2
  libgnome-vfs2.24-cil libgnome2-0 libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.24-cil libgnomekbd-common libgnomekbd3
  libgnomekbdui3 libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtkhtml-editor0
  libgtkhtml3.14-19 libgweather-common libgweather1 libkcddb4 liblpint-bonobo0
  libmetacity0 libpanel-applet2-0 libpurple-bin lsb-release mail-notification
  metacity metacity-common miro mousetweaks nautilus nautilus-data
  nautilus-sendto nautilus-share network-manager network-manager-gnome
  nvidia-common onboard openoffice.org-emailmerge openoffice.org-gnome pidgin
  pidgin-libnotify pidgin-otr policykit-gnome pyroom python python-apport
  python-apt python-brlapi python-cairo python-central python-cups
  python-cupshelpers python-dbus python-debian python-fstab python-gconf
  python-gdata python-gdbm python-glade2 python-gmenu python-gnome2
  python-gnome2-desktop python-gnome2-extras python-gnomecanvas
  python-gnupginterface python-gobject python-gst0.10 python-gtk2
  python-gtkhtml2 python-gtksourceview2 python-imaging python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-lxml python-newt
  python-notify python-numpy python-pkg-resources python-problem-report
  python-psyco python-pyatspi python-pyorbit python-pysqlite2 python-rdflib
  python-renderpm python-reportlab python-reportlab-accel python-sexy
  python-smbc python-software-properties python-support python-uniconvertor
  python-uno python-usb python-virtkey python-vte python-xapian python-xdg
  python-xkit rhythmbox screen-profiles screen-resolution-extra seahorse
  seahorse-plugins software-properties-gtk system-config-printer-common
  system-config-printer-gnome tomboy totem totem-common totem-gstreamer
  totem-mozilla totem-plugins tsclient tucan ubufox ubuntu-artwork
  ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-system-service
  ubuntu-wallpapers ufw unattended-upgrades update-manager update-manager-core
  update-notifier update-notifier-common usb-creator vinagre vino
  xulrunner-1.9-gnome-support yelp
0 upgraded, 0 newly installed, 228 to remove and 0 not upgraded.
After this operation, 760MB disk space will be freed.[/COLOR]
[COLOR=Red]Do you want to continue [Y/n]? [/COLOR]

---

### Post by pablo.s on 2009-05-16
Si desinstaló Nautilus y etcetera
instalando ubuntu-desktop lo
reinstala.

---

### Post by rubioo on 2009-05-16
Auch.. creo que voy a tener que ir buscando el cd para reinstalar :(

---

### Post by rubioo on 2009-05-16
Bueno, creo que ya instale todo lo que no tendria que haber desinstalado.
 Volviendo al tema, para desinstalar python solamente como hago entonces?

     Gracias

---

### Post by guillermolisi on 2009-05-16
> **pablo.s said:**
> Si desinstaló Nautilus y etcetera
instalando ubuntu-desktop lo
reinstala.
Y posiblemente reinstale Python de nuevo .....

Creo que se deberia ser mas especifico en las soluciones que se dan para evitar el sindrome de "Si facil" u "Ok complaciente" :)

Ademas si este tema o similar ya se toco en el foro y alguien recuerda quien lo inicio, parace que fue Josecuervo, con buscar el o los threads y/o mencionar un link a el/ellos seria de muy buena ayuda.

Tal como mencione en una reciente oportunidad, hay que considerar que no se saben de antemano que conocimientos y habilidades poseen quienes leen las sugerencias y si alguien lleva a la practica algo deberia saber como volver al punto de partida cuando las cosas no salen como se esperaban (best practices again).

---

### Post by rubioo on 2009-05-16
> **guillermolisi said:**
> Y posiblemente reinstale Python de nuevo .....

Creo que se deberia ser mas especifico en las soluciones que se dan para evitar el sindrome de "Si facil" u "Ok complaciente" :)

Ademas si este tema o similar ya se toco en el foro y alguien recuerda quien lo inicio, parace que fue Josecuervo, con buscar el o los threads y/o mencionar un link a el/ellos seria de muy buena ayuda.

Tal como mencione en una reciente oportunidad, hay que considerar que no se saben de antemano que conocimientos y habilidades poseen quienes leen las sugerencias y si alguien lleva a la practica algo deberia saber como volver al punto de partida cuando las cosas no salen como se esperaban (best practices again).

 Todo bien guille ;)
 A mi no me molesta tener que instalar y reinstalar 20 veces, porque hice las cosas mal (ademas asi aprendo un poco tambien)

---

### Post by pablo.s on 2009-05-16
> **guillermolisi said:**
> Creo que se deberia ser mas especifico en las soluciones que se dan para evitar el sindrome de "Si facil" u "Ok complaciente" :)

100% de acuerdo.

> **guillermolisi said:**
> Ademas si este tema o similar ya se toco en el foro y alguien recuerda quien lo inicio, parace que fue Josecuervo, con buscar el o los threads y/o mencionar un link a el/ellos seria de muy buena ayuda.

Lo único que puso José es que
habia desintalado Python.

> **guillermolisi said:**
> Tal como mencione en una reciente oportunidad, hay que considerar que no se saben de antemano que conocimientos y habilidades poseen quienes leen las sugerencias y si alguien lleva a la practica algo deberia saber como volver al punto de partida cuando las cosas no salen como se esperaban (best practices again).

100% de acuerdo de nuevo, Guille. 
Pero hay que tener en cuenta que por
los pasos que dimos para solucionar el
problema, hasta el punto en que todo
se fué por el inodoro, venia bien encarado.
Lo lamento por el desastre, no estoy al
lado de rubioo como para advertirle que
está por cometer una equivocación. Una
vez en un post le advertí algo y Hei Ku me
dijo que los usuarios no advierten nada, solo
los moderadores.

---

### Post by guillermolisi on 2009-05-16
> **pablo.s said:**
> 100% de acuerdo.



Lo único que puso José es que
habia desintalado Python.



100% de acuerdo de nuevo, Guille. 
Pero hay que tener en cuenta que por
los pasos que dimos para solucionar el
problema, hasta el punto en que todo
se fué por el inodoro, venia bien encarado.
Lo lamento por el desastre, no estoy al
lado de rubioo como para advertirle que
está por cometer una equivocación. Una
vez en un post le advertí algo y Hei Ku me
dijo que los usuarios no advierten nada, solo
los moderadores.
Ok. Tudo bem ! Tudo legal !

Mis comentarios no deberian ser tomados como reprimendas, solo los hago como en un intento de que se consideren algunas situaciones en base a, casualmente, lo que bien decis respecto que uno no esta sentado al lado del otro.

Son indicaciones para pensar en como se dice lo que se dice y que podria pasar al repetir un proceso/procedimiento hecho por un tercero que no tengo al lado, como parte del aporte que se hace cuando se interviene para ayudarlo.

Por ejemplo, para tener alguna idea se podria preguntar "Usaste alguna vez en consola el comando 'fliqui' ?" Y a partir de su respuesta se ve como continuar el dialogo.

No conozco la situacion que mencionas, pero una cosa es sugerir, comentar, observar y otra distinta advertir.

Todos estamos aprendiendo de todos.

---

### Post by josecuervo86 on 2009-05-16
Que quilombo se armo! :P

El problema que tenia yo era debido a una instalacion bastante anormal de python. Pero no lo solucione desinstalandolo, lo unico que hice fue eliminar los archivos que empezaban con python de la carpeta usr/local/bin, pero de ningun modo desisntalando python!

Igual me parece que el problema no es el mismo que el mio, ya que a mi me saltaba por el lado de pygtk. Ojala que asi se solucione

---

### Post by pablo.s on 2009-05-16
Ya pasó.
La experiencia es el peine
que te regalan cuando te 
quedás pelado.

---

### Post by josecuervo86 on 2009-05-16
Totalmente de acuerdo

---

### Post by rubioo on 2009-05-16
Igual por ahora, a este problema no le voy a dar mucha importancia
 Porque como desinstale ubuntu-desktop y lo instale de nuevo,
 cuando reinicie no se veia nada, entonces agarre el cd de ubuntu y
 reinstale todo. 
 Pero ahora estoy peliando con compiz, porque se ve toda la
 pantalla en blanco si lo activo...

---

### Post by hernan blau on 2009-05-17
Yo tuve un problema parecido e instalé Kaffeine. Suerte. HB

---

### Post by felipe1942 on 2010-03-23
La solucion que me ha servido, en el caso que vlc se cierra al intentar abrir un video es:

preferencias,video,salida de video OpenGL

---

