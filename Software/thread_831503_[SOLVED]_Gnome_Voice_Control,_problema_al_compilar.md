---
title: "[SOLVED] Gnome Voice Control, problema al compilar"
date: 2008-06-16
forum: Software
---

### Post by Flechagorda on 2008-06-16
Como andan todos....:

Tengo un problema al intentar compilar el gnome-voice-control-0.3

Pego el error que me tira:

> checking for GNOME_PANEL... configure: error: Package requirements (libpanelapplet-2.0 gtk+-2.0 libgnomeui-2.0 gstreamer-0.10 gstreamer-base-0.10 gdk-2.0 libwnck-1.0 cspi-1.0 libnotify) were not met:

No package 'libpanelapplet-2.0' found
No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'cspi-1.0' found
No package 'libnotify' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_PANEL_CFLAGS
and GNOME_PANEL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Obviamente googlee como loco antes de mostrar el error aca...

Por lo que entendi, me faltan algunas librerias(libpanelapplet-2.0 gtk+-2.0 libgnomeui-2.0 gstreamer-0.10 gstreamer-base-0.10 gdk-2.0 libwnck-1.0 cspi-1.0 libnotify). 
Pero cuando le doy a "sudo apt-get install libpanelapplet-2.0 gtk+-2.0 libgnomeui-2.0 gstreamer-0.10 gstreamer-base-0.10 gdk-2.0 libwnck-1.0 cspi-1.0 libnotify" me tira que no puede encontrar los paquetes.....

Ahora, busque de ajustar el PKG_CONFIG_PATH, lo hice con SET y con EXPORT, pero me sigue dando error...

Por supuesto que busque en Synaptic, pero esta la version 0.2-ubuntu05, que tiene un BUG que para repararlo, hay que instalar desde el source, y aca volvemos a lo mismo...

Segun la pagina oficial, la version 0.2-ubuntu06 tiene solucionado este bug, pero en los repositorios todavia aparece la 05...


Mi inquietud es si tengo que solucionar algo del PGK_CONFIG_PATH...

Saludos para todos......

Santi

---

