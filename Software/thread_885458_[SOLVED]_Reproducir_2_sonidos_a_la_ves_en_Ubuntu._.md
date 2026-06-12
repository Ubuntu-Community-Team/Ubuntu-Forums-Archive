---
title: "[SOLVED] Reproducir 2 sonidos a la ves en Ubuntu. Se puede?"
date: 2008-08-10
forum: Software
---

### Post by victor_nesta on 2008-08-10
Buenas a tod@s!
Voy a explicar paso a paso lo que hice. un poquitin de paciencia :)

  Instale el Hardy, termino con toda la perinola de actualizaciones compiz y empiezo a disfrutarlo. Creo el .asoundrc para mi placa SB SL (CA0106) y el sistema 5.1. y ya escucho musica en mis 6 parlantes con ALSA.
De pesado que soy, quiero probar el micrófono (para tenerlo ahi, por las dudas); <Conferencia de Sonidos> la reproducion con el ALSA, pero la captura no hubo forma (o no encontré) y lo deje en Pulseaudio que si termino funcionando. Todo listo (me dije), pruebo acá, pruebo allá y me doy cuenta que mi reproductor de musica, reproducía pero no emitía sonido, ya nada emitía sonido salvo mi micrófono y los vídeos de youtube. 

Leyendo un por ahí, encontré esto
[I]  
Fabián Montealegre:    
Ya lo medio arreglé.
Era un problema con el  Pulse-audio. Lo que hice fue volver a poner el
ALSA de siempre. No sabía que Ubuntu había cambiado los drivers de
sonido.
Ahora solo falta hacer que sirva el audio en el Zsnes :P
	
Jorge Vargas :
esto es un bug feo que tiene 8.04 realmente el problema esta alrededor
de flash y ff3 ya que el primero funcionando sobre el segundo no esta
soltando el canal de audio así que cualquier cosa que corras que tenga
sonido mientras flash y ff3 este arriba no va a sonar, si cierras ff3
debería funcionar."[/I]

Esto es o tiene parte de cierto ya que o escuchas una cosa o la otra.

Resumiendo.... Hay alguna forma de poder escuchar 2 cosas a la ves?


Gracias!! :guitar: <--- pero en una sola pista :lolflag:

---

### Post by [P]oli on 2008-08-10
Habría que probar alguna forma de hacer andar el micrófono en ALSA, yo tengo programas de ejecutados bajo WINE, el Exaile, y youtube sonando al mismo tiempo y no tengo ningún problema :S

---

### Post by victor_nesta on 2008-08-11
Me levante super temprano con esto de las Olimpiadas :)
Bueno, primero lo primero. Gracias por la respuesta!!
Ya configure el Mic en ALSA, ni idea como pero lo tomo sin problemas.
Pongo un Vídeo, después un MP3 y nada de sonido. (aunque se estaban reproduciendo evidentemente)
Miro bien, y en un escritorio tenia el VirtualBox funcionando. Lo cierro, vuelvo a abrir mi MP3 y salio el sonido a baldazos.
En fin, evidentemente la primer aplicación en ser ejecutada (independientemente de cual sea) se hace con el control total del ALSA.

Les muestro mi .asoundrc

#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels.
#So if you fx want to watch a 5.1 movie, on the analog output, this is the option you want.

pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}

#####################END ASOUNDRC#################################

Estará por acá la cuestión? 
Tendrá que ver con el Duplex? Es lo que se me ocurre, si es así ni idea donde se habilita. :confused:

Saludos y Gracias!

---

### Post by sdennie on 2008-08-11
Yo también tenia muchos problemas con Pulse Audio.  Cambié todo a ALSA con Sistema->Preferencias->Sonido y ahora anda mucho mejor.  No se si ALSA usa el .asoundrc (me parece que si) pero debes probarlo sin .asoundrc también.

Igual fijate en la configuracion de tus aplicaciones si estan usando Pulse Audio o ALSA o OSS.  Con una mixta vas a tener problemas.

---

### Post by victor_nesta on 2008-08-11
Gracias por la respuesta.
Me di cuenta de dos cosas.
[INDENT]La primera, de que soy un pendejo :mad: (por no decir otra cosa), tendría que haber probado antes lo de eliminar el .asoundrc, si ya se, soy un pelo##**.[/INDENT]

[INDENT]Segunda, no existe ningún Bug, el único que existe es el que yo hice en el .asoundrc. Ahora bien, lo malo es no duplica el sonido a todos los parlante, solo escucho en 2 como era de esperar.[/INDENT]

Ahora necesito ayuda con el .asoundrc o con algun truco para reproducir en mi 5.1.

Gracias a todos!

Me voy con dos frase de Sherlock Holmes
"El mundo esta lleno de cosas evidentes en la que nadie se fija ni por casualidad"
"Como regla general, cuanto mas extravagante es una cosa, menos misteriosa suele resultar"

