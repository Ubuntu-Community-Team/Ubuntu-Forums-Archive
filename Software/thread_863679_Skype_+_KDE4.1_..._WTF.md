---
title: "Skype + KDE4.1 ... WTF??"
date: 2008-07-18
forum: Software
---

### Post by SLA_leandrin on 2008-07-18
Buenas a todos,

Lo que voy a preguntar seguramente tiene una solución sencilla, pero como no lo puedo arreglar, entonces, ahí voy. 

El otro día instalé KDE4.1 beta a mi Ubuntu Hardy, sólo para testearlo. No me gustó y lo desinstalé. 
Lo instalé agregando esta línea a los repos;

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

y corriendo 
```

sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop kdeplasmoids
```

Luego, lo desinstalé así:

```
sudo apt-get remove --purge kubuntu-kde4-desktop kdeplasmoids
```

El problema es que durante la instalación del KDE4.1 baja e instala un montón de otros paquetes, obiamente, que me preguntó y le metí que sí. La lista es interminable. Los borré luego a algunos, hasta que me duraron las ganas, de a uno. Entonces, cuando me cansé hice;

```
 sudo apt-get remove --purge kubuntu-*
 sudo apt-get remove --purge kde*
sudo apt-get remove --purge kdeplasmoids-libs4
sudo apt-get autoremove --purge
```

El tema por el cual pregunto es que el Skype está usando (CREO) qt, y me cambió totalmente el look & feel, no me gusta nada. Además, tiene [ESTE]("http://http://ubuntuforums.org/showthread.php?t=795676&highlight=skype+kde") problema también. 

Probé reinstalarlo borrando antes mi carpeta /home/.skype, pero no sigue estando igual. Por favor, alguien que me pueda ayudar a dejar el skype como estaba originalmente!!

Gracias.

---

### Post by fedeavila on 2008-07-28
> **SLA_leandrin said:**
> Buenas a todos,

Lo que voy a preguntar seguramente tiene una solución sencilla, pero como no lo puedo arreglar, entonces, ahí voy. 

El otro día instalé KDE4.1 beta a mi Ubuntu Hardy, sólo para testearlo. No me gustó y lo desinstalé. 
Lo instalé agregando esta línea a los repos;

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

y corriendo 
```

sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop kdeplasmoids
```

Luego, lo desinstalé así:

```
sudo apt-get remove --purge kubuntu-kde4-desktop kdeplasmoids
```

El problema es que durante la instalación del KDE4.1 baja e instala un montón de otros paquetes, obiamente, que me preguntó y le metí que sí. La lista es interminable. Los borré luego a algunos, hasta que me duraron las ganas, de a uno. Entonces, cuando me cansé hice;

```
 sudo apt-get remove --purge kubuntu-*
 sudo apt-get remove --purge kde*
sudo apt-get remove --purge kdeplasmoids-libs4
sudo apt-get autoremove --purge
```

El tema por el cual pregunto es que el Skype está usando (CREO) qt, y me cambió totalmente el look & feel, no me gusta nada. Además, tiene [ESTE]("http://http://ubuntuforums.org/showthread.php?t=795676&highlight=skype+kde") problema también. 

Probé reinstalarlo borrando antes mi carpeta /home/.skype, pero no sigue estando igual. Por favor, alguien que me pueda ayudar a dejar el skype como estaba originalmente!!

Gracias.
Es la primera vez que intento ayudar a un participante jaja... Mira yo hace un par de horas instale el skype y tampoco me gustaba mucho como se veia, encontre una especie de solucion (quizas) para lo que vos estas buscando, es re facil tenes que instalar el paquete qt3-qtconfig + polymer y luego configurarlo con el comando "qtconfig" ... lo hace mucho mas agradable, fijate en esta guia explica todo paso a paso [http://guia-ubuntu.org/index.php?title=Skype#Mejorar_el_aspecto](http://guia-ubuntu.org/index.php?title=Skype#Mejorar_el_aspecto) yo encontre la version 4 de Qt, igual seguro a esta altura ya lo habras solucionado :P

Saludos

---

