---
title: "Error al instalar tema de sonidos"
date: 2009-08-07
forum: Software
---

### Post by sergiom99 on 2009-08-07
Hola gente, 
tengo un problema con las notificaciones de sonido de Empathy (para Gtalk)
Buscando, encontre la causa: 
> 
**I can't hear any sound notifications**

In Ubuntu the sound themes doesn't contain yet the sounds needed by Empathy, there is a bug reported on Launchpad. At the moment you can use this sound theme ([http://people.freedesktop.org/~mccann/dist/sound-theme-freedesktop-0.2.tar.bz2](http://people.freedesktop.org/~mccann/dist/sound-theme-freedesktop-0.2.tar.bz2)). Make sure the sound notification are activated both in Empathy preference and Gnome sound properties. You will also need to set the sound theme to Default instead of Ubuntu. [1]

Resulta que al bajar el tema y tratar de instalarlo con los clasicos './configure; make; make install' me salen estos errores:
```

**$ ./configure **
checking for a BSD-compatible install... /usr/bin/install -c   
checking whether build environment is sane... yes              
checking for a thread-safe mkdir -p... /bin/mkdir -p           
checking for gawk... gawk                                      
checking whether make sets $(MAKE)... yes                      
checking whether NLS is requested... yes                       
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
checking dependency style of gcc... none                       
checking for intltool >= 0.40.0... 0.40.6 found                
checking for intltool-update... /usr/bin/intltool-update       
checking for intltool-merge... /usr/bin/intltool-merge         
checking for intltool-extract... /usr/bin/intltool-extract     
checking for xgettext... /usr/bin/xgettext                     
checking for msgmerge... /usr/bin/msgmerge                     
checking for msgfmt... /usr/bin/msgfmt                         
checking for gmsgfmt... /usr/bin/msgfmt                        
checking for perl... /usr/bin/perl                             
checking for XML::Parser... ok                                 
checking how to run the C preprocessor... gcc -E               
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
checking locale.h usability... yes                             
checking locale.h presence... yes                              
checking for locale.h... yes                                   
checking for LC_MESSAGES... yes                                
checking libintl.h usability... yes                            
checking libintl.h presence... yes                             
checking for libintl.h... yes                                  
checking for ngettext in libc... yes                           
checking for dgettext in libc... yes                           
checking for bind_textdomain_codeset... yes                    
checking for msgfmt... (cached) /usr/bin/msgfmt                
checking for dcgettext... yes                                  
checking if msgfmt accepts -c... yes                           
checking for gmsgfmt... (cached) /usr/bin/msgfmt               
checking for xgettext... (cached) /usr/bin/xgettext            
configure: creating ./config.status                            
config.status: creating Makefile                               
config.status: creating stereo/Makefile                        
config.status: creating po/Makefile.in                         
config.status: executing depfiles commands                     
config.status: executing default-1 commands                    
config.status: executing po/stamp-it commands                  
**$ make        **
Making all in stereo                                           
make[1]: se ingresa al directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/stereo'
make[1]: No se hace nada para `all'.                                                    
make[1]: se sale del directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/stereo'  
Making all in po                                                                        
make[1]: se ingresa al directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/po'    
make[1]: No se hace nada para `all'.                                                    
make[1]: se sale del directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/po'      
make[1]: se ingresa al directorio `/home/sergio/temp/sound-theme-freedesktop-0.2'       
/usr/bin/intltool-merge  ; /usr/bin/intltool-merge ./po index.theme.in index.theme -d -u -c ./po/.intltool-merge-cache
Usage: intltool-merge [OPTION]... PO_DIRECTORY FILENAME OUTPUT_FILE                                                   
Generates an output file that includes some localized attributes from an                                              
untranslated source file.                                                                                             

