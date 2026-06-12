---
title: "[SOLUCIONADO] Barra de menú perdida... ayuda!"
date: 2009-07-23
forum: Software
---

### Post by pbarros on 2009-07-23
[FONT="Arial"]Hola a todos...
soy nuevo por acá y en Linux también... hace no más de 2 semanas que instalé Linux (Jaunty) en otro disco que tengo... de a poco acostumbrándome a la interfaz y probando cosas, como el famoso Wine.
Entre las tantas cosas que probé fue el Globalmenu... que parecía una buena idea... dentro de todas las cosas que he visto para Ubuntu... y es ahí cuando empezaron mis problemas.
Resulta que nunca encontré el Globalmenu en ninguno de los menús... y mi Nautilus (o como se escriba) ahora no tiene la barra de menú y varios otros programas tampoco. Ayer por fin encontré el Globalmenu, no tenía idea que estaba en el panel... bueno, en mi caso el de arriba sólo lo dejé con el Globalmenu y el de abajo con otras cosas.
De todas formas no me acomoda usar un panel, ya sea abajo o arriba que muestre los menús de todo, y me gustaría restablecer los menús como venían originalmente.
¿Se puede hacer?

Por cierto... es genial el Ubuntu, no conozco otro, pero me gusta... si todo va bien, Windows pasa al olvido.
[/FONT]

---

### Post by aledruetta on 2009-07-23
> **pbarros said:**
> [FONT=Arial]...me gustaría restablecer los menús como venían originalmente.
¿Se puede hacer? [/FONT]
Haciendo click con el botón derecho del mouse en el panel y seleccionando "añadir al panel", vas encontrar dos opciones: "Barra de menús" y "Menú principal". Es alguna de esas dos, no recuerdo cuál.


Editado: es "Barra de menús", ahí me fijé.

---

### Post by pbarros on 2009-07-23
Apenas llegue a la casa voy a probar...

Gracias

---

### Post by pbarros on 2009-07-23
> **aledruetta said:**
> Haciendo click con el botón derecho del mouse en el panel y seleccionando "añadir al panel", vas encontrar dos opciones: "Barra de menús" y "Menú principal". Es alguna de esas dos, no recuerdo cuál.


Editado: es "Barra de menús", ahí me fijé.

Ni una ni otra... no tengo "perdido" el menú de aplicaciones, sino que los menús de las aplicaciones... Nautilus no tiene menú, sólo la barra de Herramientas, los gestores de paquetes tambien... Evolution no sé si nunca ha tenido menú, pero si lo tenía tampoco lo veo, y así un montón de otras aplicaciones.

:(

---

### Post by radixs on 2009-07-23
> **pbarros said:**
> Ni una ni otra... no tengo "perdido" el menú de aplicaciones, sino que los menús de las aplicaciones... Nautilus no tiene menú, sólo la barra de Herramientas, los gestores de paquetes tambien... Evolution no sé si nunca ha tenido menú, pero si lo tenía tampoco lo veo, y así un montón de otras aplicaciones.

:(

Porque mejor no mandas un screenshot asi enteremos mejor ;)

---

### Post by pbarros on 2009-07-23
> **radixs said:**
> Porque mejor no mandas un screenshot asi enteremos mejor ;)

Ahí van las pantallas... si saco el globalmenu no me aparecen los menus.... y no sé como reestablecerlos...


Borré el Globalmenu desde los repositorios, y los gestores de paquetes, hasta con el Tweak, saqué el panel de arriba y reinicié y ahí volvieron los menús.

---

### Post by Patriciologico on 2009-07-24
Lo que hiciste fue instalar un menu tipo macosx, este elimina el menu de las aplicaciones y los va poniendo en el panel superior. La ultima vez que lei sobre ese proyecto no estaba muy estable, no se ahora, el tiempo pasa rapido en software.

Buscando informacion, veo que no es llegar y borrar. Puedes leer el instructivo oficial para desinstalar [http://code.google.com/p/gnome2-globalmenu/issues/detail?id=466](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=466)

Y ver mas ayudas en [http://ubuntuforums.org/showthread.php?p=3121960&highlight=uninstall#post3121960](http://ubuntuforums.org/showthread.php?p=3121960&highlight=uninstall#post3121960) y  en [http://ubuntuforums.org/showthread.php?t=987341](http://ubuntuforums.org/showthread.php?t=987341)

Saludos!

PD: Se que no es la idea estar enlazando respuestas, pero en este caso las respuestas están en el mismo servidor y y pienso que es mejor no duplicar contenido.

---

### Post by pbarros on 2009-07-24
Busqué en varias partes y sale muy poca información de este "applet gnome-globalmenu" o como se llame. En varias páginas salía como la gran novedad y como elemento casi necesario para dejar el sistema ok... como novato en Linux hice caso... eso fue antes de registrarme acá.
La cosa es que para sacar el famoso globalmenu, aparte de cerrar el panel superior, borrarlo con el comando $ sudo apt-get remove gnome-globalmenu, revisé los repositorios en donde aparecía (origenes de sw), del ubuntu tweak también lo saqué, y del listado de synaptic (así se llama??). Reinicié la máquina y no estaba!... alegría para mi.
Gracias por sus respuestas.

---

### Post by nopersona on 2009-07-24
Una vez probé algo así en la 6.06, gran error, tuve que volver a compilar las librerías de nautilus, un cachito. Lo solucionaste? creo que de esa fecha hasta ahora hay una solución más "elegante" para eso :popcorn:

---

### Post by pbarros on 2009-07-24
> **nopersona said:**
> Una vez probé algo así en la 6.06, gran error, tuve que volver a compilar las librerías de nautilus, un cachito. Lo solucionaste? creo que de esa fecha hasta ahora hay una solución más "elegante" para eso :popcorn:
Si lo arreglé, ahora veo los menús... hice los pasos que escribí arriba... en pocas palabras borré todo lo que decía globalmenu, de los repositorios y de los instaladores.

Y hasta el momento no he tenido problemas de librerías ni nada... así que si a alguien le sucede lo mismo, que lo borre... no es un buen programa, para los que estamos recién experimentando Linux.

Es por lo mismo de la apariencia que le di... mi polola sólo a visto Windows, y no se acostumbró al entorno que le ofrecía Ubuntu, así que busqué temas e iconos similares.

---

