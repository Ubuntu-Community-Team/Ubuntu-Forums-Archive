---
title: "Problema con flash en ubuntu 9.04"
date: 2009-06-08
forum: Software
---

### Post by Meisterwerk on 2009-06-08
Saludos a todos, hace algunas semanas me estoy trasladando lentamente a Ubuntu, de a poco surgen los problemas producto de la ignorancia, ocurre lo siguiente:

Cuando ingreso a una pagina con contenido flash (creo que es asi) como por ejemplo, myspace, o paginas que tengan reproductores de musica on line, el reproductor en cuestion no aparece por ninguna parte, y tampoco se oye nada. En myspace, la parte donde va el reproductor se queda del color de fondo simplemente. Ya instale los paquetes de adobe flash para ubuntu, probe con otros navegadores...y nada parece dar resultado.

Si sirve de algo, no tengo problemas con el sonido en mi pc, y con el video tampoco...alguien puede ayudarme porfavor??

gracias!

PD: supongo que esto va en esta seccion, si no es asi, porfavor muevanlo donde corresponda, y disculpen el desorden
salud!!!

---

### Post by phantomcl on 2009-06-08
Tengo el mismo problema.
Sonido ok, pero luego de instalar el flash, no carga el flash del youtube, por ejemplo (todo lo demas de la pagina si)
Ojo que en un principio (luego de instalar) estaba por debecto deshabilitado el pluggin, pero se habilito desde firefox.

Alguna idea ?

---

### Post by moreback on 2009-06-08
Tengo la impresión que no son reproductores Flash, si no que streaming para Windows Media. En este caso el plugin por defecto es Totem y si no sale nada a lo mejor te falta instalar algunos paquetes de drivers ugly.

Si alguien sabe como se llaman esos driver, que los postee, yo estoy medio olvidadizo.

---

### Post by phantomcl on 2009-06-08
Tengo el mismo problema.
Sonido ok, pero luego de instalar el flash, no carga el flash del youtube, por ejemplo (todo lo demas de la pagina si)
Ojo que en un principio (luego de instalar) estaba por debecto deshabilitado el pluggin, pero se habilito desde firefox.

Alguna idea ?

---

### Post by Patriciologico on 2009-06-09
> **phantomcl said:**
> Alguna idea ?

Abre Synaptic y busca flash, postea aca cual tienes instalado. Tal vez firefox te instalo la version libre que a veces no funciona bien.

---

### Post by Meisterwerk on 2009-06-09
Yo revise, tengo instalado:
EL flashplugin installer.
Tambien revise lo que dijeron mas arriba acerca Totem, efectivamente al hacer click derecho en la pantalla donde deberia estar el reproductor, me entrega informacion acerca de Totem y sobre swedec...pero no se ve absolutamente nada....
salud!!!

---

### Post by Meisterwerk on 2009-06-09
Ya lo solucione, fue bastante simple...desintale todo lo que tuviera que ver con swfdec, especificamente desintale completamente el swf-genome (incluyendo archivos de configuracion) y solo deje instalado el adobe-flash-installer, todo esto desde synaptic.

Al parecer se creaba un conflicto entre swfdec y adbe flash, ojo que tambien probe dejando solo swfdec y no funcionaba...

saludos, ojala a alguien mas le sirva mi solucion.

---

### Post by Iced_R on 2009-06-09
La solución más cómoda y fácil es instalar el flashplayer que aparece en la página oficial de Adobe ([www.adobe.com](www.adobe.com)). Ese flash player no exige tantos recursos como el de los repositorios oficiales de Ubuntu, y además no necesita de swfdec y gnash. Simplemente bajas el archivo tar.gz, lo descomprimes, y ejecutas el archivo flashplayer.so desde una terminal. La instalación es muy Windows mode: Amén+Aceptar+Amén xDDD.


Saludos.

---

### Post by RafaelG on 2009-06-10
[FONT=Arial][SIZE=2]Hola Yo tuve el mismo problema un conflicto entre Flash y [/SIZE][/FONT]Swfdec por eso es recomendable instalar el flash directamente desde Adobe Website para Flash. aca dejo Link donde presenta varias Soluciones para problemas con flash:
[FONT=Arial][SIZE=2] [B]
Soluccionar problemas con Adobe Flash Player en Ubuntu 9.04 Jaunty:
[/B][/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2][http://www.tuxapuntes.com/drupal/node/1372](http://www.tuxapuntes.com/drupal/node/1372)[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT]   [FONT=Arial][SIZE=2][/SIZE][/FONT][FONT=Arial][SIZE=2][]("http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/")[/SIZE][/FONT]

---

### Post by Dame Cruz on 2009-06-10
Yo tengo un problema similar, tengo instalado el flash player nonfree y veo el youtube y otras aplicaciones, pero el problema es que en lo que es animación flash se cuadricula y pestañean las figuras (aparecen y desaparecen), aparte de que se ve mas lento.
Me han dicho que es posible que sea producto de mi tarjeta de video intel integrada.

---

### Post by kamus on 2009-06-10
> **Dame Cruz said:**
> Yo tengo un problema similar, tengo instalado el flash player nonfree y veo el youtube y otras aplicaciones, pero el problema es que en lo que es animación flash se cuadricula y pestañean las figuras (aparecen y desaparecen), aparte de que se ve mas lento.
Me han dicho que es posible que sea producto de mi tarjeta de video intel integrada.

Deben tener instalado los paquetes flashplugin-nonfree  y  flashplugin-nonfree-extrasound (via synaptic o apt-get).

Saludos ;)

