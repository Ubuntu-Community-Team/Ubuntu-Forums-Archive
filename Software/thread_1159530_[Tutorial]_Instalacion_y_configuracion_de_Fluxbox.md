---
title: "[Tutorial] Instalacion y configuracion de Fluxbox"
date: 2009-05-14
forum: Software
---

### Post by emiliano_raso on 2009-05-14
AVISO IMPORTANTE! 
Si sos newbie en Linux, no te asustes porque hay muchos comandos en el tutorial. Tene paciencia y lee bien. Los beneficios de fluxbox son muchos y muy buenos como para tirarse para atras. 
Cualquier cosa soy del foro, me podes preguntar, y si queres charlar un rato de Linux y matarte de risa agregame al msn xD [email]raso.emiliano (at) gmail.com[/email]
No tengo ningun problema de ayudar, por mas pavota que sea tu pregunta. 
Igual puse todo bien explicado, asi que no creo que tengan problemas.

[quote="Wikipedia"]"Fluxbox es un gestor de ventanas. Su objetivo es ser ligero y altamente personalizable, con sólo un soporte mínimo para iconos, gráficos, y sólo capacidades básicas de estilo para la interfaz. Se utilizan atajos de teclado, tabs, y menús simples como interfaces, los cuales pueden ser editados. Algunos usuarios prefieren Fluxbox sobre otros gestores de ventanas debido a su velocidad y simplicidad."[/quote]

