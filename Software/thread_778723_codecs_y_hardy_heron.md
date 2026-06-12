---
title: "codecs y hardy heron"
date: 2008-05-02
forum: Software
---

### Post by hernan blau on 2008-05-02
Hola. INstalé 8.04 y el firefox no me abre vínculos que remiten a audio o video. Por ejemplo: en la página de Infobae no abre los vínculos a las radios mega y amadeus. Lo mismo sucede con la página de tn en vivo. Se abre el totem (creo) y sale una leyenda que dice "no video". Los dvd sólo los pude abrir con VLC y algunos con Kaffeine. En fin, parece que el problema son otra vez los códecs, como cada vez que cambiamos de versión. Ah. instalé libdvd.... y ubuntu-restricted-extras. ¿Se les ocurre algo? Cordialmente, HB.

---

### Post by Mauro22 on 2008-05-02
Hasta que lo mencionaste!!


Me meti en la pagina de TN para corroborar y efectivamente no reproduce.

Me sale este error:

"La reproducción de esta película requiere un complemento Fuente de protocolo Microsoft Media Server (MMS) que no está instalado."


Asi que voy a dar vueltas por synaptic :confused:

---

### Post by MeduZa on 2008-05-02
desde consola :

sudo apt-get install ubuntu-restricted-extras

o en synaptics:
buscar: ubuntu-restricted-extras y listo
con eso deberia andar, ademas del plugin de audio y video para redireccionar.
PD:necesitan tener activados todos los repositorios.

---

### Post by Mauro22 on 2008-05-02
> **hernan blau said:**
> .... Ah. instalé libdvd.... y ubuntu-restricted-extras. ¿Se les ocurre algo? Cordialmente, HB.


Ya los tiene instalado!



----------------------------------------------------------

Instale el paquete mimms y ahora TN se me ve :D
Me fije las radios que pones ahi y tambien andan!


Probalo!

---

### Post by hernan blau on 2008-05-02
Probé con mimms y no pasa nada !! Gracias.

---

### Post by Mauro22 on 2008-05-02
sudo apt-get install libmms ffmpeg


A ver si va?

---

