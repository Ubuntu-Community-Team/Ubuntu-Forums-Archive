---
title: "Jugar T.E.G. online"
date: 2007-11-06
forum: Software
---

### Post by elaleph on 2007-11-06
Hola comunidad,

Necesito una ayudita para configurar una jugada online en el mejor juego del universo que es el T.E.G. para Linux, o sea, Tenés Empanadas Graciela.
Hasta ahora sólo he podido jugar localmente contra jugadores robots. 


Si alguien me puede ayudar le estaré eternamente agradecido.
Saludos y gracias.

---

### Post by sajnox on 2007-11-06
Con gusto te ayudamos....

Podrias darnos un par de datos mas de lo que necesitas?

En que pagina lo jugas??

---

### Post by leo_rockway on 2007-11-06
tambien podes jugar localmente contra jugadores humanos.

vos queres jugar por inet? yo nunca lo hice...

quizas hamachi no sea mala idea.

---

### Post by elaleph on 2007-11-06
Hola Gente,

Gracias por responder. Al TEG lo instalé de los repositorios de Ubuntu Gutsy vía Synaptic. Hasta ahora he logrado jugarlo contra la máquino, pero lo que me interesaría es jugarlo por servidor en Internet, ya que la inteligencia artificial no es muy buena y no se hace difícil encontrar una estrategia para ganar casi siempre.

Ni bien inicia el TEG se abre una ventanita para conectarse al servidor. Ahí es dónde me pierdo. Está la opción de jugar localmente y entonces el parámetro predefinido es localhost y el puerto es el 2000. Ambos pueden modificarse, pero no sé qué valores ingresar. Hay otra pestaña que dice Meta-servidor, ahí no me permite ingresar ningún dato, sólo hay un botón que dice Actualizar.

Me imagino que necesito el nombre de un servidor, pero por más que he buscado no encuentro. Además no entiendo mucho de esos temas, a lo mejor encontré y no supe interpretar.

En fin, si alguien sabe y me puede dar una mano.

Saludos y muchas gracias.

---

### Post by elaleph on 2007-11-06
Hola Gente,

Gracias por responder. Al TEG lo instalé de los repositorios de Ubuntu Gutsy vía Synaptic. Hasta ahora he logrado jugarlo contra la máquina, pero lo que me interesaría es jugarlo por servidor en Internet, ya que la inteligencia artificial no es muy buena y no se hace difícil encontrar una estrategia para ganar casi siempre.

Ni bien inicia el TEG se abre una ventanita para conectarse al servidor. Ahí es dónde me pierdo. Está la opción de jugar localmente y entonces el parámetro predefinido es localhost y el puerto es el 2000. Ambos pueden modificarse, pero no sé qué valores ingresar. Hay otra pestaña que dice Meta-servidor, ahí no me permite ingresar ningún dato, sólo hay un botón que dice Actualizar.

Me imagino que necesito el nombre de un servidor, pero por más que he buscado no encuentro. Además no entiendo mucho de esos temas, a lo mejor encontré y no supe interpretar.

En fin, si alguien sabe y me puede dar una mano.

Saludos y muchas gracias.

---

### Post by facundocorradini on 2007-11-06
Hola.

Efectivamente, tenés que ingresar la dirección y puerto del server en que querés jugar.

Yo lo he hecho varias veces hace unos meses, la verdad es que se arman partidas bastante buenas... El problema es que no me acuerdo los datos del servidor que usaba...

Pero bueno, googleá "servidor de tenes empanadas graciela" , y avisanos así armamos una partida entra la gente de ubuntu-ar, seguro que hay varios que se prenden.

saludos!

---

### Post by elaleph on 2007-11-06
No hay caso, muchachada, no encuentro nada que me oriente. Bajé, incluso, una versión Jteg, en Java, que decía Teg Cliente, pero también me pide un servidor y eso es lo que no encuentro por ningún lado.

---

### Post by leo_rockway on 2007-11-07
si queres jugar con gente que conoces hamachi te saca del apuro en seguida.

---

### Post by elaleph on 2007-11-07
Gracias, lo voy a probar. Pero la verdad que me gustaría jugar con cualquiera que ande por ahí en el ciberespacio. Debe haber alguna forma.

---