### Post by faktorqm on 2008-06-17
Con lo del pkg_config_path aca yo explico algo: [http://ubuntuforums.org/showthread.php?t=730856&highlight=PKG_CONFIG_PATH&page=2](http://ubuntuforums.org/showthread.php?t=730856&highlight=PKG_CONFIG_PATH&page=2)
pero yo te diria que no le hagas caso, hay un 99% de posibilidades de que no sea eso.

Proba con esto:

```
sudo apt-get install libpanelappletmm-2.6-1c2 libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgnomeui-0 libgnomeui-common libgnomeuimm-2.6-1c2a libgstreamer0.10-0 gdk-imlib11 gdk-imlib11-dev  libgdk-imlib11 libwnck22 libwnck-common libnotify1 libnotify1-gtk2.10
```

Todos los paquetes los busque poniendo 

```
aptitude search nombre_del_paquete
```

puse siempre el nombre sin la version, sino nunca encontrarias nada....

¿Cómo estas compilando? estas usando la opcion --prefix=/usr ?

Espero que te haya servido de algo. Salu2!!

---

### Post by sdennie on 2008-06-17
Tambien como ya esta una version en los repos podes usar:

```

sudo apt-get build-dep gnome-voice-control

```

Con eso bajas todas las cosas para compilar gnome-voice-control de los repos.  Deben ser los mismos.

---

### Post by Flechagorda on 2008-06-17
Gracias Faktorqm y Vor....

Mire el post donde hablas del PKG_CONFIG....
Probe con  --prefix=/usr , con  --prefix=/usr/bin, etc etc...
Y me sigue tirando lo mismo-!!
hoy voy a probar un par de cosas que encontre en unos post, sino, quedara para cuando este en repositorios....::

Abrazo y gracias

---

### Post by Hei Ku on 2008-06-17
lo que te falta para compilar son los headers de esas aplicaciones. O sea, lo mismo que te pasaron antes, pero los paquetes seguramente se llaman -dev
Cuando instalas un programa normalmente solo te instala el binario. Cuando compilas otro que necesita el primer programa necesitas al menos parte del codigo fuente, para que ambos programas puedan comunicarse. Esos son los headers.
Vas a tener que buscar el paquete -dev de cada uno y bajarlo.

---

### Post by Flechagorda on 2008-06-17
Gracias Hei Ku, voy a arrancar haciendo eso........

---

### Post by Hei Ku on 2008-06-17
algo que te puede venir bien para buscar el paquete equivalente es la opcion de busqueda por nombre en Synaptics o Adept, o sino en la consola: apt-cache search xxxxx

Si pones el nombre del paquete, en general vas a encontrar 3 distintos al menos. El programa en sí, los fuentes (-dev) y documentacion (-doc)

---

### Post by faktorqm on 2008-06-17
Claro, es como dice Hei Ku, en realidad no te queria tirar a instalar los -dev de una pero creo que no queda opcion. Fijate que todos los paquetes que te puse ahi tienen version nombre_del_paquete-dev. Salu2!!

---

### Post by sdennie on 2008-06-17
Flechagorda: No te funcionó el "apt-get build-dep"?  Por ejemplo con una maquina con nada nada:

```

$ sudo apt-get build-dep gnome-voice-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libgtk1.2-dev instead of libgtk-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev build-essential check debhelper dpkg-dev
  g++ g++-4.2 gettext html2text intltool-debian libart-2.0-dev libatk1.0-dev
  libatspi-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libc6-dev libcairo2-dev
  libdbus-1-dev libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libglib1.2-dev
  libglib1.2ldbl libglib2.0-dev libgnome-keyring-dev libgnome2-dev
  libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev
  libgnutlsxx13 libgpg-error-dev libgstreamer0.10-dev libgtk1.2
  libgtk1.2-common libgtk1.2-dev libgtk2.0-dev libice-dev libidl-dev
  libjpeg62-dev liblzo2-dev libopencdk10-dev liborbit2-dev
  libpanel-applet2-dev libpango1.0-dev libpixman-1-dev libpng12-dev
  libpopt-dev libpthread-stubs0 libpthread-stubs0-dev libselinux1-dev
  libsepol1-dev libsm-dev libsphinx2-dev libsphinx2g0
  libstartup-notification0-dev libstdc++6-4.2-dev libtasn1-3-dev
  libtimedate-perl libwnck-dev libx11-dev libxau-dev libxcb-xlib0-dev
  libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev
  libxrandr-dev libxrender-dev libxres-dev libxtst-dev linux-libc-dev m4 patch
  po-debconf x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-resource-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
The following packages will be upgraded:
  cpp gcc libgnome-keyring0 libgnomeui-0 libpanel-applet2-0
5 upgraded, 107 newly installed, 0 to remove and 113 not upgraded.
Need to get 32.0MB of archives.
After this operation, 120MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

Asi vas a tener todos los paquetes -dev para compilar gnome-voice-control.

---

### Post by Flechagorda on 2008-06-17
Vor, el "sudo apt-get build-dep gnome-voice-control" funciona, me baja todas las dependencias etc etc...
Ahora, la version que esta en los repositorios es la 0.2ubuntu5, que tiene un bug, que para arreglarlo, hay que instalar desde el source......

Baje todas las dependencias dev, como 80 megatototes....Listo dije, ahora tiene que andar....
NAAA...... ERRORRRRRRRRR, Voice control no querer funcionarrrr:

> checking for POCKETSPHINX... configure: error: Package requirements (sphinxbase >= 0.3 pocketsphinx >= 0.4) were not met:

No package 'sphinxbase' found
No package 'pocketsphinx' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables POCKETSPHINX_CFLAGS
and POCKETSPHINX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Google mediante, baje los dos paquetes. Los pude compilar segun las instrucciones de [http://www.speech.cs.cmu.edu/pocketsphinx/]("http://www.speech.cs.cmu.edu/pocketsphinx/")...No me tira ningun error...
Pero cuando vuelvo a querer compilar el VOICE, de vuelta lo mismo....

Je, mientras ya estoy pensando como voy a hacer para sacar tanto paquete instalado al divino boton...
Igual no me voy a dejar co*er por este coso, aunque sea un novatoide...

Abrazo

---

### Post by Hei Ku on 2008-06-17
que te tira si pones esto? 

slocate sphinxbase

por alguna razon deben haber quedado instalados en una ruta no standard.

---

### Post by Flechagorda on 2008-06-17
Me tira:

santiago@santiago-laptop:~/gnome-voice-control-0.3$ slocate sphinxbaseslocate: fatal error: Could not find user database '/var/lib/slocate/slocate.db':  No such file or directory

Jajaja, no se como agregar esa base de datos...
Ahora voy a probar a recompilar los paquetes phinx.....

---

### Post by sdennie on 2008-06-17
Aparentemente sphinxbase y pocketsphinx no estan en los repos de Ubuntu.  Asi que hice:

```

wget http://voxel.dl.sourceforge.net/sourceforge/cmusphinx/sphinxbase-0.3.tar.bz2
wget http://voxel.dl.sourceforge.net/sourceforge/cmusphinx/pocketsphinx-0.4.1.tar.bz2
tar xvf sphinxbase-0.3.tar.bz2
tar xvf pocketsphinx-0.4.1.tar.bz2
cd sphinxbase-0.3/
./configure
make
sudo make install
cd ../pocketsphinx-0.4.1
./configure
make
sudo make install
cd ../gnome-voice-control-0.3/
./configure
make
sudo make install

```

Y listo.  Lamentablemente lo hice en una maquina virtual sin sonido asi que no lo puedo probar pero, por lo menos, instalo.

(Normalmente es mejor a usar checkinstall y no "sudo make install" pero no funciona con las cosas de sphinx).

---

### Post by faktorqm on 2008-06-18
A mi me tiró esto, aunque la opcion de vor me parece la mas sensata, aunque la mas peligrosa, pues, aun esos paquetes te pueden pedir nuevas dependencias.... 

```

faktorqm@the-edge:~$ aptitude search sphinx
p   libsphinx2-dev                  - speech recognition library - development k
p   libsphinx2g0                    - speech recognition library                
p   sphinx2-bin                     - speech recognition utilities              
p   sphinx2-hmm-6k                  - speech recognition library - default acous
faktorqm@the-edge:~$ 
```

---

### Post by sdennie on 2008-06-18
> **faktorqm said:**
> A mi me tiró esto, aunque la opcion de vor me parece la mas sensata, aunque la mas peligrosa, pues, aun esos paquetes te pueden pedir nuevas dependencias.... 

```

faktorqm@the-edge:~$ aptitude search sphinx
p   libsphinx2-dev                  - speech recognition library - development k
p   libsphinx2g0                    - speech recognition library                
p   sphinx2-bin                     - speech recognition utilities              
p   sphinx2-hmm-6k                  - speech recognition library - default acous
faktorqm@the-edge:~$ 
```

Ya probé todas las paquetes "sphinx" en los repos en una maquina virtual.  La nueva version de gnome-voice-control necesita sphinxbase y pocketsphinx desde sourceforge si o si.  Estoy de acuerdo de que no es el metodo mas lindo pero, me parece que no hay otra opcion para usar gnome-voice-control 0.3.

---

### Post by Flechagorda on 2008-06-18
Segui todos los pasos que puso Vor y compilo bien...
Pero anoche habia probado haciendo lo mismo (casi se ve) y me tiraba error, se ve que algo me salteaba....


Gracias Vor, Faktorqm y  Hei Ku por todo....

Asi dan ganas de postear problemas....

---

### Post by Flechagorda on 2008-06-18
La **** es que ahora no me aparece cuando lo quiero agregar en la barra.....
Es decir, cuando lo quiero añadir al panel, me aparecen todos los applets menos ese....
Con la version 0.2, me aparecia pero me daba error. Ahora ni aparece.....
Pero cuando lo compile no me tiro ningun error.....

No se si sera porque no hice todavia ninguna de las actualizaciones que entraron estos dos dias, la del Kernel 19 etc etc....

Lo que pasa es que estoy de viaje laburando y aca en el hotel la conexion es de 128kb.....y va para trasssss...

Cuando vuelva a Bsas pruebo de vuelta.....

Abrazo

Santiago

---

### Post by Hei Ku on 2008-06-18
No creo que sea un tema de las actualizaciones. 
Tenes forma de intentar ejecutarlo a mano?
Reiniciaste el Gnome despues de instalarlo?

---

### Post by Flechagorda on 2008-06-19
A mano creo que los applet de gnome no se pueden iniciar..

Probe reiniciando gnome, reiniciando la maquina, todo....
Cuando vuelva y pueda hacer todas las actualizaciones vuelvo a probar todos los pasos.....

---

### Post by Hei Ku on 2008-06-19
despues del configure y el make, le pusiste sudo make install ?

---

### Post by Flechagorda on 2008-06-19
Si si.....
Ahora, al final del "sudo make install", cuando termina me aparece:
> make[1]: se sale del directorio `/home/santiago/gnome-voice-control-0.3/po'
make[1]: se ingresa al directorio `/home/santiago/gnome-voice-control-0.3'
make[2]: se ingresa al directorio `/home/santiago/gnome-voice-control-0.3'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/santiago/gnome-voice-control-0.3'
make[1]: se sale del directorio `/home/santiago/gnome-voice-control-0.3'


Eso que dice "no se hace nada para...." esta bien????

Porque con otros programas que instale no me acuerdo que apareciera algo asi..

---

### Post by Hei Ku on 2008-06-19
si, es normal. depende de como sea la estructura del directorio.

es raro que siga sin reconocertelo como applet. 

Alguien tiene experiencia en la instalacion de los applets? Yo tengo KDE y Xubuntu, asi que ni idea en este punto?

---

### Post by faktorqm on 2008-06-20
Che yo no entendi lo que queres hacer, pero si es lo que creo, sabes cual es el comando para ejecutarlo? si sabes eso, hace click derecho en la barra que contiene aplicaciones;lugares;sistema etcetc y elegis "añadir al panel". Ahi elegis la opcion "Lanzador de aplicacion personalizado" y te abre un cuadrito para poner el comando y el icono, la descripcion, etc. El comando te recomiendo que lo pongas con la ruta completa. Luego ya te lo crea. no se si es eso lo que estabas buscando. Salu2!!!

---

### Post by sdennie on 2008-06-24
Si tenés problemas todavia, aparentemente se puede arreglar la version 0.2: [http://ubuntuforums.org/showpost.php?p=5253985&postcount=10](http://ubuntuforums.org/showpost.php?p=5253985&postcount=10).

Pero, antes de instalar lo del repos, debés desinstalar lo que compilaste.  Asi que, en cada directorio que hiciste "make install", tenés que "make uninstall".

---

### Post by Flechagorda on 2008-06-25
Sos un grosso Vor, ahora anda de primera.....
Graciasssssssssss

Santiago

---

### Post by cabez0n on 2009-11-10
> **faktorqm said:**
> Che yo no entendi lo que queres hacer, pero si es lo que creo, sabes cual es el comando para ejecutarlo? si sabes eso, hace click derecho en la barra que contiene aplicaciones;lugares;sistema etcetc y elegis "añadir al panel". Ahi elegis la opcion "Lanzador de aplicacion personalizado" y te abre un cuadrito para poner el comando y el icono, la descripcion, etc. El comando te recomiendo que lo pongas con la ruta completa. Luego ya te lo crea. no se si es eso lo que estabas buscando. Salu2!!!

Esto no funciona para los applets, eso es para agregar lanzadores, accesos directos, pero en este caso el applet debe aparecer en el lista de Añadir panel, sino, es que gnome aun no lo ve como un applet instalado.

---