---

### Post by [P]oli on 2008-08-11
> **victor_nesta said:**
> Gracias por la respuesta.
Me di cuenta de dos cosas.
[INDENT]La primera, de que soy un pendejo :mad: (por no decir otra cosa), tendría que haber probado antes lo de eliminar el .asoundrc, si ya se, soy un pelo##**.[/INDENT]

[INDENT]Segunda, no existe ningún Bug, el único que existe es el que yo hice en el .asoundrc. Ahora bien, lo malo es no duplica el sonido a todos los parlante, solo escucho en 2 como era de esperar.[/INDENT]

Ahora necesito ayuda con el .asoundrc o con algun truco para reproducir en mi 5.1.

Gracias a todos!

Me voy con dos frase de Sherlock Holmes
"El mundo esta lleno de cosas evidentes en la que nadie se fija ni por casualidad"
"Como regla general, cuanto mas extravagante es una cosa, menos misteriosa suele resultar"

Pero ahora suena TODO y BIEN?

---

### Post by victor_nesta on 2008-08-11
> **'[P]oli said:**
> Pero ahora suena TODO y BIEN?

Gracias por el interés!

Ahora suenan varias cosas a la ves, puedo tener abierto youtube y Totem a la ves y suenan los al mismo tiempo sin problemas. :)

Lo que perdí al borrar el .asoundrc es la duplicación de los canales, ya que solo suenan 2 parlantes de mis 5+1. :(

Saludos

---

### Post by faktorqm on 2008-08-12
Tenes el iconito del parlantito al lado del relojito? (jajajaj)
we, hacele click derecho -> abrir control de volumen. Ahi te abre el control de volumen, y vas a editar -> preferencias. Ahi te abre una ventana con cosas, activa lo que quieras, pero principalmente tenes que activar uno que se llama "channel mode". Le das cerrar y ahi vas a ver que tenes una pestaña nueva que se llama "opciones" (al menos en mi caso) y ahi elegis que sistema de sonido elegis. Espero haber sido de ayuda. Salu2!!

---

### Post by pol666 on 2008-08-12
Estas usando 8.04? por que estas modificando el asound? tendrias que usar pulseaudio. Sii queres ahora te digo como tener 5.1 con pulseaudio, Si queres seguir usando alsa, no modifiques mas el asoundrc, modifica el esd.conf ahora en un rato te paso mi codigo de Debian, que ahi tengo alsa,

---

### Post by victor_nesta on 2008-08-13
Hola, Gracias!!!
Después de un día mas que largo puedo sentarme un rato a la pc o en el pc (como se diga! :) ) 

faktorqm: 
[INDENT]Gracias por responder. 
Te comento el "channel mode" del que me hablas no lo tengo, pero supongo que te referís a activar los diferente canales "analog center/LFE, side, rear" y las opciones del Source.[/INDENT]
Eso ya lo tengo activado y funcionando, pero cuando le saque el .asoundrc, dejaron de tener efecto salvo el Analog side.