---

### Post by Dame Cruz on 2009-06-10
> **kamus said:**
> Deben tener instalado los paquetes flashplugin-nonfree  y  flashplugin-nonfree-extrasound (via synaptic o apt-get).

Saludos ;)

Ambos están instalados.

---

### Post by Iced_R on 2009-06-10
Se está desordenando el hilo, apuesto a que habrá advertencia xD

La otra vez un amigo tuvo ese mismo problema. Lo solucionó instalando una librería que le faltaba, que era libflashsupport. La pueden instalar de cualquier forma, mediante consola (con apt-get o aptitude) o desde Synaptic.

Saludos. Ojalá sea la solución

---

### Post by moreback on 2009-06-10
> **Dame Cruz said:**
> Me han dicho que es posible que sea producto de mi tarjeta de video intel integrada.
mija, actívele el UXA: [http://ubuntuforums.org/showthread.php?t=1166388](http://ubuntuforums.org/showthread.php?t=1166388)

;)

---

### Post by kamus on 2009-06-10
> **Dame Cruz said:**
> Ambos están instalados.

ups, quotie mal jeje .. eso era para la solucion anterior! :P

Volviendo al topic, quizas deberias revisar el controlador de tu tarjeta de video sea el correcto (deberias usar el controlador libre que viene en la distro, almenos en la mayoria de los casos anda bien), y lo otro en el mismo foro hay algunas guias de configuracion para las tarjetas intel :p

---

### Post by nopersona on 2009-06-11
Ánimo, el foro ahora será distinto, pero la opción "buscar" sigue aportando el mismo resultado :p


[http://ubuntuforums.org/showthread.php?t=1180886](http://ubuntuforums.org/showthread.php?t=1180886)

---

### Post by Eddy_Kine on 2009-06-12
En su momento tuve el mismo problema, pero la solución más apropiada es el segundo link puesto por NoPersona.-
Recomendación para la otra: Instalar  los paquetes flashplugin-nonfree  y  flashplugin-nonfree-extrasound (via synaptic o apt-get) desde cero, es decir, no deben instalarlo cuando firefox lo pide, sino antes que todo, como una especie de "calentamiento previo" por decrilo de alguna forma ;)

---

### Post by tuxsarge on 2009-06-13
hola!!!

aparte de todo eso, es recomendable instalar mozilla-plugin-vlc ya que se necesita el reproductor para sitios online

Saludos

---

### Post by DHPERU666 on 2009-06-13
No puedo instalar el plugin Flash Player version 10, tengo Ubuntu 9.04 64bits, elegi instalar el .deb for ubuntu 8+ y aparece Error:wrong architecture
mi pc es Amd phenom II X3, 2GB Ram, video Nvidia 512mb

---

### Post by Carlos C on 2009-06-13
> **DHPERU666 said:**
> No puedo instalar el plugin Flash Player version 10, tengo Ubuntu 9.04 64bits, elegi instalar el .deb for ubuntu 8+ y aparece Error:wrong architecture
mi pc es Amd phenom II X3, 2GB Ram, video Nvidia 512mb

Disculpa pero, ¿por qué no instalas el paquete que está en los repositorios? Siempre prefiere la versión de los repositorios antes de probar otras fuentes. Puedes instalarlo usando el Gestor de paquetes synaptic.

Saludos.

---

### Post by moreback on 2009-06-13
Me acabo de pasar a 64 bits y no tuve problemas en instalar el Flash, se hace desde el mismo Firefox cuando te pide instalar el plugin. Te da tres opciones de la que tienes que seleccionar "Adobe Flash Player" y dejarlo que se instale (se puede colgar el Firefox, pero la idea es que dejen que termine de instalar los paquetes)

Saludos.

---

### Post by radixs on 2009-06-16
> **DHPERU666 said:**
> No puedo instalar el plugin Flash Player version 10, tengo Ubuntu 9.04 64bits, elegi instalar el .deb for ubuntu 8+ y aparece Error:wrong architecture
mi pc es Amd phenom II X3, 2GB Ram, video Nvidia 512mb

Bajate esto: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

descomprimes, vas al directorio home, buscas la carpeta .mozilla (esta oculta ctrl+h para mostrar), dentro creas la carpeta plugin y copias el archivo descomprimido "libflashplayer.so" en la carpeta plugin

espero te sirva ;)

---

### Post by ppellet on 2009-08-02
Estimados

Instalé Ubuntu 9.04 y posteriormente, a través de synaptic, *flashplugin-installer* (Adobe Flash Player plugin installer).

Antes de *flashplugin-installer* no podía ver los videos de youtube, después de instalarlo reinicié firefox y listo. Cero problemas para ver videos.

Saludos cordiales,

---

