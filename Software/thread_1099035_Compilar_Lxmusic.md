---
title: "Compilar: Lxmusic"
date: 2009-03-17
forum: Software
---

### Post by NickCis on 2009-03-17
Hola, recientemente me propuse la tarea de compilar un programa. Quise probar la suite completa lxde (cosa que no esta en lo repositorios) y lo ultimo que me falto es el LXmusic (es una interfas grafica de xmms2).

Me baje el source de la pagina de lxde del sourceforge ( [http://sourceforge.net/project/showfiles.php?group_id=180858](http://sourceforge.net/project/showfiles.php?group_id=180858) ).

Las instrucciones eran estas:
```
To build this program, you have to install following developing packages:

pkg-config
gtk+ 2.0
xmms2-client
xmms2-client-glib

The last 2 dev packages are provided by xmms2, and will be installed when you install
 xmms2 from tarball.
Since LXMusic is only a GUI frontend, you should have xmms2 in order to use it.
See the official homepage of XMMS2 project <http://wiki.xmms2.xmms.se/> for detail.

After you get these required packages installed, just type "make", and 
LXMusic will be compiled. Then, type "make install" with root access, and lxmusic
will be installed to /usr/bin.

```

Entonces instale las cosas necesarias:
```

sudo apt-get install build-essential xmms2 pkg-config
```
Despues fui hasta la carpeta donde descomprimi el archivo, hice un make y me aparecio esto en consola:
```
make: *** No se especifico ningun objetivo y no se encontro ningun makefile. Alto.
```

Si hago "./configure":
```
oldpc@oldpc:~/lxmusic-0.2.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for XMMSC... configure: error: Package requirements (xmms2-client >= 0.5	xmms2-client-glib) were not met:

No package 'xmms2-client' found
No package 'xmms2-client-glib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XMMSC_CFLAGS
and XMMSC_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

oldpc@oldpc:~/lxmusic-0.2.3$ 
```
Y si dsp hago un make el mismo problema de arriba.

Que puede estar pasando?, tengo que compilar tambien el xmms2?

Saludos.

P.D: tengan en cuenta que es la primera vez que compilo, perdonenme por cualquier error de novato xD..

---

### Post by pablo.s on 2009-03-17
[http://twemu.no-ip.org/apt/lxmusic/](http://twemu.no-ip.org/apt/lxmusic/)

---

### Post by NickCis on 2009-03-17
Ok, muchas gracias.

Ahora tengo una pregunta, si yo quiero actualizar estos programas, pero la vercion de los repositorios sigue siendo vieja. Como hago para desde el source (que esta en [http://sourceforge.net/project/showfiles.php?group_id=180858](http://sourceforge.net/project/showfiles.php?group_id=180858) y [http://sourceforge.net/project/showfiles.php?group_id=156956](http://sourceforge.net/project/showfiles.php?group_id=156956) ) actualizarlos?.

Tengo que primero crear el deb y despues actualizar?, si es asi como creo un paquete deb desde el source?

Saludos.


Edit: intente instalar el nuevo panel, lo compile todo bien, pero parece que se murio el plugin del menu, no tengo menu de aplicaciones :S...

---

### Post by pablo.s on 2009-03-17
> **NickCis said:**
> Ok, muchas gracias.

Ahora tengo una pregunta, si yo quiero actualizar estos programas, pero la vercion de los repositorios sigue siendo vieja. Como hago para desde el source (que esta en [http://sourceforge.net/project/showfiles.php?group_id=180858](http://sourceforge.net/project/showfiles.php?group_id=180858) y [http://sourceforge.net/project/showfiles.php?group_id=156956](http://sourceforge.net/project/showfiles.php?group_id=156956) ) actualizarlos?.

Tengo que primero crear el deb y despues actualizar?, si es asi como creo un paquete deb desde el source?.

Cuando compilás un programa no se arma un paquete. Se crean ejecutables y las librerias que corresponden. Armar un paquete implica mucho mas que compilar.
Si llega a pasar que necesitás la ultimisima versión y no encontrás en ningun repositorio ni PPA el paquete, lo compilás. Pero no te rompas el siete si te es muy complicado. Podés pedir ayuda por acá. Igual ya que te interesa el tema de armar paquetes podés ver [esto]("https://wiki.ubuntu.com/MOTU/Videos") que es muy interesante


> **NickCis said:**
> Saludos.

Edit: intente instalar el nuevo panel, lo compile todo bien, pero parece que se murio el plugin del menu, no tengo menu de aplicaciones :S...

Nuevo panel?

---

### Post by NickCis on 2009-03-18
Si, el panel del lxde, el lxpanel.

Parece que hay un bug o algo asi con la nueva vercion, y no existe el plugin de menu, como podria desinstalarlo y volver a la vercion de los repositorios?.

Saludos.

---

### Post by pablo.s on 2009-03-18
Si lo reinstalas desde el repositorio seguramente va a sobreescribir los archivos que compilaste. En este mismo momento lo estoy probando desde el repositorio de Jaunty, supongo que es la última versión (ya que dice 0.3.2.1+svn) y funciona correctamente.

A proposito hoy salió la versión 2.26 de GNOME. No tiene grandes novedades, basicamente tiene  ****GTK+ 2.16, algunas APIs nuevas para integrar, Empathy tiene soporte de videollamadas (se ve interesante), y alguna que otra cosita. Podria hacer un nuevo thread para esto pero veo que hay muchachada que hincha para KDE y hay que quedarse en el molde. Saludos.

---

### Post by NickCis on 2009-03-18
Pude solucionarlo haciendo un "sudo make uninstall" y despues volviendo a instalar la barra desde lo repositorios... :P

Tengo este problema al instalar lxmusic desde el deb que me pasaste

```
oldpc@oldpc:~/deb$ sudo dpkg -i lxmusic*
[sudo] password for oldpc: 
Seleccionando el paquete lxmusic previamente no seleccionado.
(Leyendo la base de datos ...  
53475 ficheros y directorios instalados actualmente.)
Desempaquetando lxmusic (de lxmusic_0.2.3-1+svn090103_i386.deb) ...
dpkg: problemas de dependencias impiden la configuración de lxmusic:
 lxmusic depende de libxmmsclient-glib1 (>= 0.5DrLecter); sin embargo:
  La versión de `libxmmsclient-glib1' en el sistema es 0.2DrJekyll-4ubuntu4.
 lxmusic depende de libxmmsclient4 (>= 0.5DrLecter); sin embargo:
  El paquete `libxmmsclient4' no está instalado.
dpkg: error al procesar lxmusic (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 lxmusic
oldpc@oldpc:~/deb$ 

```
Alguna idea?

Offtopic: si, no se por que pero hay muychos qe inchan por kde en este foro, estamos rodeados, hablemos mientras podamos (??) XD

---

### Post by pablo.s on 2009-03-18
Mmmm mira, la última que te queda es probar con instalar todo LXDE desde el PPA de el proyecto, a ver que tal resulta: [**https://launchpad.net/~lxde/+archive/ppa**]("https://launchpad.net/%7Elxde/+archive/ppa") . Mas centros no te puedo tirar, che.

Yo no uso KDE porque Stallman me dijo hace mucho que no era software libre. Me incitó a usar GNOME y a rezarle a San Ignucius para que no me fuera al infierno. Después se puso una túnica negra y un plato de cobre de un disco rigido muy viejo en la cabeza y salió a pontificar las cuatro libertades esenciales por ahi.

Saludos.

---

### Post by NickCis on 2009-03-19
Yo instale lxde desde esos repositorios, el problema es que lxmusic no esta ahi, la lista de programas que estan ahi son:
```
* PCManFM: File manager, provides desktop icons, currently has 2 branches
    * PCManFM experimental branch, with support for mounting fuse network filesystem (smbnetfs, sshfs, curlftpfs)
    * PCManFM legacy stable branch, this is the old version of the file manager without the fuse fs support
* LXPanel: Desktop panel, based on FBPanel
* LXSession: X11 session manager
    * lxsession with x session management protocol support, partially broken code
    * lxsession-lite has that part of the code removed
* GPicView: A very simple, fast, and lightweight image viewer featuring immediate startup.
* lxappearance: A handy program to switch gtk themes
* lxlauncher: a launcher for the eeepc
* lxnm: a network manager
* lxtask: a task manager

NEW:
* lxrandr: a tool to set up your screen via xrandr
* lxterminal: simple, lightweight and useful terminal program
```

Viendo el problema que tenia, segun lo que tengo entendio es un problema de dependencias con el xmms2. Nececito libxmmsclient-glib1 y libxmmsclient4 . Como y de donde las puedo instalar?.

Saludos, muchas gracias por ayudar.

Offtopic: jajajaj, cuando agarre mi primer linux, no use uno con KDE, por que estaba cambiando de SO, no queria que se viera parecido al winchot que tenia antes

---

### Post by pablo.s on 2009-03-19
[http://packages.ubuntu.com/hardy/libxmmsclient-glib1](http://packages.ubuntu.com/hardy/libxmmsclient-glib1) - [http://packages.ubuntu.com/intrepid/libxmmsclient4](http://packages.ubuntu.com/intrepid/libxmmsclient4)

No hay de qué. Saludos.

PD: hoy tuve que compilar Mplayer bajado de git. Compiló todo muy bien pero no le puse las opciones que queria y después me dió fiaca compilarlo con las flags asi que lo bajé de un PPA.

---

### Post by NickCis on 2009-03-19
Aca encontre la raiz del problema!
Yo estoy usando hardy Heron, la vercion de libxmmsclient-glib1 de los repositorios es vieja, tendria que conseguir una mas actualizada. La de los repos de ubuntu es 0.2DrJeckyl y nececito la 0.5DrLecter.
Despues el otro paquete, libxmmsclient4, directamente no esta en los repositorios de Hardy :(.

Alguna idea de donde puedo sacar estos paquetes, ambos en la vericon 0.5DrLecter (o superior) para hardy?.

Saludos.

Edit: Solucionado. En la pagina de xmms2 te dan unos repositorios para tener una vercion mas actualizada.
Link de launchpad: [https://launchpad.net/~bdrung/+archive/ppa](https://launchpad.net/~bdrung/+archive/ppa)
Repos:
Hardy
```
deb http://ppa.launchpad.net/bdrung/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/bdrung/ppa/ubuntu hardy main
```
Intrepid:
```
deb http://ppa.launchpad.net/bdrung/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/bdrung/ppa/ubuntu intrepid main
```

Fuente: [http://wiki.xmms2.xmms.se/wiki/Download_XMMS2](http://wiki.xmms2.xmms.se/wiki/Download_XMMS2)

Gracias por toda la ayuda!!

---

