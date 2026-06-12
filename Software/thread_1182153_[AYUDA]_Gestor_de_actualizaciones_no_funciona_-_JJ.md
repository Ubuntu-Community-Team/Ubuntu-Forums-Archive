---
title: "[AYUDA] Gestor de actualizaciones no funciona - JJ 9.04"
date: 2009-06-08
forum: Software
---

### Post by r@fitiiixxx on 2009-06-08
Hola comunidad,

mi problema es el siguiente, ayer a la noche noté que mi ubuntu Jaunty Jackalope 9.04 tenía un icono en el area de notificación del panel inferior derecho que mostraba un signo de "STOP" pero que en realidad decía que algo fallaba. cuestión le hago click y me doy cuenta de que es el gestor de actualizaciones. Pidiendome actualizar algunos paquetes de programas
los paquetes son:
-ACTUALIZACIONES RECOMENDADAS:
>libtrackerclient0 (tamaño 187 KB)
-ACTUALIZACIONES DE LA DISTRO:
>build-essential (tamaño 7 KB)
>dpkg-dev (tamaño 628 KB)
>g++ [Compilador de C++ de GNU](tamaño 1 KB)
>G++-4.3 "" (tamaño 3.0 MB)

el tema es que cuando yo pongo "descargar paquetes me aparece el siguiente cartel de:

"Ud. tiene 2 paquetes rotos"

hago click en aceptar y me aparece otro cartel:
> Por favor, introduzca el disco con la etiqueta:
Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)
en la unidad /cdrom/
yo le pongo el CD de Kubuntu, porque tengo los dos CD, Ubuntu y Kubuntu por suerte, y pongo aceptar pero no pasa nada, no sale el cartel, así que pongo cancelar y me sale esto:
> W: Falló al obtener cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/pool/main/d/dpkg/dpkg-dev_1.14.24ubuntu1_all.deb
y solo puedo poner cancelar.

leí por ahí en inet que para arreglar estos paquetes hay que ir a Synaptic > Editar > Reparar paquetes rotos > aplicar. y listo, pero no funciona, me sale el mismo mensaje de poner el cd de Kubuntu y despues de que pongo cancelar me sale el msje del fallo al obtener el cdrom kubuntu... y yo tengo Ubuntu no Kubuntu instalado,

esto me pasó después de querer instalar el "Global Menú", un applet para el panel de GNOME estilo Mac que su función es poner la barra de herramientas (Archivo Editar Ver Ir Marcadores Solapas Ayuda ... )  de cualquier aplicación GTK+ en el panel de Gnome y así se ve mas "piola"
para instalarlo requiere que se agreguen sources al source list + la instalación del Ubuntu tweak, creo que hay que agregar sources de medibuntu si no me equivoco

lo de instalar el global menú lo saqué de esta pag;

_**[Global Menu, applet para el panel de Gnome al estilo de Mac OSX]("http://vijamaroylinux.blogspot.com/2009/04/global-menu-applet-para-el-panel-de.html")**_

Mi hard/soft: AMD Athlon X2 64, dual core 4600 Mhz 2.4, memoria ram 2 GB DDR2, Chipset nForce 410 AM2 Socket, Placa de video (lo pongo por las dudas)  NVIDIA Geforce 8600 GT 512 mb con los drivers actualizados [ver. 180 recomendada].

Ubuntu JJ 9.04, instalado con wubi todavía, con GNOME, la versión con la que viene, ya no se si es la 2.20 o 2.2x o 2.xx, Compiz Fusion Instalado con su administrador, Gnome Do Docky, Beryl Emerald Theme, y bueno de paquetes no se mucho así que si necesitan algo de extra info me dicen como obtenerla y listo.

desde ya muchas gracias, un salu2

---

### Post by pablo.s on 2009-06-08
Empeza por deshabilitar
en los repositorios el
CD de Kubuntu. Luego si
vas a poder desinstalar 
los paquetes rotos.

---

### Post by r@fitiiixxx on 2009-06-09
> **pablo.s said:**
> Empeza por deshabilitar
en los repositorios el
CD de Kubuntu. Luego si
vas a poder desinstalar 
los paquetes rotos.

