---
title: "Existe algun emulador para los productos de adobe"
date: 2008-07-25
forum: Software
---

### Post by Verys on 2008-07-25
hola, gracias a ubuntu estoy recuperando unos documentos de la pc, y quisiera instalar definitivamente ubuntu, pero yo uso los productos de adobe (photoshop, illustrator, indesign, etc) tambien autocad, corel, 3d max, el unico que funcionaria creo que es blender :KS

se que hay emuladores de windows para mac, y por eso mi pregunta es si tambien hay emuladores de windows para ubuntu? 

o si hay alguna otra forma de instalar estos programas en ubuntu?

Saludos =)

---

### Post by Mauro22 on 2008-07-25
WINE no es un emulador, pero soporta gran variedad de software diseñado para windows.


Lo podes bajar desde synaptic o desde la consola con:

sudo apt-get install wine

Y el programa de instalacion lo abris con:

wine nombredelprograma

---

### Post by pol666 on 2008-07-25
como sos muy nueva:

Wine es COMO un emulador. lo podes instalar desde el gestor de paquetes y para ejecutar un instalador o cualquier .exe solo tenes que hacerle doble click o click derecho>abrir con wine.

Nada raro

---

### Post by leo_rockway on 2008-07-25
Mauro22 dice que WINE no es un emulador porque ese es justamente el significado del acrónimo (Wine Is Not an Emulator). WINE es una reimplementación libre de las APIs de Windows.

En la página de WINE hay una base de datos con las aplicaciones que funcionan [0] que aclara que funciona y que no de cada aplicación.

[0] [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Verys on 2008-07-25
hola, gracias por responder, pero este programa acepta bien los programas que nombro? porque entonces no habria problema en instalar ubuntu con toda tranquilidad :KS

Saludos =)

---

### Post by leo_rockway on 2008-07-25
> **leo_rockway said:**
> 
en la página de wine hay una base de datos con las aplicaciones que funcionan [0] que aclara que funciona y que no de cada aplicación.

[0] [http://appdb.winehq.org/](http://appdb.winehq.org/)

; -)

---

### Post by Verys on 2008-07-25
> [QUOTE]Quote:
Originally Posted by leo_rockway View Post
en la página de wine hay una base de datos con las aplicaciones que funcionan [0] que aclara que funciona y que no de cada aplicación.

[0] [http://appdb.winehq.org/](http://appdb.winehq.org/)
; -)
[/QUOTE]


ok, veo que photoshop cs3 si lo soporta, no se si sera lo mismo con los demas programas de la suite de adobe cs3, lei por ahi illustrator cs, autoca 2008 (yo tengo el 2007) corel no lo nombra, voy a tener que seguir investigando :KS

Saludos =)

---

### Post by facundocorradini on 2008-07-27
Hola Verys,

De los programas que nombrás todos funcionan a la casi-perfección mediante wine. 

El único que te puede llegar a traer problemas es AutoCad, que está bastante complicado de instalar, pero que se puede se puede. 

saludos!

---

