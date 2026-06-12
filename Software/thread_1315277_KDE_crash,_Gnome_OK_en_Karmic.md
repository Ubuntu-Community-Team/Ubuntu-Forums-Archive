---
title: "KDE crash, Gnome OK en Karmic"
date: 2009-11-05
forum: Software
---

### Post by electronpositivo on 2009-11-05
Buenas.

La semana pasada instalé Ubuntu Karmik Koala y todo perfecto.

El problema lo tengo al intentar iniciar sesión KDE (tras instalar kubuntu-desktop)... En un principio parece que carga bien: aparece el icono de disco duro, aparece el icono del destornillador y la llave inglesa, aparece la bola del mundo, pero cuando aparece el cuarto icono del splash de KDE, vuelve a aparecer el gdm. He probado a cargar kdm en lugar de gdm y sigue igual, el problema creo que no viene por ahí.

El syslog muestra lo siguiente:

```
Nov  5 09:45:16 pc221 gdm-simple-slave[8789]: WARNING: Unable to load file '/etc/gdm/custom.conf': No existe el fichero ó directorio
Nov  5 09:45:16 pc221 console-kit-daemon[983]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nov  5 09:45:16 pc221 acpid: client 7450[0:0] has disconnected
Nov  5 09:45:16 pc221 acpid: client connected from 7692[0:0]
Nov  5 09:45:16 pc221 kernel: [  521.748451] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Nov  5 09:45:16 pc221 kernel: [  521.748481] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Nov  5 09:45:16 pc221 kernel: [  521.748490] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Nov  5 09:45:16 pc221 kernel: [  521.748540] pci 0000:01:00.0: putting AGP V2 device into 4x mode

```

El fichero .xsession-errors contiene lo siguiente
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=es_ES.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
X Error: XSyncBadAlarm 154
  Extension:    144 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
X Error: XSyncBadAlarm 154
  Extension:    144 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(8995)/ KStartupInfo::createNewStartupId: creating:  "pc221;1257411666;729311;8995_TIME0" : "unnamed app"
kephald starting up 
XRANDR error base:  164 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  115 1280 x 960 
RandRScreen::loadSettings - adding mode:  116 1152 x 864 
RandRScreen::loadSettings - adding mode:  117 1152 x 864 
RandRScreen::loadSettings - adding mode:  118 1152 x 864 
RandRScreen::loadSettings - adding mode:  119 1024 x 768 
RandRScreen::loadSettings - adding mode:  120 1024 x 768 
RandRScreen::loadSettings - adding mode:  121 1024 x 768 
RandRScreen::loadSettings - adding mode:  122 1024 x 768 
RandRScreen::loadSettings - adding mode:  123 832 x 624 
RandRScreen::loadSettings - adding mode:  124 800 x 600 
RandRScreen::loadSettings - adding mode:  125 800 x 600 
RandRScreen::loadSettings - adding mode:  126 800 x 600 
RandRScreen::loadSettings - adding mode:  127 800 x 600 
RandRScreen::loadSettings - adding mode:  128 800 x 600 
RandRScreen::loadSettings - adding mode:  129 640 x 480 
RandRScreen::loadSettings - adding mode:  130 640 x 480 
RandRScreen::loadSettings - adding mode:  131 640 x 480 
RandRScreen::loadSettings - adding mode:  132 640 x 480 
RandRScreen::loadSettings - adding mode:  133 640 x 480 
RandRScreen::loadSettings - adding mode:  134 720 x 400 
RandRScreen::loadSettings - adding mode:  135 720 x 400 
RandRScreen::loadSettings - adding mode:  136 720 x 400 
RandRScreen::loadSettings - adding mode:  137 640 x 400 
RandRScreen::loadSettings - adding mode:  138 640 x 350 
RandRScreen::loadSettings - adding crtc:  113 
RandRScreen::loadSettings - adding output:  114 
Setting CRTC 113 on output "default" (previous 0 ) 
CRTC outputs: (114) 
Output name: "default" 
Output refresh rate: 60 
Output rect: QRect(0,0 1280x960) 
Output rotation: 1 
XRandROutputs::init 
  added output  114 
