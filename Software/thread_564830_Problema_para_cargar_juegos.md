---
title: "Problema para cargar juegos"
date: 2007-10-01
forum: Software
---

### Post by Cripton on 2007-10-01
Hola Comunidad, tengo este problema, y hace ya mucho tiempo que no lo puedo resolver, los juegos con wine andan bien, el tema es cuando quiero hacer un lanzador para dichos juegos.

Por ejemplo supongamos que mi quake3.exe se encuentra en el directorio "/home/user/Desktop/quake3"

si con la consola tipeo: cd /home/user/Desktop/quake3
y luego: wine quake3.exe

esto lanza el juego y todo bien. el tema es como hago para poner esto en un lanzador,

probé escribiendo en el campo "comando" esto: wine /home/user/Desktop/quake3/quake3.exe 

Esto lanza el juego, pero me tira errores de que no encuentra tal archivo y otras frutas y verduras, así que me di cuenta que estaba corriendo el exe desde otro directorio "/home/user"

Mi pregunta es la siguiente: ¿como hago para cambiar el directorio de trabajo, y a su vez ejecutar el archivo exe, todo en un mismo comando para ser utilizado en el lanzador?

Gracias y aguante ubuntu y la FIUBA!

---

### Post by santiagoward2000 on 2007-10-01
Hola,
Ahora no estoy completamente seguro, yo lo hacia con el rollecoaster 2. Me parece que el comando deberia ser:
"wine /home/user/Desktop/quake3/quake3.exe"

---

### Post by leo_rockway on 2007-10-01
cuando creas el lanzador tenes que especificarle la carpeta de trabajo para que encuentre los archivos (al menos asi lo hice para agregar juegos al menu de kde)

---

