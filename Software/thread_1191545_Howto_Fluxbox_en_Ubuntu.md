---
title: "Howto: Fluxbox en Ubuntu"
date: 2009-06-19
forum: Software
---

### Post by nopersona on 2009-06-19
Howto rescatado del antiguo foro. Trataré de irlo actulizando para mantenerlo completo.

**Howto: Fluxbox en Ubuntu**

En este Howto trataré de aclarar bastantes dudas al momento de querer usar Fluxbox en nuestro querido Ubuntu. Si bien la información que está en la red es suficiente, a veces las redundancias resultan un poco difusas, y si a esto le sumamos el brusco cambio desde gnome, el resultado, para todo aquel que quiere probar este entorno, es desastroso. Sí señores, en Fluxbox tenemos que trabajar &#8220;con las manitos&#8221; y con &#8220;la cabecita&#8221;, no hay apliaciones que hacen todo por nosotros, y si las queremos, hay que ponerlas, o compilarlas.. Si queremos ventanas lindas hay que hacerlas, si queremos menús lindos, hay que hacerlos, en fin... al final el resultado será fabuloso. Un entorno limpio, bello, veloz y funcional. 

Manos a la obra. 


**1.INSTALANDO FLUXBOX**

En los respositorios podemos encontrar la versión 0.9.15.1+1.0rc2-1 de Fluxbox, que es la última disponible. En synaptic seleccionaremos lo siguiente para tener un entorno medianamente utilizable:

[B]1.- Fluxbox 
2.- Backstep 
3.- Alltray 
4.- Bbpager
5.- Bbtime
6.- Fbpager
7.- Bbrun
8.- Kdocker[/B]

**2.CONFIGURANDO LO BÁSICO**

 No creo que haya mayores inconvenientes al momento de instalar los paquetes. Fluxbox y todos sus componentes se instalarán y, al momento de reiniciar, en nuestro GDM, aparecerá la opción Fluxbox. Comienza la diversión.

    La primera visión después de la carga de 2 segundos (qué velocidad niñ@s!) es un fondo sin imágen, un barra semi cortada abajo y si damos click con el botón derecho tendremos el menú de Fluxbox. Todo muy simple. Hasta puede parecer feo. Horrible. Calma. 

    Lo primero que haremos es ir a nuestro Home y comprobar que existe el directorio .fluxbox Allí guardaremos parte de la configuración. Si llegasen a faltar los archivos init, menu, y titlebar, simplemente los tomamos de /usr/local/share/fluxbox y los copiamos a .fluxbox (también pueden estar en /usr/share/fluxbox) 

    En Fluxbox la apariencias del menú, de los botones de las ventanas y de la barra, se llaman &#8220;styles&#8221;. Los styles son simples configuraciones hechas en editores de texto sencillos, aunque poseen una gran eficiencia.  Dos muy buenos lugares donde encontrar styles son:

[http://www.box-look.org/index.php?xcontentmode=7400](http://www.box-look.org/index.php?xcontentmode=7400)
[http://customize.org/fluxbox](http://customize.org/fluxbox)


Yo te tomado mi style de aquí:

[http://www.box-look.org/content/show.php/Conceptual?content=67019](http://www.box-look.org/content/show.php/Conceptual?content=67019)

y lo he modificado según mis necesidades. En el menú de fluxbox podrán cambiar los styles que gusten. Para agregar un estile al menú, en este caso el nuestro, en el directorio .fluxbox crearemos una carpeta con el nombre styles, allí guardaremos todas nuestros temas. Si a alguien le interesa, mi style es el siguiente: (simplemente descargan el tema ya señalado, descomprimen en  .fluxbox/styles, y reemplazan el theme.cfg por este)

```
! Neo-conceptual by No-Persona
toolbar.borderWidth:         0
toolbar.borderColor:            #272c30
toolbar:                        Flat Solid
toolbar.shaped:                 false
toolbar.height:                 22
toolbar.clock:                  Flat Solid
toolbar.clock.color:            #272c30
toolbar.clock.textColor:        #bfc0d0
toolbar.clock.justify:          Right
toolbar.alpha:                  200
toolbar.color:                  #272c30
toolbar.label:                  ParentRelative
toolbar.windowLabel:            ParentRelative
toolbar.button:                 ParentRelative
toolbar.button.pressed:         Flat Solid
toolbar.button.pressed.color:   #272c30
toolbar.button*picColor:        #272c30
toolbar.textColor:              #bfc0d0
toolbar.justify:                center
toolbar.workspace.textColor:    #bfc0d0
toolbar.pixmap: toolbar.xpm
toolbar.clock.pixmap: toolbar.xpm
toolbar.workspace.pixmap: toolbar.xpm
toolbar.iconbar.focused: Flat Solid
toolbar.iconbar.unfocused: Flat Solid
toolbar.iconbar.empty: Flat Solid
toolbar.iconbar.focused.pixmap: toolbar_focus.xpm
toolbar.iconbar.unfocused.pixmap: toolbar.xpm
toolbar.iconbar.empty.pixmap: toolbar.xpm
toolbar.iconbar.focused.borderWidth: 0
window.title.focus:             Flat Solid
window.title.focus.color:       #272c30
window.title.unfocus:           Flat Solid
window.title.unfocus.color:     #272c30
window.label.focus:             ParentRelative
window.label.focus.textColor:   #eeeeee
window.label.unfocus:           ParentRelative
window.label.unfocus.textColor: #9394a2
window.button.focus:            ParentRelative
window.button.focus.picColor:   #272c30
window.button.unfocus:          ParentRelative
window.button.unfocus.picColor: #272c30
window.button.pressed:          ParentRelative
window.handle.focus:            Flat Solid
window.handle.focus.color:      #272c30
window.handle.unfocus:          Flat Solid
window.handle.unfocus.color:    #272c30
window.grip.focus:              Flat Solid
window.grip.unfocus:            Flat Solid
window.grip.focus.color:        #272c30
window.grip.unfocus.color:      #272c30
window.justify:                 center
window.bevelWidth:              0
window.title.height:            16
window.handleWidth:             1
window.alpha:                   200
window.close.pixmap:                            close.xpm
window.close.pressed.pixmap:                    close.xpm
window.close.unfocus.pixmap:                    close.xpm
window.iconify.pixmap:                          icon.xpm
window.iconify.pressed.pixmap:                  icon.xpm
window.iconify.unfocus.pixmap:                  icon.xpm
window.maximize.pixmap:                         max.xpm
window.maximize.pressed.pixmap:                 max.xpm
window.maximize.unfocus.pixmap:                 max.xpm
window.shade.pixmap:                            shade.xpm
window.shade.pressed.pixmap:                    shade.xpm
window.shade.unfocus.pixmap:                    shade.xpm
window.shade.focus.pixmap:                      shade.xpm
window.menuicon.pixmap:                         menuicon.xpm
window.menuicon.unfocus.pixmap:                 menuicon.xpm
window.menuicon.focus.pixmap:                   menuicon.xpm
window.menuicon.pressed.pixmap:                 menuicon.xpm
window.stick.pixmap:                            stick.xpm
window.stick.unfocus.pixmap:                    stick.xpm
window.stick.focus.pixmap:                      stick.xpm
window.stick.pressed.pixmap:                    stick.xpm
window.font: Avantgarde LT Medium-12
window.justify: left
window.borderWidth: 1
menu.title:                     Flat Solid
menu.frame:                     Flat Solid
menu.hilite:                    Flat Solid
menu.title.color:               #272c30
menu.title.textColor:           #eeeeee
menu.title.font:                Avantgarde LT Medium-12
menu.title.justify:             Center
menu.itemHeight:                8
menu.frame.color:               #272c30
menu.frame.textColor:           #9394a2
menu.frame.justify:             Left
menu.submenu.pixmap:            bullet.xpm
menu.hilite.color:              #272c30
menu.hilite.textColor:          #eeeeee
menu.bullet:                    Empty
menu.bullet.position:           Right
menu.alpha:                     100
menu.borderWidth:               1
borderColor:                    #272c30
bevelWidth:                     0
borderWidth:                    0
handleWidth:                    1
*Font:                          Avantgarde LT Medium-13
*color:   #728188
*colorTo: 728188
```Ahora el tema &#8220;conceptual&#8221; aparecerá en el menú de styles. Ya tenemos lo básico. 



**3.- CONFIGURANDO LO NO TAN BÁSICO: MENÚS, ENTORNO, ÍCONOS, FONDO DE PANTALLA Y EL FAMOSO GTK. **

Ahora comienza el baile. Si se dieron cuenta el menú de fluxbox trae varias aplicaciones que no necesitamos, o menús que no nos gustan. También es bastante complicado (para el que nunca ha usado este entorno) ingresar al navegador de ficheros, en mi caso Thunar (no tengo nada contra ustedes si usan nautilus xd) si logran ingresar, por ejemplo haciendo un $ thunar, dirán: HORROR!!! los iconos y el tema del navegador, y los de cualquier aplicación, son los que por defecto (a veces ni eso)&#8220;fluxbox encuentra a mano&#8221;, en definitiva, los menos agraciados. Todos esto tiene solución.  Después de darme cabezasos 2 semanas por páginas rusas (sí, en ninguna otra parte encontré una solución que diera resultado) di con la clave. El truco para que nuestro navegador de ficheros y nuestras aplicaciones reconozcan el tema GTK y los íconos que nosotros queremos, es bastante sencillo, pero es un trabajo de precisión. 

Comienzo por lo más delicado para que después trabajemos tranquilos:

Lo primero es definir nuestro tema GTK y los íconos en la sesión de Gnome. Sí, en Gnome. 

Los que yo elegí son los siguientes:

GTK
[http://www.gnome-look.org/content/show.php/ClearClossy-Grey?content=46052](http://www.gnome-look.org/content/show.php/ClearClossy-Grey?content=46052)

Iconos: Oxygen Icons 0.3.5.7.5
[http://www.gnome-look.org/content/show.php/gtk-oxygen-theme+%22icons%2Cwallp.%2Ctheme%22?content=63893]("http://www.gnome-look.org/content/show.php/gtk-oxygen-theme+%22icons%2Cwallp.%2Ctheme%22?content=63893")

Es preferible que el tema sea con colores definidos, así nos ahorramos una cuántos ajustes. 

Luego copiamos el tema y los íconos en:

/usr/share/themes
/usr/share/icons


Así nos aseguramos que fluxbox los encontrará.  Después de  estos pequeños ajustes volvemos a Flubox.  Ahora viene **el GRAN truco.** 

En nuestro home se encuentra un archivos llamado &#8220;.gtkrc-2.0&#8221; (si no es así, simplemente lo creamos) En ese archivos podemos indicar ciertas características que deseamos para nuestro entorno, por ejemplo, algunas personas aceleran la carga de los menús insertando un pequeño script.  Lo que nosotros haremos será forzar la carga del tema definido anteriormente, le indicaremos a nuestro navegador de ficheros y a todas las aplicaciones, qué tema y qué iconos deben emplear. Si gtkrc-2.0 tiene algo escrito, podemos hacer una copia o simplemente borrarla, no sucederá nada si borramos su contenido (pueden conservar el script de los menús) al contrario, las cosas se complicarán ( en Gnome) si escribimos algo erróneo. Lo que copiaremos en gtkrc-2.0 será:  

```
gtk-font-name = "Sans 11"
include "/usr/share/themes/ClearClossy-grey/gtk-2.0/gtkrc"
gtk-icon-theme-name = "Oxygen-Gnome"

```**Donde:**

**gtk-font-name:** corresponde a la tipografía y al tamaño de esta para nuestras aplicaciones.

**include:** la ruta exacta de nuestro tema GTK

**gtk-icon-theme-name:** el nombre de nuestro tema de íconos en /usr/share/icons


Ese es **el GRAN truco**, sencillo no?. Ahora reiniciamos Fluxbox y... sorpresa, nuestro navegador de ficheros y nuestras aplicaciones se ven como en gnome! 

Ahora bien, es bueno comprobar si la configuración de  .gtkrc-2.0 no ha afectado a Gnome, esto lo notaremos de 2 maneras, una más traumática que la otra: 

1.- Al cargar Gnome, si usamos conky, notaremos que el proceso del &#8220;theme&#8221; gasta casi el 80% o 90% de la CPU. Mal indicio. Volver a Fluxbox y configurar el  .gtkrc-2.0 nuevamente. También se puede hacer desde Gnome. 

2.- Al cargar Gnome...Al cargar Gnome...Al cargar Gnome... nada, ni gnome ni nautilus cargarán, todo se quedará en el splash. CRTL+ALT+BORRAR. Y configurar el  .gtkrc-2.0 nuevamente.

Esto podría llegar a ser lo más molesto a la hora de configurar Fluxbox correctamente, lo digo por experiencia. 

Otra cosa. Si deseamos cambiar el theme, ya sea el GTK o el de los íconos, SIEMPRE hacerlo desde GNOME y no desde Fluxbox, por qué?, porque si lo hacemos desde Fluxbox, modificando el .gtkrc-2.0, al momento de querer entrar a Gnome, este querrá entrar al tema antes asignado, pero como estamos forzando otra configuración en  .gtkrc-2.0, el chiquillo se quedará pegado, es como decirle a un perro que ladre callado. Desde Gnome vamos al archivo  .gtkrc-2.0, borramos su contenido, cambiamos el tema con las opciones de gnome, y cargamos las nuevas rutas en  .gtkrc-2.0. Sólo eso. Con esto nos evitamos todos los problemas. Ya hemos hecho lo más complejo.

Si desean que sus aplicaciones root tengan el mismo tema, basta con copiar el .gtkrc-2.0 a su directorio root. 


**3.1. MENÚS Y FONDO DE PANTALLA**

Volvemos a Fluxbox, esto está cobrando vida, se dan cuenta? Pero todavía nos faltan un par de cosas. Por defecto fluxbox no posee herramientas gráficas para ciertas útiles aplicaciones, como por ejemplo, algo para los fondos de pantalla, esto lo solucionaremos con Nitrogen.

Nitrogen depende de:

gcc - (4.2.0)
m4 - (1.4.9)
libtool - (1.5.22)
automake - (1.10)
autoconf &#8211; (2.61)
pkg-config &#8211; (0.21)
GTK2+ - (2.10.12)
Gtkmm - (2.10.0)

Desde su web nos podemos bajar un .Deb para instalar. 
[http://l3ib.org/nitrogen/](http://l3ib.org/nitrogen/)

Lo bueno y práctico de nitrogen es que especificando el directorio de las imágenes, inmediatamente estas son cargadas a la lista, no es necesario añadirlas una a una como la herramienta de gnome. 

Después de instalarlo bastará con abrir un terminal y escribir: nitrogen la_ruta_de_las_imagenes

y aparecerá en nuestra pantalla. 

[[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1476280Pantallazo-1.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo1-1476280.html")

Para que nitrogen guarde el fondo, debemos agregralo al inicio de Fluxbox en el archivo starup de nuestro .fluxbox, agregándole una & al final, quedaría más o menos así:
> 
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
adesklets &
#conky &
**nitrogen --restore &**
update-notifier &Si deseamos cargar algo al inicio, simplemente agregamos el comando más una & al final.  Ya tenemos wallpaper. 


Ahora, la gran tarea es modificar el menú de Fluxbox a nuestro gusto. Esto se puede hacer a &#8220;mano&#8221; editando el archivo menú, pero encontré una aplicación gráfica bastante útil: Fluxbox Menú Editor.

Con esta aplicación podemos modificar el menú a nuestro gusto, agregar separadores, submenús y hasta íconos de manera muy sencilla. El único requisito es que hay que compilarlo. Algo complicado para los más novatos, pan comido para los más familizarizados.

Desde la web de Fluxbox Menú Editor podemos bajarnos el último paquete para compilar.

[http://fme.rhymux.info/download/](http://fme.rhymux.info/download/)

Fluxbox Menú Editor depende de:

gcc - (4.1.1)
 m4 - (1.4.
libtool - (1.5.22)
make - (3.81)
automake - (1.9.10)
autoconf - (2.61)
pkg-config - (0.21)
gettext - (0.16.1)
bison - (2.3)
Librerías
Gtkmm - (2.10.0)
Libglademm - (2.6.3)
Libsigc++ - (2.0.16)
Boost - (1.33.1)


Una vez desembalado, podemos compilarlo de la siguiente forma:

Abrir terminal en la ruta del directorio y 
 
```
./configure &#8211;disable-dependency-tracking
```esto acelera la compilación, después, lo de siempre:

```
# make
# su (contraseña)
# make install
```Para lanzarlo escribimos en un terminal: 

[[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1476270Pantallazo.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo-1476270.html")

Ahora podemos editar el menú a nuestro antojo. Si quieren poner íconos estos deben ser en formato .xpm Yo sólo uso unos pocos para el inicio.


Si queremos íconos en el escritorio, les recomiendo usar idesk, y si quieren poner desklets, usen Adesklest, en este otro Howto especifiqué cómo hacerlo. 

[http://foros.ubuntu-cl.org/viewtopic.php?t=2809&highlight=](http://foros.ubuntu-cl.org/viewtopic.php?t=2809&highlight=)



Ahora, si quieren una barrita distinta a Yab de los Adesklest, pueden probar Wbar. Está escrita en C++, es liviana y bastante atractiva. 

Depende de:

*imlib2-dev

La descargan desde acá

[http://freshmeat.net/projects/wbar/](http://freshmeat.net/projects/wbar/)

Luego lo de siempre. Abrimos terminal en el directorio y, como root:

```
make
make install
```Para que Wbar se ejecute necesitamos crear un archivo llamado .wbar en nuestro home. Lo podemos tomar desde /usr/share/wbar/dot.wbar, luego lo copiamos  al home como .wbar y listo, allí guardaremos nuestra configuración.

Para llamar a Wbar simplemente escribirmos en un terminal

```
wbar
```Un  punto en contra es su posición, hasta el momento sólo es posible ubicarla arriba o abajo de nuestra pantalla. Adjunto  los parámetros para ello si alguien desea experimentar.

# Options:
#   -config conf-file (eg: $HOME/.wbar)
#   -above-desk       run over a desktop app (ie: xfdesktop)
#   -isize  i         icon size (eg: 32)
#   -idist  d         icon dist (eg: 1)
#   -zoomf  z         zoom factor (eg: 1.8 or 2.5)
#   -jumpf  j         jump factor (eg: 1.0 or 0.0)
#   -pos    p         position:
#                        top | bottom | left | right | 
#                        center | <bot|top>-<right|left>
#   -dblclk ms        ms for double click (0: single click)
#   -bpress           icon gets pressed
#   -vbar             vertical bar
#   -balfa  i         bar alfa (0-100)
#   -falfa  i         unfocused bar alfa (0-100)
#   -filter i         color filter (0: none 1: hovered 2: others, 3: all)
#   -fc  0xAARRGGBB   filter color (default green 0xff00c800)
#   -nanim  i         number of animated icons: 1, 3, 5, 7, 9, ...
#   -nofont           if set disables font rendering

[IMG]http://download.freshmeat.net/screenshots/61844.png[/IMG]

Si todo ha salido bien, tendremos Fluxbox corriendo en nuestro pc y dándole nueva vida a Ubuntu. El resto es imaginación. 



Como es la primera versión de este  Howto acepto sugerencias, dudas, reclamos y se validan todas las faltas ortográficas y de sintaxis que se me colaron. 

Y como no, las caps. 

**Quién dijo que Fluxbox era feo?** 


[[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1475845Pantallazo-1.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo1-1475845.html") [[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1475850Pantallazo-2.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo2-1475850.html")
[[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1478597Pantallazo-2.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo2-1478597.html") [[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1543677Pantallazo-3.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo3-1543677.html")

  
Si quieren velocidad extrema, también pueden probar instalando **Rox File** (disponible desde synaptic)  para navegar por sus directorios... si tan solo tuviese el soporte para unidades como Thunar. De todos modos, es una real bala, en español y con vista para imágenes en miniatura 


  [[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1543700Pantallazo-4.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo4-1543700.html")

*****TIPS*****

Acá pueden encontrar unos cuántos tips que les ayudarán a configurar cosas menores, como el formato de la hora, las ventanas, barras y muchas otras cosas. (ojo que el tip para GTK que allí aparece NO DA RESULTADO. Utilizen el de este howto) 

[http://www.damog.net/?p=544](http://www.damog.net/?p=544)

[http://fluxbox-wiki.org/index.php/Category:Espa%C3%B1ol_/_Spanish_howtos](http://fluxbox-wiki.org/index.php/Category:Espa%C3%B1ol_/_Spanish_howtos)

[http://www.gentoo.org/doc/es/fluxbox-config.xml](http://www.gentoo.org/doc/es/fluxbox-config.xml)



Para lo de la fecha y la hora recomiendo darle un ojo al formato strftime.

De todas formas, el que use para que se viera como el del panel de gnome fue (esto lo modifican en .fluxbox/init) el siguiente:

```
session.screen0.strftimeFormat:    %a %d %b - %R
```[http://www.php.net/strftime](http://www.php.net/strftime)

---

