---
title: "[SOLVED] Como visualiza videos you tube con Opera?"
date: 2009-07-10
forum: Software
---

### Post by matias_tati on 2009-07-10
Tengo Ubuntu 9.04 y no logro visualizar videos you tube con el opera y es una lastima pq en windows siempre use Opera y me puse muy feliz cuando vi que estaba para linux. Y con Mozilla Fire fox no sirve el control de volumen de You Tube. Hay alguna solucion para estas cuestiones?
Gracias.!!!

---

### Post by staar on 2009-07-10
podrías ser más específico, donde debería estar el video, hay algo? si le haces click te sale el menu de flash? o directamente hay un espacio en blanco? como instalaste flash? y opera?

saludos

---

### Post by matias_tati on 2009-07-10
Hola, te paso a contar el opera baje un ejecutable que me instalo el programa (no se si se llamara asi), flash no instale intente googleando pero no funcionaron las veces que lo intente y donde deberia estar el video hay un espacio en blanco. Gracias....

---

### Post by staar on 2009-07-10
la forma correcta de instalar opera es bajando desde la página oficial el archivo .deb, no se si a eso te referis...

flash se instala desde Synaptic, buscalo e instalalo, después opera lo va a cargar solo...

saludos

---

### Post by PiterUy on 2009-07-10
yo tengo un problema similar, pero con firefox. Instalé el flash 10, pero los videos los veo cortados, muchas veces sale el sonido pero el video se ve solo como una foto. He instalado flash de mil formas distintas para tratar de solucionarlo, pero nada.... muchas gracias!!

---

### Post by staar on 2009-07-11
flash es malo, no solo el plugin para linux, que en si es malo, si no que el mismo flash es malo por como esta hecho, concebido y realizado, asi que no te extrañes de que ande mal, lamentablemente ya es algo normal y nada podemos hacer, más que esperar que adobe algún día haga algo bien...

saludos

---

### Post by matias_tati on 2009-07-11
Instale estos dos pero todo sigue igual donmde debe estar el vdeo hay un espacio en blanco

[IMG]http://img291.imageshack.us/img291/603/pantallazouxs.png[/IMG]

---

### Post by papachan on 2009-07-11
No se si te sirve. pero puede ser que esto se resuelve con el instalador del Opera 10 beta para ubuntu.