### Post by margori on 2007-11-07
Lo que yo siempre he hecho para jugar con amigos por la red es que uno del grupo que tenga una IP publica sea el servidor y pase se la pase a los otros por chat. Ponen ese IP como servidor y listo.

---

### Post by elaleph on 2007-11-07
¿Qué significa tener una IP pública?

---

### Post by margori on 2007-11-07
Buena pregunta.

Cada maquina que tiene internet tiene que tener una IP que la identifica en la red. Hay ciertas IP que estan reservadas para usos particulares.

Por ejemplo: 192.168.x.x son IPs privadas, es decir se puede "ver" dentro de la misma red y navegar por internet pero desde fuera de la red privada no se puede acceder. (Ese es mi caso)

Hay otros ejemplo como 127.0.0.1 y 10.0.x.x (o algo asi) que tambien son privadas.

Para conocer tu IP, anda a la pagina [www.iptools.com](www.iptools.com). En la parte de arriba dice el IP que tenes. Se lo pasas por chat a los otros jugadores para que se conecten si queres ser el servidor.

No tengas miedo de pasar el IP por chat si tenes bien configurado el firewall o si usas linux.

---

### Post by elaleph on 2007-11-07
Muchas gracias por tu respuesta Margori, muy clara e instructiva.

---

### Post by margori on 2007-11-07
Uf. Zafe. La verdad, pense que te hiba a enredar mas aun.

Me falto decirte que hay mucho mas escondido atras del protocolo TCP/IP. Es bueno saber de eso cuando jugas online, uses Torrent o  eMule, etc.

Te recomiendo que hagas tu propia invetigacion.

Nos vemos. Suerte.

PD: Por otro lado, tambien me prendo a jugar un super TEG. Avisame.

---

### Post by elaleph on 2007-11-07
Hola Margori,

Ingresé a la página de IPtools y me surge una duda.
Según la página mi IP es 190.7.XX.XXX, pero según mis Gdesklets es eth0 10.51.XX.XX.
¿A qué se debe la diferencia?

Gracias de nuevo.

---

### Post by margori on 2007-11-07
Estas en una situacion parecida a la mia. Te cuento:

