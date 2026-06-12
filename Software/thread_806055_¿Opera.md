---
title: "¿Opera?"
date: 2008-05-24
forum: Software
---

### Post by _kAz_ on 2008-05-24
Como andan???

Me instalé el Opera en vistas de reemplazar a Firefox. He leído que es más seguro y más rápido que el zorrito. Este aspecto se convierte en especial teniendo en cuenta que cada dos por tres se me cuelga Ubuntu, generalmente cuando tengo el Firefox andando.

Ahora bien, he encontrado algunos inconvenientes con Opera:

1. No me reproduce videos y algunos contenidos flash. Supongo que debo bajar la versión correspondiente, pero no se bien cuál. Hace un tiempo cuando usaba Kubuntu también probé el Opera e le instalé algo por este motivo pero no lo pude hacer funcionar; tampoco le preste mucha atención.

2. El segundo problema es mas bien un detalle. Me gusta tener todo a mano así que los favoritos los voy disponiendo en una barra siendo identificados sólo por los iconos de la página, los FAVICON como se suelen llamar. El problema es que a varias páginas no le reconoce ese icono, ¿hay algo que pueda hacer yo o eso depende pura y exclusivamente de la página que no puso un icono para opera (o algo similar)?

Salu3.

---

### Post by faktorqm on 2008-05-24
Hola, yo uso Opera.

1) Para lograr esto, tenes que ir hasta la pagina de adobe, bajar el flash para linux, descomprimir el tar.gz que te bajas, y copiar el archivo "libflashplayer.so" a la carpeta "/usr/lib/opera/plugins". 

Luego, asegurate de tener java instalado, o sino instalate el java de sun (yo hice eso con "sudo apt-get install sun-java-6) y en el opera, vas a "herramientas" -> "opciones" -> "avanzado" (pestaña) -> "Contenido" en el menu de la izquierda, apretas donde dice "Opciones de java" y en el cuadrito que te aparece le pones "/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386" y apretas el boton que te dice "verificar ruta de java". Ahi le das todo ok y deberias salir viendo videos en youtube.

2) No se a que te referis con eso, pero tenes los 9 "marcadores" rapidos con fotito de las paginas. 

Espero que te haya servido. Salu2!!

---

### Post by _kAz_ on 2008-05-24
> **faktorqm said:**
> 

1) Luego, asegurate de tener java instalado, o sino instalate el java de sun (yo hice eso con "sudo apt-get install sun-java-6)

De esa forma me dice que no se pudo encontrar el paquete. Copié el libflashplayer.so pero no pasó nada.

> 2) No se a que te referis con eso, pero tenes los 9 "marcadores" rapidos con fotito de las paginas. 

Están muy buenos los speed dial, pero son muy pocos... Te adjunto una imágen; el inconveniente es que esos iconos que no aparecen en Opera si lo hacen en Firefox o Konqueror cuando lo usaba.

Ah y otra duda: ¿cómo lo paso a castellano?

---

### Post by Thalskarth on 2008-05-24
> **_kAz_ said:**
> De esa forma me dice que no se pudo encontrar el paquete. Copié el libflashplayer.so pero no pasó nada.


Lo más facil es que bajes la version 9.5b2 desde la págiona de _Opera, ese lo reconoce sin dramas...


si no, para traducir la version, vas a la pagina de opera, basjas el archivo del lenguasje deseado -8esp) y lo copias a la carpeta-: /usr/share/opera/locale/

---

### Post by osensei on 2008-05-25
Qué bueno ver que hay más gente que usa Opera! :) Soy usuario de Opera desde el 98!!!

En fin... fanatismo dejado de lado, te cuento... tengo entendido que la última versión del flash player no corre en opera 9.2x, pero sí en el 9.5b2, el cual recomiendo altamente que lo bajes.