### Post by Patriciologico on 2009-08-02
> **ppellet said:**
> Estimados

Instalé Ubuntu 9.04 y posteriormente, a través de synaptic, *flashplugin-installer* (Adobe Flash Player plugin installer).

Antes de *flashplugin-installer* no podía ver los videos de youtube, después de instalarlo reinicié firefox y listo. Cero problemas para ver videos.

Saludos cordiales,

Hola ppellet,

Eso es porque Ubuntu no trae por defecto ningún tipo de flash, ni siquiera el de formato libre. Lo que hiciste fue instalar el plugin, y es lo que todos lo que quieran ver flash deben hacer.

Saludos!

---

### Post by daniel7110 on 2009-08-02
> **ppellet said:**
> Estimados

Instalé Ubuntu 9.04 y posteriormente, a través de synaptic, *flashplugin-installer* (Adobe Flash Player plugin installer).

Antes de *flashplugin-installer* no podía ver los videos de youtube, después de instalarlo reinicié firefox y listo. Cero problemas para ver videos.

Saludos cordiales,

> **Patriciologico said:**
> Hola ppellet,

Eso es porque Ubuntu no trae por defecto ningún tipo de flash, ni siquiera el de formato libre. Lo que hiciste fue instalar el plugin, y es lo que todos lo que quieran ver flash deben hacer.

Saludos!


POR FIN!!! 
Luego de instalar Ubuntu 9.04 y maldecirlo 765 veces he podido ver un video de youtube sin que consuma 99% de cpu!](*,)
El culpable...
Ubuntu por no tener por defecto un buen controlador de flash, ALGO INDISPENSABLE HOY EN DÍA, ya que el flash-plugin de ubuntu no solo no viene en el sistema sino que no funciona bien y al parecer crea conflicto con otros controladores.

CONCLUSIÓN:
En suma, cerca de 5 horas perdidas, googleando, instalando, probando, desinstalando controladores y cuanta cosa veía en foros, para hacer lo que hago en windows con un click de 0,2 segundos  =D>=D>=D>

Los desarrolladores de Ubuntu deberían pensar que una de las prioridades de un sistema operativo en nuestros días es el Internet, y tener por defecto en el sistema todo lo que el 90% de los usuarios puedan necesitar, para no andar foreando (perdon por la palabra) y perdiendo tiempo por 1000 estupideces de fácil solución. #-o

---

### Post by Carlos C on 2009-08-05
> **daniel7110 said:**
> Los desarrolladores de Ubuntu deberían pensar que una de las prioridades de un sistema operativo en nuestros días es el Internet, y tener por defecto en el sistema todo lo que el 90% de los usuarios puedan necesitar, para no andar foreando (perdon por la palabra) y perdiendo tiempo por 1000 estupideces de fácil solución. #-o

Flash es un tema complicado en Linux, de eso hay bastante información en internet. Existe más de una opción para instalar en tu sistema y lo que hay en juego se relaciona con cuestiones prácticas, pero también ideológicas. Lo que crees es una estupidez para mi no lo es, es un asunto importante. Te recomiendo leer, investigar un poco más sobre el tema.

En el foro hemos puesto un thread con fuentes donde buscar información:

[http://ubuntuforums.org/showthread.php?t=1198911](http://ubuntuforums.org/showthread.php?t=1198911)

Una de las recomendaciones es [https://help.ubuntu.com](https://help.ubuntu.com). Si en ese sitio buscas flshplugin, el primer enlace que aparece te explica las opciones con las que cuentas.

---

### Post by psyched on 2009-10-16
A mi me solucionó la papeleta la aportación de [COLOR=Red]Meisterwerk [COLOR=Black]con lo del conflicto entre swfdec y adobe flash, auque a diferencia de él dejé adobe-flash plugin y flash plugin-installer, y con esto me va de muerte.graciaaas:P:P[/COLOR]
[/COLOR]

---

### Post by vaisen on 2010-01-06
Hola buenos dias!soy bastante nuevo en esto del mundo ubuntu...y debido a mis pocos conocimientos requiero vuestra ayuda. Para no abrir otro hilo os lo espondre aqui que el tema es realacionado. Llevo como dos dias intentando poder ver videos del youtube...he hecho mil formas para poder conseguirlo pero ninguna con exito.
 -adquirir permisos con nautilus y copiar el archivo .so de adobe flash player en la carpeta de modzilla
-entrar en terminal,desinstalar lo anterior y instalar en non free..
 estoy bastante perdido ya que hago todo eso y al poner la pagina de youtube no se ven o si hacen intento se oyen entrecortaos...el bufer fatal..
 espero alguna solucion efectiva estoy en ubuntu 9.04

---

### Post by Carlos C on 2010-01-06
Hola ¿Tienes Ubuntu 32 o 64bit?

---

### Post by vaisen on 2010-01-06
como debo saberlo?

---

### Post by Carlos C on 2010-01-06
> **vaisen said:**
> como debo saberlo?
Escribe en el terminal:
```
uname -a
```
Si tienes Ubuntu 64bit puedes mirar [acá]("http://ubuntuforums.org/showthread.php?t=1369992").

Saludos.

---

