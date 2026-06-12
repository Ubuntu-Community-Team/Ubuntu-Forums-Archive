---
title: "ext2fsd No veo el contenido de Home"
date: 2009-09-11
forum: Software
---

### Post by akiestudio on 2009-09-11
Hola buenas , desde windows uso este programa ,parar ver los archivos de ubuntu, y puedo ver todo el contenido de las carpetas , etc,var.... pero la de home esta vacia, no puedo acceder a mi escritorio de linux por ejemplo , quien podria decirme como solucionar este problema...
gracias

---

### Post by Soulinux on 2009-09-11
prueva hacer click en: Ver--> archivos ocultos.
Quiza asi te aparezca.

---

### Post by akiestudio on 2009-09-12
Muchas gracias pero ya probe eso ....no se cual sera el problema . alguna otra sugerencia...

---

### Post by akiestudio on 2009-09-30
Nadie sabria decirme como puedo ver mis archivos desde windows, ¿Quizas al hacer la instalacion , puse que mis archivos fuesen privado? ¿Alguien puede echarme una mano en este tema? Gracias

---

### Post by josecuervo86 on 2009-09-30
Una pregunta, no habrás usado Ext4 no?

---

### Post by emiliano_raso on 2009-10-01
> **akiestudio said:**
> Hola buenas , desde windows uso este programa ,parar ver los archivos de ubuntu, y puedo ver todo el contenido de las carpetas , etc,var.... pero la de home esta vacia, no puedo acceder a mi escritorio de linux por ejemplo , quien podria decirme como solucionar este problema...
gracias

Te cuento mi experiencia:
Tenía instalado Ubuntu con EXT3 y en Windows la aplicación ext2fsd.
Me dejaba ver todo pero el home no, como si me mostrara una partición generica de cualquier sisitema GNU/Linux.
Despues me di cuenta que si tengo una particion con EXT3 y un programa que lee EXT2 no iba a llegar a ningun lado (ext2fsd)
Así que me bajé ext3fsd.

Cuando salió Ubuntu 9.04, lo instalé con EXT4, razón por la cual, nuevamente ext3fsd no me lo leyó por mas piruetas que hice.

SOLUCIÓN: Fijate en que sistema de archivos tenés Ubuntu (ext3 o ext4) y bajate para windows el programa correspondiente.
Sinceramente no se si hay uno para ext4 porque cuando instalé Ubuntu 9.04 no usé mas Windows por un tiempo largo, y ahora me pasé a Debian y lo tengo con EXT3 :-P

Espero que te sirva.

---

