---
title: "Problema con &quot;Now Playing&quot; Screenlet"
date: 2009-10-02
forum: Software
---

### Post by baila0 on 2009-10-02
Hola, resulta que tengo instalado el screenlet de Now Playing... sin embargo al usarlo con Rhythmbox, no me reconoce que hay alguna cancion sonando ni tampoco el album art... la cancion esta sonando pero el Now Playing no muestra nada. (en Now Playing tengo seleccionao Rhythmbox obviamente)
 
Probé con Banshee, y el resultado fué mas o menos igual ya que Si me reconoce la canción que está sonando pero no me reconoce el album art (que si aparece en banshee). 
 
Nose que puede ser... ojalá alguien pueda ayudarme, gracias!
Por si acaso uso Ubuntu 9.04 y las versiones de Rhythmbox y Banshee son las que vienen instaladas y en los repositorios respectivamente.
 
Saludos

---

### Post by moreback on 2009-10-02
Es obvio que el problema es del screenlet, probaste con la última versión?

---

### Post by baila0 on 2009-10-02
Mmm, creo que tengo la ultima version, osea tengo la versión que venía "preinstalada" con los screenlets (instalados por synaptic)

---

### Post by Can+~ on 2009-10-03
Revisa si el screenlet y rythmbox tienen alguna forma de comunicarse, dos programas que no se conocen deben hablar por un mismo "canal". Por lo general se usa [DBUS]("http://en.wikipedia.org/wiki/DBus") o (mas especializado) [MPRIS]("http://en.wikipedia.org/wiki/Media_Player_Remote_Interfacing_Specification").

No he hecho la prueba, pero ahí tienes algo mas que buscar.

Edit: Parece que es un [bug conocido]("https://lists.launchpad.net/screenlets-dev/msg00080.html").

Por mientras, puedes usar [Songbird]("http://getsongbird.com/") y contentarte con sus plugins (FireTray, entre otros).

---