adding an output 0 with geom:  QRect(0,0 1280x960) 
output: "SCREEN-0" QRect(0,0 1280x960) 858857504 true true 
load xml 
connected: 1 
looking for current "SCREEN-0" 
known "*" has score: 0.125 
screen: 0 QRect(0,0 1280x960) 
looking for a matching configuration... 
connected: 1 
looking for current "SCREEN-0" 
known "*" has score: 0.125 
found outputs, known: false 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
kglobalaccel: Fatal IO error: client killed
kwin: Fatal IO error: client killed
Qt-subapplication: Fatal IO error: client killed
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
klauncher: Exiting on signal 15
klauncher: Exiting on signal 1
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
Unexpected response from KInit (response = 0).
startkde: Could not start ksmserver. Check your installation.
kded4: Fatal IO error: client killed
Error: Can't open display: :0
Could not connect to D-Bus server: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-0w3L5KGslP: Conexión rechazada
startkde: Shutting down...
kdeinit4_wrapper: Warning: connect(/home/admin2/.kde/socket-pc221/kdeinit4__0) failed: : No such file or directory
Error: Can not contact kdeinit4!
startkde: Running shutdown scripts...
No protocol specified
xprop:  unable to open display ':0'
No protocol specified
xprop:  unable to open display ':0'
startkde: Done.
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
```

¿Alguna pista?

---

### Post by electronpositivo on 2009-11-06
Imaginaba que era complicado el tema...

Se me ha ocurrido instalar el paquete xorg-driver-fglrx y con esto consigo que inicie la sesión en KDE, pero me aparece una ventana con el siguiente error:

KWin no está estable.
Parece haber terminado inesperadamente varias veces seguidas.
Puede seleccionar otro gestor de ventanas:

Y abajo me aparece una lista en la que puedo seleccionar "metacity" o "kwin".

El caso es que no funciona del todo bien...

A ver si con esto he dado más información para resolver este tema.

¿A quién le parece esto interesanta para ayudarme a resolverlo?

---

### Post by guillermolisi on 2009-11-06
> **electronpositivo said:**
> Imaginaba que era complicado el tema...

Se me ha ocurrido instalar el paquete xorg-driver-fglrx y con esto consigo que inicie la sesión en KDE, pero me aparece una ventana con el siguiente error:

KWin no está estable.
Parece haber terminado inesperadamente varias veces seguidas.
Puede seleccionar otro gestor de ventanas:

Y abajo me aparece una lista en la que puedo seleccionar "metacity" o "kwin".

El caso es que no funciona del todo bien...

A ver si con esto he dado más información para resolver este tema.

¿A quién le parece esto interesanta para ayudarme a resolverlo?
Mas alla de si el tema es o no interesante, tenes que pensar que puede ser que no todos tengan una respuesta que consideren de valor para el problema y por eso no han respondido aun.

Que version de KDE estas usando ?

A mi me parece que faltan cosas en KDE, lo que aun no se es que le falta para no tener esos comportamientos. Por el lado de Gnome algo tampoco esta bien dados los mensajes que mostraste y mas alla de que te parezca que funciona bien.

Esta actualizado con los ultimos paquetes toda la instalacion de KK o instalaste y te pusiste a probar ?

---

### Post by electronpositivo on 2009-11-06
Gracias Guillermo.

Se trata de una instalación limpia de Ubuntu KK y tras esto una instalación de los paquetes de kubuntu via aptitude.

La versión de KDE es la de los repositorios oficiales (4.3.2). Tengo todos los paquetes actualizados.

Por lo que he averiguado el paquete xorg-driver-fglrx es para gráficas ATI. En mi caso se trata de una gráfica integrada VIA. Supongo que por eso KWin no funciona correctamente. Los errores que posteé inicialmente salían antes de instalar xorg-driver-fglrx.

No pretendo conseguir aceleración gráfica, simplemente me gustaría poder elegir acceder con KDE o Gnome indistintamente.

¿Alguna idea?

---

### Post by guillermolisi on 2009-11-06
> **electronpositivo said:**
> Gracias Guillermo.

Se trata de una instalación limpia de Ubuntu KK y tras esto una instalación de los paquetes de kubuntu via aptitude.

La versión de KDE es la de los repositorios oficiales (4.3.2). Tengo todos los paquetes actualizados.

Por lo que he averiguado el paquete xorg-driver-fglrx es para gráficas ATI. En mi caso se trata de una gráfica integrada VIA. Supongo que por eso KWin no funciona correctamente. Los errores que posteé inicialmente salían antes de instalar xorg-driver-fglrx.

No pretendo conseguir aceleración gráfica, simplemente me gustaría poder elegir acceder con KDE o Gnome indistintamente.

¿Alguna idea?
Ahora esta algo mas clara la situacion.

El tema es que con video VIA estas literalmente "en el horno". Ademas cualquier componente que sea para ATI o nVidia solo complicara las cosas.

Con VIA lo mejor que podes hacer es agregar una placa adicional de las marcas mencionadas; intentar hacer funcionar los drivers Openchrome (con resultados impredecibles) o utilizar driver VESA con una configuracion adecuada del xorg.conf para obtener la mejor resolucion posible para tu monitor.

Luego, la ultima version de KDE es la 4.3.3 (dos o tres dias de antigüedad).
Si vas a seguir usando KDE, te sugiero agregar [sus repositorios]("http://www.kubuntu.org/news/kde-4.3.3") y actualizar para luego ver que cosas cambiaron respecto de los problemas que mencionaste.

---

### Post by electronpositivo on 2009-11-07
> **guillermolisi said:**
> Ahora esta algo mas clara la situacion.

El tema es que con video VIA estas literalmente "en el horno". Ademas cualquier componente que sea para ATI o nVidia solo complicara las cosas.

Con VIA lo mejor que podes hacer es agregar una placa adicional de las marcas mencionadas; intentar hacer funcionar los drivers Openchrome (con resultados impredecibles) o utilizar driver VESA con una configuracion adecuada del xorg.conf para obtener la mejor resolucion posible para tu monitor.

Luego, la ultima version de KDE es la 4.3.3 (dos o tres dias de antigüedad).
Si vas a seguir usando KDE, te sugiero agregar [sus repositorios]("http://www.kubuntu.org/news/kde-4.3.3") y actualizar para luego ver que cosas cambiaron respecto de los problemas que mencionaste.

OK, seguiré tus consejos los próximos días a ver si lo consigo.

Muchas gracias Guillermo. ;)

---

### Post by electronpositivo on 2009-12-14
Finalmente lo di por imposible.

Probé con la versión live de Kubuntu Karmic y nada, la sesión gráfica se reinicia continuamente... continuaré actualizando a las próximas versiones que vayan saliendo, pues por ahora no encuentro otra solución que cambiar la tarjeta gráfica y no es viable puesto que se trata de bastantes ordenadores.

Gracias

---

