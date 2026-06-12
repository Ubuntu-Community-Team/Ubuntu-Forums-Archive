---
title: "Desde Intrepid Ibex"
date: 2008-08-06
forum: Software
---

### Post by Mauro22 on 2008-08-06
Hola!! :)


Les quiero comentar los avances que tiene esta version, actualmente en alpha 3.

En este momento estoy usando el liveCD y la verdad es que me impresiona.


Realmente estable, totalmente funcional (instalar paquetes y usar varios dispositivos y aplicaciones a la vez sin que caiga el rendimiento)


Hasta ahora:
* Levanto la capturadora enltv-fm de encore (saa7134)
* Levanto la placa wifi sin problemas (rt6100 o algo asi es el chip, marca edimax)
* Instale tvtime y emesene y todo al pelo hasta ahora
* Sonido. Algo raro. El hardware lo levanto (Nvidia HDA Sound) pero PulseAudio esta muerto. Solo levanta con ALSA o OSS lo cual trae aparejado una salida de audio a la vez. (Si, la pesadilla de atari130xe jeje esta de vuelta)
* Los drivers propietarios de la placa de video (nvidia onboard) aparecen 3 versiones (Ver Imagen)
* Sino me olvido nada mas :)


Les dejo la imagen (ahh, cambiaron el tema Human por uno grisesito)


Si alguien lo prueba que comente!!


:lolflag:

---

### Post by atari130xe on 2008-08-06
> **Mauro22 said:**
> Hola!! :)


Les quiero comentar los avances que tiene esta version, actualmente en alpha 3.

En este momento estoy usando el liveCD y la verdad es que me impresiona.


Realmente estable, totalmente funcional (instalar paquetes y usar varios dispositivos y aplicaciones a la vez sin que caiga el rendimiento)


Hasta ahora:
* Levanto la capturadora enltv-fm de encore (saa7134)
* Levanto la placa wifi sin problemas (rt6100 o algo asi es el chip, marca edimax)
* Instale tvtime y emesene y todo al pelo hasta ahora
* Sonido. Algo raro. El hardware lo levanto (Nvidia HDA Sound) pero PulseAudio esta muerto. Solo levanta con ALSA o OSS lo cual trae aparejado una salida de audio a la vez. (Si, la pesadilla de atari130xe jeje esta de vuelta)
* Los drivers propietarios de la placa de video (nvidia onboard) aparecen 3 versiones (Ver Imagen)
* Sino me olvido nada mas :)


Les dejo la imagen (ahh, cambiaron el tema Human por uno grisesito)


Si alguien lo prueba que comente!!


:lolflag:

