---
title: "problemas con escritorio remoto"
date: 2010-03-06
forum: Software
---

### Post by granjero on 2010-03-06
buenas, les cuento mi tema:

en casa tengo instalado ubuntu 9.10 y a mi hno le instale en su maquina (pentiun IV, gforce mx400, 512 ram) el mismo. anoche quise ayudarlo con unas configuraciones y le dije que tilde en Sistema>Preferencias>Escritorio Remoto las opciones de permitir ver y permitir controlar el escritorio y que le ponga una pass

todo eso parece que lo hizo bien porque cuando desde el visor de escritorios remotos puse su ip y la clave que me pasó se conecta. pero después no pude hacer más que mover el mouse por la pantalla...

no me detectaba clicks y nada... y el refresh era malísimo....

el se cansó  yo me puse a investigar un poco... como tengo otra compu me baje el vnc viewer para ipod touch.

cuando me conecto a mi máquina desde el ipod pasa algo similar... 

no tengo refresh de la sesión, si minimizo una ventana desde el ipod o "cliqueo" en Sistema o donde fuere, en la pantalla de la pc sucede lo que debería pero el ipod no refresca....

me parece que es el mismo síntoma que tenía mi pc con la conexión de mi hno....

desactivé el vino server y puse VNCSERVER

cuando me conecto con el ipod a teniendo vncserver activo sucede algo muy extraño:

es como si con la conexión remota se abriera una sesión **paralela** o sea:

el ipod refresca bárbaro pero nada de lo que hago se refleja en la pantalla de mi pc

es más si pongo play en rythmbox desde el ipod arranca la música en la pc pero no aparece puesto play en el programa y si le doy play desde la pc arranca la música de nuevo pero la que estaba sonando activada desde el ipod sigue sonando también....

es muy extraño....

imaginaba que el visor iba a andar de 10....  :cry::cry::cry::cry:

alguna punta?


salud!

---

### Post by juancarlospaco on 2010-03-07
[NxNoMachine]("http://www.nomachine.com/select-package.php?os=linux&id=1")

:)

---

### Post by granjero on 2010-03-08
voy a probarlo!

gracias!

---

### Post by tekzool on 2010-05-12
A mí me pasa exactamente lo mismo. Lo he intentado con tightvnc pero me hace lo mismo que a tí; si me inicia la sesión en otro escritorio va bien, pero evidentemente no se ve en el equipo controlado, aunque oye, me deja hacer cualquier tarea. Eso sí, como ponga entre los programas de inicio tightvncserver me jode el sistema al completo; llega a la pantalla de login en un flash como siempre (hasta aquí me saco el sombrero, ole la gente de ubuntu), pero una vez que meto usuario y contraseña le lleva un mundo arrancar el escritorio y, una vez hecho, pasa de consumir unos 300 mb de ram a consumir 1,8 gb, y además va como el culo. Esto último (es decir, si pongo entre los programas de inicio tightvncserver) pasa tanto en 32 como en 64 bits. Lo de que no refresque la pantalla parece privilegio de la versión de 64 bits. Espero que sirva de ayuda.

---

### Post by Xtreme945 on 2010-05-12
A mi tambien!

---

### Post by santiagoward2000 on 2010-05-12
Hola gente!
Pregunta: ¿En sus respectivos equipos controlados ¿están usando Compiz? Si ese es el caso, ya es un [bug reportado]("https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442"), VNC no refresca la imagen si la máquina controlada tiene Compiz activado. Prueben desactivarlo y ver si entonces refresca.
Suerte!

---

### Post by tekzool on 2010-05-13
Esta noche lo probaré. En todo caso me alegra saber que alguien ya ha reportado el bug, ya que he encontrado muy poca información en la red.

---

### Post by biale on 2010-05-13
Si Uds prueban con livecd de Karmic no van a tener problemas de refresco. O sea que los problemas arrancan con compiz.

Muy configurable, yo uso x11vnc con la opción '-noxdamage' y los problemas con compiz desaparecen. A costa de una cierta pérdida de performance por la mayor tasa de refresco de pantalla. 

No tuve grandes resultados con NxNoMachine. Recuerdo que entre alguna otra cosa fallaba el escalado de pantalla y dejaba los screenlets e íconos de escritorio batidos. 

Un saludo a todos

---

### Post by tekzool on 2010-05-13
Bueno, tras echar un vistazo al bug que mencionan mas arriba, que resulto ser un duplicado de otro bug, tan solo es necesario poner en las opciones de efectos de escritorio "ninguno" y va como la seda. Se que esto no es aceptable para algunos, pero en mi caso, y para otra gente que no use o bien no le importe usar los efectos visuales funciona. Desde luego no soluciona el bug, que lo hay y sigue ahi, pero evidencia que el problema tiene que ver con la interaccion de vino y compiz. Espero que le ayude a alguien.

---

### Post by thegreeneyes on 2012-02-03
Hola, yo desde ubuntu 8 o 9 que no podía hacer login remoto viendo el desktop a full desde otra máquina, pero casualmente encontré este link : 

[http://codeghar.wordpress.com/2011/11/15/remote-desktop-in-ubuntu-oneiric-ocelot/#comment-994](http://codeghar.wordpress.com/2011/11/15/remote-desktop-in-ubuntu-oneiric-ocelot/#comment-994)

y siguiendo las instruciones todo funcionó bárbaro con total simpleza, y puedo ver el desktop de una máquina remota desde otra, ambas con linux.  Lo único que tuve que hacer para que funcione fue remover el archivo 

rm ~/.ssh/known_hosts

y listo.

Los pasos a seguir son:

Instalación en el server (máquina remota): 
[nota: donde aparecen las caritas debería decir ": x" sin el encomillado ni el espacio intermedio]

sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goserver

Instalación en el cliente (máquina local):

sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goclient
rm ~/.ssh/known_hosts

y listo, a correr X2Go Client desde 

Administración->Internet->X2Go Client

Suerte!!

---