### Post by spg76 on 2008-05-02
¿Tenes instalado w32codecs?
Si no es así, lo podés instalar agregando el repositorio de Medibuntu.
Para Hardy, ingresa en una terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install w32codecs
```
Si tenes 64 bits, cambia el nombre del paquete por **w64codecs**.

---

### Post by niko_3100 on 2008-05-02
Los codecs son los gstreamer0.10-ffmpeg fijate esos y conta si te sirvieron.

---

### Post by srmantis on 2008-05-02
Para firefox escribe:
about: plugins (todo junto, o separe para que no apareciera la cara)
revisa que tengas instalado programas para reproducir mp3, rm y cosas asi.

si te falta para mp3: ubuntu restricted extra y tambien GStreamer extra plugins y en general todos los que empiecen con gstreamer.

Por defecto usa totem, pero para algunos sitios necesita mplayer para firefox:
sudo apt-get install mozilla-mplayer

uno de esos deberia resolver el problema.

---

### Post by lushnok on 2008-05-11
> **MeduZa said:**
> desde consola :

sudo apt-get install ubuntu-restricted-extras

o en synaptics:
buscar: ubuntu-restricted-extras y listo
con eso deberia andar, ademas del plugin de audio y video para redireccionar.
PD:necesitan tener activados todos los repositorios.

Estimados:
ya he instalado estos extras... pero naranjas aun. Ni TN, ni las radios, ni MP3 ni WMA ni nada...

¿vale aclarar que es mi segundo día en Ubuntu?

---

### Post by spg76 on 2008-05-11
> **lushnok said:**
> Estimados:
ya he instalado estos extras... pero naranjas aun. Ni TN, ni las radios, ni MP3 ni WMA ni nada...

¿vale aclarar que es mi segundo día en Ubuntu?

Para ver TN, escuchar algunas radios y WMA tenés que instalar w32codecs.
Yo te recomiendo lo que posteé [más arriba]("http://ubuntuforums.org/showpost.php?p=4862158&postcount=7").
Para escuchar MP3, abri un archivo de este tipo con Totem y automaticamente te debería aparecer un cuadro para instalar los codecs correspondientes.
Espero que te sirva.

---

### Post by lushnok on 2008-05-11
Gracias, gracias,

hice ambas cosas:
1) con los codecs w32, copiando y pegando exactamente eso que ponías más arriba, me da como resultado esto:
nazareno@nazareno-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for nazareno: 
--21:21:55--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolviendo [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Conectando a [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

21:21:55 (15.66 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' guardado [226/226]


Pero tampoco pasa nada.

2) probé abrir mp3 con con Totem y con Rythmbox (o como se escriba) y tampoco pasa naranja. (tira un error)

Es raro, por que, por ejemplo en [www.tn.com.ar](www.tn.com.ar) carga una primera imágen pero después se pone la pantalla (donde está el video) negra.
Con los mp3, como dije, da un error...

Creo que tendré que tomar un curso!

---

### Post by lushnok on 2008-05-11
No sé que pasó. Pero después de un rato el reproductor de música se colgó (sin haber funcionado nunca ningún mp3 ni nada). Luego no respondía nada. Apagué, reinicíe y comenzó a funcionar todo correctamente.

Gracias a todos!

---

### Post by Marcelo Ramone on 2008-05-14
Esta guía la rompe:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by EnriqueK on 2008-05-14
El problema viene de parte de Firefox 3 beta 5 que trae instalado Hardy por defecto , sugiero desinstalarlo y en su lugar instalar Firefox-2 (está en repositorios) , esto por que permite instalar la extensión **MediaPlayerConnectivity** (en FF3 no está disponible), con esta extensión se abre el reproductor adecuado para el tipo de Streaming , normalmente con Mplayer alcanza para todos siempre que se tenga instalado el W32codec , también lo podés configurar para que abra con VLC, pero este soporta menos tipos de Streaming que el  Mplayer.
Para instalar el Firefox-2 además de desinstalar el Firefox-3 hay que borrar además la carpeta **.mozilla** que se encuentra oculta en la carpeta del usuario , previo respaldo de marcadores y otros archivos que puedan ser útiles como por ejemplo cookies. Con estos pasos previos, recién se instala el Firefox-2.
Otra posibilidad es instalar el navegador **Flock** que se lo puede descargar de la página de **Getdeb** , la ventaja es que no interfiere con la instalación actual de Firefox y se puede instalar la extensión MediaPlayerConnectivity, en lo personal prefiero instalar Firefox-2 por que la versión actual presenta varios fallos y sobretodo muchas son las extensiones que no fueron portadas y en base a Udrades anteriore, me temo que varias no estarán disponibles para FF3 .

---

### Post by faktorqm on 2008-05-14
no estoy de acuerdo que vlc soporte menos formatos que mplayer...
yo uso vlc + w32codecs + gstreamer*  y me reproduce el 95% de lo que necesito. (me faltan algunas cosas que usan java, pero eso es problema aparte)

[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)
[http://www.mplayerhq.hu/design7/info.html#docs](http://www.mplayerhq.hu/design7/info.html#docs)

Aparte hay una realidad, vlc al tener los codecs embebidos ocupa 5% (en mi caso) en memoria mientras que el mplayer tiene que ir a buscar las .so, cargarlas y usarlas, y ocupa mucho mas (casi el 20% en mi caso). Salu2!

---

### Post by EnriqueK on 2008-05-14
El VLC, no soporta Shoutcast audio , tampoco MOV y creo que tampoco los streamings de Real Player y por si fuera poco, algunas variantes de streaming para WMP tampoco las soporta, a parte de todo esto, como dije antes,  toda la dificultad radica en tener FF3  que no permite instalar la extensión MediaPlayerConnectivity para poder detectar los archivos de audio/video incrustados que vienen en las páginas oficiales desde donde se emiten.
Para hacerlo fácil y rápido, instalen el navegado Flock que está basado en Firefox-2 y allí pueden instalar el complemento o extensión MediaPlayerConnectivity, con la ventaja de no interferir con la instalación actual de Firefox3 beta 5.

---

### Post by faktorqm on 2008-05-14
shoutcast audio: fijate esta direccion, yo la escucho, adjunto screenshot.

[http://213.251.190.147:9500](http://213.251.190.147:9500)

[[img=http://img205.imageshack.us/img205/2589/lalalazj6.th.jpg]](http://img205.imageshack.us/my.php?image=lalalazj6.jpg)

mov: Los .mov los puedo ver, la camara digital codifica con quicktime y de hecho el vlc es el unico que me lo reproduce sin cortarse. no te puedo poner el screenshot por que sale azul la parte del video y no tiene gracia, si saco con la digital tambien se ve mal :( 

VLC tiene el paquete mozilla-plugin-vlc que se te adapta. no lo probe en ff3, uso opera :D

en el wiki de vlc dice que si soporta Real media: [http://wiki.videolan.org/RealMedia](http://wiki.videolan.org/RealMedia)

el unico que dice unsupported es el wm9. Salu2!!

---

### Post by GGsalas on 2008-05-16
Acabo de entrar a [http://www.tn.com.ar/](http://www.tn.com.ar/) y veo bien el video, sólo instalé Ubuntu Restricted extras.

---

### Post by lushnok on 2008-05-19
Volvieron los problemas.

tengo instalado (según synaptic) el W32Codecs. También los restricted extras.

pero dejaron de funcionar los sonidos, el Rhythmbox directamente se cuelga cuando intento ejecutar un mp3. El totem da el siguiente error: "failed to connect stream: invalid argument"

en la terminal tengo este error (que por ahí puede dar un poco más de luz al tema: 
para w32codecs
nazareno@nazareno-laptop:~$ sudo apt-get install w32codecs
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

para nazareno@nazareno-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any ideas?

PD: las noticias de [www.lanacion.com](www.lanacion.com) que son videitos pueden cargarse, creo que son en flash o java... 
PD: los sonidos del Pidgin tampoco funcan ¿tendrá algo que ver?
PD: en TN el error que aparece al cliquear en la pantalla negra: "Ha ocurrido un error. se pudo abrir la dirección: quizá no tiene permiso para abrir el archivo"

---

### Post by lushnok on 2008-05-19
Lo de TN lo resolví con:
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer 

instaló, como ven, el gecko player, que sí está reproduciendo mp3 y wma por ejemplo. También se ve como dije antes TN (sin ver los controles en la pantalla, salvo que lo pase a pantalla completa).

El rhythmbox y el totem siguen sin funcionar.

---

### Post by GGsalas on 2008-05-19
No creo que te sirva de mucho, pero yo tengo Ubuntu hardy heron y lo único que instalé es Ubuntu restricted extras desde Sinaptic y hasta lo que probé no tuve probblemas de codecs. A la página de TN ingreso y veo todo blanco, pero si voy a minuto1.com a la derecha se autoejecuta un video de tn en vivo :P

Saludos

---

### Post by lega on 2008-05-20
Aprovecho y pregunto acá, ayer quise escuchar la rock and pop y al hacer click en la web,donde decia "en vivo" me apareció un cartel para que eligiera la aplicación con que quería que se abriera el link...y ahí quede...no supe para donde ir...donde debería buscar el ejecutable para que se abra el mplayer?

---

### Post by lushnok on 2008-06-12
Mil idas, mil vueltas, no sé por donde anduve solo sé a donde llegué.
Ahora volví a poder usar Rhythmbox y totem! solo que sigo sin poder ver el P*t* TN!

---

### Post by Simbiosys on 2008-06-12
Yo tengo HH y tampoco puedo.
Instale todo lo que mencionan en esta pagina...
ni rock and pop ni tn... 

cuando entro a TN aparece el plugin media player, se conecta con el server y despues aparece "Detenido".
La rock and pop, me abre el Totem y me dice que "Es posible que no tenga permisos"...

---

### Post by hernan blau on 2008-06-12
Aún hoy, mucho después de iniciar este hilo, no puedo ver tn ni acceder a varias radios de la red. Reinstalé HH, seguí todas las sugerencias y seguimos igual. ¡¡¡¡¡¡¡Automatix volvé que te perdonamos !!!!!!!!!!!!

---

### Post by faktorqm on 2008-06-13
Al automatix yo todavia no lo perdoné....

faktorqm ve TN en VLC (con sonido y video), poniendo esta direccion:

mms://streamtn.uigc.net/TN

No sale en el pantallazo, sale negro, pero bueno.

faktorqm ve TN desde la página con plugin de mplayer para mozilla desde opera... tambien con sonido. adjunto screenshot.

faktorqm no quiere ser malo ni gozarlos ni nada de eso, va con la mejor intencion para que vean que se puede. :lolflag:

---

### Post by hernan blau on 2008-06-13
Les cuento que con el Konqueror actualizado puedo acceder a Tn, Amadeus, la Mega y seguiré probando con otras.

---

### Post by lushnok on 2008-06-15
nada

---

### Post by valucha on 2008-06-17
[COLOR="DarkOrchid"]Yo abrí tn desde el totem y la primera vez me bajó los codecs y ya funciona a la perfección.

Este tutorial [http://ubuntu-ar.org/soporte/comos/radios-argentinas](http://ubuntu-ar.org/soporte/comos/radios-argentinas) es muy bueno, está desactualizado peor lo que yo hago es:
-Para las radios copio el link que me da de cada radio (ej: para la Rock&Pop mms://200.59.146.10/rockandpop-ba) y lo pego cuando creo una "radio nueva" en el Rhythmbox.
-Para tn, copio la dire que te da mms://wmedia01.uigc.net/TN y la pego en elTotem en : Abrir dirección....

En ambos programas me pidió que baje codecs, los bajé y funciona todo, y desde internet también puedo ver tn y escuchar radios.

Los codecs que tengo instalados son:

gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad/-plugins-base/plugins-base-apps/plugins-good/plugins-ugly/
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x

No instalé ni el mplayer ni nigun otro programa para hacer esto.


OJalá que les sirva o al menos los guíe.[/COLOR]

---

### Post by hernan blau on 2008-06-19
Valucha: Hice lo que indicás. Pegué la dirección de TN en "abrir dirección del Totem y salió una leyenda que dice que ocurrió un error y que "No se pudo abrir la dirección; quizá no tiene permiso para abrir el archivo." Tengo esos plugins que tenés vos. Cosa de mandinga. Lo abro con Konqueror. Cordialmente HB.

---

### Post by lushnok on 2008-06-19
exactamente el mismo issue.
me mata :(

---

### Post by valucha on 2008-06-20
[COLOR="DarkOrchid"]El tema es, a mi me pasó que cuando lo intento abrir por primera vez por el totem que funciona siempre. Me bajo los codecs y listo.
Pero ante una instalación no nueva, nunca he podido.
Tampoco en otras compus.
No sé cuál será el problema :S[/COLOR]

---