Tu servidor de internet es un revendedor de internet en realidad. Te esta asignando una ip privada de una red local (10.51.x.x) Si te fijas en esta pagina [http://es.wikipedia.org/wiki/Red_privada](http://es.wikipedia.org/wiki/Red_privada) vas a ver cuales son todas la direcciones privadas. Ahora bien, como es que podes navegar po la red? Dentro de la red privada en la que estas exite una maquina que esta directamente conectada a internet y tiene una ip publica (190.x.x.x) Esta computadora es la que recibe tus peticiones, cambia el encabezado para poner su IP y lo envia. Cuando lo recibe vuelve a poner el encabezado para que llegue a tu maquina. Eso se llama enmascaramiento de IP.

Yo tengo tengo como IP 192.168.70.110 dentro de la red privada, pero todas las peticiones se hacen a traves del 200.112.145.x

Conclusion: Como tenes una IP privada no podes recibir peticiones externas. Al igual que yo. Vos sos el que tiene que conectarse.
Normalmente servidores como Speedy o los mas caros te dan un IP publico.

Existen formas de arreglar eso, pero son muy complicadas y requiere configuracion de tu servidor de internet.

Espero haber sido claro. Nos vemos.

---

### Post by elaleph on 2007-11-07
Excelente tus conocimientos y tu disposición!
Si no entendí mal, en este caso en particular, ni yo te podría invitar a jugar al TEG ni vos podrías invitarme a mí... ¿o me equivoco? ¿a eso te referías con que no podemos recibir peticiones externas?

Prometo que no te molesto más,
Mil gracias.

---

### Post by margori on 2007-11-07
Asi es ambos estamos atras de una pared :(

Seria bueno que exista un servidor publico de partidas TEG, pero no he encontrado nada aun.

Por las molestias, por favor, no es ninguna. Para eso estoy dando vueltas por este foro, quiero ayudar. Digamos que me muevo con la regla de oro de la convivencia humana "Has a los demas lo que te gustaria que te hagan."

Pero no desistas en buscar la forma de jugar al TEG. Si encuentras una solucion, comentala.

Nos vemos.

---

### Post by margori on 2007-11-08
PUede que me estae equivocando.

Lo pense un poco y me di cuenta que me falta informacion de la forma en que te conectas a la red.

Si tienes un router y ese router es el que te da la IP 10.50.x.x, entonces lo que tienes que hacer es configurar el router para que los paquetes que llegan a la IP del router 190.x.x.x puerto 2000 (o el que elijas para que reciba el servidor TEG) sean retransmitidos al IP 10.x.x.x puerto 2000.

---

### Post by elaleph on 2007-11-08
Pero no tengo router (que yo sepa, en realidad no sé lo que es un router, pero si tuviera alguien me hubiera dicho, supongo), se trata de un PC conectado directamente a Internet por cable. Creo que debe ser el caso que mencionabas antes, el de un servicio que te asigna una IP privada. 

Mi conexión es de Gigared. Debe ser la misma razón por la que no puedo usar ningún tipo de P2P (amule, bittorrent, etc.)

---

### Post by Mauro22 on 2007-11-08
Si vos directamente salis a internet sin ningun tipo de router switch y todo eso, seguro que "Gigared" tiene algun tipo de proxy que te bloquea algunos puertos...

Supongo que un llamado a atencion al cliente deberia solucionarlo, pidendo que te abran X puerto.


Que opinan:confused:

---

### Post by margori on 2007-11-11
La solucion para el problema de TEG y los benditos puertos es Hamachi.

Este programa crea rapidamente una VPN utilizando un servidor propio de Hamachi.

Tambien puede ser la solucion para muchos juegos en red, aunque todos los clientes tendran un lag bastante grande.

Lo he probado con Starcraft y la verdad es imposible jugar, pero se conecta facilmente.

---

### Post by leo_rockway on 2007-11-11
> **margori said:**
> La solucion para el problema de TEG y los benditos puertos es Hamachi.

Este programa crea rapidamente una VPN utilizando un servidor propio de Hamachi.

Tambien puede ser la solucion para muchos juegos en red, aunque todos los clientes tendran un lag bastante grande.

Lo he probado con Starcraft y la verdad es imposible jugar, pero se conecta facilmente.

Fue lo que yo recomende desde un principio. El TEG no creo que necesite de mucho ancho de banda...

---

### Post by margori on 2007-11-25
Por fin logre hacer andar a Don Hamachi en Ubuntu. No funciona cuando se tiene una instalación estandar de Ubuntu.

La solucion la encontre en este foro [http://forums.hamachi.cc/viewtopic.php?t=16174&highlight=upx](http://forums.hamachi.cc/viewtopic.php?t=16174&highlight=upx)

La diferencia de que funcione o no esta en instalar el paquete upx-upx-ucl-beta, aunque creo que tambien funciona con el paquete upx-ucl.

Por otro lado, no lo he confirmado, pero parece que no son compatibles TEGNet de Windows y Tenes Empanads Graciela de Linux.

Por otro lado más, parece que hamachi no es muy estable se se realiza la conexion de computadoras con ISP que filtran protocolos o puertos.

Eso es lo que averigue hasta ahora. Espero sirva. Nos vemos.

---

### Post by Fernando100%TEG on 2009-01-12
Necesito ayuda!!! :(

---

### Post by Fernando100%TEG on 2009-01-12
nose como jugar al TEG ONLINE alguien me explica?? porfabor ayudenmeee!!!!:confused:

---

### Post by Hei Ku on 2009-01-12
Si pones un poco mas de detalle a tu pedido, capaz podamos ayudarte.

---

### Post by aledruetta on 2010-01-10
¿Y alguien consiguió jugar al TEG online? Que cuente cómo lo hizo.

---

### Post by guillermolisi on 2010-01-10
> **alojarteya said:**
> hola mmm alguna de mis dudas es que mi routeer tiene una ip del tipo 10.0.1.x ysegun lo que lei es que del tipo 192.168.0.xx se adquiere mas seguridad en funcin de entrada de intrusos, y no hablo de virus sino de persones de mal proceder. siendo que creo que seme estan metiendo en mis conexiones. el pasarme de ip me dara mas seguridad. gracias por responderme un abrazo
Movido a un thread aparte, en la seccion Software, porque para este es OT.

---

### Post by ereinoso1982 on 2010-06-15
Hola gente, quiero jugar al TEG gciela y tengo windows ¿se puede? como se puede hacer?

---