pol666:
[INDENT]Hola, Gracias por la respuesta
Si, estoy usando 8.04 y modifique el .asoundrc por que fue la opción mas sencilla y efectiva (hasta que encontré este problema) para usar mi 5.1 y en Alsa. [/INDENT]
En pulseaudio se me entrecorta la musica (como si fueran lag's), pero mientras funcione bien con el 5.1, puedo usar ALSA o Pulseaudio ya que no se las diferencias entre uno y otro.
Pasame el esd.conf  o el tip del pulseaudio, que lo pruebo y vamos viendo entre todos como sigue la cosa.

Muchas Gracias!!
Saludos!

---

### Post by faktorqm on 2008-08-13
proba de poner en una consola "alsamixer" sin comillas...
ahi te abre el configurador de alsa con todas las opciones. salu2!!

---

### Post by victor_nesta on 2008-08-13
Probé y me salio el Alsamixer, con los mismos parámetros que en modo gráfico.
dejo una captura por si las dudas.
[IMG]http://img354.imageshack.us/img354/3820/pantallazokm4.png[/IMG]

---

### Post by pol666 on 2008-08-13
Alsa es el driver de sonido y pulseaudio es un cliente que se encarga de gestionar los sonidos del sistema, antes se usaba ESD pero con pulseaudio que es mejor el ESD dejalo de lado 

Yo no tocaria el ASound.con o asounrc por que es algo muy delicado.

Tenes un SB como yo, mira te digo como hago yo para no tener problemas con el sonido.


*Desactive la intel on board de la Bios sin dramas, ubuntu ya no la toma
*Seleccione Pulseaudio en las propiedades de sonido, Active todos los canales en el mixer de gnome y obviamente los subi
* Hago **sudo gedit /etc/pulse/daemon.conf** con eso entro en las configuraciones de pulseaudio y edito donde dice **;default-sample-channels = 2** lo cambio por 
**default-sample-channels = 6** NO ME EQUIVOQUE SACANDOLE EL PUNTO Y COMA. SACASELO.

yo pensaba que se habia equivocado el que escribio eso en su blog jeje, despues probe que tenia que sacar el ; y poner 6 en ves de 2.

Bueno listo, ahi reinicio la PC y capas que tampoco tenes 5.1 pasa que a veces se bajan los mixer, volvelos a cambiar y listo.

---

### Post by victor_nesta on 2008-08-13
Bueno funciono el pulseaudio, cuando reinicie tenia 6 controladores en ves de uno en Pulse.

Pero sigo sin poder reproducir 2 secuencias a la misma ves, abro MP3 bien abro Youtube al mismo tiempo y este ultimo no se escucha.
Cierro todo.
Abro youtube todo bien, abro al mismo tiempo mp3 y este ultimo no se escucha.

Pero hay diferencias, ahora al abrí youtube y despues mp3 el reproductor me permite subir y bajar el volumen (Aunque no tenga efecto alguno) que antes no me dejaba.
Y se entrecorta el supuesto audio (ya que no lo escucho). 
Aclaro, Si esta el reproductor solito funciona bien.

Seguimos probando
Mucha Gracias!

Edito: Subi un video en Youtube para que vean lo que pasa. No grabo el sonido pero se entiende!!

[http://www.youtube.com/watch?v=op0IJkMl96M](http://www.youtube.com/watch?v=op0IJkMl96M)

---

### Post by pol666 on 2008-08-13
Si hiciste lo que puse yo. Saca cualquier cosa que hallas puesto en esd.conf, asound.con, asounrc o cualquier cosa que hallas tocado antes. Pero antes hace un bakcup de esos archivos

---

### Post by victor_nesta on 2008-08-13
pol666: Gracias per tutti.
lo único que le agregue fue el .asoundrc, que apenas me dijiste que lo saque, lo hice.
ahora volví a dejar el daemon.conf en 2. pero manteniendo las preferencias de sonido en pulseaudio.
Igualmente sigue sucediendo lo mismo, suena una cosa y otra no.
La única manera de reproducir varias cosas a la ves es dejando todo en alsa, pero en 2 parlantes obviamente.

Un misterio, hasta el momento.

Saludos

---

### Post by pol666 on 2008-08-13
Te dijaste en preferencias<Sonido?


Fijate ahi esta el problema me parece fiajte que todos esten marcados para funcionar con pulceaudio.

---

### Post by victor_nesta on 2008-08-13
Creo que si, desde que me dijiste que use pulseaudio lo tengo así.
[IMG]http://xs330.xs.to/xs330/08333/pantallazo449.png[/IMG]

---

### Post by victor_nesta on 2008-08-13
Creo que si, desde que me dijiste que use pulseaudio lo tengo así.
[IMG]http://xs330.xs.to/xs330/08333/pantallazo449.png[/IMG]

Actualizo, después de realizar un par de pruebas mas, obtuve un resultado Diferente.
volvi a modificar el daemon.conf y para los 6 canales, reinicie y abri el totem por un lado y el Rhythmbox por el otro, y funcionaban las dos pistas en simultaneo sin problema.
ahora cuando el Flash *youtube* toma el control, salta el bug y solo escucho el youtube.

en Firefox desactive el Ubuntu Firefox Mod
y los plugins Default y Totem Web Browser por si generaban el conflicto, pero no, por ahí no es la cosa. El plugin de flash lo baje desde la pagina oficial de adobe. 

Sigo en la busqueda...

---

### Post by Hei Ku on 2008-08-13
Busca por firefox y flash, que hay un seteo para los sonidos de flash. Quizas eso te ayude.

---

### Post by pol666 on 2008-08-13
Listo, ahora solo falta libflashsuport (o algo asi) buscalo en synaptic , Le da soporte pulseaudio a flash.

Me imagino que tenes el flash 9, el 10 necesita otra libreria pero por lo que probe anda igual. proba con lo que te dije

---

### Post by victor_nesta on 2008-08-13
pol666: Lo tuyo es monumental!!! 
Esta funcionando!!!! un paquetito lo arreglo todo. 
:guitar::guitar::guitar:
**1.000 Gracias**

Gracias a todos!! (tenemos Ubuntu para rato!!, jeje.)

ya abro un topic con otras preguntas :lolflag:

Gracias por la tremenda paciencia!

---

### Post by pol666 on 2008-08-13
Ni problema!  lo que tuve que lidear con el sonido fue terrible, ahora esta facil todo.. AH una cosa vos si llegaste a lo del Esd, asound y eso fue por google, un consejo es que siempre busques con Ubuntu hardy. por que a veces las cosas antes eran distintas y terminas leyendo manuales viejos o en deshuso, bueno, Sacale provecho al sonido y marca el topic como solved

---

