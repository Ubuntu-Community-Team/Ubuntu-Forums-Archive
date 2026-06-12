---
title: "Un programa se maximiza y tapa todo"
date: 2009-05-15
forum: Software
---

### Post by drazhe on 2009-05-15
La cosa es mas o menos asi, instale el programa Krusader en mi ubuntu 8.10, pero cuando lo abro este se maximiza hasta tapar las 2 borras del SO la que tienes las aplicaciones, lugares y sistema y la de debajo, donde aparecerian los programas abiertos. otra cosa que me sucede con este programa es que la barra donde estaria el titulo (Donde diria krusader en el medio) tambien desaparece y solo veo las ordenes de Archivo, editar, ir, vista, etc.... 
Alguien me puede decir que hice mal y como solucionar este problema? repito que solo sucede con el Krusader, con el opera, openoffice, juegos, firefox y sea el programa que sea no pasa...

Aca adjunto una imagen para mostrar el problema, notece que las barras superiores e inferiores no estan.... 

[http://www.subirimagenes.com/fotos-pantallazo-2542713.html](http://www.subirimagenes.com/fotos-pantallazo-2542713.html)

---

### Post by Hei Ku on 2009-05-15
Me parece que es porque el programa es para KDE4, pero no tenes instaladas las decoraciones de ventanas para kde, y gnome no es tan buen amigo de "prestarselas". Podrias probar instalando kdelibs5, que son los paquetes basicos de KDE.

Otra cosa, tenes habilitado Compiz o los efectos de escritorio?

PD: Movido al subforo de Software, donde corresponde. (al Krusader solo se lo puede insultar)

---

### Post by emiliano_raso on 2009-05-15
Lo mismo me habia pasado en 8.10 con Kolourpaint. Pensé que era problema de Intrepid Ibex con qt pero despues me pasó con Firefox tambien :-S

Formateé y dejó de pasar (NOTA: No formateé por eso xD)
Lo que pasa es que las aplicaciones se autoejecutan en fullscreen. Porque? No se. Lo que hice fue cada vez qeu usaba Kolourpaint apretar "ctrl+shift+F" y sacaba la pantalla completa.
Lo mismo con firefox.

Fijate, solo pasa con aplicaciones que permiten poner fullscreen.

---

### Post by drazhe on 2009-05-15
al 1ero que me respondio (Disculpe, no recuerdo su nomnbre), instale el krusader porque soy u fanatico fundamentalista del total commander y por desgracia no hay un TC para ubuntu, sino usaria el TC, buscando por ahi, encontre el krusader, que es lo mas parecido, aunque le falta al TC, cuando lo instale andaba barbaro, no tenia este problema que digo que tengo ahora. Creo que el problema comenzo a pasar despues de instalar el compiz, me pasaba lo mismo con el Opera, pero dejo de pasar, y ahora solo pasa con el krusader.... 

al 2do que me respondio (Disculpe, no recuerdo su nombre) probe lo de cnrtl+shift+F, pero no pasa nada...

---

### Post by emiliano_raso on 2009-05-15
> **drazhe said:**
> al 2do que me respondio (Disculpe, no recuerdo su nombre) probe lo de cnrtl+shift+F, pero no pasa nada...

No no, me referia a que ctrl+shift+f es lo que saca el fullscreen de Kolourpaint, y el F11 de Firefox.
Fijate si la aplicacion con la que tenes problemas tiene la opcion de fullscreen, y seguramente va a tener un acceso de teclado y asi lo sacas.

---

### Post by PatoDB on 2009-05-16
A mi me pasaba eso con el Firefox...

La solucion fue:

Dos veces al F11 seguidas, para sacarle la pantalla completa (o una vez, depende el caso)

Una vez que tenia la barra de titulo a la vista, click derecho (en la barra de titulo) y elegir **Desmaximizar**.

A mi me funciono con el Firefox, fijate si en las otras aplicaciones podes buscar una opción igual. O trata de buscar algo con **Desmaximizar** quizás por ahi venga la cosa...

Espero que sirva de algo.. ^^

---

### Post by Hernán-Amaya on 2009-05-16
Si te gusta el TC acá esta le MC [1] pero es para consola como el viejo Norton Commander si mal no recuerdo esta en los repositorios.

[1] [http://es.wikipedia.org/wiki/Midnight_Commander](http://es.wikipedia.org/wiki/Midnight_Commander)

---

### Post by hictio on 2009-05-16
> **PatoDB said:**
> A mi me pasaba eso con el Firefox...

La solucion fue:

Dos veces al F11 seguidas, para sacarle la pantalla completa (o una vez, depende el caso)

Una vez que tenia la barra de titulo a la vista, click derecho (en la barra de titulo) y elegir **Desmaximizar**.

A mi me funciono con el Firefox, fijate si en las otras aplicaciones podes buscar una opción igual. O trata de buscar algo con **Desmaximizar** quizás por ahi venga la cosa...

Espero que sirva de algo.. ^^

A mi también me pasaba muy seguido en Firefox en Intrepid, con Jaunty, hasta el momento no me ocurrió.

---

### Post by drazhe on 2009-05-16
> **Hernán-Amaya said:**
> Si te gusta el TC acá esta le MC [1] pero es para consola como el viejo Norton Commander si mal no recuerdo esta en los repositorios.

[1] [http://es.wikipedia.org/wiki/Midnight_Commander](http://es.wikipedia.org/wiki/Midnight_Commander)


ya lo probe, el mas parecido es el krusader, o por lo menos es el que tiene muchas opciones y caracteristicas del TC... y por cierto, mi mayor reticencia a pasarme de lleno a linux es que no haya un TC para linux... odio de un modo inimaginable al nautilis y al explorador de window$ y todos esos programas... uso TC desde el 1994 cuando salio la version 1 y aun lo sigo usando... y antes usaba el norton commander... jamas use un winrar o winzip o algo de eso, porque el TC lo hace solito y sin problema y tener que involucionar con el nautilis me pone loco.... 

pero el que no se vea la barra del titulo es un detalle menor, mientras que el programa funcione por mi esta bien, era solo para saber que podia estar pasando y seguramente es como dicen, el krusader es para KDE y GNOME no le presta las librerias.... creo que este problema comenzo a pasar despues de activar los efectos visuales del compiz... pero no estoy seguro ahora... 

Gracias de todos modos....

---

### Post by Hei Ku on 2009-05-16
KDE y Compiz no se llevan bien. Podes probar desactivando Compiz a ver que pasa.

El Dolphin tambien tiene un modo de vista dividida, aunque no se cuales son las funciones especificas que estas buscando.

---

### Post by drazhe on 2009-05-16
> **Hei Ku said:**
> KDE y Compiz no se llevan bien. Podes probar desactivando Compiz a ver que pasa.

El Dolphin tambien tiene un modo de vista dividida, aunque no se cuales son las funciones especificas que estas buscando.

uuuy es dificil, porque yo con el TC no solo me muevo en mis HDs, sino que tambien, comprimo, descomprimo en todas las extenciones, pruebo paginas web, comparo directorios, paquetes y archivos, divido y compilo, renombro masivamente, lo uso como cliente FTP, visor de archivos, dwg, jpg, gif, swf, doc, docs, xls, xlsx, etc, edicion del registro en window$ entre otras funciones y la idea es que pueda hacer todo eso en linux, sino lo puedo hacer, este solo programa ya justifica seguir con windows... jejejeje es terrible lo que digo, pero bueno, es lo cierto, aun no consigo hacer lo que hago en windows con linux.... de hecho el TC es el programa que mas utilizo, si pueda instalar el SO desde el TC lo haria, por desgracia tengo que instalar primero el SO... jejeje

---

### Post by Hei Ku on 2009-05-16
Entonces pasate a KDE y usa Dolphin o Konqueror. Lo unico que no tienen es edicion del registro de windows. :lolflag:

Por otro lado, te vas a tener que acostumbrar que las cosas en linux se hacen diferentes. Todas las funciones que queres hacer se pueden hacer, pero algunas vas a tener que configurarlas a tu gusto, quizas no vengan de entrada. Si no estas dispuesto a aprender y a cambiar algunos habitos, la experiencia va a ser  torturante y no algo que disfrutes hacer, como deberia ser. 

Te lo digo porque no sos el primero que viene y dice: "si esto no es asi, me vuelvo". Hace falta flexibilidad para cambiar los habitos arraigados. Pero si vas a sufrir, no vale la pena.

---

### Post by drazhe on 2009-05-16
> **Hei Ku said:**
> Entonces pasate a KDE y usa Dolphin o Konqueror. Lo unico que no tienen es edicion del registro de windows. :lolflag:

Por otro lado, te vas a tener que acostumbrar que las cosas en linux se hacen diferentes. Todas las funciones que queres hacer se pueden hacer, pero algunas vas a tener que configurarlas a tu gusto, quizas no vengan de entrada. Si no estas dispuesto a aprender y a cambiar algunos habitos, la experiencia va a ser  torturante y no algo que disfrutes hacer, como deberia ser. 

Te lo digo porque no sos el primero que viene y dice: "si esto no es asi, me vuelvo". Hace falta flexibilidad para cambiar los habitos arraigados. Pero si vas a sufrir, no vale la pena.

ya lo se, un gran inconveniente es por ejemplo cuando le doy al alt+f1 o alt+f2 que en el TC me abre las etiquetas de unidades y aca con esa convinacion de teclas me abre el menu aplicaciones del SO... pero dentro de todo la voy piloteando bien... el konkeror que dices no lo consegui instalar, pero seguro fue un error mio... en cuanto tenga algo de tiempo voy a ver que onda...

---

### Post by Hei Ku on 2009-05-16
Si usas gnome, sobre todo en la ultima version parece que se lleva mal con la ultima version de KDE, asi que no sé cuánto te conviene mezclar.
KDE soporta un poco mejor las aplicaciones gnome, pero ya que estás aprendiendo gnome te va a resultar mas facil al principio. En cuanto a los shortcuts, eso es configurable.

---

### Post by biale on 2009-05-16
Bajo Intrepid + Kdebase yo ese problema solo lo tengo con Konqueror. Me aburri de hacer ctrl+shift+F y directamente lo ajuste para que arranque en una ventana del tamaño adecuado.

Lo que no probe todavía es activar KWin desde el icono de compiz fusion.

Salu2!

---