Mandatory options: (exactly one must be specified)
  -b, --ba-style         includes translations in the bonobo-activation style
  -d, --desktop-style    includes translations in the desktop style          
  -k, --keys-style       includes translations in the keys style             
  -s, --schemas-style    includes translations in the schemas style          
  -r, --rfc822deb-style  includes translations in the RFC822 style           
      --quoted-style     includes translations in the quoted string style    
      --quotedxml-style  includes translations in the quoted xml string style
  -x, --xml-style        includes translations in the standard xml style     

Other options:
  -u, --utf8             convert all strings to UTF-8 before merging
                         (default for everything except RFC822 style)
  -p, --pass-through     deprecated, does nothing and issues a warning
  -m, --multiple-output  output one localized file per locale, instead of
                         a single file containing all localized elements
  -c, --cache=FILE       specify cache file name
                         (usually $top_builddir/po/.intltool-merge-cache)
  -q, --quiet            suppress most messages
      --help             display this help and exit
      --version          output version information and exit

Report bugs to http://bugzilla.gnome.org/ (product name "intltool")
or send email to <xml-i18n-tools@gnome.org>.
Generating and caching the translation database
Merging translations into index.theme.
make[1]: se sale del directorio `/home/sergio/temp/sound-theme-freedesktop-0.2'
**$ make install**
Making install in stereo
make[1]: se ingresa al directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/stereo'
make[2]: se ingresa al directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/stereo'
make[2]: No se hace nada para `install-exec-am'.
test -z "/usr/local/share/sounds/freedesktop/stereo" || /bin/mkdir -p "/usr/local/share/sounds/freedesktop/stereo"
/bin/mkdir: no se puede crear el directorio «/usr/local/share/sounds»: Permiso denegado
make[2]: *** [install-soundDATA] Error 1
make[2]: se sale del directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/stereo'
make[1]: *** [install-am] Error 2
make[1]: se sale del directorio `/home/sergio/temp/sound-theme-freedesktop-0.2/stereo'
make: *** [install-recursive] Error 1


```

Que me falta? Que esta mal? Porque a mi? :D

Tengo Kubuntu JJ actualizado al dia.

[1] [http://live.gnome.org/Empathy/FAQ#head-abaca5d3b9aa0775c6c3f3588ddb064e5632228e](http://live.gnome.org/Empathy/FAQ#head-abaca5d3b9aa0775c6c3f3588ddb064e5632228e)

---

### Post by pablo.s on 2009-08-07
Creo que lo que estás
tratando de compilar
aparece en [este PPA]("https://launchpad.net/%7Echeleb/+archive/ppa").
Chequealo, puede ser 
eso que buscás.

---

### Post by sergiom99 on 2009-08-07
gracias Pablo!
Es eso y se instaló OK.
Ahora tengo que encontrar en que parte de KDE cambio el tema de sonido...

---

### Post by guillermolisi on 2009-08-07
> **sergiom99 said:**
> gracias Pablo!
Es eso y se instaló OK.
Ahora tengo que encontrar en que parte de KDE cambio el tema de sonido...
Is this thread solved ? :cool:

---

### Post by sergiom99 on 2009-08-07
> **guillermolisi said:**
> Is this thread solved ? :cool:

Not yet... KDE4 parece no tener un lugar para cambiar el tema de sonido... que vuelva Kcontrol!!!

---

### Post by pablo.s on 2009-08-07
Acá no te puedo ayudar
porque KDE y yo nunca
pegamos onda.
En QT4Config no se puede
modificar?

---

### Post by guillermolisi on 2009-08-07
Sergio, no termino de entender bien que es lo que queres hacer pero .... lo que buscas no esta en System Settings ?

---

### Post by sergiom99 on 2009-08-07
> **guillermolisi said:**
> Sergio, no termino de entender bien que es lo que queres hacer pero .... lo que buscas no esta en System Settings ?

No, o por lo menos esta BIEN escondido. Tampoco en QT4Settings.

Quiero instalar un tema de sonidos, que incluya sonidos para los eventos de Empathy.

---

### Post by guillermolisi on 2009-08-07
Extractado de userbase.kde.org:> 
**kcontrol no longer exists **

 kcontrol no longer exists. Use the program systemsettings instead. 
**Included, at least in KDE 4.2.1**


Estoy indagando en Systems Settings y en el site que mencione, hasta ahora no encontre nada que siquiera me de un indicio para modificar el sistema de sonidos ....

---

### Post by sergiom99 on 2009-08-07
Guille, yo tampoco pude encontrar demasiado en google. ](*,)


