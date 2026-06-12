---
title: "Soporte RGBA en aplicaciones, desde Murrine"
date: 2008-11-17
forum: Software
---

### Post by User21 on 2008-11-17
Estaba viendo desde el blog de [Andrea Cimitan]("http://www.cimitan.com/blog/"), acerca de la posibilidad de añadir soporte de transparencias en las aplicaciones de Gnome, con el motor Murrine (RGBA). Para quien no está al tanto, aqui un [screenshot]("http://www.cimitan.com/blog/wp-content/rgba-murrine-170208.png").
Alguien lo ha probado? Es factible que con tan solo parchear o modificar CADA APLICACIÓN (como explican [aqui]("http://www.cimitan.com/murrine/rgba-support/list")), con el actual motor MURRINE que usa Hardy / Intrepid, ya funcione?  o Necesito recompilar todo el motor murrine, y las aplicaciones, o como?
Algún atrevido lo implementó?

---

### Post by c4d0rn4 on 2008-11-17
se ve interesante, ojalá se pueda con xcompmgr =p

[http://www.chilewarez.org/index.php?showtopic=596748](http://www.chilewarez.org/index.php?showtopic=596748)
[http://ubuntuforums.org/showthread.php?t=881836](http://ubuntuforums.org/showthread.php?t=881836)

a la noche, cuando regrese, si mi hna no está usurpandome la pc pruebo jaja xD

---

### Post by Mauro22 on 2008-11-17
Perdon que me meta

Hay algo que no entiendo... esto no es lo mismo que el plugin de compiz para transparencias ??? 


o algo distinto ?

---

### Post by spg76 on 2008-11-17
> **User21 said:**
> Estaba viendo desde el blog de [Andrea Cimitan]("http://www.cimitan.com/blog/"), acerca de la posibilidad de añadir soporte de transparencias en las aplicaciones de Gnome, con el motor Murrine (RGBA). Para quien no está al tanto, aqui un [screenshot]("http://www.cimitan.com/blog/wp-content/rgba-murrine-170208.png").
Alguien lo ha probado? Es factible que con tan solo parchear o modificar CADA APLICACIÓN (como explican [aqui]("http://www.cimitan.com/murrine/rgba-support/list")), con el actual motor MURRINE que usa Hardy / Intrepid, ya funcione?  o Necesito recompilar todo el motor murrine, y las aplicaciones, o como?
Algún atrevido lo implementó?

Yo no lo probé, pero por ahora solo se puede implementar via parches para cada aplicación individualmente y teniendo instalada la versión de SVN de Murrine.
Podés bajar una versión bastante nueva de Murrine (24 de Septiembre, no sé si hay alguna más nueva), que ya tiene soporte para esto, desde la página del tema Dust ([https://wiki.ubuntu.com/Artwork/Incoming/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme)) [[Link directo al paquete para Intrepid i386]("http://launchpadlibrarian.net/17546183/gtk2-engines-murrine_0.60-0ubuntu1%7Eppa4_i386.deb")].
La idea es que GNOME soporte RGBA de manera nativa para que no haya que parchear nada y los desarrolladores de aplicaciones puedan habilitarlo facilmente.

> **c4d0rn4 said:**
> se ve interesante, ojalá se pueda con xcompmgr =p

[http://www.chilewarez.org/index.php?showtopic=596748](http://www.chilewarez.org/index.php?showtopic=596748)
[http://ubuntuforums.org/showthread.php?t=881836](http://ubuntuforums.org/showthread.php?t=881836)

a la noche, cuando regrese, si mi hna no está usurpandome la pc pruebo jaja xD

Para que funcionen las transparencias se necesita un gestor composite, así que en teoría debería funcionar.
De todas maneras, el motor está hecho de tal manera que si no hay un gestor composite los widgets se dibujan sin transparencias con lo cual no sé genera ninguna incompatibilidad.

> **Mauro22 said:**
> Perdon que me meta

Hay algo que no entiendo... esto no es lo mismo que el plugin de compiz para transparencias ??? 


o algo distinto ?

No, no es lo mismo. Con esto los desarrolladores pueden utilizar transparencias en el aspecto visual de sus programas.
[Según lo explica Cimi]("http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/#comment-2939"): Las transparencias de Compiz son lo que se llama "falsa transparencia", en donde las ventanas y su contenido se dibujan con la misma opacidad dando el efecto de transparencia.
En este caso la transparencia es real, selectiva y controlada completamente por el motor.

---

### Post by pol666 on 2008-11-17
Bueno veo que por ahora no se puede, pero es accesible, (esto lo estaba desarollando hace tiempo, pero no lo habian liberado)

---

### Post by User21 on 2008-11-17
De lujo! Gracias, spg76!
Ya lo tengo andando, pero solo aquellos que usan plugins. Me temo que esta algo verde para parchear todas las aplicaciones. Bah, eso me temo, no se... Ahi va una captura...

---

### Post by hictio on 2008-11-17
Que lindo que se ve este efecto, yo habia encontrado por casualidad el screenshot que postearon el link en el primer post de este thread hace unas semanas, buscando ni me acuerdo que.
A riesgo de sonar un vejete, me impresiona lo "claro" que se ve todo, irónico, porque en realidad se hizo para poder usar transparencias... Si, lo se.

---