¡¡¡Noooo!!! ¿¿¿otra vez sopa??? :( y yo que creìa que ya no iba a tener màs drama con el tema del audio, me pregunto: los desarrolladores, despuès de los tropecientos de posts con el problema del audio, no vèn la posibilidad de cambiar ese problema?, espero que para la version final eso, estè finiquitado. Sinò haremos lo mismo que en esta versiòn: eliminar PulseAudio y dejar el viejito de ALSA.

---

### Post by lega on 2008-08-06
preguntonta, como se hace para instalar cosas desde un livecd? la verdad es que nunca lo use mas que iniciar e instalar el SO no sabia que podias instalarle cosas, donde va a parar lo que instalas? según el calendario el jueves que viene sale la 4, probablemente la baje para probarla.

---

### Post by pol666 on 2008-08-07
hay marky marky de mal en peor vamos con los temas... muy feo el skin a mi gusto

---

### Post by lega on 2008-08-07
Una propuesta que me pareció interesante que esta en el artwork es wall-ligth, ta bien, es solo un Mockup, pero se ve más lindo que el marrón aburrido ese que tiene la alpha.

[Artwork Intrepid]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Wall-light")

[willwill100 galería en deviantArt]("http://willwill100.deviantart.com/gallery/")

---

### Post by luchardi on 2008-08-07
> **lega said:**
> Una propuesta que me pareció interesante que esta en el artwork es wall-ligth, ta bien, es solo un Mockup, pero se ve más lindo que el marrón aburrido ese que tiene la alpha.

[Artwork Intrepid]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Wall-light")

[willwill100 galería en deviantArt]("http://willwill100.deviantart.com/gallery/")

Impresionante ese Mockup ... estaría lindo que alguien lo haga realidad ... quedaría impresionante!!

---

### Post by valucha on 2008-08-07
[COLOR="DarkOrchid"]¿Qué significan esas 3 versiones del driver :S? SOlo difieren en números:S


PD: se me cae la baba por esto [http://willwill100.deviantart.com/art/Interpid-Ibex-Mockup-Part-3-93585184](http://willwill100.deviantart.com/art/Interpid-Ibex-Mockup-Part-3-93585184). [/COLOR]

---

### Post by vk-cdg on 2008-08-07
> **Mauro22 said:**
> 

* Los drivers propietarios de la placa de video (nvidia onboard) aparecen 3 versiones (Ver Imagen)


Yo iría por el mas nuevo!



> **lega said:**
> Una propuesta que me pareció interesante que esta en el artwork es wall-ligth, ta bien, es solo un Mockup, pero se ve más lindo que el marrón aburrido ese que tiene la alpha.


Lo vi hoy a la mañana y casi me hago encima. Está.... simplemente HERMOSO!

---

### Post by Mauro22 on 2008-08-07
> **lega said:**
> preguntonta, como se hace para instalar cosas desde un livecd? la verdad es que nunca lo use mas que iniciar e instalar el SO no sabia que podias instalarle cosas, donde va a parar lo que instalas? según el calendario el jueves que viene sale la 4, probablemente la baje para probarla.


Es la primera vez que instalo cosas con un livecd. Lo podes hacer mientras no reinicies.

Para poder bajar cosas (tvtime y emesene en mi ejemplo), tenes que editar el sources.list del apt, porque los repos vienen todos deshabilitados.
Una vez eso haces un update y listo. A instalar.

Todo se instala en la RAM asi que al salir se borra todo. Pero esta bueno para probar.

---

### Post by lega on 2008-08-07
Gracias Mauro voy a probar en la próxima alpha, a proposito del tema que hablabamos mas arriba el gdm ya se puede bajar, no es exactamente igual pero se acerca bastante [http://danrabbit.deviantart.com/art/Willwill-s-Intrepid-GDM-94051500](http://danrabbit.deviantart.com/art/Willwill-s-Intrepid-GDM-94051500)

---

### Post by luchardi on 2008-08-07
Lega, lo baje yo el GDM pero no tengo idea de como instalarlo, al desempaquetarlo veo solo archivos sueltos? me estará faltando algo más que el selector de Ventanas de Entrada?

---

### Post by valucha on 2008-08-07
> **luchardi said:**
> Lega, lo baje yo el GDM pero no tengo idea de como instalarlo, al desempaquetarlo veo solo archivos sueltos? me estará faltando algo más que el selector de Ventanas de Entrada?
[COLOR="DarkOrchid"]
FIjate arrastrando el archivo comprimido en el cuadro que aparece cuando vas a:
sistema->administracion->ventana de entrada.(posicionate en la 2da pestaña "local")
AHi te lo instala automáticamente.
[/COLOR]

---

### Post by luchardi on 2008-08-07
10 puntos, realmente siempre me olvido de hacer el drag and drop, ahora cuando cierre sesión veo como quedo!

Gracias!!

---

### Post by pol666 on 2008-08-07
quieren ver algo que sobrepasa sus expectativas?

[IMG]http://worldimages.nirudia.com/photos/normal/worldimages-20080506124723.jpg[/IMG]


HERMOSO!

---

### Post by leo_rockway on 2008-08-08
Demasiado Vistaish para mi gusto.

Igualmente, sea cual sea el default yo siempre lo cambio.

---

### Post by faktorqm on 2008-08-08
Siempre me pregunto lo mismo.. es como que tendrian que hacer un boton tipo "modo transparente/modo normal" por que por ejemplo, yo quiero que todas las ventanas sean transparentes... y basta con abrir oo.org u opera para que el lookeo se caiga al piso.... es posible lograr que TODAS las ventanas sean transparentes o estoy completamente loco? Salu2!

---

### Post by vk-cdg on 2008-08-08
> **pol666 said:**
> quieren ver algo que sobrepasa sus expectativas?

[IMG]http://worldimages.nirudia.com/photos/normal/worldimages-20080506124723.jpg[/IMG]


HERMOSO!

Todos mis aplausos para los paneles y sobre todo para el logo de Ubuntu. El resto no me termine de convencer demasiado. De todas formas es de los mejorcitos que vi.

---

### Post by madelaki on 2008-08-08
> **pol666 said:**
> quieren ver algo que sobrepasa sus expectativas?

[IMG]http://worldimages.nirudia.com/photos/normal/worldimages-20080506124723.jpg[/IMG]


HERMOSO!

Lo unico bueno son los iconos, pero esa es **mi** opinion...

En cuanto al thread, Mauro22, dejame decirte que me habria encantado tener la suerte que vos tuviste.

---

### Post by vk-cdg on 2008-08-08
Hoy cuando llego a casa pruebo el liveCD en la note para ver que tal reconoce todo.
Hardy va bien excepto por la wifi que anda con los drivers de madwifi. Compilar cada vez que actualiza el kernel me esta cansando un poco. Sobre todo ultimamente que baja 2 o tres veces el mismo kernel

---

### Post by pol666 on 2008-08-08
Igual es un mopck up eso no existe :(

---

### Post by jpmorelli on 2008-08-08
> **lega said:**
> Una propuesta que me pareció interesante que esta en el artwork es wall-ligth, ta bien, es solo un Mockup, pero se ve más lindo que el marrón aburrido ese que tiene la alpha.

[Artwork Intrepid]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Wall-light")

[willwill100 galería en deviantArt]("http://willwill100.deviantart.com/gallery/")

Terriblemente grosooooo !!! Me parece lo mejor que vi !!! Que sea asi Marquitos !!! jaja :lolflag:

---

### Post by lega on 2008-08-16
Ayer bajé e instalé la alpha 4, renegué un poco con los drivers de nvidia, de los 3 disponibles me funcionó el segundo, es todo lo que hice, instalé drivers, actualicé (la alpha salio anteayer, había 45 actualizaciones aprox.:confused: son actualizaciones desde que salio la primer alpha o solo de estos dos dias?) y me tuve que ir a trabajar, me llamó la atencion la velocidad de booteo, notable con respecto a hardy, le voy a tomar el tiempo a los dos para ver si solo es una ilusión, mañana si me acuerdo pongo alguna captura.

---

### Post by luchardi on 2008-08-16
Yo actualize desde update manager la semana pasada y funciona perfecto, en Gnome se nota que se estan agregando funcionalidades nuevas todos los dias!

Buenisimo! la verdad ni se nota que es Alpha todavia!

---

### Post by vk-cdg on 2008-08-18
> **lega said:**
> Ayer bajé e instalé la alpha 4, renegué un poco con los drivers de nvidia, de los 3 disponibles me funcionó el segundo, es todo lo que hice, instalé drivers, actualicé (la alpha salio anteayer, había 45 actualizaciones aprox.:confused: son actualizaciones desde que salio la primer alpha o solo de estos dos dias?) y me tuve que ir a trabajar, me llamó la atencion la velocidad de booteo, notable con respecto a hardy, le voy a tomar el tiempo a los dos para ver si solo es una ilusión, mañana si me acuerdo pongo alguna captura.


Lo probaste en la desktop o en la note?

---

### Post by lega on 2008-08-18
lo instalé en la desktop y probé fugazmente,muy fugazmente, acordate que la note es de mi señora :)  el livecd en la note, el wifi no lo levantó, pero no sé por ahí instalando levanta, que se yo, cuando salga la final veré si quiere que se la instale.

---

### Post by vk-cdg on 2008-08-18
Me sigue quedando la esperanza que la nueva versión la soporte nativamente, sin compilar nada cada vez que actualice el kernel.

---

### Post by majatu on 2008-08-19
Ojalá elijan alguno de los temas q andan dando vuelta por ahi, estan mucho mas q barbaros! jeje :)

---

### Post by Mauro22 on 2008-08-19
Ya es un hecho :D


8.10 Alpha 4 Instalado !!


Diferencias (Hasta ahora):

* **No se apaga ni reincia**. Hay que salir (cerrar sesion) y hacerlo desde el menu del GDM
* El splash de carga se ajusta a la resolucion final, es decir, no cambia entre la carga y el SO.
* Varios sonidos a la vez :D:D
* La pantalla no se TAN bien como en hardy. Ya probe todo local asi que debe ser tema de drivers o algo. Cerca del borde derecho, se bien, pero con un efecto medio Blur; muy bajo pero a la vez molesta.
* La escritura del teclado es mas fluida. En hardy se trababa a veces y luego aparecia todo junto.
* Reconocio la capturadora de TV y radio (ENLTV-FM) y la PCI WiFi (Ralink) + Todo lo onboard, audio, video, usb etc, todo chipset nVidia.
* La interfaz de gnome anda medio "colgada", como que reacciona lento en algunos casos (cuando se apura en los menues por ejemplo).


Esto es lo que me voy acordando....

Si me dejan inicio el ¿Como se ve tu SO? -Intrepid Edition- :D


Saludos!!
:lolflag:

---

### Post by pol666 on 2008-08-19
Nah Mauro, espera a que salga, se va la emocion sino.

---

### Post by atari130xe on 2008-08-19
> **Mauro22 said:**
> Ya es un hecho :D


8.10 Alpha 4 Instalado !!


Diferencias (Hasta ahora):

* **No se apaga ni reincia**. Hay que salir (cerrar sesion) y hacerlo desde el menu del GDM
* El splash de carga se ajusta a la resolucion final, es decir, no cambia entre la carga y el SO.

[COLOR="Red"]_* Varios sonidos a la vez :D:D_[/COLOR]
[B][COLOR="Blue"][SIZE="4"]¿Por favor como hacen? 
jejeje 3 pc`s diferentes y no logro tener los benditos sonidos simultaneos, ¿que hacen uds, para que eso funcione? :confused:
Chips de sonido diferentes, configuraciones idem y nada..., que se yo... es mi karma :lolflag:
[/SIZE][/COLOR][/B]

* La pantalla no se TAN bien como en hardy. Ya probe todo local asi que debe ser tema de drivers o algo. Cerca del borde derecho, se bien, pero con un efecto medio Blur; muy bajo pero a la vez molesta.
* La escritura del teclado es mas fluida. En hardy se trababa a veces y luego aparecia todo junto.
* Reconocio la capturadora de TV y radio (ENLTV-FM) y la PCI WiFi (Ralink) + Todo lo onboard, audio, video, usb etc, todo chipset nVidia.
* La interfaz de gnome anda medio "colgada", como que reacciona lento en algunos casos (cuando se apura en los menues por ejemplo).


Esto es lo que me voy acordando....

Si me dejan inicio el ¿Como se ve tu SO? -Intrepid Edition- :D


Saludos!!
:lolflag:

Me voy a hacer un harakiri con una semi corchea..... ya vengo ](*,)

---

### Post by pol666 on 2008-08-19
yo tengo varios sonidos desde Hardy. Igual ojo, yo tengo placa de sonido no se vos.

Perdon la re desvirtue..

---

### Post by lega on 2008-09-06
Instalada la alpha 5, me fue como el cu**, de los 3 drivers de nvidia que me ofrecía 96, 173 y 177 para instalar, ninguno funcionó, en la anterior alpha me funcionaba perfecto el driver 177, esta vez extrañamente los instalaba y no me pedía reiniciar, reiniciaba de todos modos y lo hacia en baja resolución, en fin...a esperar que en la alpha 6 se arregle.:(

---

### Post by santiagoward2000 on 2008-09-18
Acabo de instalar Xubuntu Intrepid alpha 5 y (aunque me tengo que comer como 7 hrs de actualizaciones) por ahora anda todo bien. Veo que por alguna razón viene con Midori y Firefox instalados, no sé por qué los 2... Pero bue, Midori es MUCHO más estable que en Hardy! :)
Veo que cambiaron muchos programas y agregaron otros. Por ejemplo, viene con Catfish :) y Audacious :confused: (nunca lo usé, pero no me convence la facha) instalados , y me cambiaron Ristretto por una cosa rara que no sé como se llama para ver imágenes :(
Por ahora anda bien lo poco que probé, pero hay algo que me llama la atención: en **Restricted Hardware Drivers** no me aparece mi placa ATI, pero puedo prender el compositor de Xfce sin haber instalado nada. Viene con los drivers abiertos de ATI?
Mañana me pongo a actualizar todo, veo como anda y les cuento.
Saludos!

---

### Post by lega on 2008-09-18
sino instalaste nada de drivers seguramente viene con los drivers abiertos, eso es genial! lastima que yo tengo nvidia :( , a mi despues de un par de actualizaciones pude hacer andar mi placa de video, de todos modos sino me equivoco creo que hoy 18 sale la alpha 6, así que volveré a hacer una instalación limpia a ver que onda :)

---

### Post by santiagoward2000 on 2008-09-18
> **lega said:**
> sino instalaste nada de drivers seguramente viene con los drivers abiertos, eso es genial! lastima que yo tengo nvidia :( , a mi despues de un par de actualizaciones pude hacer andar mi placa de video, de todos modos sino me equivoco creo que hoy 18 sale la alpha 6, así que volveré a hacer una instalación limpia a ver que onda :)

En serio sale hoy? O sea que estuve 5hrs bajando para nada? ](*,)
Tengo que revisar el schedule la próxima.
Con lo de la placa, no, no toqué nada. Abrí el **Hardware Drivers** y solo estaban los del modem. No probé si anda Compiz, pero el compositor de Xfce anda, con todas las sombras y transparencias!! :D

---

### Post by leo_rockway on 2008-09-18
> **santiagoward2000 said:**
> hay algo que me llama la atención: en **Restricted Hardware Drivers** no me aparece mi placa ATI, pero puedo prender el compositor de Xfce sin haber instalado nada. Viene con los drivers abiertos de ATI?

Si no me equivoco los drivers libres de ATI tenian composite mucho antes que los privativos. El problema con los drivers libres creo que es el direct rendering... no tenés aceleración 3D. Igualmente AMD liberó sus specs y están laburando para que los drivers libres sean cada vez mejores. Hay algunas placas que ya tienen aceleración 3D funcionando.

---

### Post by santiagoward2000 on 2008-09-18
> **leo_rockway said:**
> Si no me equivoco los drivers libres de ATI tenian composite mucho antes que los privativos. El problema con los drivers libres creo que es el direct rendering... no tenés aceleración 3D. Igualmente AMD liberó sus specs y están laburando para que los drivers libres sean cada vez mejores. Hay algunas placas que ya tienen aceleración 3D funcionando.

No es para pelearte Leo, pero yo en Hardy no podía prender el Compositor si no instalaba antes los restringidos (técnicamente sí podía si editaba el xorg, pero se veía todo en cualquier parte, por ejemplo, si cerraba una ventana, algunas partes quedaban como pegadas en el escritorio y cosas así medio raras).

---

### Post by leo_rockway on 2008-09-18
> **santiagoward2000 said:**
> No es para pelearte Leo, pero yo en Hardy no podía prender el Compositor si no instalaba antes los restringidos (técnicamente sí podía si editaba el xorg, pero se veía todo en cualquier parte, por ejemplo, si cerraba una ventana, algunas partes quedaban como pegadas en el escritorio y cosas así medio raras).

Ah, no... que eran (y hasta cierto punto todavía siguen siendo) un desastre no te lo niego. Pero con Feisty instalar Beryl con fglrx me costo muchísimo y con los drivers libres no tanto. De todas formas tanto con los libres como con fglrx la computadora se arrastraba. Ahora los drivers libres mejoraron muchísimo gracias a AMD que se puso las pilas.

Justo en el momento que liberaron las especificaciones, ATI sacó los drivers fglrx con aiglx.

---

### Post by Hei Ku on 2008-09-18
Dependiendo del modelo de ATI que tenias, los drivers libres andaban bien. Mientras mas nueva, peor andaban.
Despues AMD libero las especificaciones de AtomBIOS, y con eso mejoraron MUCHO la performance de las placas mas nuevas. Al punto que andan muy bien con los drivers libres.

Muchachos, acostumbrense que la velocidad de cambios en el soft libre es mucho mayor a la de ese otro mundo mas gris y triste donde estaban antes. :D

---

### Post by santiagoward2000 on 2008-09-18
> **Hei Ku said:**
> Dependiendo del modelo de ATI que tenias, los drivers libres andaban bien. Mientras mas nueva, peor andaban.
Despues AMD libero las especificaciones de AtomBIOS, y con eso mejoraron MUCHO la performance de las placas mas nuevas. Al punto que andan muy bien con los drivers libres.

Muchachos, acostumbrense que la velocidad de cambios en el soft libre es mucho mayor a la de ese otro mundo mas gris y triste donde estaban antes. :D

Esta placa no es tan nueva, una Xpress 200m, tiene como 3 años. Igual en Hardy los drivers libres no me andaban ni ahí. Ahora en Intrepid es una locura. PUEDO VER LOS SCREENSAVERS EN 3D!! :lolflag:
Ya voy a ver si Compiz anda razonablemente bien, pero sino igual estoy contento :)

---

### Post by pol666 on 2008-09-18
me parece a mi o se estan atrasando un poquito?


van por el aplpha 6 y falta solo 1 mes, tendria que estar ya la primer Beta. por mas que figure en el calendario así....

---

### Post by Hernán-Amaya on 2008-09-18
por lo que vi en el schedule[1] no hay ninguna beta programada

[1]https://wiki.ubuntu.com/IntrepidReleaseSchedule

---

### Post by lega on 2008-09-18
para el 2 de octubre esta programada la beta, en cuanto al alpha 6 parece que no va a salir hoy

---

### Post by santiagoward2000 on 2008-09-18
> **lega said:**
> para el 2 de octubre esta programada la beta, en cuanto al alpha 6 parece que no va a salir hoy

Bueno, mientras espero que salga, me puse a probar Xfce 4.6 beta. No hay grandes cambios, pero cambiaron algunos programitas, como el appfinder o el Settings Manager y mejoraron un poco el menú. Voy a seguir probándolo un rato. Si a alguien le interesa probarlo, dejo aca los repositorios:
**deb [http://ppa.launchpad.net/xubuntu-dev/ubuntu](http://ppa.launchpad.net/xubuntu-dev/ubuntu) intrepid main**
que saqué del Newsletter:
[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue106]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue106")
Supuestamente es inestable, y dicen que está para que lo prueben los desarrolladores, pero soy curioso!
Saludos

---

### Post by atari130xe on 2008-09-18
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-September/000487.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-September/000487.html") salio la alpha 6 :)

---

### Post by lega on 2008-09-19
Instalada la alpha 6 versión Ubuntu, no alcanzé a ver como quedó porque terminó, reinicié, y me tuve que venir a laburar, lo que si vi es que el particionador de discos tiene una lavadita de cara que me gusto :)

---

### Post by leo_rockway on 2008-09-20
> **Hei Ku said:**
> Muchachos, acostumbrense que la velocidad de cambios en el soft libre es mucho mayor a la de ese otro mundo mas gris y triste donde estaban antes. :D

Cuando migré definitivamente a GNU (con Feisty) mi placa de video ATI no funcionaba con el driver libre, sólo podía usar vesa... o los privativos, claro, pero en ese momento apestaban incluso más que un vesa pelado.
Ayer volví a probar los drivers libres (radeonhd, que salieron desde que AMD liberó las especificaciones) y salen como piña. No tengo direct rendering pero la verdad que no lo uso y de todas formas hay placas que ya tienen direct rendering funcionando, así que es cuestión de tiempo.
Pensé que no iba a funcionar nada 3D pero Blender y Marble funcionan perfectamente. Así que acá estoy, muy cómodo usando drivers de video libres.

Ahora sólo me quedan privativos el BIOS y el firmware de la placa WiFi broadcom, absolutamente todo lo demás es libre.

---

### Post by vk-cdg on 2008-09-22
> **lega said:**
> Instalada la alpha 6 versión Ubuntu, no alcanzé a ver como quedó porque terminó, reinicié, y me tuve que venir a laburar, lo que si vi es que el particionador de discos tiene una lavadita de cara que me gusto :)

Bueno, bien ahí, por fin graficos un poco mas atractivos. 
Creo que la calidad de las interfases gráficas es algo que todavía se puede mejorar mucho. Es impresionante las opciones de personalización que tiene, pero la imagen como que se ve distinta en los windowze que en Ubuntu. 
Vamos por buen camino, me gusta.

---