Originalmente (apenas lo terminas de instalar) se ve asi:
[http://i.i.com.com/cnwk.1d/i/tr/contentPics/techrepublic_fluxbox_desktop.jpg](http://i.i.com.com/cnwk.1d/i/tr/contentPics/techrepublic_fluxbox_desktop.jpg)
Y el mio se ve asi:
[http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/fluxboxscreenshot.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/fluxboxscreenshot.png)
En cuanto a Conky, lo hice hace bastante tiempo esto y ya ni me acuerdo realmente como se configura :-P

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


Ahora si. **El tutorial:**
_- Instalar Fluxbox (el entorno de escritorio):_
> sudo aptitude install fluxbox
Aceptar toda confirmacion que pida (si es que la pide). Se descarga e instala en cuestion de segundos, literalmente, porque es RE liviano.


_- Acceder a Fluxbox:_
Cerramos la sesion una vez termine la instalacion y en la pantalla para loguearse clickeamos "Sesion" y elegimos "Fluxbox". Aceptamos e iniciamos sesion. Si tenian Gnome, les va a preguntar si quieren que quede como predeterminado siempre que entren Fluxbox o que sea solo esa vez hasta que cierren la sesion. Hagan como quieran.

Ya estamos dentro de Fluxbox. Cargo rapidisimo, no? Es una porquería esteticamente, no? Ahora arreglamos esto ultimo.


_- Cambiar la apariencia en Fluxbox:_
Te metes en esta pagina: [http://www.box-look.org/index.php?xcontentmode=7400&PHPSESSID=ce83ccd764b988fbf76cf4de6cd2165b](http://www.box-look.org/index.php?xcontentmode=7400&PHPSESSID=ce83ccd764b988fbf76cf4de6cd2165b)
Elegi el tema que mas te guste.
Lo descargas y lo descomprimis.
Copia y pega la carpeta en este directorio: /home/TU_NOMBRE_DE_USUARIO/.fluxbox/styles
Ahora haciendo click derecho en el escritorio te va a aparecer el menú. Anda a la opcion Styles y clickea el que agregaste vos a la carpeta.

Es una horrible ese menú, viste? A mi me sacó la cabeza cuando lo vi.


_- Modificando el menú de Fluxbox:_
Tirá este comando en una consola:
> gedit home/TU_NOMBRE_DE_USUARIO/.fluxbox/menu
Ese archivo es el menú. Despues buscá en internet que hay tutoriales de como armarte el tuyo como mas te guste.
Yo te tiro el codigo del mio, que me lo modifiqué a mi gusto, con "accesos directos" y nombrecitos lindos.
Lo que tenes que hacer es borrar lo que tenga ese archivo y copiar y pegar esto:
> [begin] (Linux) {}
[exec] (HOME Thunar) { thunar $HOME} <>
[exec] (HOME Nautilus) { nautilus --no-desktop $HOME} <>
    [separator] () {}
[exec] (Opera) {opera} <>
[exec] (Pidgin) {pidgin} <>
[exec] (Thunderbird) {thunderbird} <>
[exec] (Amarok) {amarok} <>
[exec] (Firefox) {firefox} <>
[exec] (Gedit) {gedit} <>
[exec] (Terminal) {gnome-terminal} <>
[exec] (Monitor del sistema) {gnome-system-monitor} <>
[exec] (Screenshot) {gnome-screenshot} <>
[exec] (Agregar/Quitar) {gnome-app-install} <>
    [separator] () {}
    [submenu] (Sistema) {}
        [include] (/etc/X11/fluxbox/fluxbox-menu) {}
    [submenu] (Styles) {}
        [stylesdir] (/usr/share/fluxbox/styles) {}
        [stylesdir] (~/.fluxbox/styles) {}
    [end]
[end]
Fijate que al principio estan todos los "accesos directos" a programas que YO uso. Si usas otros, cambialos. Lo que va entre parentesis es el nombre que aparece en el menú, lo que va entre llaves es el comando de ejecucion de la aplicacion.
Por ejemplo, yo tengo (Pidgin) {pidgin}, si usas aMSN, entonces mandale (aMSN) {amsn}.


_- Elementos en panel inferior:_
Primero que nada explico una cosa. Tirá este comando en consola:
> gedit home/TU_NOMBRE_DE_USUARIO/.fluxbox/init
Este es el archivo de configuración de todo el entorno. Si mas o menos tenes idea de ingles y le pones onda, vas a entender que es cada cosa. Los del principio son el ancho de las barras, titulos, tamaños de letra, etc...
Nos vamos a la linea que dice session.screen0.rootCommand:
Despues de los dos puntos no hay nada, porque lo vamos a agregar nosotros. Que es esta linea? Aca se ponen las cosas que queres que se ejecuten automaticamente cuando inicias sesion. Por si no te diste cuenta, en el panel inferior, no tenes el administrador de redes, y si tenes notebook, tampoco tenes el monitor de bateria. Como los agregas?
>  session.screen0.rootCommand: nm-applet & gnome-power-manager &
Los "&" son separadores para que la maquina sepa cual es el nombre del programa.
Tampoco tenes para modificar el sonido! OH MY GOD!
Tampoco tenes el iconito que te avisa cuando hay actualizaciones disponibles. Asi que a la misma linea a la que le agregamos antes, ahora le agregas esto:
>  session.screen0.rootCommand: nm-applet & gnome-power-manager & update-notifier &
Obviamente que solo le agregas el "update-notifier &", porque el resto ya lo tenes.


_- Wallpaper:_
Primero instalamos esto:
> sudo aptitude install eterm
Te recomiendo poner el wallpaper que quieras usar en esta carpeta /home/TU_NOMBRE_DE_USUARIO/.fluxbox/backgrounds
Con este comando pones el wallpaper:
> fbsetbg -f /home/TU_NOMBRE_DE_USUARIO/.fluxbox/backgrounds/NOMBRE_DEL_WALLPAPER
Que significa el comando? "fbsetbg" (fb = FluxBox, set = poner xD, bg = BackGround)
El "-f" indica "fullscreen", es decir, pantalla completa. Si lo queres centrado, entonces poné "-c", e imaginate las demas variantes.
Que problema tenemos ahora? Que es un comando el poner el fondo de pantalla, que no es autoejecutable al inicio del sistema. Entonces? Que hachemo'?
Lo agregamos al init! Tonce... Otra linea mas:
>  session.screen0.rootCommand: nm-applet & gnome-power-manager & update-notifier & fbsetbg -f /home/TU_NOMBRE_DE_USUARIO/.fluxbox/backgrounds/NOMBRE_DEL_WALLPAPER &
Cada vez que cambien el wallpaper tienen que cambir el nombre del wallpaper en esa linea, obviamente.


_- Gvtray (programita para controlar el volumen):_
Como se dieron cuenta, no hay nada que les ayude a regular el sonido. Yo les recomiendo GVTRAY. Como lo instalan? Aca les digo:
> 
Descargamos el programa:
sudo apt-get install python-alsaaudio python-gnome2-extras
wget [http://gtk-tray-utils.googlecode.com/svn/trunk/gvtray-1.1.tar.gz](http://gtk-tray-utils.googlecode.com/svn/trunk/gvtray-1.1.tar.gz)

Lo descomprimimos y nos metemos en la carpeta:
tar -xvf gvtray-1.1.tar.gz
cd gvtray-1.1

Ahora metan estos comandos xD :
sudo mkdir /usr/share/gvtray
sudo cp gvtray /usr/bin
sudo cp gvtray.py /usr/share/gvtray/
sudo cp -r gvtray_about/ /usr/share/gvtray/gvtray_about

Finalmente, agregan a la linea "session.screen0.rootCommand" del INIT el GVTRAY. Como les quedaria el INIT entonces?
> 
session.screen0.rootCommand: nm-applet & gnome-power-manager & update-notifier & fbsetbg -f /home/TU_NOMBRE_DE_USUARIO/.fluxbox/backgrounds/NOMBRE_DEL_WALLPAPER & gvtray &



_- Mejorar apariencia de aplicaciones GTK:_
Para mejorar su aspecto, ya que originalmente se ven "mal", instalamos este programa:
>  sudo aptitude install gtk-chtheme 
No recuerdo si se necesita alguna repo aparte. Si no se los instala de una diganme que la busco.
Una vez instalado lo ejecutamos escribiendo en consola:
> gtk-chtheme
Elijan el estilo que quieran, y listo.

Los iconos no son los que queres? Asi se cambian:
Te vas a esta carpeta /usr/share/icons y te fijas como se llaman los iconos que queres (son los mismos que tenias en gnome).
Despues abris el archivo .gtkrc-2.0 que esta en tu carpeta Home y al final de todo le agregas esta linea:
> gtk-icon-theme-name = NOMBRE_DE_LOS_ICONOS
Taran. Ya esta. Andate al menú, clickea "Restart" y listo.


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


[b]_ACLARACIONES IMPORTANTES_:
- El archivo "keys" en el directorio /home/TU_NOMBRE_DE_USUARIO/.fluxbox/ es en el que se manejan los accesos directos por teclado. Yo lo configure como esta en Gnome. Si quieren, copien y peguen:
> OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F2 :ExecCommand fbrun
Mod1 F4 :Close
Mod1 = Tecla ALT

- Si les falta algun directorio de los que nombré en el tutorial, o algun archivo, entonces creenló ustedes :-P No hay drama, suele pasar.
En caso del archivo init, si no tenes la linea "session.screen0.rootCommand:", agregala.

- Donde vean "ALFA" y al lado un numero (255), eso es la cantidad de transparencia de algo. Por ejemplo, haciendo click derecho sobre el panel inferior con la ruedita del mouse podes regular la cantidad de transparencia.
Tambien tenes en el menú en el escritorio, en la configuracion de Fluxbox, para regular la transparencia en los bordes de ventanas.
Yo lo puse asi:
Alfa 150 para el panel inferior.
Alfa 200 para la ventana activa.
Alfa 100 para la ventana inactiva.

- Revisen ustedes y no tengan miedo. Es cuestion de amigarse con el init y de aprenderse como configurar el menú para armarse uno propio (yo todavia no aprendi, me robe el de un amigo y le modifique los accesos directos y algun que otro nombre xD)

- Para Ubuntu 9.04, no es necesario modificar las KEYS ya que cuando instalamos Fluxbox, la config de las keys esta muy buena, y no como en las versiones anteriores que es diferente.

- Si usan WICD y/o kpowersave en vez de las aplicaciones de GNOME, entonces agreguen asi al init:
>  session.screen0.rootCommand: wicd-client & kpowersave &
Y asi todas las demas aplicaciones, por ejemplo, yo ahora tengo tambien klipper, y agrego "klipper &".[/b]

---

### Post by staar on 2009-05-14
muy bueno el tutorial (aunque no soy muy amigo de los *box), te agregaría una cosa, para cambiar el tema Gtk, usaría lxappearance, que es el de lxde, casi no tiene dependencias, y también permite cambiar la fuente, los íconos...

saludos

---

### Post by sp33d3rs on 2009-05-14
Ok, yo soy mas nuevo que los nuevos... jejeje

vamos por parte, que son los "boxs", son como "entornos de escritorio", "entornos gráficos"??

---

### Post by emiliano_raso on 2009-05-14
> **staar said:**
> muy bueno el tutorial (aunque no soy muy amigo de los *box), te agregaría una cosa, para cambiar el tema Gtk, usaría lxappearance, que es el de lxde, casi no tiene dependencias, y también permite cambiar la fuente, los íconos...

saludos

Muchas gracias... lo voy a probar ahora.


> **sp33d3rs said:**
> Ok, yo soy mas nuevo que los nuevos... jejeje

vamos por parte, que son los "boxs", son como "entornos de escritorio", "entornos gráficos"??

Box se le dice a los entornos de escritorio:
- Fluxbox [http://es.wikipedia.org/wiki/Fluxbox](http://es.wikipedia.org/wiki/Fluxbox)
- Blackbox [http://es.wikipedia.org/wiki/Blackbox](http://es.wikipedia.org/wiki/Blackbox)
- Openbox [http://es.wikipedia.org/wiki/Openbox](http://es.wikipedia.org/wiki/Openbox)

Me falta probar OpenBox a mi. Blackbox no me convence :-P

Por las dudas la explicacion de entorno de escritorio xD [http://es.wikipedia.org/wiki/Desktop_environment](http://es.wikipedia.org/wiki/Desktop_environment)
Los entornos son lo que seguramente escuchaste: Gnome, KDE, XFCE
Es por eso el nombre de cada version de Ubuntu:
- Kubuntu: Ubuntu con KDE
- Xubuntu: Ubuntu con XFCE
- Fluxbuntu: Ubuntu con Fluxbox
etc...

---

### Post by sp33d3rs on 2009-05-14
> **emiliano_raso said:**
> Muchas gracias... lo voy a probar ahora.




Box se le dice a los entornos de escritorio:
- Fluxbox [http://es.wikipedia.org/wiki/Fluxbox](http://es.wikipedia.org/wiki/Fluxbox)
- Blackbox [http://es.wikipedia.org/wiki/Blackbox](http://es.wikipedia.org/wiki/Blackbox)
- Openbox [http://es.wikipedia.org/wiki/Openbox](http://es.wikipedia.org/wiki/Openbox)

Me falta probar OpenBox a mi. Blackbox no me convence :-P

Por las dudas la explicacion de entorno de escritorio xD [http://es.wikipedia.org/wiki/Desktop_environment](http://es.wikipedia.org/wiki/Desktop_environment)
Los entornos son lo que seguramente escuchaste: Gnome, KDE, XFCE
Es por eso el nombre de cada version de Ubuntu:
- Kubuntu: Ubuntu con KDE
- Xubuntu: Ubuntu con XFCE
- Fluxbuntu: Ubuntu con Fluxbox
etc...

Muy buena explicación :D, clarisimo, sobre todo con las paginas de wiki. Gracias!

---

### Post by emiliano_raso on 2009-05-14
> **sp33d3rs said:**
> Muy buena explicación :D, clarisimo, sobre todo con las paginas de wiki. Gracias!

De nada. Igual ahora me emocioné con LXDE jajaja... lo acabo de instalar...
Es mas rapido que fluxbox me parece, e incluso tiene mas opciones. Pero no se si es tan customizable.

---

### Post by guillermolisi on 2009-05-14
> **emiliano_raso said:**
> Muchas gracias... lo voy a probar ahora.




Box se le dice a los entornos de escritorio:
- Fluxbox [http://es.wikipedia.org/wiki/Fluxbox](http://es.wikipedia.org/wiki/Fluxbox)
- Blackbox [http://es.wikipedia.org/wiki/Blackbox](http://es.wikipedia.org/wiki/Blackbox)
- Openbox [http://es.wikipedia.org/wiki/Openbox](http://es.wikipedia.org/wiki/Openbox)

Me falta probar OpenBox a mi. Blackbox no me convence :-P

Por las dudas la explicacion de entorno de escritorio xD [http://es.wikipedia.org/wiki/Desktop_environment](http://es.wikipedia.org/wiki/Desktop_environment)
Los entornos son lo que seguramente escuchaste: Gnome, KDE, XFCE
Es por eso el nombre de cada version de Ubuntu:
- Kubuntu: Ubuntu con KDE
- Xubuntu: Ubuntu con XFCE
- Fluxbuntu: Ubuntu con Fluxbox
etc...
Generalmente se los menciona como Windows Manager, Administradores de ventanas, porque solo hacen eso.

Los entornos graficos de escritorios son mas complejos, poseen muchas mas funcionalidades y mayor integracion entre ellas que los Windows Managers, por lo tanto mas pesados al momento de usarlos - comparativamente hablando, y consumen mas recursos de maquina a raiz de todo lo anterior.

Logicamente, su configuracion si bien no es extremadamente compleja, a veces resulta algo criptica para los que recien se inician en este paraiso. Son recomendables cuando ni siquiera hay posibilidades para un XFCE o un LXDE por las limitaciones de hardware.

---

### Post by guillermolisi on 2009-05-14
Emiliano

Podemos contar con tu permiso para publicar el tuto en la seccion de Tutoriales del sitio web de Ubuntu-ar ?

---

### Post by sp33d3rs on 2009-05-14
> **guillermolisi said:**
> Emiliano

Podemos contar con tu permiso para publicar el tuto en la seccion de Tutoriales del sitio web de Ubuntu-ar ?

Totalmente de acuerdo, aunque estoy conforme con el escritorio de GNU, el tutorial es genial:popcorn:

---

### Post by JUTGtgRB7z on 2009-05-14
Yo uso Xubuntu y es rapidisimo. Recursos me sobran ¿Da para cambiarse o no?

---

### Post by emiliano_raso on 2009-05-14
> **guillermolisi said:**
> Emiliano

Podemos contar con tu permiso para publicar el tuto en la seccion de Tutoriales del sitio web de Ubuntu-ar ?

Por supuesto! No hay ningun problema! Va a ayudar mucho mas asi, y es para ayudar que hice el tutorial ^^

Lo que si, te pido que me vuelvas a explicar lo de "entornos de escritorio" y "administradores de ventanas" porque me mareaste xD

---

### Post by guillermolisi on 2009-05-14
> **pmzerdan said:**
> Yo uso Xubuntu y es rapidisimo. Recursos me sobran ¿Da para cambiarse o no?
Hay una regla de oro que todos deberian aplicar que dice "Si funciona bien, no lo toques".

Luego, si queres conocer nuevas cosas y aprender mas, probalo.

Eso si, antes informate como haces para volver atras y dejar las cosas como las tenes ahora, por las dudas.

---

### Post by emiliano_raso on 2009-05-14
> **pmzerdan said:**
> Yo uso Xubuntu y es rapidisimo. Recursos me sobran ¿Da para cambiarse o no?

Acabo de instalar XFCE4, LXDE y los BOX.
El mas rapido de todos hasta ahora es LXDE. Incluso mas rapido que fluxbox.

---

### Post by emiliano_raso on 2009-05-14
> **guillermolisi said:**
> Hay una regla de oro que todos deberian aplicar que dice "Si funciona bien, no lo toques".

Luego, si queres conocer nuevas cosas y aprender mas, probalo.

Eso si, antes informate como haces para volver atras y dejar las cosas como las tenes ahora, por las dudas.

JO JO JO! ESO ES MUY CIERTO! XD

Pero igual no trae ninguna complicacion el volver para atras de Flux a XFCE.

---

### Post by sp33d3rs on 2009-05-14
> **guillermolisi said:**
> Hay una regla de oro que todos deberian aplicar que dice "Si funciona bien, no lo toques".

Amennnn[-o<

---

### Post by guillermolisi on 2009-05-14
> **emiliano_raso said:**
> Por supuesto! No hay ningun problema! Va a ayudar mucho mas asi, y es para ayudar que hice el tutorial ^^

Lo que si, te pido que me vuelvas a explicar lo de "entornos de escritorio" y "administradores de ventanas" porque me mareaste xD
A los escritorios/entornos graficos tipo Gnome, KDE, XFCE, LXDE, por mencionar los mas conocidos (por lo menos por mi) se los diferencia de los Windows Managers por su funcionalidad e integracion entre las aplicaciones que los componen.

Es decir, van mas alla de lo que un WM realiza, que es estrictamente administrar la parte visual del contenido de la pantalla, sin otros servicios adicionales para el usuario y entre aplicaciones.

Inclusive hay ejemplos interesantes que mixturan Gnome con Enlightement, por ejemplo (un escritorio grafico y un WM) en la distribucion OpenGEU donde usan algunas cosas del primero con el agregado de partes de Gnome.

Es decir, un escritorio grafico incluye un gestor de ventanas pero un gestor de ventanas no incluye un escritorio grafico.

---

### Post by emiliano_raso on 2009-05-14
Entonces, los que yo conozco (Gnome, KDE, LXDE, 'box, XFCE, etc) son simplemente entornos de escritorio (desktop enviroment). Dan apariencia.

Y un ejemplo de Windows Manager cual seria?

EDIT: Ya entendi xD BUscando info en internet entendi.

Pero si los 'box son gestores de ventanas, y gnome es un entorno de escritorio, cual es el gestor de ventanas de gnome? Metacity?

---

### Post by Tosh78 on 2009-05-14
Emiliano, te aconsejo que edites tu direccion de mail, ya que te va a llegar muchisimo spam. Podes poner (A) en vez de @.

Mil gracias por el tutorial, esta muy bueno!

---

### Post by emiliano_raso on 2009-05-14
> **Tosh78 said:**
> Emiliano, te aconsejo que edites tu direccion de mail, ya que te va a llegar muchisimo spam. Podes poner (A) en vez de @.

Mil gracias por el tutorial, esta muy bueno!

Uh cierto... gracias por avisar u.u

Y de nada por el tutorial :-P

---

### Post by staar on 2009-05-14
> Pero si los 'box son gestores de ventanas, y gnome es un entorno de escritorio, cual es el gestor de ventanas de gnome? Metacity? el window manager oficial de gnome es metacity, pero lo podés usar con compiz (si, compiz es un gestor de ventanas, nada más), openbox, enlightenment, o el que quieras, el de kde es kwin, y el de xfce creo que se llama xfwm...

la cantidad de WMs es enorme (algunos son realmente raros en como manejan las ventanas), tenés awesome, dwm, evilwm, los *box, y muchisimos más (es lo lindo del SL :-D)...

saludos

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> el window manager oficial de gnome es metacity, pero lo podés usar con compiz (si, compiz es un gestor de ventanas, nada más), openbox, enlightenment, o el que quieras, el de kde es kwin, y el de xfce creo que se llama xfwm...

la cantidad de WMs es enorme (algunos son realmente raros en como manejan las ventanas), tenés awesome, dwm, evilwm, los *box, y muchisimos más (es lo lindo del SL :-D)...

saludos

Ah genial... ahora entendi xD Gracias xD

---

### Post by totolinux on 2009-05-15
gracias por tu tutorial muy bueno. Lo único que no puedo lograr es cambiar el canal que controla el volumen de gvtray que supongo esta en master a pcm 
si alguien me puede ayudar estaria muy agradecido.

---

### Post by emiliano_raso on 2009-05-15
> **totolinux said:**
> gracias por tu tutorial muy bueno. Lo único que no puedo lograr es cambiar el canal que controla el volumen de gvtray que supongo esta en master a pcm 
si alguien me puede ayudar estaria muy agradecido.

No es la solucion mas ortodoxa y correcta que existe pero, me di cuenta que cambiandoló desde Gnome y volviendo a Fluxbox despues queda.
Me pasó que tenía muteado el sonido en Gnome y en Fluxbox el Gvtray no me daba ni bola.
No se porque pasa eso.

Sin embargo, como alternativa al Gvtray tendría que de alguna forma poder agregarse al init con algun comando el control de volumen de gnome, pero no tengo idea de como.

---

### Post by totolinux on 2009-05-15
Gracias seguiré buscando, mientras tanto el volumen  lo manejo desde el terminal
con "$ amixer sset PCM 10%+ "

---

### Post by Hei Ku on 2009-05-15
Probaste abrir el alsamixer en la terminal y verificar la configuracion ahi?

---

### Post by emiliano_raso on 2009-05-15
> **Hei Ku said:**
> Probaste abrir el alsamixer en la terminal y verificar la configuracion ahi?

Esa es buena, no se me habia ocurrido.
Lo acabo de hacer, pero como edito cosas desde el alsamixer en terminal?

---

### Post by Hei Ku on 2009-05-15
Las flechas y el tab son tus amigos.

---

### Post by emiliano_raso on 2009-05-15
> **Hei Ku said:**
> Las flechas y el tab son tus amigos.

Ahi entendí xD Esas interfaces graficas en consola me re marean xD

Gracias...

---

### Post by totolinux on 2009-05-16
> **Hei Ku said:**
> Probaste abrir el alsamixer en la terminal y verificar la configuracion ahi?

Gracias por contestear tu metodo es mejor que el mio pero no modifija el canal de gvtray. asi que mientras tanto seguiré usando alsamixer en terminal.:KS
se me ocurre que podría hacer un lanzador con el comando alsamixer o asignar alguna tecla de teclado para el volumen.

---

### Post by Hei Ku on 2009-05-16
Fijense que hay una manera para guardar la configuracion del alsamixer, de tal manera de no tener que hacerlo siempre. Tambien existe seguro alguna forma de ejecutarlo con parametros para subir o bajar el volumen con una tecla.

---

### Post by emiliano_raso on 2009-05-16
Jajaja Esta es genial, se me ocurrió recien. Es de las soluciones que le ENCANTAN a guillermo xD jajaja

Primero instalamos Alltray (alltray permite que las aplicaciones que ejecutemos se agreguen al area de notificacion con un icono)
```
sudo aptitude install alltray
```
Y ahora en el init agregamos:
```
session.screen0.rootCommand: alltray gnome-volume-control &
```

Y listo...

---

### Post by totolinux on 2009-05-16
a mi no me funca.. me quedó asi init (session.screen0.rootCommand:	pidgin & conky & nm-applet & gvtray &  alltray gnome-volume-control & )
no me rindo no me gana nadie a porfiado ja

---

### Post by emiliano_raso on 2009-05-16
> **totolinux said:**
> a mi no me funca.. me quedó asi init (session.screen0.rootCommand:	pidgin & conky & nm-applet & gvtray &  alltray gnome-volume-control & )
no me rindo no me gana nadie a porfiado ja

Que raro. A mi si me funcionó:

```
session.screen0.rootCommand:	wicd-client & kpowersave & update-notifier & klipper & alltray gnome-volume-control & fbsetbg -f /home/emiliano/.fluxbox/backgrounds/muelle.jpg &
```

---

### Post by guillermolisi on 2009-05-16
> **totolinux said:**
> a mi no me funca.. me quedó asi init (session.screen0.rootCommand:    pidgin & conky & nm-applet & gvtray &  alltray gnome-volume-control & )
no me rindo no me gana nadie a porfiado ja
No deberia haber un solo simbolo "&", al final, en lugar de todos esos entre medio ?

---

### Post by emiliano_raso on 2009-05-16
> **guillermolisi said:**
> No deberia haber un solo simbolo "&", al final, en lugar de todos esos entre medio ?

No. Lo tiene bien escrito.

Lo que si, fijate una cosa totolinux...
Entre "session.screen0.rootCommand:" y "pidgin" tenes una tabulacion o un espacio?
Yo tengo tabulacion... NO CREO QUE SEA ESO... Peeeeeeeero...

Mas alla de eso, tenes gnome instalado en la maquina? O al menos el gnome-volume-control instalado? Fijate en el synaptic.

---

### Post by totolinux on 2009-05-16
si tengo gnome, lo de el espacio no es, igual hace como un més que configuro fluxbox y tiene metida mucha mano. un consejo hay que hacer una copia de la carpeta .fluxbox. porque cuando metes la pata fuiste hoy me salvó;)

---

### Post by totolinux on 2009-05-17
listo solucionado lo del volumen de esta manera

 $ sudo apt-get install wmix

luego agregar la orden en home/TU_USUARIO/.fluxbox/init 

de esta manera

session.screen0.rootCommand: pidgin & conky & nm-applet & wmix &
 
gracias a todos. disfrutando de fluxbox:D

---

### Post by emiliano_raso on 2009-05-18
> **totolinux said:**
> listo solucionado lo del volumen de esta manera

 $ sudo apt-get install wmix

luego agregar la orden en home/TU_USUARIO/.fluxbox/init 

de esta manera

session.screen0.rootCommand: pidgin & conky & nm-applet & wmix &
 
gracias a todos. disfrutando de fluxbox:D

Lo probe pero no me lo tira en el system tray. Se abre en el escritorio. Es asi y yo esperaba fallidamente que se abriera en el ST?

---

### Post by totolinux on 2009-05-18
Perdona la demora, no se abre en el sistem tray. Solo queda en el escritorio en el angulo inferior derecho, hay más modulos yo solo instale este. Que digamos muy lindo no es, pero me soluciono el problema.

---

### Post by emiliano_raso on 2009-05-29
Ah ok... Me parecía ... Probá de abrir el gnome-volume-control con Alltray como una aplicacion normal.

O sea: Alt+F2 y poné
```
alltray gnome-volume-control
```

Fijate si te anda asi.

---

### Post by Asterión libre on 2009-06-08
Emiliano:
¡Sos un capo! Estaba buscando algo liviano para mi vieja maquinita y encontré tu tutorial. Todo muy claro y a prueba de tontos. Ya lo estoy configurando. Gracias!

---

### Post by r@fitiiixxx on 2009-06-09
> **staar said:**
> el window manager oficial de gnome es metacity, pero lo podés usar con compiz (si, compiz es un gestor de ventanas, nada más), openbox, enlightenment, o el que quieras, el de kde es kwin, y el de xfce creo que se llama xfwm...

la cantidad de WMs es enorme (algunos son realmente raros en como manejan las ventanas), tenés awesome, dwm, evilwm, los *box, y muchisimos más (es lo lindo del SL :-D)...

saludos

Waw cuantos que hay!, habría que hacer una lista!


> **guillermolisi said:**
> A los escritorios/entornos graficos tipo Gnome, KDE, XFCE, LXDE, por mencionar los mas conocidos (por lo menos por mi) se los diferencia de los Windows Managers por su funcionalidad e integracion entre las aplicaciones que los componen.

Es decir, van mas alla de lo que un WM realiza, que es estrictamente administrar la parte visual del contenido de la pantalla, sin otros servicios adicionales para el usuario y entre aplicaciones.

Inclusive hay ejemplos interesantes que mixturan Gnome con Enlightement, por ejemplo (un escritorio grafico y un WM) en la distribucion OpenGEU donde usan algunas cosas del primero con el agregado de partes de Gnome.

Es decir, un escritorio grafico incluye un gestor de ventanas pero un gestor de ventanas no incluye un escritorio grafico.

acá hay algo que no me cierra, o debería pero no, Emiliano dijo que el LXDE es mas liviano que el fluxbox, pero el fluxbox es solo un Window manager y el LXDE segun Guillermolisi es un entorno de escritorio.

Ahora, como puede ser que LXDE sea mas liviano que fluxbox si es un entorno completo y el otro es solo el manejo de ventanas?, es eso posible?.

tal vez entendí mal y Flux si es un Entorno de escritorio xD

extra: alguien dijo por ahí que el compiz es un Window Manager, pues algunos están pensando en grande ya ;) 

[Compiz Desktop Environment: ¿es posible?]("http://www.genbeta.com/linux/compiz-desktop-environment-es-posible")

off: quiero saber porque planeo instalar ubuntu en una pc con 512 mb de ram pero procesador chico y le quiero meter el Entorno mas liviano, pensaba que este tuto me venía bien, pero si hay uno más liviano todavía mejor, lo mas raro sería que además de liviano sea mas completo.

---

### Post by staar on 2009-06-09
LXDE no es mas liviano que fluxbox, eso fue una opinión de emiliano, entendiste bien, el primero es un DE y el segundo solo un WM...

si tenés 512 Mb de ram no te preocupes, podés aspirar a algo 'medio' como XFCE, un entorno completo, muy similar a Gnome, tené en cuenta que los WM tienen sus mañas, no son muy agradables para configurar (más para alguien que recién empieza como vos)...

y compiz si puede correr solo, pero como WM, como está el proyecto Compiz, no creo que se largen a hacer un DE, es mucho laburo (y podrían tardar años, más los desarrolladores de compiz, que se llevan como el ****) y ya tienen uno, Gnome (es el más soportado, aunque corre en otros DE también)

saludos

---