Por otro lado, más allá de que en la versión 9.5b2 funciona la última versión de flash player, no funciona del todo bien. El flash player que mejor funciona es el 9.0.r48 (este sí funciona en las versiones 9.2x). Para conseguirlo necesitás bajarte un zip que contiene varias versiones viejas, el zip se encuentra en [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Trae un script de instalación, aunque particularmente yo copié directamente el archivo libflashplayer.so en /usr/lib/opera/plugins, si querés podés copiarlo en /usr/lib/flashplugin-nonfree y también te lo tomaría el firefox.

Si lo copiás en /usr/lib/opera/plugins entonces vas a tener que ir a Tools -> Preferences -> Advanced -> Downloads, ahí seleccionar "application/x-shockwave-flash", seleccionar "Edit" y luego asegurarte de que donde diga "Use plug-in" figure el que vos copiaste en /usr/lib/opera/plugins.

Saludos!

Opera rules!

---

### Post by faktorqm on 2008-05-25
Pense que ya lo habias pasado al castellano... 

en este pagina te bajas el archivo, [http://www.opera.com/download/languagefiles/](http://www.opera.com/download/languagefiles/) luego lo copias en /usr/share/opera/locale/ y luego vas a herramientas (tools) -> opciones (option) y en el ultimo boton que te aparece detalles (detail) y arriba en el cuadrito9 que te dice, le pones esto: "/usr/share/opera/locale/ouw927_es-LA.lng" sin comillas.
le das aceptar y automaticamente te lo pasa a español. Ojo, yo tengo la 9.27, vos tenes que poner tu version.

Con el tema del flash, lo copias y listo, no tenes que hacer nada mas. Lo del java es otra cosa independiente, pero para ver videos en youtube necesitas los dos, Y SI NO ENCONTRAS EL PAQUETE BUSCALO CON SYNAPTIC.... ¬¬

Espero que te haya servido. Salu2!!

---

### Post by _kAz_ on 2008-05-25
> **faktorqm said:**
> Pense que ya lo habias pasado al castellano... 

en este pagina te bajas el archivo, [http://www.opera.com/download/languagefiles/](http://www.opera.com/download/languagefiles/) luego lo copias en /usr/share/opera/locale/ y luego vas a herramientas (tools) -> opciones (option) y en el ultimo boton que te aparece detalles (detail) y arriba en el cuadrito9 que te dice, le pones esto: "/usr/share/opera/locale/ouw927_es-LA.lng" sin comillas.
le das aceptar y automaticamente te lo pasa a español. Ojo, yo tengo la 9.27, vos tenes que poner tu version.

Con el tema del flash, lo copias y listo, no tenes que hacer nada mas. Lo del java es otra cosa independiente, pero para ver videos en youtube necesitas los dos, Y SI NO ENCONTRAS EL PAQUETE BUSCALO CON SYNAPTIC.... ¬¬


Yo también tengo la versión 9.27, instale el sun-java-6 desde synaptic como me dijiste y además copie el flash, pero no pasa naranja con youtube; a vos te anda???

Mientras otra pregunta: como hago para que la tipografía de las páginas no se la predeterminada por el sitio sino la que yo quiera???

---

### Post by faktorqm on 2008-05-25
Me anda pero se me cuelga con videos largos, por ejemplo si quiero ver uno de 15 minutos, tengo que andar rezando que no se me cuelgue.... por que agarra y me muestra una pantalla gris de la que no puedo salir, y se cuelga el opera. :S

Herramientas -> opciones -> ficha "paginas web" o sino en herramientas -> opciones -> ficha "avanzado" -> a la izquierda "fuentes". Salu2!

---

### Post by _kAz_ on 2008-05-25
> **faktorqm said:**
> Me anda pero se me cuelga con videos largos, por ejemplo si quiero ver uno de 15 minutos, tengo que andar rezando que no se me cuelgue.... por que agarra y me muestra una pantalla gris de la que no puedo salir, y se cuelga el opera. :S

Herramientas -> opciones -> ficha "paginas web" o sino en herramientas -> opciones -> ficha "avanzado" -> a la izquierda "fuentes". Salu2!

Lo de las fuentes ya lo hice pero la mayoría de las páginas no responde. De hecho dice "para páginas sin ningún estilo aplicado" y yo quiero que sea para TODAS, o sea obviar el estilo tipográfico que tenga cualquier página y que muestre las letras que yo le digo.

Por lo otro... FLASH ni para atrás, en cualquier página que tenga contenido flash no funca. Será por eso que me dijo **osensei** que flash funciona bien bien sólo en versiones anteriores???

---

### Post by Thalskarth on 2008-05-25
> **_kAz_ said:**
> Por lo otro... FLASH ni para atrás, en cualquier página que tenga contenido flash no funca. Será por eso que me dijo **osensei** que flash funciona bien bien sólo en versiones anteriores???

Biem bien, solo funcionan las versiones anteriopres de flash.

La ukltima version de flash, a mi solo me funciona bien con el opera 9.5b2

---

### Post by _kAz_ on 2008-05-25
Uhhhh que macana!!!

Taría bueno que anduviese bien, el Firefox me sigue jodiendo con los cuelgues pero si no hay opción mejor me tendré que quedar con ese :(

Ya me sucedió con el Konqueror en KDE, tenía todo ese tipo de quilombos y al final por más que uno quiera te terminas quedando con lo que sí funciona completo por más que te ralentize la maquina.

---

### Post by faktorqm on 2008-05-25
Repito lo de Thalskarth: Si y solo si queres la ultima version de flash, opera 9.5 beta 2, si no te calienta, opera 9.27 estable y el flash anterior que ni idea cual es.
Para mi Opera supera a Firefox en varias cosas, y Firefox supera a Opera en otras tantas, yo tengo los dos, por compatibilidad de paginas, nada mas, de todas maneras el firefox no se me cuelga. Salu2!

---

### Post by _kAz_ on 2008-05-31
**[SIZE="4"]ESTOY HARTOOOOO!!!!!!![/SIZE]**

En los últimos 10 minutos Ubuntu se me colgó 3 veces:mad::mad::mad::mad:

Y él UNICO programa que tenía funcionando era el *** FIREFOX. Basta!!!

Alguien por favor que me diga donde puedo conseguir la versión anterior del flash así me funciona en el Opera, o cualquier flash que funcione en el Opera 9.27, o algo por Dios!!! No puedo darme más el lujo de seguir perdiendo información importante culpa del Firefox.

---

### Post by osensei on 2008-05-31
Fijate en este mismo thread en mi post anterior!

Saludos!

---

### Post by _kAz_ on 2008-06-01
> **osensei said:**
> Fijate en este mismo thread en mi post anterior!

Saludos!

Que gilll!!!! Se me re pasó por alto... Creo que interprete que me decías que bajara una versión anterior pero de Opera.

Ya anda!!!

Muchas Gracias a todos!!!

PD: el único "inconveniente" que no pude solucionar es que me siguen apareciendo las paginas con la tipografía predeterminada del sitio y no con la que yo quiero.

PD2: CHAU FIREFOX!!! Avisen cuando lancen una versión que no me cuelgue la máquina y lo pruebo de nuevo, jeje...

---

### Post by lega on 2008-06-03
Hola hoy bajé el Opera 9.27 todavía no configuré el flash ni lo pasé a castellano,porque tuve que irme al laburo, algo que me llamó la atención,(he usado Opera en xp hace muchisimo)es por ejemplo uno tipea la dirección en la barra de direcciones le da enter y no hay ningun indicio que el navegador esta llendo hacia ahí o esta parado o que...se entiende? no hay una ruedita que gira? como en Firefox? que indique que esta cargando la pagina? o como la e del Explorer?:shock: por ahí está y yo no la he visto...

---

### Post by Mister X on 2008-06-03
Hay una mini-barra de progreso al final de la barra de direcciones, desaparece cuando la pagina terminó de cargar

---

### Post by _kAz_ on 2008-06-03
Aca estoy luego de unos días de ser usuario Opera... Por ahora todo bien, algun par de contratiempos pero nada grave.

Lo de la tipografía default ya lo encontre, pero no tendría solución aparente. Las modificaciones se pueden hacer desde los estilos (autor y usuario), puedo efectivamente deshabilitar la hoja de estilo del sitio, con ello se activa la tipografía que yo quiero, pero en detrimento de la disposición de los elementos del sitio. Por ejemplo en este foro, si deshabilito esa opción se me desacomoda todo el menú del mismo, es decir que User CP, Forum Help, etc, salen uno abajo del otro y sin formato. En consecuencia, queda la tipografía default porque sino "se rompe" el sitio.

Otra cosa más particular que encontre es que no puedo entrar a GMail, se queda en blanco en la página http : // mail.google.com/mail/ ?ui=1 &disablechatbrowsercheck=1.

---

### Post by Thalskarth on 2008-06-03
> **_kAz_ said:**
> Otra cosa más particular que encontre es que no puedo entrar a GMail, se queda en blanco en la página http : // mail.google.com/mail/ ?ui=1 &disablechatbrowsercheck=1.

no se en la 9.27. 

Con las version de la 9.5 ya solucionaron eso. Aunque, solo funca la version 'vieja' de Gmail... la nueva todavia no.

---

### Post by _kAz_ on 2008-06-03
Y bueno... no es de mayor importancia tampoco ya que uso el acceso IMAP del Thunderbird. De todas formas necesitaba comprobar algo desde el sitio así que tuve que utilizar firefox.

Debo decir que me sienta bien Opera eh... salvando lo de la tipografía, me siento muy cómodo :)

---

### Post by lega on 2008-06-04
> **osensei said:**
> 
 El flash player que mejor funciona es el 9.0.r48 (este sí funciona en las versiones 9.2x). Para conseguirlo necesitás bajarte un zip que contiene varias versiones viejas, el zip se encuentra en [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Trae un script de instalación, aunque particularmente yo copié directamente el archivo libflashplayer.so en /usr/lib/opera/plugins, !

Alguien que haya bajado el zip del que habla osensei sería tan amable de subir el archivo libflashplayer.so de la versión que el habla? estoy tratando de bajarlo del link que puso pero no hay caso no puedo..:(

Edit: ya lo bajé gracias :)

---