se habra caido el mito de que en KDE podias configurar hasta lo que no existe?

asi era con Kcontrol :cry:

---

### Post by staar on 2009-08-07
para cambiar los sonidos del sistema (por lo menos de las aplicaciones KDE) es System Settings > Notificaciones > Notificaciones del sistema, ir a al menú deplegable y salen los diferentes subsistemas a los que podés modificar, pero si es una aplicación de gnome no sé si se podrá...

saludos

---

### Post by guillermolisi on 2009-08-07
Confirmado.

En System Settings - Notifications vas a poder habilitar los sonidos que quieras siempre que tengas los archivos correspondientes en /usr/share/sounds que es el path que toma por defecto como repositorio de sonidos.

O sea que si pones en ese directorio los sonidos nuevos, luego es cuestion de configurar cual debe actuar con que accion y en que momento.

KDE4.3

---

### Post by Hei Ku on 2009-08-07
Sergio, sobre el error original al compilar, el problema fue que no usaste sudo, por eso te dio error de permiso denegado. ;)

---

### Post by sergiom99 on 2009-08-07
> **guillermolisi said:**
> Confirmado.

En System Settings - Notifications vas a poder habilitar los sonidos que quieras siempre que tengas los archivos correspondientes en /usr/share/sounds que es el path que toma por defecto como repositorio de sonidos.

O sea que si pones en ese directorio los sonidos nuevos, luego es cuestion de configurar cual debe actuar con que accion y en que momento.

KDE4.3

Gracias Guille, el problema es que solo podes elegir aplicaciones ya predeterminadas. Es como dijo staar, si no son las de KDE no las podes agregar, como es el caso de Empathy.

> **Hei Ku said:**
> Sergio, sobre el error original al compilar, el problema fue que no usaste sudo, por eso te dio error de permiso denegado. ;)
Gracias Alvaro.

Creo que queda 'Solved' por resignacion.

---

### Post by guillermolisi on 2009-08-07
> **sergiom99 said:**
> Gracias Guille, el problema es que solo podes elegir aplicaciones ya predeterminadas. Es como dijo staar, si no son las de KDE no las podes agregar, como es el caso de Empathy.


Gracias Alvaro.

Creo que queda 'Solved' por resignacion.
Ahora me resisto yo :)

Seguramente hay una forma de incorporar una aplicacion instalada por el usuario a la lista de aplicaciones "conocidas" por KDE.

---

### Post by Hei Ku on 2009-08-07
Es parte del nuevo sistema de notificaciones de KDE. Un area en pugna, sobre todo en Ubuntu que quiere imponer su version "mutilada", no solo a gnome sino a los otros desktops.

---

### Post by pablo.s on 2009-08-07
> **Hei Ku said:**
> Un area en pugna, sobre todo en Ubuntu que quiere imponer su version "mutilada", no solo a gnome sino a los otros desktops.

No se si este tema que le
pasa a Sergio es para culpar
a Ubuntu o a KDE. Me parece
que el tema es que está probando
una versión que no está muy
afinada todavia. Igualmente
si quiere probar un software
de mensajeria instantanea que
tenga soporte de KDE más Gmail,
está [Synapse]("http://synapse.im/").

---

### Post by Hei Ku on 2009-08-07
Me refiero a que toda el area de notificaciones esta en movimiento constante, incluso a nivel de opendesktop.org, con nuevas especificaciones de ambos lados, asi que en general esta bastante "crudo".
En principio, los frameworks de KDE y de Gnome no son compatibles.

