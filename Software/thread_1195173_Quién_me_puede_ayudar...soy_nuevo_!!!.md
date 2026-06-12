---
title: "Quién me puede ayudar??...soy nuevo !!!"
date: 2009-06-23
forum: Software
---

### Post by Foxtrot_35 on 2009-06-23
Hola Amigos...soy nuevo en Ubunto y ya tengo algunas preguntas...
saben??...no hay caso en poder reproducir DVD en mi notebook, probé con el TOtem y el Dragon...pero nada de nada...busqué en todos los foros hice todo lo que se exponia pero sin resultados.
Lo mismo que con las páginas con contenido JAVA, que estoy haciendo mal? 
Desde ya agradezco su ayuda
chaooo

---

### Post by PabloBS on 2009-06-23
Yo utilizo mis discos DVD muy bien con Totem, Mplayer y GNOMEplayer.  Pero antes hay que bajar los codecs.

Este enlace te puede ayudar a hacer esto, y muchas otras cosas mas...

[http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/](http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/)

Saludos

---

### Post by bichopro on 2009-06-23
Te respondi en el otro mensaje que dejaste y por favor se mas descriptivo con el titulo de tus post para que sea mas facil ayudarte

tu otro post esta aqui:
[http://ubuntuforums.org/showthread.php?p=7501862#post7501862](http://ubuntuforums.org/showthread.php?p=7501862#post7501862)

y te copio la solucion:

Hola..
Agrega estos repositorios, busca la aplicacion terminal y copia pega y enter, cuando te pida la contraseña tecleala y enter tambien.

aqui van os comando en el orden que corresponde:

> sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

> sudo apt-get install libdvdcss2

y finalmente...

> sudo apt-get install w32codecs

o si tienes un ubuntu de 64...

> sudo apt-get install w64codecs

y tb puedes instalar en añadir y quitar el paquete ubuntu-restricted-extras

y agrego lo de otro usuario:

> sudo apt-get install vlc

---

### Post by blackxored on 2009-06-23
Instala ubuntu-restricted-areas y mplayer, audacious.

---

### Post by Foxtrot_35 on 2009-06-23
Antes que nada...gracias amigos por responder,
PabloBs ya había probado esa página que tu mencionas, sin embargo, no tuve resultados positivos, lo instalé por medio del terminal, pensé que al reiniciar iba a tener la solución pero no fue así.
Quizás me estoy saltando algún paso...no losé.
 
Bichopro...nosé porque razón cuando ingresé a la página hoy en la mañana no estaba mi pregunta que la había hecho ayer, por eso tuve que formularla de nuevo.
Creo que esa secuencia de comandos que mencionas ya la hice...sin resultados, quizás algo me falto, lo haré nuevamente como mencionas y les digo como me fue.
gracias por su ayuda.

---

### Post by felipeleven on 2009-06-23
**Foxtrot_35**, por favor lee esto:
[http://ubuntuforums.org/showthread.php?t=1162701](http://ubuntuforums.org/showthread.php?t=1162701)

El post que hiciste no corresponde a la sección "comunidad", comprendo que no hayas encontrado tu post anterior pero por favor se mas atento a la sección donde lo publicas.

Saludos

---

### Post by Carlos C on 2009-06-24
Como ya se dijo el thread no corresponde al subforo comunidad así que lo he movido. Es un thread además repetido así que lo cierro. Por favor utiliza títulos más descriptivos (algo que también otros ya te dijeron) ya que la idea es que tus dudas sean leídas por quienes tengan inquietudes similares.

Saludos.

---