y como hago eso?. Perdón todavía soy algo nuevo en Linux y hay muchas cosas que todavía no manejo :-k , yo solo copio y pego... y después enter  8-[

---

### Post by josecuervo86 on 2009-06-09
Anda a **Synaptic** y una vez ahi anda a **Configuración > Repositorios**. Despues desmarca la casilla donde dice **Cd-Rom de Ubuntu....** que esta abajo de todo

---

### Post by guillermolisi on 2009-06-09
> **r@fitiiixxx said:**
> y como hago eso?. Perdón todavía soy algo nuevo en Linux y hay muchas cosas que todavía no manejo :-k , yo solo copio y pego... y después enter  8-[
Fijate en Administracion - Origenes del Software - Software de terceros (o algo asi) y desmarca las lineas que hagan referencias a CDRom de lo que sea.

---

### Post by r@fitiiixxx on 2009-06-09
> **josecuervo86 said:**
> Anda a **Synaptic** y una vez ahi anda a **Configuración > Repositorios**. Despues desmarca la casilla donde dice **Cd-Rom de Ubuntu....** que esta abajo de todo

Ese casillero del Cd-Rom de Ubuntu no estaba marcado, el de UUUbuntu, de KKKKubuntu no decía nada, lo digo por las dudas

también probé activarlo y me dá una solución para el soporte del CD que no estoy seguro de para que me sirve, la solución es poner el CD de Ubuntu y ejecutar un cmd en la terminal bash, pero eso es creo para otra cosa verdad?

> **guillermolisi said:**
> Fijate en Administracion - Origenes del Software - Software de terceros (o algo asi) y desmarca las lineas que hagan referencias a CDRom de lo que sea.

Al desmarcar la opción del Cd-Rom de Kubuntu me pide que "recargue" la lista de los origenes del software y luego me salta este error cuando termina de actualizar
```
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
 Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible:
 NO_PUBKEY 7889D725DA6DEEAA
```

a ver si con eso me pueden ayudar a resolver el asunto y de paso aprendo algo de esto jeje.

---

### Post by gmunioz on 2009-06-09
Hola r@f....:

Ese error no es importante.

simplemente te faltan las claves

gpg del repositorio

El amigo pablo.s se ha molestado

En escribir un largo tutorial al

respecto:

```
http://ubuntuforums.org/showthread.php?t=1174296
```

Merece, por su esfuerzo, que al menos lo leas.

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - 22 - Mad Karmic & Gnome-shell User.**

---

### Post by r@fitiiixxx on 2009-06-10
> **gmunioz said:**
> Hola r@f....:

Ese error no es importante.

simplemente te faltan las claves

gpg del repositorio

El amigo pablo.s se ha molestado

En escribir un largo tutorial al

respecto:

```
http://ubuntuforums.org/showthread.php?t=1174296
```

Merece, por su esfuerzo, que al menos lo leas.

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - 22 - Mad Karmic & Gnome-shell User.**

Ok Gabriel, ;) gracias por orientarme, ahora no porque es de noche, pero mañana a primera hora lo leo, pruebo, y vuelvo a comentar

gracias :D

---

### Post by r@fitiiixxx on 2009-06-10
Bueno primero que nada pude resolver el problema! gracias foro!!
:popcorn:
gracias a pablo.s, josecuervo86, guillermolisi & gmunioz por ayudarme y orientarme en el problema,

les cuento mas que para uds que me ayudaron, es para todos en general por si alguien tuvo, tiene o va a tener este problema,

yo muy bien no entiendo pero cuando uno agrega software que no es soportado por los repositorios de Ubuntu según entendí, necesita agregar la fuente de donde es, para eso agrega a los source lists, los agregué con el comando en terminal (Aplicaciones > Accesorios > Terminal)
```
sudo gedit /etc/apt/sources.list
```
y ahí agregué las lineas que empiezan con 
"deb http://ppa.launchpad.net/xxxxxxx/xxxxxx/xxxx"
luego tuve que agregar una llave que permite descargar estos archivos, algo así como para validarlos, hacerlos que sean viables, esta llave es la llave publica llamada PPA, yo la conseguí en, o mejor dicho, es mas seguro conseguirla en la pagina:

_[www.launchpad.net](www.launchpad.net)_

como el programa que quería estaba en un blog tuve que ir a launchpad y buscar el programa con el buscador de la pagina, allí en la sección de **DESCARGAS** estaba el programa en .tar.gz y abajo estaba el archivo public key PPA,

lo descargué y lo puse en mi directorio /home/nicolas/Documentos/nombredelapublickey_nocambiarporlasdudas**.gpg**  .
luego salí a escritorio y fui a "Sistema > Administración > Orígenes del Software".
=>
y ahí hice 2 cosas muy importantes

1°)fui a la solapa Software de terceros y agregué las fuentes y las activé, luego...

2°) fuí a la solapa Autentificación y pulsé la tecla "[+Importar clave]"
busqué el archivo **.gpg** y lo agregué.

> luego puse "cerrar" y ahí me pidió de "recargar" las fuentes y todo eso... y LISTO!! me dejó de saltar el error de la públic key y el disco de Kubuntu y el disco de Ubuntu y el disco de Xub... a, ese nunca me lo pidió, todavía :D

así resolví el problema de las actualizaciones y también pude instalar este fantástico applet que me encanta porque ahora puedo liberar espacio en la ventana para que se vea mejor ^^

Aclaración:
 Este post fue mas que nada un review del problema y la solución que le encontré, por si a alguien le pasa algo parecido o lo mismo, ya tiene mi versión, porque en internet yo no encontré nada en concreto, no se si porque busqué mal, o si no había, pero siempre es mejor compartir la solución verdad?

igual después de esto me doy cuenta de que cada vez se me hace mas urgente buscar información fácil de asimilar con respecto a la trata de paquetes, repositorios, llaves (publicas & privadas) y directorios.
así que voy a seguir con mi cruzada.

Salu2 ):P y gracias por todo otra ves ^^

---

### Post by Hei Ku on 2009-06-10
Y para la proxima, tenes un Sticky en este mismo subforo que explica justamente esto. ;)

---

