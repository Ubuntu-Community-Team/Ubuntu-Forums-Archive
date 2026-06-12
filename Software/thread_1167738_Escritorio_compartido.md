---
title: "Escritorio compartido"
date: 2009-05-22
forum: Software
---

### Post by aledruetta on 2009-05-22
Hola KaKus y Hei Ku,

Me sumo al hilo. Estoy con el mismo problema que "greynand". Tengo una portátil Acer 4310 con Ubuntu Jaunty, conectada por medio de wifi a un router TP-Link modelo TL-WR542G. 

Soy profesor de lenguas, y a veces doy clases en línea. Antes, cuando tenía instalado Windows, usaba Microsoft SharedView para compartir el escritorio con mis alumnos y, la verdad que estoy extrañando la sencillez del procedimiento.

Los equipos y formas de conexión de mis alumnos son muy diversas y, muchas veces, directamente, no se cuál es la configuración.

He intentado con el Cliente de Terminal Server, el Visor de Escritorios Remotos, instalé FreeNX y NoMachine NX, pero nunca conseguí una conexión. Obviamente, esto se debe a mi falta de conocimientos en la materia y no al sistema ni a las aplicaciones que deben ser tanto o más buenas que la de Microsoft.

Incluso, instalé VirtualBox y virtualicé un XP con el Microsoft SharedView, y no es posible la conexión. No sé si es que Ubuntu cierra algún puerto que la aplicación precisa para comunicarse o qué. La cuestión es que no estoy dando "pié con bola".

Ojalá Ustedes, o cualquier ubuntero que se "pele" con estas cuestiones, me pueda dar una mano.

Saludos y gracias,
Alejandro.

---

### Post by biale on 2009-05-22
En principio para acceder en forma gráfica al escritorio de otra máquina solo habría que tener en cuenta tres cosas. (1) Una tiene que estar corriendo un servicio especial (VNC o sus derivados, por ejemplo). (2) La máquina desde donde yo accedo un cliente compatible (vncviewer, por ejemplo) y (3) Se necesita "Una red limpia" entre ambas. Si ese es el caso informo la dirección de IP y  el port de la máquina a la que voy a acceder, luego la clave especial del servicio si la tiene y listo el pollo.

Y aqui comienzan los problemas porque las redes aportan todas las complicaciones. El caso mas sencillo se da cuando ambas computadoras se encuentran en la misma red local, diría una al lado de la otra. Y aún en este caso se requiere que la computadora "servidora" tenga habilitado el port específico (el port default de VNC es el 5900).

Si el acceso se hace vía internet, hay que validar dos condiciones mas. (1) Tenemos que conocer la dirección de IP flotante de la máquina a la cual queremos acceder o estar en condiciones de resolver su nombre. y (2) atención que los "modems" de red, routers, etc no esten filtrando el port (5900) por razones elementales de seguridad. Incluso los ISP también podrían estar filtrando el port, en este último caso por otras razones que nada tienen que ver con la seguridad.

Para ajustar conocimientos y habilidades lo mejor es arrancar con dos computadoras conectadas a la misma red local. Salvo algún caso especial y si la máquina a la que voy a acceder es WXP todo tendría que salir andando de una.

Y si aparecen problemas hay que usar algunas herramientas. Por ejemplo para averiguar si el servidor de escritorio remoto tiene abierto el port (firewall local) pueden usar "Zenmap" bajo Linux o "superscan" bajo windows. 

Aclaro que acceder teniendo la internet entre medio es algo que nunca hice. Esperando la perorata sea de alguna ayuda y poco embrollo saludo a todos.

---

### Post by aledruetta on 2009-05-22
Biale,

Gracias por tu respuesta.

La verdad, es que me dan ganas de salir corriendo. Pero voy a tratar de tener un umbral de tolerancia a la frustración que me permita seguir intentando. Imaginate que antes, era cuestión de colocar mi dirección de hotmail, la contraseña; del otro lado hacían lo mismo, y ya estaba, no había que hacer otra cosa. Ahora, si tengo que averiguar todo esto y resolverlo para cada caso en particular que me presenten mis alumnos, creo que voy a terminar loco, o hacker (o hacker loco). 

A ver si me podés ayudar un poco más.
Te doy la que podría ser una situación de prueba para ir empezando a manejar el procedimiento:

Tengo dos portátiles conectadas a internet por medio del router que antes mencioné. Las dos están conectadas vía wifi con ese router.

¿Qué hago para que se pueda compartir el escritorio entre esos dos equipos?

Saludos, nuevamente,
Alejandro.

---

### Post by biale on 2009-05-22
Alejandro: 

La perorata trata de considerar que hay muchos casos posibles y para seguir adelante tendríamos que precisar dos cosas. Primero que Sistema operativo usan tus alumnos (Linux? WXP?) y segundo si las computadoras estan en la misma aula, o sea en red local.

Suponiendo que estemos en la misma aula y que tus alumnos usen Windows, tendran que instalar un módulo ("programa gratuito") para servicio de escritorio remoto. "Real Vnc", "Ultra Vnc"... 

Abajo y la derecha les va a aparecer "un ojito" o las siglas de VNC. Apuntando el mouse sobre el icono les aparecera la famosa dirección de IP.

En tu Linux, arrancas el visor de escritorio remotos, ingresas "esa" dirección de IP que un alummno te haya dicho y listo. 

Algunas veces he tenido que acomodar la firewall de Windows estableciendo a mano una excepción para VNC. Y aclaro que con accesos "Windows a Windows". Esperemos no caer en este caso

Ahora bien, si vas a dar soporte desde tu casa al aula, hay que tener en cuenta varias cosas mas. Por ejemplo, yo no podría conectarme desde mi casa a mi trabajo, porque por razones de seguridad esta previsto que no se pueda hacer.

El caso hotmail (MSN) es un tanto especial, y así son los problemas que tiene!. Es cierto que se pueden transferir archivos pero no tengo claro que se pueda acceder en forma completa al escritorio de otra computadora (?)

Saludos!

---

### Post by biale on 2009-05-22
Alejandro: 

La perorata trata de considerar que hay muchos casos posibles y para seguir adelante tendríamos que precisar dos cosas. Primero que Sistema operativo usan tus alumnos (Linux? WXP?) y segundo si las computadoras estan en la misma aula, o sea en red local.

Suponiendo que estemos en la misma aula y que tus alumnos usen Windows, tendran que instalar un módulo ("programa gratuito") para servicio de escritorio remoto. "Real Vnc", "Ultra Vnc"... 

Abajo y la derecha les va a aparecer "un ojito" o las siglas de VNC. Apuntando el mouse sobre el icono les aparecera la famosa dirección de IP.

En tu Linux, arrancas el visor de escritorio remotos, ingresas "esa" dirección de IP que un alummno te haya dicho y listo. 

Algunas veces he tenido que acomodar la firewall de Windows estableciendo a mano una excepción para VNC. Y aclaro que con accesos "Windows a Windows". Esperemos no caer en este caso

Ahora bien, si vas a dar soporte desde tu casa al aula, hay que tener en cuenta varias cosas mas. Por ejemplo, yo no podría conectarme desde mi casa a mi trabajo, porque por razones de seguridad esta previsto que no se pueda hacer.

El caso hotmail (MSN) es un tanto especial, y así son los problemas que tiene!. Es cierto que se pueden transferir archivos pero no tengo claro que se pueda acceder en forma completa al escritorio de otra computadora (?)

Saludos!

---

### Post by KaKuS on 2009-05-23
Como que desvirtuaron el post, una cosa es un entorno compartido de trabajo y otra distinta es un escritorio remoto. Uno esta apuntado a realizar una tarea en conjunto y la otra a usar un equipo a distancia.

Sigo el tema en privado con greynand

Saludos

---

### Post by Hei Ku on 2009-05-23
Movido a un thread aparte, porque los temas se resuelven de manera distinta.

---

### Post by aledruetta on 2009-05-23
Pido perdón, pero como entiendo poco del tema, ni siquiera me doy cuenta de qué cosa estoy desvirtuando.

Respecto a la pregunta de Biale. Doy clases en línea, es decir, desde mi casa le doy clases a alguien en su casa. Hasta donde yo sé, ninguno de ellos está usando Linux. Algunos tienen XP y otros Vista; algunos tienen portátil otros PC de escritorio; algunos se conectan por modem, otros ADSL, otros... vaya a saber cómo.

Ese es el problema, y entiendo que es una situación difícil y poco corriente.