### Post by faktorqm on 2007-10-02
che crypton, te copas con una guia para hacer andar el q3?
yo todavia no pude...... snif snif!!!!!!
tengo 3 instaladores distintos, y en todos pasa lo mismo........ no arranca!
me baje el q1, se ve negro...... pero en ventana.
consegui el q2, se ve negro pero a pantalla completa, entonces tengo que cerrar todo desde una terminal...............
el q3 no hay manera :(:(
en guindous, andan los 3 lo mas bien... grrrrrrr
sugerencias? ideas? gracias de antemano!

---

### Post by Cripton on 2007-10-05
> **faktorqm said:**
> che crypton, te copas con una guia para hacer andar el q3?
yo todavia no pude...... snif snif!!!!!!
tengo 3 instaladores distintos, y en todos pasa lo mismo........ no arranca!
me baje el q1, se ve negro...... pero en ventana.
consegui el q2, se ve negro pero a pantalla completa, entonces tengo que cerrar todo desde una terminal...............
el q3 no hay manera :(:(
en guindous, andan los 3 lo mas bien... grrrrrrr
sugerencias? ideas? gracias de antemano!

andar me anda el juego, pero solo si lo cargo desde consola, el otro pibe no me leyó creo, puso el comando tal cual lo probé yo, 

y faktorqm taría hacer una guia general para los juegos de güindous, pero sin poder resolver ese problema de los lanzadores no se como quedaría piola

---

### Post by leo_rockway on 2007-10-05
yo no puedo ser mas especifico porque yo uso kde. lo que yo hice fue lo que comente en mi post anterior. al momento de crear un lanzador en kde esta para rellenar el campo "comando" y el campo "ruta de trabajo"

en comando tengo algo asi por ej: wine '/windows/Archivos de programa/Max Payne/MaxPayne.exe'

y en ruta de trabajo: /windows/Archivos de programa/Max Payne

entonces los archivos que necesita los busca en /windows/Archivos de programa/Max Payne y no en mi home.

---

### Post by godzeus on 2007-10-05
> **faktorqm said:**
> che crypton, te copas con una guia para hacer andar el q3?
yo todavia no pude...... snif snif!!!!!!
tengo 3 instaladores distintos, y en todos pasa lo mismo........ no arranca!
me baje el q1, se ve negro...... pero en ventana.
consegui el q2, se ve negro pero a pantalla completa, entonces tengo que cerrar todo desde una terminal...............
el q3 no hay manera :(:(
en guindous, andan los 3 lo mas bien... grrrrrrr
sugerencias? ideas? gracias de antemano!
Lo queres hacer andar con wine o con CEDEGA, con CEDEGA es muy facil, lo unico que todavia no pude hacer andar es el Counter Strike Source, si alguie me puede dar una mano se lo voy a agradecer. Igual me envicio con el Urban Terror 4.0, si no lo probaron, se estan perdiendo de algo muy groso, 92fps se consiguen como si nada, una definicion de la san p***, la verdad que me gusta mas que el counter comun. 
[:)]("http://www.urbanterror.net")

---

### Post by niko_3100 on 2007-10-06
Gente supongamos que quiero jugar al.. age of empires 2 como ahira para correrlo con wine? Tengo que instalarlo? como? despues busco el .exe y hago wine age2.exe?

---

### Post by santiagoward2000 on 2007-10-06
Normalmente, si el CD tiene un autorun.exe, el wine lo detecta y lo corre como en Windows. Sino, podes abrir wine-file, buscar el instalador y hacer doble click.
Después para correrlo, seguramente va a aparecer en Applications, buscalo ahi.

---

### Post by Pse on 2007-10-06
La pregunta es...por qué querrías correr el Quake3 en Wine? :confused: Tiene binarios nativos para Linux (¿o no entendí algo?).

---

### Post by faktorqm on 2007-10-08
tenes razon. el problema es que yo tengo supuestamente el cd del quake 3 para linux con el instalador, y toda la bola. pero cuando lo pongo a instalar, o no pasa nada, o tira error al toque y sale. tonces de ultima lo emulo xD
igual voy a reinstalar el ubuntu por que la verdad que lo deje hecho bolsa, probe 7000 cosas de las cuales nunca anduvo ninguna y anda medio para atras. jijijiji no lo pude romper, pero por lo menos lo arruine xDxDxD salu2!!

---

### Post by MeduZa on 2007-10-09
> **leo_rockway said:**
> yo no puedo ser mas especifico porque yo uso kde. lo que yo hice fue lo que comente en mi post anterior. al momento de crear un lanzador en kde esta para rellenar el campo "comando" y el campo "ruta de trabajo"

en comando tengo algo asi por ej: wine '/windows/Archivos de programa/Max Payne/MaxPayne.exe'

y en ruta de trabajo: /windows/Archivos de programa/Max Payne

entonces los archivos que necesita los busca en /windows/Archivos de programa/Max Payne y no en mi home.

yo tengo el mismo problema para crear accesos tengo que hacer un sh y no me gusta! en gnome no tiene ruta de acceso :S como se hace en gnome?

---

### Post by eldragon on 2008-07-13
asi lo instale yo cuando tuve que....

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)


lo mismo  para quake4, doom3 y.. bueno, idsoftware en general


para agregar algo al plato..prueben urbanterror, que es una modificacion del quake3 ala counterstrike. y hay servers en argentina muy rapidos.

inlcuso el instalador y todo el circo es un zip que copias a donde se te canta. viene con un ejecutable open source de quake3.

---

### Post by charlymx on 2011-09-15
hola usen PLayonlinux al terminar de instalar el juego te crea los accesos directos y te administra la versión de wine que debe correr caga juego.

lo pueden descargar de acá [http://www.playonlinux.com/es/download.html](http://www.playonlinux.com/es/download.html) solo escoge tu distro me imagino ubuntu jajaja.

aparte tiene una base de datos que te dice si ya otra persona lo ha instalado y te baja unos scrips para ayudarte con la instalación según el juego. :P

---

