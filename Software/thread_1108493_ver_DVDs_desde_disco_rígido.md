---
title: "ver DVDs desde disco rígido"
date: 2009-03-27
forum: Software
---

### Post by exegeses on 2009-03-27
el asunto es que ripeo un DVD. lo tengo en mi disco rigido y cuando quiero verlo, no me deja.
ya me está poniendo de los pelos.

no me los reproduce ni el VLC, ni el MPlayer, ni el Totem ni el KMPlayer.

nota: puedo ver algunos alchivos .VOB si los selecciono por separado, pero no puedo seleccionar el VIDEO_TS.IFO (indice del DVD) ni el directorio del DVD.

alguien sabe cómo solucionarlo?

desde ya, muchas gracias.

---

### Post by pablo.s on 2009-03-27
En VLC tenés la opción Abrir Directorio, entonces abris la carpeta VIDEO_TS.

PD: Si seguis posteando consultas en Comunidad el admin te va a dar con 
un caño!

---

### Post by exegeses on 2009-03-27
> **pablo.s said:**
> En VLC tenés la opción Abrir Directorio, entonces abris la carpeta VIDEO_TS.

ahora que me lo decís, me fijé en otro DVD que tengo ripeado. con uno se puede ver el directorio y con otro no. eso es raro.
calculo que debe ser un bug, como el del screensaver.
ni idea de cómo solucionarlo.


> **pablo.s said:**
> PD: Si seguis posteando consultas en Comunidad el admin te va a dar con 
un caño!

gracias por la sugenrencia, ya envié MP a los admins para mover estos mensajes.

saludos.

---

### Post by z37a on 2009-03-27
El SMplayer que se basa en el Mplayer tiene la opcion de "dvd de carpeta...", igualmente tambien podes usar el Kaffeine, en las opciones donde dice lector de dvd pones la ruta de donde esta la carpeta que contiene el Video_ts y audio_ts, le das play dvd y listo(te recomiendo este ultimo, el smplayer no te reproduce el menu y todo lo demas)

---

### Post by rvm4000 on 2009-03-27
> **z37a said:**
> (te recomiendo este ultimo, el smplayer no te reproduce el menu y todo lo demas)

Si se usa la última versión (0.6.7) junto con una versión reciente del mplayer, **sí** reproduce los menús.

[https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)

[[IMG]http://e.imagehost.org/t/0598/dvdmenus.jpg[/IMG]](http://e.imagehost.org/view/0598/dvdmenus)

---

### Post by exegeses on 2009-03-28
gracias rvm4000. la verdad da gusto ver respuestas rápido y acerca de nuevas versiones de soft.

aún no lo pude probar, pero cuando actualice la versión delmplayer te cuento.

este es mi USUAL SO (SO de USO) o sea, el mío propio,  de uso. así que trato de usar soft "stable" en cuando enganche el estable lo actualizo.
soyy, parece una pavada, pero el uso uso/trabajo me  ha ensañado a usar estables y bueno o siempre trato de tener la ulta versión del soft STABLE.

muchas gracias nuevamente y espero poder contribuir con esta comunidad.
saludos


exegeses

---

### Post by exegeses on 2009-03-28
estuve investigando, no pudo con mi propio ser.

te comento que uso Gusty Gibbon...

o sea que 

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) hardy main

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) intrepid main

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) jaunty main

no los tengo actualizados.

o sea que no encontré las versiones para Gutsy Gibbon.
espero no sea comentario "newbbie" o "lammer", pero si lo es, estoy con muchas ganas de aprender.

saludos
exegeses

---

### Post by guillermolisi on 2009-03-28
> **exegeses said:**
> estuve investigando, no pudo con mi propio ser.

te comento que uso Gusty Gibbon...

o sea que 

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) hardy main

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) intrepid main

deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) jaunty main

no los tengo actualizados.

o sea que no encontré las versiones para Gutsy Gibbon.
espero no sea comentario "newbbie" o "lammer", pero si lo es, estoy con muchas ganas de aprender.

saludos
exegeses
Se entiende el criterio de usar versiones estables pero entre GG y HH tenes la misma estabilidad con el agregado de que HH es LTS, Long Term Support, y te garantiza actualizaciones por mucho mas tiempo que una version normal.

Por que no actualizas a HH ?

---

### Post by josecuervo86 on 2009-03-28
De una, si queres estabilidad no hace falta quedarte en Gutsy! Pone HH que te da, como dijo guillermo, un soporte mas extenso (desconta que gutsy ya no lo tiene) y como sabras mientras mas tiempo se le dedica a algo, ganas en estabilidad.

---