Con la aplicación que usaba antes en Windows (Microsoft ShareView) podía compartir mi escritorio y las aplicaciones que estaba usando en él, inclusive, darle el control a la otra persona, o viseversa, era la otra persona la que me daba el control de su escritorio y sus aplicaciones a mí. De esa maner, sumado a Skype, armábamos un ambiente colaborativo y desarrollábamos la clase, con textos, slides, videos, etc. Con esa aplicación, lo único que necesitaba era crear una sesión con mi dirección de Hotmail y punto. No necesitaba saber nada del equipo de mi alumno, ni -que es lo que más me preocupa- tener que explicarle a esta persona como abrir los puertos del firewall, del router, etc., etc.

Ahora que migré a Ubuntu, quedé aislado. Estoy buscando algún procedimiento para resolver este problema. Por eso, en principio, me gustaría poder experimentar con las dos portátiles que tengo en casa, a ver si al menos logro que se comuniquen entre ellas.

Instalé, en la mía, que tiene Ubuntu: freeNX + Nomachine NX node y cliente; en la otra, que tiene Vista, instalé el cliente de Nomachine NX. Estuve leyendo varios blogs donde se dice que la tecnología NX es superior a la de VNC, por eso opté por NX.

Les recuerdo que esas portátiles están en conexión wifi con el router que, a su vez, está conectado al cablemodem del servicio de Internet.

No sé si alcanzo a ser claro en lo que pretendo lograr. Cualquier cosa, me dicen qué datos están faltando.

Saludos y muchas gracias,
Alejandro.

---

### Post by guillermolisi on 2009-05-23
> **aledruetta said:**
> Pido perdón, pero como entiendo poco del tema, ni siquiera me doy cuenta de qué cosa estoy desvirtuando.

Respecto a la pregunta de Biale. Doy clases en línea, es decir, desde mi casa le doy clases a alguien en su casa. Hasta donde yo sé, ninguno de ellos está usando Linux. Algunos tienen XP y otros Vista; algunos tienen portátil otros PC de escritorio; algunos se conectan por modem, otros ADSL, otros... vaya a saber cómo.

Ese es el problema, y entiendo que es una situación difícil y poco corriente.

Con la aplicación que usaba antes en Windows (Microsoft ShareView) podía compartir mi escritorio y las aplicaciones que estaba usando en él, inclusive, darle el control a la otra persona, o viseversa, era la otra persona la que me daba el control de su escritorio y sus aplicaciones a mí. De esa maner, sumado a Skype, armábamos un ambiente colaborativo y desarrollábamos la clase, con textos, slides, videos, etc. Con esa aplicación, lo único que necesitaba era crear una sesión con mi dirección de Hotmail y punto. No necesitaba saber nada del equipo de mi alumno, ni -que es lo que más me preocupa- tener que explicarle a esta persona como abrir los puertos del firewall, del router, etc., etc.

Ahora que migré a Ubuntu, quedé aislado. Estoy buscando algún procedimiento para resolver este problema. Por eso, en principio, me gustaría poder experimentar con las dos portátiles que tengo en casa, a ver si al menos logro que se comuniquen entre ellas.

Instalé, en la mía, que tiene Ubuntu: freeNX + Nomachine NX node y cliente; en la otra, que tiene Vista, instalé el cliente de Nomachine NX. Estuve leyendo varios blogs donde se dice que la tecnología NX es superior a la de VNC, por eso opté por NX.

Les recuerdo que esas portátiles están en conexión wifi con el router que, a su vez, está conectado al cablemodem del servicio de Internet.

No sé si alcanzo a ser claro en lo que pretendo lograr. Cualquier cosa, me dicen qué datos están faltando.

Saludos y muchas gracias,
Alejandro.
Para mi esta claro y segun entiendo lo que pareceria adecuado es LTSP - Light Terminal Server Project ( [http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/ltsp](http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/ltsp) )

Igual, las alternativas con VNC me parecen validas.

---

### Post by gmunioz on 2009-05-23
Hola ald....:

Interesante labor docente la tuya.

Microsoft ShareView, es una herramienta perteneciente a la suite de

Microsoft Office 2007, mediante ella se puede compartir un documento de 

cualquier aplicación de la suite con un máximo de hasta 15 usuarios como 

así tambien se pueden visualizar en tiempo real los cambios o información 

que se está agregando en ese mismo momento por cada diferente usuario.