Probaste KCall?

---

### Post by staar on 2009-08-07
e instalando el gnome-control-center (con su linda cantidad de dependencias) y modificando lo necesario en el gnome-sound-properties?

saludos

---

### Post by pablo.s on 2009-08-07
> **Hei Ku said:**
> Probaste KCall?

Quien, yo? No. 
C´est pour quoi?

---

### Post by Hei Ku on 2009-08-07
Ce n'est pas pour toi.

Sergio, probaste KCall?
Y la opcion de Staar de usar el panel de control de gnome no es mala idea. Para nada.

---

### Post by sergiom99 on 2009-08-07
> **staar said:**
> e instalando el gnome-control-center (con su linda cantidad de dependencias) y modificando lo necesario en el gnome-sound-properties?

Lo pense, pero me molesta que enchastre todo arrastrando medio Gnome para cumplir dependencias.

> **Hei Ku said:**
> 
Probaste KCall?
No, voy a investigar si soporta VoIP con Gtalk.

> **pablo.s said:**
> No se si este tema que le pasa a Sergio es para culpar a Ubuntu o a KDE. Me parece que el tema es que está probando
una versión que no está muy afinada todavia. Igualmente
si quiere probar un software de mensajeria instantanea que
tenga soporte de KDE más Gmail, está [Synapse]("http://synapse.im/").
Por lo que vi, no tiene el soporte del VoIP de Gtalk. 

Empathy si lo tiene. Me funciona aceptablemente, pero no emite sonidos de notificacion. Como lo uso para trabajar desde casa, me pierdo un monton de mensajes por estar lejos de la PC.

Kcontrol, en KDE3, estaba barbaro, podias configurar un monton de cosas. Porque se habra perdido? System Settings es muy basico, se "gnomizo" :-)

---

### Post by Hei Ku on 2009-08-07
> **sergiom99 said:**
> 
Empathy si lo tiene. Me funciona aceptablemente, pero no emite sonidos de notificacion. Como lo uso para trabajar desde casa, me pierdo un monton de mensajes por estar lejos de la PC.

Kcontrol, en KDE3, estaba barbaro, podias configurar un monton de cosas. Porque se habra perdido? System Settings es muy basico, se "gnomizo" :-)

Fijate si podes configurar Epiphany para que emita algo. Desde adentro de Epiphany.

Por otro lado, fijate si Qutecom te sirve.


Adiviná quienes hicieron el systemsettings, y vas a entender por qué parece "gnomizo".

---

### Post by sergiom99 on 2009-08-08
Hei Ku, estuve mirando las páginas de Kcall y Qutecom. Según entiendo, ambos son aplicaciones VoIP  (softphones) pero usando el protocolo SIP, algo así como ekiga, pero lo que yo hago con empathy/telepathy es usar el canal de voz del Gtalk (Nadie lo usa??)

Supongo que donde pusiste epiphany era en realidad empathy, no?
Bueno, ahí tengo puesto que haga ruido en cada evento, hasta los que me molestan, pero según su propia página no vienen sonidos para estos eventos en los sound schemes estándar. Es por eso que arrancó esto, para instalar un esquema nuevo y asociarle sonidos a estos eventos.

Y volvemos de nuevo a.... quién corno sacó Kcontrol??!!

---

### Post by guillermolisi on 2009-08-08
The Ubuntu Desktop Team ?

Tadavia no busque, pero si hay una wish list para la proxima version de KDE anoto lo de Kcontrol.

De ultima, que sea implementado como plug in, add on, enhancement/improvement, etc.

---

### Post by Hei Ku on 2009-08-08
Considerando quien hizo systemsettings, yo iria a pedir al lugar correcto
[http://brainstorm.forum.kde.org](http://brainstorm.forum.kde.org)

---

