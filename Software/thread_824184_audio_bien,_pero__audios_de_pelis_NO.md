---
title: "audio bien, pero  audios de pelis NO"
date: 2008-06-09
forum: Software
---

### Post by dgcampos on 2008-06-09
Gente :

usando debian etch tengo el siguiente inconveniente : los sonidos del KDE me funcionan muy bien, esucho MP3s y todo bien, pero cuando entro a youtube, el flash instalado no emite ningun sonido...tampoco pude escuchar el audio del corto Buck Bunny, tienen idea de donde tengo que configurar el audio del flash o el audio del noatun media player????

desde ya muchas gracias a todos,

saludos,

dgc

---

### Post by pol666 on 2008-06-09
Creo creo que tenes q bajar una libreria de flash  no me acuerdo cual era

---

### Post by atatiducken on 2008-06-10
**libflashsupport**
por lo menos con ese paquete se soluciono mi problema de sonido

---

### Post by osensei on 2008-06-10
En la configuración de audio (imagino que está en System->Preferences->Sound), estás usando PulseAudio o ALSA? En el caso de que esté en ALSA o Autodetect... aparece PulseAudio en la lista?

Hasta donde tengo entendido, Debian Etch no viene por default con PulseAudio, aunque quizá me equivoque.

La librería **libflashsupport** es soporte de pulseaudio para flash. Si estás usando pulseaudio, entonces instalando esa librería probablemente se solucione el problema de sonido en flash. 

En cuanto al reproductor de video, que no lo conozco, siguiendo con la suposición de que estés usando pulseaudio para el sonido, fijate si no tiene alguna opción en la parte de sonido que diga algo como "output plugin" o algo así donde tengas para elegir la salida del sonido. Ahí probablemente tengas una lista con opciones como ALSA, OSS, y... quizá PulseAudio. Deberías asegurarte de que esté seleccionada PulseAudio, si es que aparece, y, vuelvo a repetir... si es que estás usando pulseaudio como server de sonido.

Si no estás usando PulseAudio, entonces nada de lo que te dije sirve... je. (A menos que decidas instalarlo)

---

### Post by dgcampos on 2008-06-10
mmm, en mi KDE tengo K-> System ... pero no esta el tal Sound...de todos modos gracias por la ayuda. 

Tampoco puedo encontrar la libreria libflashsupport :

dgc@dgclaptop:~$ su
Password:
dgclaptop:/home/dgc# apt-get install libflashsupport
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete libflashsupport
dgclaptop:/home/dgc#

para ver peliculas tengo en el KDE 3.5 el noatun media player y el Kaboodle media player, los dos me muestran el **video pero el audio no funciona... ** que podra estar mal??????

mil gracias por la ayuda.

---

### Post by atatiducken on 2008-06-10
tal vez tenes q ampliar la lista de los repositorios, en synaptic **configuracion - repositorios** y ahi marca universe, restricted y multiverse, luego trata de instalar libflashsupport

EDIT: proba **smplayer** un gran reproductor, es mplayer modificado

---

### Post by gefarion on 2008-06-10
Te recomiendo para ver videos el smplayer, es muy intuitivo y reproduce practicamente todo sin problemas, yo lo uso en kde.

Saludos.

---

### Post by dgcampos on 2008-06-10
te cuento q no encuentro el synaptic en mi sistema pero uso el Adept Installer...de todos modos entro en el buscador y pongo smplayer y no lo encuentra...tenes idea de como configurar el sources.list desde el adept installer?

gracias por la ayuda !!!!!

---

### Post by gefarion on 2008-06-10
Si, anda a Adept->Gestionar los Repositorios. 
Luego actualiza y fijate si ahora esta.

sino instalalo por consola: sudo apt-get install smplayer

Saludos.

---

### Post by dgcampos on 2008-06-10
no...no existe tal Adept->Gestionar los repositorios, el KDE esta en ingles.

De todos modos intente : 
dgc@dgclaptop:~$ su
Password:
dgclaptop:/home/dgc# apt-get install smplayer
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete smplayer
dgclaptop:/home/dgc#

no se cual sera el repositorio de donde bajas ese soft...hoy ya se me hizo tarde maniana sigo con la instalacion...

gracias gefarion!!!!

---

### Post by atatiducken on 2008-06-10
probaste con instalar el synaptic, creo q es mejor q el adept

---

### Post by gefarion on 2008-06-10
Perdon, no me di cuenta que usabas debian, con razon no estaba en los repositorios. El smplayer es solo una interface del mplayer, asi que instala este, yo lo usaba en debian:

apt-get install mplayer

Ya me fije y ese si esta en los repositorios. Disculpa por mi error.
Te recomiendo en debian instalar synaptic para la gestion mas amigable de los paquetes si no estas familiarizado con la consola.

El mplayer soporta casi todo, y tiene muchas opciones muy interesantes.
Sino otra alternativa tambien es el conocido vlc, este tambien esta en lso repositorios de etch.

Saludos.

---

### Post by Hei Ku on 2008-06-10
Instala los language pack de kde para español. Y de ultima, no es Gestionar repositorios, es Manage repositories. 

Como dice faktor, media pila.

---

### Post by faktorqm on 2008-06-11
Foro de Debian en español: [http://www.esdebian.org/foro](http://www.esdebian.org/foro)

---

### Post by dgcampos on 2008-06-11
> **faktorqm said:**
> Foro de Debian en español: [http://www.esdebian.org/foro](http://www.esdebian.org/foro)

perdon por usar el foro de ubuntu pero es que TAMBIEN USO UBUNTU!!!! tengo el ubuntu 7.04 en mi otra pc y el Debian etch 4.0 en mi laptop. Con el ubuntu no tengo ningun problema, funciona de maravillas, pero el debian hasta ahora solo me dio este problemita...y como ubuntu deriva del debian...no se enojen conmigo!!!

hoy cuando llegue a casa pruebo con instalar el mplayer, gracias a todos !!!!!

saludos,

dgc

---