Permite además, no solamente compartir los archivos, con acciones 

individuales, es decir que solo una persona tenga el control, si no que 

cada quien puede trabajar en el documento independientemente de sus 

herramientas y su puntero, de manera que el administrador de la sesión 

transfiere el control a un usuario que será quien tenga el control real 

del documento original, mientras los demás pueden continuar con el mismo 

documento editándolo de diferente forma. 

Esta aplicación tiene que ser instalada en todas las PC’s que lo vayan a 

usar con la cual se debe iniciar sesión con alguna de las cuentas de 

Windows Live ID. 



Lo único que conozco que se le parece , es Moodle, que es un sistema de 

gestión de cursos, de distribución libre, destinado a los educadores que 

desean crear comunidades de aprendizaje en línea. 

Moodle es una aplicación web que se ejecuta sin modificaciones en Unix, 

GNU/Linux, OpenSolaris, FreeBSD, Windows, Mac OS X, NetWare y otros 

sistemas que soportan PHP.

Moodle soporta un rango de mecanismos de autenticación a través de 

módulos, que permiten una integración sencilla con los sistemas 

existentes.

Las características principales incluyen:

Método estándar de alta por correo electrónico: los estudiantes pueden 

crear sus propias cuentas de acceso. La dirección de correo electrónico 

se verifica mediante confirmación.

Método LDAP: las cuentas de acceso pueden verificarse en un servidor 

LDAP. El administrador puede especificar qué campos usar.

IMAP, POP3, NNTP: las cuentas de acceso se verifican contra un servidor 

de correo o de noticias (news). Soporta los certificados SSL y TLS.

Base de datos externa: Cualquier base de datos que contenga al menos dos 

campos puede usarse como fuente externa de autenticación.

Cada persona necesita sólo una cuenta para todo el servidor. Por otra 

parte, cada cuenta puede tener diferentes tipos de acceso. Con una cuenta 

de administrador que controla la creación de cursos y determina los 

profesores, asignando usuarios a los cursos.

Este es su sitio

[http://download.moodle.org/](http://download.moodle.org/)

Aqui un listado de tutoriales respecto de instalacion y uso

[http://www.google.com.ar/search?hl=es&q=moodle+tutorial&btnG=Buscar&meta=lr%3Dlang_es](http://www.google.com.ar/search?hl=es&q=moodle+tutorial&btnG=Buscar&meta=lr%3Dlang_es)

Suerte con tu tarea.

---

### Post by aledruetta on 2009-05-25
Hola gmunioz,

Puede que me esté equivocando, pero hay una aplicación de Office que es OfficeLive, que responde mucho a la descripción que vos hiciste. La aplicación que yo mencioné, Microsoft SharedView, creería que no es una aplicación de Office. Lo que hace es compartir el escritorio y cualquier aplicación que se esté ejecutando en él. 

Por ejemplo, en estos días estoy haciendo un cursito de Flash. Yo estoy viviendo en Sao Paulo, Brasil, y mi hermana y mi cuñado en Santa Fe, Argentina. Entonces yo les estaba pasando lo que aprendía por medio de esa aplicación. Es decir ellos veían en mi escritorio, la ventana de Macromedia, yo les mostraba los pasos a seguir, si ellos querían me pedían el control y eran ellos los que actuaban sobre la aplicación, etc. Lo mismo podía hacer sobre cualquier aplicación.

Con mis alumnos empleaba, por ejemplo, Power Point, Rosetta Stone, diccionarios como el Ultralingua, el de la RAE, textos en Word, les mostraba, ejemplificando en mi escritorio, cómo activar alguna opción o instalar una aplicación. Inclusive, si ellos me dan el control de su escritorio, se las instalo yo ¿Se entiende? No es simplemente escritura colaborativa, cosa que podría resolverlo perfectamente con Google Docs.

Ahora, en Ubuntu, se me complicó la cosa. Creo, por lo que voy viendo hasta ahora, que implementar la tecnología VNC o NX, no va a ser factible, ya que requeriría adaptarla a cada situación concreta que me presenta cada alumno, cosa que varía permanentemente.

Creo que lo ideal sería, lograr que el Microsoft SharedView funcione por medio de Wine o del XP que virtualicé con VirtualBox. Hasta ahora no lo conseguí.

Saludos y muchas gracias,
Alejandro.

---

