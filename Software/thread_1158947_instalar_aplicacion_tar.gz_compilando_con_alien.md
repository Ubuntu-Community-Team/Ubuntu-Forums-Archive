---
title: "instalar aplicacion tar.gz compilando con alien"
date: 2009-05-14
forum: Software
---

### Post by fran280673 on 2009-05-14
hola buenos dias. 
perdonadme por mi torpeza a la hora de explicar el proceso que llevé a cabo, pero soy bastante novato con la consola. 
la versión es ubuntu 9.04. El programa es un juego llamado crossfire-client (aunque el juego es lo de menos, porque lo que quiero es aprender a compilar e instalar aplicaciones tar.gz, tar.bz, etc). El juego lo he descargado de esta página: 
[http://www.gnomefiles.org/app.php/Crossfire](http://www.gnomefiles.org/app.php/Crossfire) 
Usé alien porque, según he leido es la forma más fácil de hacerlo. 
Esto lo he hecho según guia de esta página: 
[http://www.amics-mania.com/amics/blog/?p=341](http://www.amics-mania.com/amics/blog/?p=341) 

y he hecho lo siguiente: 
1º me he descargado el juego archivo tar.gz en el escritorio. 
2º he creado una carpeta en el escritorio. 
3º he metido el archivo tar en esa carpeta. 
4º con la mini-aplicación nautilus-open-terminal he abierto consola en esa carpeta. 
5º sudo alien crossfire-client-1.11.0.tar.gz (desde esa carpeta en el escritorio). se ha creado en la misma carpeta crossfire-client_1.11.0-2_all.deb 
6º le doy doble clic e instala los repositorios. 
En synaptic me dice que los repositorios están instalados. 

hasta ahí todo bien, porque no me da ningún tipo de error, pero ahora no se como hacer para instalar el juego. Desde instalar y desinstalar programas no lo encuentro para instalarlo. 

Por favor, necesito ayuda, y muchas gracias por las respuestas que he tenido.

---

### Post by guillermolisi on 2009-05-14
> **fran280673 said:**
> hola buenos dias. 
perdonadme por mi torpeza a la hora de explicar el proceso que llevé a cabo, pero soy bastante novato con la consola. 
la versión es ubuntu 9.04. El programa es un juego llamado crossfire-client (aunque el juego es lo de menos, porque lo que quiero es aprender a compilar e instalar aplicaciones tar.gz, tar.bz, etc). El juego lo he descargado de esta página: 
[http://www.gnomefiles.org/app.php/Crossfire](http://www.gnomefiles.org/app.php/Crossfire) 
Usé alien porque, según he leido es la forma más fácil de hacerlo. 
Esto lo he hecho según guia de esta página: 
[http://www.amics-mania.com/amics/blog/?p=341](http://www.amics-mania.com/amics/blog/?p=341) 

y he hecho lo siguiente: 
1º me he descargado el juego archivo tar.gz en el escritorio. 
2º he creado una carpeta en el escritorio. 
3º he metido el archivo tar en esa carpeta. 
4º con la mini-aplicación nautilus-open-terminal he abierto consola en esa carpeta. 
5º sudo alien crossfire-client-1.11.0.tar.gz (desde esa carpeta en el escritorio). se ha creado en la misma carpeta crossfire-client_1.11.0-2_all.deb 
6º le doy doble clic e instala los repositorios. 
En synaptic me dice que los repositorios están instalados. 

hasta ahí todo bien, porque no me da ningún tipo de error, pero ahora no se como hacer para instalar el juego. Desde instalar y desinstalar programas no lo encuentro para instalarlo. 

Por favor, necesito ayuda, y muchas gracias por las respuestas que he tenido.
Lo que estas haciendo nada tiene que ver con compilar aplicaciones ya que instalar un paquete .deb o .rpm no es exactamente compilar como para aprender como se hace, sino que en el paquete ya deberian estar resueltas las situaciones de dependencias y manejo de errores que en una compilacion manual pueden no existir.

Ademas la compilacion necesariamente se inicia desde un programa fuente y no de un binario que es lo que normalmente se encuentra dentro de un paquete .deb o .rpm.
El binario es el programa compilado.

En los archivos README e INSTALL tenes, en Ingles, todas las instrucciones necesarias para configurar (con "configure") y compilar el programa (make) y de esa forma podras aprender y no solo instalar. Tambien ahi encontraras los prerequisitos de dependencias que hay que cumplimentar.

---

### Post by sajnox on 2009-05-14
Guille,

No se si no tiene nada que ver con compilar, ya que algo debe compilar ya que el tar.gz es una archivo de fuentes.

Fran, el tema es el siguiente. Si la salida de la consola no te tiro ningun error y al hacer doble click el programa se instala el unico problema que tenes es que no sabes donde esta el programa para ejecutarlo y no sabes donde buscarlo para ejecutarlo.

Es decir, se instalo pero no lo ves en el menu....no es tan grave

En primer lugar proba con el siguiente comando

```
whereis crossfire
```

Guille, si bien no es tan ortodoxo como ./configure make make_install el comando alien es de ayuda y te permite manejar los programas instalados con synaptic ya que instala desde un .deb 

Fran: Otra cosa, estas seguro que el juego que buscas no esta en los repositorios de ubuntu, es muy comun que la gente busque programas que estan en los repositorios.

Como saberlo?

```
sudo apt-get cache search crossfire
```

Contanos como viene

Saludos

---

### Post by Hei Ku on 2009-05-14
O directamente:

```

apt-cache search crossfire

```

---

### Post by fran280673 on 2009-05-14
> **sajnox said:**
> Guille,
 
No se si no tiene nada que ver con compilar, ya que algo debe compilar ya que el tar.gz es una archivo de fuentes.
 
Fran, el tema es el siguiente. Si la salida de la consola no te tiro ningun error y al hacer doble click el programa se instala el unico problema que tenes es que no sabes donde esta el programa para ejecutarlo y no sabes donde buscarlo para ejecutarlo.
 
Es decir, se instalo pero no lo ves en el menu....no es tan grave
 
En primer lugar proba con el siguiente comando
 
```
whereis crossfire
```
 
Guille, si bien no es tan ortodoxo como ./configure make make_install el comando alien es de ayuda y te permite manejar los programas instalados con synaptic ya que instala desde un .deb 
 
Fran: Otra cosa, estas seguro que el juego que buscas no esta en los repositorios de ubuntu, es muy comun que la gente busque programas que estan en los repositorios.
 
Como saberlo?
 
```
sudo apt-get cache search crossfire
```
 
Contanos como viene
 
Saludos
 
hola.
 
muchas gracias por la respuesta. lo intentaré cuando llegue a casa. Pero, he ido a instalar este juego como si hubiese instalado otro, eso es lo de menos, lo que quiero es aprender a compilar o como se llame, porque hay muchos programas que traen el archivo tar.gz o tar.bz, y es necesario que un linuxero o principiante a linuxero aprenda a compilar.
muchas gracias, y luego os cuento.

---

### Post by fran280673 on 2009-05-14
hola.

la respuesta que me da consola a este comando es:
whereis crossfire
crossfire:

la respuesta que me da consola a este comando es:
sudo apt-get cache search crossfire
[sudo] password for casaubuntu: 
Sorry, try again.
[sudo] password for casaubuntu: 
E: Operación inválida: cache
casaubuntu@casaubuntu-desktop:~$ apt-cache search crossfire
crossfire-client-gtk - GTK+ Client of the game Crossfire
crossfire-client-gtk2 - GTK+ 2 Client of the game Crossfire
crossfire-client-images - Base crossfire-client images
crossfire-client-sounds - sound files for playing crossfire
crossfire-client-x11 - XLib Client of the game Crossfire
crossfire-common - Common files for Crossfire
crossfire-doc - Documentation for Crossfire
crossfire-edit - Map editor for the Crossfire Gameset
crossfire-maps - Standard set of maps for crossfire
crossfire-maps-small - Small set of maps for crossfire
crossfire-server - Server for Crossfire Games
crossfire-client - Converted Slackware tgz package

esto es lo que me dice, no se como seguir.
muchas gracias por tu preocupacion

---

### Post by EnriqueK on 2009-05-14
Me parece que hay una confusión con esta forma de instalar programas, el uso de alien es para convertir de binarios a binarios , esto muestra Synaptic en una breve descripción
 ```
Convierte e instala paquetes rpm y de otros tipos

Alien permite convertir paquetes LSB, Red Hat, Stampede y Slackware en
paquetes Debian, que se puedan instalar con dpkg.

También puede generar paquetes en cualquiera de los otros formatos.

Esta herramienta sólo es apropiada para paquetes binarios.
```
Para mi el error está en confundir los paquetes de Slackware (creo que son tgz) con aechivos empaquetados  como por ejemplo un tar.gz u otro similar que puede poner en dudas.
Para compilar primero que nada lee las instrucciones que se encuetran dentro de la carpeta de las fuentes , normalmente son los archivos Readme o Install

---

### Post by guillermolisi on 2009-05-14
> **EnriqueK said:**
> Me parece que hay una confusión con esta forma de instalar programas, el uso de alien es para convertir de binarios a binarios , esto muestra Synaptic en una breve descripción
 ```
Convierte e instala paquetes rpm y de otros tipos

Alien permite convertir paquetes LSB, Red Hat, Stampede y Slackware en
paquetes Debian, que se puedan instalar con dpkg.

También puede generar paquetes en cualquiera de los otros formatos.

Esta herramienta sólo es apropiada para paquetes binarios.
```Para mi el error está en confundir los paquetes de Slackware (creo que son tgz) con aechivos empaquetados  como por ejemplo un tar.gz u otro similar que puede poner en dudas.
Para compilar primero que nada lee las instrucciones que se encuetran dentro de la carpeta de las fuentes , normalmente son los archivos Readme o Install
Casualmente a eso mismo me referia cuando dije lo que dije, mas alla si la estructura es propia de tal o cual distribucion.

Si la idea no es solamente instalar el juego sino aprender a compilar, entonces hay que hacer por lo menos lo que bien indica Enrique.

Se puede transformar un paquete de una distribucion a otra, rpm a deb por ejemplo, pero en la gestion de instalacion y aun habiendo compilacion y fuentes de por medio, no se aprende, solo se instala.

---

### Post by fran280673 on 2009-05-14
hola.
bueno, viendo que alien no es la forma correcta para compilar, procedo a hacerlo de la forma que me dicen que es la correcta.
Descomprimir el archivo tar:

[COLOR=Red]tar -zxvf crossfire-client.1.11.0 .tar.gz[/COLOR] (en consola desde una carpeta del escritorio)

lo descomprime perfectamente, y crea una carpeta llamada crossfire-client.1.11.0.
me cambio a la carpeta creada:

[COLOR=Red]cd crossfire-client.1.11.0[/COLOR]

Configura el programa:

[COLOR=Red]./configure[/COLOR]

y la respuesta que me da es esta:

  	 	 	 	 	 	  [COLOR=Red]casaubuntu@casaubuntu-desktop:~/Escritorio/carpeta sin título/crossfire-client-1  [/COLOR]
 [COLOR=Red].11.0$ ./configure  [/COLOR]
 [COLOR=Red]checking build system type... i686-pc-linux-gnu  [/COLOR]
 [COLOR=Red]checking host system type... i686-pc-linux-gnu  [/COLOR]
 [COLOR=Red]checking target system type... i686-pc-linux-gnu  [/COLOR]
 [COLOR=Red]checking for a BSD-compatible install... /usr/bin/install -c  [/COLOR]
 [COLOR=Red]checking whether build environment is sane... yes  [/COLOR]
 [COLOR=Red]/bin/bash: /home/casaubuntu/Escritorio/carpeta: No such file or directory  [/COLOR]
 [COLOR=Red]configure: WARNING: `missing' script is too old or missing  [/COLOR]
 [COLOR=Red]checking for gawk... no  [/COLOR]
 [COLOR=Red]checking for mawk... mawk  [/COLOR]
 [COLOR=Red]checking whether make sets $(MAKE)... yes  [/COLOR]
 [COLOR=Red]checking for mkdir... /bin/mkdir  [/COLOR]
 [COLOR=Red]checking for tar... /bin/tar  [/COLOR]
 [COLOR=Red]checking for makedepend... no  [/COLOR]
 [COLOR=Red]checking for cp... /bin/cp  [/COLOR]
 [COLOR=Red]checking for rm... /bin/rm  [/COLOR]
 [COLOR=Red]checking for perl... /usr/bin/perl  [/COLOR]
 [COLOR=Red]checking for ar... /usr/bin/ar  [/COLOR]
 [COLOR=Red]checking for pkg-config... /usr/bin/pkg-config  [/COLOR]
 [COLOR=Red]checking for svnversion... no  [/COLOR]
 [COLOR=Red]checking for style of include used by make... GNU  [/COLOR]
 [COLOR=Red]checking for gcc... gcc  [/COLOR]
 [COLOR=Red]checking for C compiler default output file name... a.out  [/COLOR]
 [COLOR=Red]checking whether the C compiler works... yes  [/COLOR]
 [COLOR=Red]checking whether we are cross compiling... no  [/COLOR]
 [COLOR=Red]checking for suffix of executables...  [/COLOR]
 [COLOR=Red]checking for suffix of object files... o  [/COLOR]
 [COLOR=Red]checking whether we are using the GNU C compiler... yes  [/COLOR]
 [COLOR=Red]checking whether gcc accepts -g... yes  [/COLOR]
 [COLOR=Red]checking for gcc option to accept ISO C89... none needed  [/COLOR]
 [COLOR=Red]checking dependency style of gcc... gcc3  [/COLOR]
 [COLOR=Red]checking how to run the C preprocessor... gcc -E  [/COLOR]
 [COLOR=Red]checking for X... no  [/COLOR]
 [COLOR=Red]checking for gcc... (cached) gcc  [/COLOR]
 [COLOR=Red]checking whether we are using the GNU C compiler... (cached) yes  [/COLOR]
 [COLOR=Red]checking whether gcc accepts -g... (cached) yes  [/COLOR]
 [COLOR=Red]checking for gcc option to accept ISO C89... (cached) none needed  [/COLOR]
 [COLOR=Red]checking dependency style of gcc... (cached) gcc3  [/COLOR]
 [COLOR=Red]checking for grep that handles long lines and -e... /bin/grep  [/COLOR]
 [COLOR=Red]checking for egrep... /bin/grep -E  [/COLOR]
 [COLOR=Red]checking for ANSI C header files... yes [/COLOR]
 [COLOR=Red]checking for sys/types.h... yes  [/COLOR]
 [COLOR=Red]checking for sys/stat.h... yes  [/COLOR]
 [COLOR=Red]checking for stdlib.h... yes  [/COLOR]
 [COLOR=Red]checking for string.h... yes  [/COLOR]
 [COLOR=Red]checking for memory.h... yes  [/COLOR]
 [COLOR=Red]checking for strings.h... yes  [/COLOR]
 [COLOR=Red]checking for inttypes.h... yes  [/COLOR]
 [COLOR=Red]checking for stdint.h... yes  [/COLOR]
 [COLOR=Red]checking for unistd.h... yes  [/COLOR]
 [COLOR=Red]checking whether byte ordering is bigendian... no  [/COLOR]
 [COLOR=Red]configure: WARNING: X11 not found - will not build X client  [/COLOR]
 [COLOR=Red]checking for gtk-config... no  [/COLOR]
 [COLOR=Red]checking for GTK - version >= 1.0.0... no  [/COLOR]
 [COLOR=Red]*** The gtk-config script installed by GTK could not be found  [/COLOR]
 [COLOR=Red]*** If GTK was installed in PREFIX, make sure PREFIX/bin is in  [/COLOR]
 [COLOR=Red]*** your path, or set the GTK_CONFIG environment variable to the  [/COLOR]
 [COLOR=Red]*** full path to gtk-config.  [/COLOR]
 [COLOR=Red]configure: WARNING: GTK 1 not found - not building building gtk-v1 client  [/COLOR]
 [COLOR=Red]checking for GTK2... configure: WARNING: GTK+ 2 libraries not found - will not build gtk-v2 client  [/COLOR]
 [COLOR=Red]checking whether to enable maintainer-specific portions of Makefiles... no  [/COLOR]
 [COLOR=Red]checking for pthread_create in -lpthread... yes  [/COLOR]
 [COLOR=Red]checking for main in -lGL... no  [/COLOR]
 [COLOR=Red]checking for main in -lGLU... no  [/COLOR]
 [COLOR=Red]checking for main in -lopengl32... no  [/COLOR]
 [COLOR=Red]checking for main in -lglu32... no  [/COLOR]
 [COLOR=Red]checking for main in -lglut... no  [/COLOR]
 [COLOR=Red]checking for a BSD-compatible install... /usr/bin/install -c  [/COLOR]
 [COLOR=Red]checking whether ln -s works... yes  [/COLOR]
 [COLOR=Red]checking whether make sets $(MAKE)... (cached) yes  [/COLOR]
 [COLOR=Red]checking how to run the C preprocessor... gcc -E  [/COLOR]
 [COLOR=Red]checking for ranlib... ranlib  [/COLOR]
 [COLOR=Red]checking for main in -lasound... no  [/COLOR]
 [COLOR=Red]checking for alNewConfig in -laudio... no  [/COLOR]
 [COLOR=Red]checking alsa/asoundlib.h usability... no  [/COLOR]
 [COLOR=Red]checking alsa/asoundlib.h presence... no  [/COLOR]
 [COLOR=Red]checking for alsa/asoundlib.h... no  [/COLOR]
 [COLOR=Red]checking sys/soundcard.h usability... yes  [/COLOR]
 [COLOR=Red]checking sys/soundcard.h presence... yes  [/COLOR]
 [COLOR=Red]checking for sys/soundcard.h... yes  [/COLOR]
 [COLOR=Red]checking sys/audioio.h usability... no  [/COLOR]
 [COLOR=Red]checking sys/audioio.h presence... no  [/COLOR]
 [COLOR=Red]checking for sys/audioio.h... no  [/COLOR]
 [COLOR=Red]Using OSS sound system  [/COLOR]
 [COLOR=Red]checking for main in -lossaudio... no  [/COLOR]
 [COLOR=Red]checking for sdl-config... no  [/COLOR]
 [COLOR=Red]checking for SDL - version >= 1.1.3... no  [/COLOR]
 [COLOR=Red]*** The sdl-config script installed by SDL could not be found  [/COLOR]
 [COLOR=Red]*** If SDL was installed in PREFIX, make sure PREFIX/bin is in  [/COLOR]
 [COLOR=Red]*** your path, or set the SDL_CONFIG environment variable to the  [/COLOR]
 [COLOR=Red]*** full path to sdl-config.  [/COLOR]
 [COLOR=Red]checking for main in -lXext... no  [/COLOR]
 [COLOR=Red]checking for gawk... (cached) mawk  [/COLOR]
 [COLOR=Red]checking for curl-config... no  [/COLOR]
 [COLOR=Red]checking whether libcurl is usable... no  [/COLOR]
 [COLOR=Red]checking for sqrt in -lm... yes  [/COLOR]
 [COLOR=Red]checking for main in -lz... yes  [/COLOR]
 [COLOR=Red]checking for main in -lpng... yes  [/COLOR]
 [COLOR=Red]checking for ANSI C header files... (cached) yes  [/COLOR]
 [COLOR=Red]checking fcntl.h usability... yes  [/COLOR]
 [COLOR=Red]checking fcntl.h presence... yes  [/COLOR]
 [COLOR=Red]checking for fcntl.h... yes  [/COLOR]
 [COLOR=Red]checking sys/ioctl.h usability... yes  [/COLOR]
 [COLOR=Red]checking sys/ioctl.h presence... yes  [/COLOR]
 [COLOR=Red]checking for sys/ioctl.h... yes  [/COLOR]
 [COLOR=Red]checking sys/time.h usability... yes  [/COLOR]
 [COLOR=Red]checking sys/time.h presence... yes  [/COLOR]
 [COLOR=Red]checking for sys/time.h... yes  [/COLOR]
 [COLOR=Red]checking for unistd.h... (cached) yes  [/COLOR]
 [COLOR=Red]checking for string.h... (cached) yes  [/COLOR]
 [COLOR=Red]checking sys/select.h usability... yes  [/COLOR]
 [COLOR=Red]checking sys/select.h presence... yes  [/COLOR]
 [COLOR=Red]checking for sys/select.h... yes  [/COLOR]
 [COLOR=Red]checking pthread.h usability... yes  [/COLOR]
 [COLOR=Red]checking pthread.h presence... yes  [/COLOR]
 [COLOR=Red]checking for pthread.h... yes  [/COLOR]
 [COLOR=Red]checking curl/curl.h usability... no  [/COLOR]
 [COLOR=Red]checking curl/curl.h presence... no  [/COLOR]
 [COLOR=Red]checking for curl/curl.h... no  [/COLOR]
 [COLOR=Red]configure: error: curl/curl.h header not found, but metaserver2 support is enable.  Install header file or use --disable-metaserver2  [/COLOR]
 [COLOR=Red]casaubuntu@casaubuntu-desktop:~/Escritorio/carpeta sin título/crossfire-client-1  [/COLOR]
 [COLOR=Red].11.0$ 
[/COLOR]


[COLOR=Red][COLOR=Black]como novato que soy no entiendo esto, pero supongo que me faltan dependencias. qué dependencias me faltan por instalar, y como las instalo?[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]el archivo install me dice lo siguiente:[/COLOR][/COLOR]


Install Steps:

0) Prerequisites:
    You will need the XPM library to compile the client.
    If you want to run the gtk client, you will need to install the gtk
    libraries.
    If you want png support, you will need to install the png
    library.
    If you want sdl support ( recommended) you will need both gtk and png
    as well as the main SDL library and the SDL_image library, both of
    which can be found at [http://www.libsdl.org](http://www.libsdl.org) if not already installed
    on your system.

1)  type './configure' to configure for your OS/system.  Most options
    normally understood by configure should be available.
    The configure script will try to make all the right decisions.  It will
    search for the needed libraries and headers.   You may need to give
    hints on the locations of some files (png library, gtk library).

    If configure finds gtk libraries, it will build the gcfclient in addition
    to the cfclient.  If you don't want this (only cfclient), use the
    --disable-gtk (there is no way to disable the cfclient at this time -
    if you are able to compile the gtk client, you also have all the tools for
    for the cfclient).

    If SDL libraries are found on your system, SDL support is automatically
    compiled it (Note: only the gcfclient supports sdl). Use --disable-sdl
    if you don't want this.

    The system will use the new sound system if available (this is a separate
    sound daemon).  If you want to use the built-in sound system, use
    the --enable-old-sound.  See sound notes further down.

    To specify additional places to find header files, use the
    --with-includes=value - this includes any -I or other options to provide
    the compiler.  Example:
    ./configure --with-includes="-I/usr/local/include -I/opt/xpm/include"

    Similarly, there is a --with-ldflags option.  Example:
    ./configure --with-ldflags="-L/usr/local/lib -R/usr/local/lib"
    -R is used on many systems to specify run location for libraries so
    you don't need to set LD_LIBRARY_PATH.

    Generally, if you are setting --with-includes, your probably need to
    set --with-ldflags, as if one is not in a standard place, the other
    probably is not either.

    The client works with the 0.5 version of the ALSA sound system.
    If you are using a newer version and are having troubles compiling,
    try running configure with the '--disable-alsa' option.

2) Type 'make depend; make' to compile the client. If you get link errors,
    it may be because you have an older version of the gtk libraries.  If
    you get errors like 'can't find target client.c', your make program
    isn't very good and use should get/use gnu make instead.

3)  Type 'make install' to install the binaries.

4)  The client can be run by typing 'cfclient' for the X11 version, gcfclient
     for the gtk client, gcfclient -sdl for the SDL version.

por favor, necesito que me ayudeis a descifrar este galimatias.
muchisimas gracias.

---

### Post by Hei Ku on 2009-05-14
Podes probar instalando el paquete libgnome-dev

Anda a tomarte un cafe porque debe ser grandecito.

---

### Post by EnriqueK on 2009-05-14
Te voy a dar un par de tips que e ayudarán a realizar copilaciones 
1.- Cuando el copilador te indica que tiene un error por que está faltando una librería, lo pri,ero que debes hacer es tomar nota de esa librería y según la nomenclatura impuesta por Debian, a este nombre le debes agregar el término lib antes del nombre, por ejemplo si te está pidiendo por ejemplo cairo , lo que debes buscar es libcairo y por supuesto la versión que te está pidiendo, esto se ve muy fácilmente usando Synaptic.
2.- Es muy común encontrarse en que te está pidiendo una librería, pero luego de usar Synaptic notas que ya la tienes instalada, lo que sucede es que en realidad te está pidiendo es la cabecera de dicha librería y estas terminan en -dev , para el ejemplo anterior sería libcairo-dev y así en base a esta simple explicación ya podrás ir poco a poco intentando compilar y ante cada error que marque configure, vas instalado las librerías que te está pidiendo y no te olvides de descargar además la librería cabecera. Una vez que configure de sin error, recién continuas con make y sudo make install.
En caso de no encontrar alguna librería en los repositorios mediante Synaptic, recién como última alternativa las buscas mediante Google y seguramente tendrás que bajar su código fuente, la tendraas que compilar e instalar y luego reción continua con la compilación principal
Pra tu caso, creo que lo que te está pidiendo es la librería libcurl y su cabecera libcurl-dev, buscala y descargala medianmte Synaptic.

---

### Post by guillermolisi on 2009-05-14
Algo que me llamo la atencion apenas lei el resultado de la corrida del script es esto:
> [COLOR=Red]casaubuntu@casaubuntu-desktop:~/Escritorio/carpeta sin título/crossfire-client-1  [/COLOR]
 [COLOR=Red].11.0$ ./configure  [/COLOR]
 [COLOR=Red]checking build system type... i686-pc-linux-gnu  [/COLOR]
 [COLOR=Red]checking host system type... i686-pc-linux-gnu  [/COLOR]
 [COLOR=Red]checking target system type... i686-pc-linux-gnu  [/COLOR]
 [COLOR=Red]checking for a BSD-compatible install... /usr/bin/install -c  [/COLOR]
 [COLOR=Red]checking whether build environment is sane... yes  [/COLOR]
 [COLOR=Red]/bin/bash: /home/casaubuntu/Escritorio/carpeta: No such file or directory  [/COLOR]
 [COLOR=Red]configure: WARNING: `missing' script is too old or missing[/COLOR][COLOR=Red] 
[COLOR=Black]Las dos ultimas lineas citadas hablan sobre un problema de referencia a un directorio. Este problema sucede porque hay un directorio que incluye espacios en blanco en su nombre y si esto no se maneja adecuadamente sucede lo que te muestra la anteultima linea: Lee el nombre hasta el primer blanco porque generalmente los blancos se usan para separar campos (opciones/parametros/nombres_de_archivos/listas) y tambien para indicar que ahi termina un string de caracteres.

Renombra ese directotio reemplazando los blancos por "guiones bajos" y volve a probar. No deberian salir mas esas dos ultimas lineas indicando que no encuentra un directorio y ese WARNING.

Todo esto agregado a las indicaciones que ya te han hecho.
[/COLOR][/COLOR]

---

### Post by fran280673 on 2009-05-15
> **guillermolisi said:**
> Algo que me llamo la atencion apenas lei el resultado de la corrida del script es esto:
 
[COLOR=red][COLOR=black]Las dos ultimas lineas citadas hablan sobre un problema de referencia a un directorio. Este problema sucede porque hay un directorio que incluye espacios en blanco en su nombre y si esto no se maneja adecuadamente sucede lo que te muestra la anteultima linea: Lee el nombre hasta el primer blanco porque generalmente los blancos se usan para separar campos (opciones/parametros/nombres_de_archivos/listas) y tambien para indicar que ahi termina un string de caracteres.[/COLOR]
 
[COLOR=red]Renombra ese directotio reemplazando los blancos por "guiones bajos" y volve a probar. No deberian salir mas esas dos ultimas lineas indicando que no encuentra un directorio y ese WARNING.[/COLOR]
 
[COLOR=red]Todo esto agregado a las indicaciones que ya te han hecho.[/COLOR]
[/COLOR]
 
muchisimas gracias a todos. ahora estoy en el curro, pero cuando salga lo miraré y comprobaré lo que me decis.
 
gracias.

---

### Post by fran280673 on 2009-05-15
hola, despues de instalar esta libreria libnome-dev, he ./configure, y me sale esto:
casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for mkdir... /bin/mkdir
checking for tar... /bin/tar
checking for makedepend... no
checking for cp... /bin/cp
checking for rm... /bin/rm
checking for perl... /usr/bin/perl
checking for ar... /usr/bin/ar
checking for pkg-config... /usr/bin/pkg-config
checking for svnversion... no
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
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
configure: X11 found - will build X client
Xlibs: -lX11
Extras:
Xpre: -lSM -lICE
checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.0.0... yes
configure: GTK 1 found - building gtk client
checking for GTK2... configure: WARNING: GTK+ 2 libraries not found - will not build gtk-v2 client
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pthread_create in -lpthread... yes
checking for main in -lGL... no
checking for main in -lGLU... no
checking for main in -lopengl32... no
checking for main in -lglu32... no
checking for main in -lglut... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking for main in -lasound... no
checking for alNewConfig in -laudio... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
Using OSS sound system
checking for main in -lossaudio... no
checking for sdl-config... no
checking for SDL - version >= 1.1.3... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
checking for main in -lXext... yes
checking for gawk... (cached) mawk
checking for curl-config... /usr/bin/curl-config
checking for the version of libcurl... 7.18.2
checking whether libcurl is usable... yes
checking for curl_free... yes
checking for sqrt in -lm... yes
checking for main in -lz... yes
checking for main in -lpng... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for string.h... (cached) yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking curl/curl.h usability... yes
checking curl/curl.h presence... yes
checking for curl/curl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking whether gcc needs -traditional... no
checking for vprintf... yes
checking for _doprnt... no
checking for mkdir... yes
checking for socket... yes
checking for strcspn... yes
checking for sysconf... yes
checking for getaddrinfo... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk/Makefile
config.status: WARNING:  gtk/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x11/Makefile
config.status: WARNING:  x11/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/Makefile
config.status: WARNING:  common/Makefile.in seems to ignore the --datarootdir setting
config.status: creating sound-src/Makefile
config.status: WARNING:  sound-src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/Makefile
config.status: WARNING:  gtk-v2/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pixmaps/Makefile
config.status: WARNING:  pixmaps/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/src/Makefile
config.status: WARNING:  gtk-v2/src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: WARNING:  help/Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/config.h
config.status: executing depfiles commands
configure: 
configure: Configuration summary....
configure: 
configure:   Paths
configure:     prefix default value                 /usr/local
configure:     exec_prefix default value            ${prefix}
configure:     Will put executables in              ${exec_prefix}/bin
configure:     Will put config in                   ${prefix}/etc
configure: 
configure:   Build options
configure:     Will build GTK1 client?              yes 
configure:     Will build GTK2 client?              no
configure:     Will build OpenGL renderer?          no
configure:     Will build SDL renderer?             no
configure:     Will build sound server?             yes  (OSS)
casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ 

por favor, no se que librerias tengo que instalar más. muchas gracias por las respuestas.

---

### Post by guillermolisi on 2009-05-15
Por lo pronto librerias GTK2, segun la ultima linea que cito:
> checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.0.0... yes
configure: GTK 1 found - building gtk client
checking for GTK2... configure: WARNING: GTK+ 2 libraries not found - will not build gtk-v2 client

Mas abajo resulta
> checking for main in -lossaudio... no
checking for sdl-config... no
checking for SDL - version >= 1.1.3... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
Es que estan faltan componentes de desarrollo (**devel**opment) de SDL para el audio.
En Synaptic busca SDL y te traera todos los paquetes relacionados.

Corregi eso (y tal vez alguna otra cosita que te lleguen a indicar) y volve a probar.

---

### Post by Hei Ku on 2009-05-15
Instala los paquetes libgtk2.0-dev y libsdl1.2-dev

---

### Post by fran280673 on 2009-05-15
hola, he instalado todas las librerias que he visto que me comentabais, y al hacer un configure, me sale esto:
casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for mkdir... /bin/mkdir
checking for tar... /bin/tar
checking for makedepend... no
checking for cp... /bin/cp
checking for rm... /bin/rm
checking for perl... /usr/bin/perl
checking for ar... /usr/bin/ar
checking for pkg-config... /usr/bin/pkg-config
checking for svnversion... no
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
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
configure: X11 found - will build X client
Xlibs: -lX11
Extras:
Xpre: -lSM -lICE
checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.0.0... yes
configure: GTK 1 found - building gtk client
checking for GTK2... yes
configure: GTK+ 2 found - will build gtk-v2 client
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pthread_create in -lpthread... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lopengl32... no
checking for main in -lglu32... no
checking for main in -lglut... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking for main in -lasound... yes
checking for alNewConfig in -laudio... no
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
Using ALSA sound system (0.9.x)
Using OSS sound system
checking for main in -lossaudio... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.3... yes
checking for IMG_LoadPNG_RW in -lSDL_image... yes
sdl image detected!
checking for main in -lXext... yes
checking for gawk... (cached) mawk
checking for curl-config... /usr/bin/curl-config
checking for the version of libcurl... 7.18.2
checking whether libcurl is usable... yes
checking for curl_free... yes
checking for sqrt in -lm... yes
checking for main in -lz... yes
checking for main in -lpng... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for string.h... (cached) yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking curl/curl.h usability... yes
checking curl/curl.h presence... yes
checking for curl/curl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking whether gcc needs -traditional... no
checking for vprintf... yes
checking for _doprnt... no
checking for mkdir... yes
checking for socket... yes
checking for strcspn... yes
checking for sysconf... yes
checking for getaddrinfo... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk/Makefile
config.status: WARNING:  gtk/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x11/Makefile
config.status: WARNING:  x11/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/Makefile
config.status: WARNING:  common/Makefile.in seems to ignore the --datarootdir setting
config.status: creating sound-src/Makefile
config.status: WARNING:  sound-src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/Makefile
config.status: WARNING:  gtk-v2/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pixmaps/Makefile
config.status: WARNING:  pixmaps/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/src/Makefile
config.status: WARNING:  gtk-v2/src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: WARNING:  help/Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/config.h
config.status: common/config.h is unchanged
config.status: executing depfiles commands
configure: 
configure: Configuration summary....
configure: 
configure:   Paths
configure:     prefix default value                 /usr/local
configure:     exec_prefix default value            ${prefix}
configure:     Will put executables in              ${exec_prefix}/bin
configure:     Will put config in                   ${prefix}/etc
configure: 
configure:   Build options
configure:     Will build GTK1 client?              yes 
configure:     Will build GTK2 client?              yes
configure:     Will build OpenGL renderer?          yes
configure:     Will build SDL renderer?             yes
configure:     Will build sound server?             yes  (Alsa 0.9.x) (OSS)

y después he hecho un make y me ha salido esto:

casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ make
Making all in common
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
OUTPUT_DATA='/* Auto-generated at build time. */'; \
    if test -n "" -a -d .svn; then \
        OUTPUT_DATA=`echo "$OUTPUT_DATA"; echo -n '#define SVN_REV "';  -n`'"'; \
    fi; \
    if test ! -e svnversion.h; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    elif test "$OUTPUT_DATA" != "`cat svnversion.h`"; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    fi
make  all-am
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
OUTPUT_DATA='/* Auto-generated at build time. */'; \
    if test -n "" -a -d .svn; then \
        OUTPUT_DATA=`echo "$OUTPUT_DATA"; echo -n '#define SVN_REV "';  -n`'"'; \
    fi; \
    if test ! -e svnversion.h; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    elif test "$OUTPUT_DATA" != "`cat svnversion.h`"; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    fi
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
Making all in pixmaps
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/pixmaps'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/pixmaps'
Making all in utils
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/utils'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/utils'
Making all in help
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/help'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/help'
Making all in x11
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/x11'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/x11'
Making all in gtk
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk'
Making all in gtk-v2
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
Making all in src
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2/src'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2/src'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
Making all in sound-src
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/sound-src'
/usr/bin/perl -p -e s#/usr/local/lib/sounds#/crossfire-client/sounds# ./sounds.dist > sounds
/usr/bin/perl ../utils/deftoheader.pl sounds soundsdef.h def_sounds
199 lines processed
if gcc -DHAVE_CONFIG_H -I. -I. -I../common  -I../common   -g -O2 -DALSA9_SOUND -DOSS_SOUND -Wall -MT cfsndserv.o -MD -MP -MF ".deps/cfsndserv.Tpo" -c -o cfsndserv.o cfsndserv.c; \
    then mv -f ".deps/cfsndserv.Tpo" ".deps/cfsndserv.Po"; else rm -f ".deps/cfsndserv.Tpo"; exit 1; fi
cfsndserv.c: En la función ‘play_sound’:
cfsndserv.c:764: aviso: se descarta el valor de devolución de ‘fread’, se declaró con el atributo warn_unused_result
gcc  -g -O2 -DALSA9_SOUND -DOSS_SOUND -Wall   -o cfsndserv  cfsndserv.o -lm  -lpng -lz -lm -lGLU -lGL -lpthread  -lcurl -lidn -lssl -lcrypto -llber -lldap -lrt -lgssapi_krb5 -lgssapi_krb5 -lssl -lcrypto -lz
if gcc -DHAVE_CONFIG_H -I. -I. -I../common  -I../common   -g -O2 -DALSA9_SOUND -DOSS_SOUND -Wall -MT alsa9.o -MD -MP -MF ".deps/alsa9.Tpo" -c -o alsa9.o alsa9.c; \
    then mv -f ".deps/alsa9.Tpo" ".deps/alsa9.Po"; else rm -f ".deps/alsa9.Tpo"; exit 1; fi
alsa9.c: En la función ‘play_sound’:
alsa9.c:364: aviso: se descarta el valor de devolución de ‘fread’, se declaró con el atributo warn_unused_result
gcc  -g -O2 -DALSA9_SOUND -DOSS_SOUND -Wall   -o cfsndserv_alsa9  alsa9.o -lasound -lm  -lpng -lz -lm -lGLU -lGL -lpthread  -lcurl -lidn -lssl -lcrypto -llber -lldap -lrt -lgssapi_krb5 -lgssapi_krb5 -lssl -lcrypto -lz
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/sound-src'
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0'
make[1]: No se hace nada para `all-am'.
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0'
casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ 

decidme por favor, y muchas gracias por vuestra paciencia.

---

### Post by Hei Ku on 2009-05-15
ehh, termino bien. :D

que dicen las instrucciones para el proximo paso?

sudo make install?

---

### Post by fran280673 on 2009-05-16
hola. en sudo make install sale esto:

casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ sudo make install
Making install in common
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
OUTPUT_DATA='/* Auto-generated at build time. */'; \
    if test -n "" -a -d .svn; then \
        OUTPUT_DATA=`echo "$OUTPUT_DATA"; echo -n '#define SVN_REV "';  -n`'"'; \
    fi; \
    if test ! -e svnversion.h; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    elif test "$OUTPUT_DATA" != "`cat svnversion.h`"; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    fi
make  install-am
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
OUTPUT_DATA='/* Auto-generated at build time. */'; \
    if test -n "" -a -d .svn; then \
        OUTPUT_DATA=`echo "$OUTPUT_DATA"; echo -n '#define SVN_REV "';  -n`'"'; \
    fi; \
    if test ! -e svnversion.h; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    elif test "$OUTPUT_DATA" != "`cat svnversion.h`"; then \
        echo "$OUTPUT_DATA" > svnversion.h; \
    fi
make[3]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
make[3]: No se hace nada para `install-exec-am'.
make[3]: No se hace nada para `install-data-am'.
make[3]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/common'
Making install in pixmaps
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/pixmaps'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/pixmaps'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/pixmaps'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/pixmaps'
Making install in utils
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/utils'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/utils'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/utils'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/utils'
Making install in help
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/help'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/help'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/help'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/help'
Making install in x11
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/x11'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/x11'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'cfclient' '/usr/local/bin/cfclient'
test -z "/usr/local/share/man/man6" || mkdir -p -- "/usr/local/share/man/man6"
 /usr/bin/install -c -m 644 './cfclient.man' '/usr/local/share/man/man6/cfclient.6'
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/x11'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/x11'
Making install in gtk
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'gcfclient' '/usr/local/bin/gcfclient'
test -z "/usr/local/share/man/man6" || mkdir -p -- "/usr/local/share/man/man6"
 /usr/bin/install -c -m 644 './gcfclient.man' '/usr/local/share/man/man6/gcfclient.6'
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk'
Making install in gtk-v2
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
Making install in src
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2/src'
make[3]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'gcfclient2' '/usr/local/bin/gcfclient2'
make[3]: No se hace nada para `install-data-am'.
make[3]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2/src'
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2/src'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
make[3]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
make[3]: No se hace nada para `install-exec-am'.
make[3]: No se hace nada para `install-data-am'.
make[3]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/gtk-v2'
Making install in sound-src
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/sound-src'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/sound-src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'cfsndserv' '/usr/local/bin/cfsndserv'
  /usr/bin/install -c 'cfsndserv_alsa9' '/usr/local/bin/cfsndserv_alsa9'
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/sound-src'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0/sound-src'
make[1]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0'
make[2]: se ingresa al directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0'
make[1]: se sale del directorio `/home/casaubuntu/Escritorio/carpetasintítulo/crossfire-client-1.11.0'
casaubuntu@casaubuntu-desktop:~/Escritorio/carpetasintítulo/crossfire-client-1.1
1.0$ 

si esto es correcto ahora que hago?

muchas gracias.

---

### Post by staar on 2009-05-16
ya está instalado, ahora corrés gcfclient2 y listo...

saludos

---

### Post by fran280673 on 2009-05-16
hola.
para ejecutarlo, me voy a consola y escribo:
gcfclient2
 
verdad?
 
Perdonadme amigos, pero aunque llevo un tiempo con ubuntu, no he manejado nunca la consola.
 
muchisimas gracias por todo.

---

### Post by Hei Ku on 2009-05-16
O fijate si te instalo algo en el menu.
Que es lo que dice el README del programa. Generalmente traen un archivo con las instrucciones. Si es un programa grafico, te debe agregar el link en el menu.

---

### Post by fran280673 on 2009-05-17
hola.

al fin esta instalado, aunque el juego no vale nada, pero es mi primera compilación. no aparece en el menu, pero he buscado la carpeta y me he encontrado con esto /usr/local/bin/cfclient.

muchisimas gracias por todo, lo hemos conseguido. digo lo hemos, porque sin vosotros hubiese sido imposible. sois geniales.

seguiré compilando otras aplicaciones, y así seguir aprendiendo.

chao.

---

### Post by Hei Ku on 2009-05-17
Para desinstarlo, en la misma carpeta que pusiste sudo make install, pones sudo make uninstall.

---

### Post by fran280673 on 2009-05-17
hola.
ya lo he desinstalado.
conoceis alguna pagina web desde la cual poder descargar software para ubuntu  archivos tar.

muchas gracias,

---

### Post by pablo.s on 2009-05-17
Si, tienes por ejemplo:

[SourceForge]("http://sourceforge.net/")
[Berlios]("http://www.berlios.de/")
[GnomeFiles]("http://www.gnomefiles.org/")

en cada uno de ellos hay
archivos de fuentes para
compilar. Muuuuuchos.

---