[http://ubuntulife.wordpress.com/2009/06/03/opera-10-beta-disponible/](http://ubuntulife.wordpress.com/2009/06/03/opera-10-beta-disponible/)

---

### Post by staar on 2009-07-11
ese paquete baja el plugin y lo instala en /usr/lib/adobe-flashplugin, en Herramientas > Opciones > Avanzado > Contenido > Opciones de contenido se pueden modificar las rutas que usa Opera para buscar plugins, podés agregar esa ruta (ojo, fijate de agregar el : para separar las rutas) y reiniciar opera para ver si lo carga, podés comprobar si opera encuentra el plugin en Herramientas > Avanzado > Conectores

saludos

---

### Post by matias_tati on 2009-07-11
Nada che

[IMG]http://img509.imageshack.us/img509/9531/pantallazorutadeconecto.png[/IMG]
[IMG]http://yfrog.com/0wpantallazorutadeconectop[/IMG]

---

### Post by staar on 2009-07-11
che que raro, a mi me lo toma de una, podés probar copiando el plugin (el archivo libflashplayer.so) desde la carpeta /usr/lib/adobe-flashplugin/ a /usr/lib/opera/plugins

saludos

---

### Post by matias_tati on 2009-07-11
No me deja
Me dice:

Error al copiar «libflashplayer.so».
Hubo un error al copiar el archivo en /usr/lib/opera/plugins.

---

### Post by alfplayer on 2009-07-11
Hay que usar la versión para Ubuntu del sitio de Opera. Con esa debería funcionar todo sin problemas.

---

### Post by staar on 2009-07-11
tenés que hacerlo con sudo ```
sudo cp /usr/lib/adobe-flashplayer/libflashplayer.so /usr/lib/opera/plugins/
```

saludos

---

### Post by matias_tati on 2009-07-11
Creo que algo mal hice pq no me aparece la carpeta adobe flsh como vos me decis sino que me aparece flash instaler. No hay forma de instalar todo nuevamente para estar seguro de que estoy haciendo todo bien, seria mejor?

---

### Post by matias_tati on 2009-07-12
Hay solucion para lo mio?

---

### Post by staar on 2009-07-12
raro... probá reinstalando flash o instalándolo desde la página oficial (para lo segundo es altamente recomendable desinstalar previamente todo rastro de flash)

saludos

---

### Post by matias_tati on 2009-07-13
Baje el flash. Copie en la carpeta de plugins del opera el archivo.so reinicie opera y nada.

---

### Post by staar on 2009-07-13
o.O

si ponés opera:plugins en la barra de direcciones, te sale la dirección al archivo .so? tenés activados los conectores?

saludos

---

### Post by matias_tati on 2009-07-13
No no me sale parece que busca en la ruta de Mozilla firefox. Agrego la ruta del archivo que baje pero nada.

[IMG]http://img179.imageshack.us/img179/9051/pantallazoo.png[/IMG]

---

### Post by staar on 2009-07-13
creo que el problema esta en que tenés un plugin de flash viejo ahí, probá desinstalando todo rastro de flash del sistema, en especial lo que sea de la versión 9 y volviendolo a instalar de nuevo...

saludos

---

### Post by alfplayer on 2009-07-13
En 9.04 yo lo tengo en /usr/lib/flashplugin-installer (ese directorio no lo tenés en la última captura).

---

### Post by matias_tati on 2009-07-13
> **staar said:**
> creo que el problema esta en que tenés un plugin de flash viejo ahí, probá desinstalando todo rastro de flash del sistema, en especial lo que sea de la versión 9 y volviendolo a instalar de nuevo...

saludos

Yo tmbn creo que viene por ahi la cosa pero como hago para desinstalarlo completamente del sistema? Quiero saber si es como pienso. Grax.

---

### Post by staar on 2009-07-13
primero otra cosa, este comando ```
sudo update-alternatives --config xulrunner-addons-flashplugin
``` servía, al menos en Hardy, para que pudieras elegir entre los distintos plugins de flash que hay instalados en el sistema, no se si seguirá siendo igual (no importa que sea para firefox, porque opera busca los plugins en la carpeta de firefox)

sino, para borrarlo, busca por Synaptic y desinstala todo lo que parezca flash (adobe-flashplugin, flashplugin-nonfree, flashplugin-installer, etc), fijate en firefox también, y de última borrándolo a mano...

saludos

---

### Post by matias_tati on 2009-07-13
Hay uno que no lo puedo borrar esta en usr/lib/adobe-flashplugin

---

### Post by matias_tati on 2009-07-14
Los aburri? Yo tmbn me hubiera aburrido de mi mismo. Que sera lo que pasa aca?

---

### Post by Hei Ku on 2009-07-15
Por que no lo podes borrar? Que mensaje te tira?

En linux son importantes los mensajes de error. Significan algo y nos dan una pista de qué hacer.

---

### Post by matias_tati on 2009-07-15
Me tira este error

[IMG]http://img505.imageshack.us/img505/83/pantallazoventanasinttu.png[/IMG]

---

### Post by staar on 2009-07-15
bastante claro el mensaje, necesitas permisos de root para hacerlo, abrí el Navegador de archivos con Alt + F2 -> *gksu nautilus* (OJO con esto, no borres nada de más)

saludos

---

### Post by matias_tati on 2009-07-15
Listo no hay rastros de Flash. Ahora baje el ultimo plugin de la pag de adobe pero no lo puedo copiar a la carpeta de plugins de mozila manualmente. El plugin que descargue lo tengo alojada en Documentos.
Gracias.
[IMG]http://img216.imageshack.us/img216/9003/pantallazoinstallflashp.png[/IMG]

---

### Post by staar on 2009-07-15
Aplicaciones > Accesorios > Terminal
```
cd Documentos/install_flash_player_10_linux/
```
```
sudo chmod 777 flashplayer-installer
```
```
sudo sh flashplayer-installer
```
el script hace el resto...

saludos

---

### Post by matias_tati on 2009-07-15
Me quede ahi

[IMG]http://img50.imageshack.us/img50/9051/pantallazoo.png[/IMG]

---

### Post by staar on 2009-07-15
poné /usr/lib/opera/

saludos

---

### Post by matias_tati on 2009-07-15
No hay caso.

---

### Post by daniel7110 on 2009-08-02
> **papachan said:**
> No se si te sirve. pero puede ser que esto se resuelve con el instalador del Opera 10 beta para ubuntu.

[http://ubuntulife.wordpress.com/2009/06/03/opera-10-beta-disponible/](http://ubuntulife.wordpress.com/2009/06/03/opera-10-beta-disponible/)

POR FIN!!! 
Luego de instalar Ubuntu 9.04 y maldecirlo 765 veces he podido ver un video de youtube sin que consuma 99% de cpu en firefox o sin que me aparezca un fondo blanco en opera!](*,)
El culpable...
Ubuntu por no tener por defecto un buen controlador de flash, ALGO INDISPENSABLE HOY EN DÍA, ya que el flash-plugin de ubuntu no solo no viene en el sistema sino que no funciona bien y al parecer crea conflicto con otros controladores. Por lo que además de instalar opera 10 Beta, tuve que desinstalar primero todo lo que había de flash desde synaptic e instalar el "flashplugin-installer". Sólo este me funcionó, porque ni el de Ubuntu, ni el de la web de adobe, ni copiando el flash a la carpeta de opera ni nada de nada!! Y NO ES PROBLEMA DE LA TARJETA GRÁFICA, QUE SI FUERA ASÍ NO FUNCIONARÍA EL FLASH EN WINDOWS.

CONCLUSIÓN:
En suma, cerca de 5 horas perdidas, googleando, instalando, probando, desinstalando controladores y cuanta cosa veía en foros, para hacer lo que hago en windows con un click de 0,2 segundos  =D>=D>=D>

Los desarrolladores de Ubuntu deberían pensar que una de las prioridades de un sistema operativo en nuestros días es el Internet, y tener por defecto en el sistema todo lo que el 90% de los usuarios puedan necesitar, para no andar foreando (perdon por la palabra) y perdiendo tiempo

---

### Post by pablo.s on 2009-08-02
Troll Alert.
El mismo exacto igual
post en el foro chileno.

---

### Post by staar on 2009-08-02
nadie te obliga a usar ubuntu si no te gusta...

---

### Post by matias_tati on 2009-08-03
Mira entiendo a esta persona pero yo hoy estuve usando la pc de mi vieja y me parecio de la edad de piedra creo que no podria volver a windows.
Staar entonces que hago ahora yo reinstale ubuntu y esta vez no probe instalar opera pero me gusta es el que siempre use y el mas rapido como tendria que hacer?

---

### Post by Cajuma on 2009-08-03
Daniel.
[LEFT]Si te referís a U-JJ o K-JJ debes haber cometido algún error de instalación, yo desde que los instale hace dos meses navego ,chateo, _veo videos de You Tube_, grabo discos imprimo, escucho musica, bajo torrents, juego, utilizo Firefox, y Konqueror, ah y escucho La cien, Radio Petti y musica de los ochenta etc. etc. solo habiendo agregado los repositorios correspondientes y las actualizaciones de rigor, Uso Firefox y Konqueror y no
tuve ningún drama, que no haya sido por mis propios errores, la solución, seguí enriqueciendo a Bill con un solo Clic.
Adiós. :D
[/LEFT]

---

### Post by staar on 2009-08-03
> **matias_tati said:**
> Mira entiendo a esta persona pero yo hoy estuve usando la pc de mi vieja y me parecio de la edad de piedra creo que no podria volver a windows.
Staar entonces que hago ahora yo reinstale ubuntu y esta vez no probe instalar opera pero me gusta es el que siempre use y el mas rapido como tendria que hacer?
me sigue pareciendo raro que no te ande, probá instalando la beta 2 de Opera 10 (o una de las builds semanales que postean [acá]("http://myopera.com/desktopteam/blog"), son estables y lo 'último' :-D <- se nota que tengo versionitis)

saludos

---

### Post by armagedonc on 2009-08-03
Hola 
estuve leyendo foros con respecto a esto, ami me paso algo parecido con opera pero yo no me hice problemas y me fui a firefox de una :P.

En la pagina de adobeflash player 10 aparecen los requerimientos de software para poder correr archivos flash entre otras cosas no sale soportado opera.[http://http://www.adobe.com/products/flashplayer/systemreqs/#ft1]("http://http://www.adobe.com/products/flashplayer/systemreqs/#ft1"). 

Bueno ya algo mas que me llama la atencion.
>    2. Only Advanced Linux Sound Architecture (ALSA) is supported (OSS/ESD will not play audio; audio will silently fail). Only GTK2-based browser versions are supported.



Y leyendo algunos foros mas, si opera 10 no funciona con gtk-2, quizas para que funcione flash deberia cambiar a una distribucion de opera mas antigua. 

saludos

---

### Post by staar on 2009-08-03
opera usa un poco de Qt en linux, pero siempre lo hizo y nunca usó gtk, y flash anda (lo comprobé personalmente) en todas las versiones...

lo que opera hace en linux es usar los plugins de mozilla (utiliza un wrapper para ello) así que no importa que adobe no haga el plugin específico para opera, si lo hace para firefox es suficiente...

saludos

---

### Post by matias_tati on 2009-08-06
Al FIIINNNNN!!!!!!!!!!!!!!!!!!!!!!!!!!
Bueno les cuento como hize y fue tan facil que me sorprendio
Primero baje Opera Beta 10 de la pag oficial(hermoss por cierto) luego en wikipedia estaba la informacion de como ver videso en you tube. baje de la pag de adobe el archivo falsh libflashplayer.so y debia copiarlo mediante sudo a /usr/lib/opera/plugins/ pero necesitas permisos de root y como no supe hacerlo mediante sudo lo copie utlizan este comando que me dio star *gksu nautilus , *lo copie y listo ningun problema, no instale nada de synapthic ni desinstale versiones anteriores de flash no hizo falta nada de eso. Hasta me funciona el control de volumen desde you tube, buenisimo!!!!!! Ahora me doy cuenta de que cometi errores tontos de principiante. Un saludo a todos y gracias por la ayuda!!!!!!!!!!!!!! Pueden cerrar esto como solucionado. GRACIAS!!!!

---

### Post by matias_tati on 2009-08-06
Hasta lo pase a español sin problemas....
Saludos!!!!

---

### Post by matias_tati on 2009-08-10
Una ultima preg note que es tan bueno este plugin que descargue desde adobe que anda mejor que en ventanas inclusive. ahora si lo copio a la carpeta de plugins de firefox me debe funcionar correctamente? Pq note que Opera ahora esta muy adelante en You Tube con este nuevo plugin. Saludos!!!!

---

