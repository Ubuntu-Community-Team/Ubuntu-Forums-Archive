---
title: "[SOLVED] Conectar al servidor"
date: 2007-08-12
forum: Software
---

### Post by Vero1 on 2007-08-12
Hola de nuevo,
Mi segundo problema es la conexión con el Servidor.
Debo haberme equivocado al configurar algo porque cuando quiero conectarme a Internet o a Nautilus, me dice que no encuentra al Servidor o al Host.
Al comprobar el error dice: Internet PAP authentication failed y se corta la presunta comunicación.
Mi Servidor de Speedy.com.ar. Tengo DSL.
Desmarqué la opción DHCP y le puse dirección IP, máscara de subred y puerta de enlace, pero sigue sin funcionar.
Alguien puede darme una mano?

Gracias:)

---

### Post by Mauro22 on 2007-08-12
Como estas conectado?

A traves de una red, con un modem directamente ?


Salu2

---

### Post by Vero1 on 2007-08-12
Hola Mauro22,

Me conecto a través de un modem-router DSL Arescom 1000 pero llamando a Speedy.com.ar o sea, por ejemplo en XP tengo el ícono de Speedy en el escritorio, le hago click y me conecta.
Aclaro que en XP mi IP es dinámica.

No sé si estos datos son suficientes.

Gracias de nuevo.

---

### Post by Mauro22 on 2007-08-12
Si tienes un modem-router, te tendrias que conectar por placa de red. y en ese caso no hace falta marcar ninguna conexion.


Lo que tienes no sera un modem USB?

---

### Post by Vero1 on 2007-08-12
No, tengo placa de red.
Tengo Ethernet.

---

### Post by rojojuan on 2007-08-12
Probá cerrando y apagando todo, inlcuso el modem. Iniciá con Ubuntu a ver que pasa; es probable que el modem quede con la configuración anterior.

---

### Post by Vero1 on 2007-08-12
ok rojojuan, probaré.
Lo único que no me queda claro es si no es necesario configurar nada para conectarme.
Informaré.

Gracias.

---

### Post by rojojuan on 2007-08-13
No tenés que tocar nada. Simplemente arrancá con todo apagado.


> **Vero1 said:**
> ok rojojuan, probaré.
Lo único que no me queda claro es si no es necesario configurar nada para conectarme.
Informaré.

Gracias.

---

### Post by faktorqm on 2007-08-13
Hola a todos. Desmitifiquemos un poco: los modems adsl por lo general tienen 2 modos de configuracion, puente, y router. INDEPENDIENTEMENTE de si la conexion a la pc es ethenet o usb. 
Cuando vino el hippie de speedy a mi casa conectó por ethernet y usó un cliente pppoe como marcador para conectarse.
Ahora bien, cual es la onda de configurarlo en modo router? la movida es que el modem se conecta directamente, en lugar de usar un cliente vos. Se entiende? En vez de tener que usar un icono para conectarte cada vez que reinicias directamente con dhcp configuras para que levante internet "derecho".
Como se hace esto es tu pregunta?

[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=135&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=135&root=132)

Guia de speedy, asi que mejor imposible. Contame como te fue. Salu2!

---

### Post by Vero1 on 2007-08-14
Hola de nuevo,
Agradezco tu link. Te diré que en una oportunidad anterior traté de seguir las instrucciones de Speedy pero sin éxito.
El router quedó en modo Bridge y no hubo forma.
Lo que debe suceder es que en Speedy tengo IP dínámica y cuando le quiero poner IP fija con todas las direcciones, inclusive DNS, Speedy lo rechaza. Es cierto que eso me pasó con Windows.
Quise hacer el cambio no a Bridge para poder usar Modo Seguro con Red y me fue imposible.
Tal vez, probando con Ubuntu me pueda salir. 
Voy a tener que imprimir en Windows las instrucciones.
Oportunamente te informaré.
Gracias de nuevo.

saludos

---

### Post by Vero1 on 2007-08-20
> **Vero1 said:**
> Hola de nuevo,
Agradezco tu link. Te diré que en una oportunidad anterior traté de seguir las instrucciones de Speedy pero sin éxito.
El router quedó en modo Bridge y no hubo forma.
Lo que debe suceder es que en Speedy tengo IP dínámica y cuando le quiero poner IP fija con todas las direcciones, inclusive DNS, Speedy lo rechaza. Es cierto que eso me pasó con Windows.
Quise hacer el cambio no a Bridge para poder usar Modo Seguro con Red y me fue imposible.
Tal vez, probando con Ubuntu me pueda salir. 
Voy a tener que imprimir en Windows las instrucciones.
Oportunamente te informaré.
Gracias de nuevo.

saludos

Hola de nuevo,
Lamentablemente las instrucciones de Speedy, en lo que a DSL se refiere, son para Mandrake y no para Feisty que es el que tengo.
No tengo forma de conectarme a Internet, haga lo que haga.
El router-bridge que tengo y que ahora trabaja como bridge, no se puede convertir en router porque Speedy no acepta IP fija y con dhcp tampoco funciona.
Tenés alguna idea mas de lo que puedo hacer?

Gracias y saludos

---

### Post by Vero1 on 2007-08-20
> **rojojuan said:**
> No tenés que tocar nada. Simplemente arrancá con todo apagado.

Hola rojojuan,

No tuvo éxito.

saludos

---

### Post by faktorqm on 2007-08-20
we, tengo varias preguntas ke hacerte:

1) el modem lo usas por cable ethernet no? (NO POR USB)
2) en windows usabas el marcador para conectarte?, no es que prendias la pc y ya estabas conectada. por lo tanto, necesitas lo mismo para linux. Ahora bien, es mejor conectaro en modo router y olvidarte del problema.
3) proba de entrar por telnet al router, escribiendo en una consola "etlnet ip_del_router". ejemplo: telnet 192.168.0.1

salu2!!

---

### Post by Vero1 on 2007-08-21
Hola factorqm y gracias por tenerme paciencia.

El modem está conectado a la Tarjeta de Red.
En Windows tengo el ícono de Speedy en el escritorio, donde hay que hacer click y te sale la pantallita para pedir conexión. Marcar nada de nada porque tengo Banda Ancha.
Imposible en modo router ya que no se puede cambiar. Ahora está en bridge y no permite el cambio, aun metiéndome en el DSL Manager.
Por eso traté de usar la opción de Configurar ADSL para Linux pero las instrucciones vienen para Mandrake, no para Feisty.
Probaré lo que indicas pero habrá que copiar todo lo que dice porque ni siquiera me funciona la impresora por falta de controlador, que tendría que bajar por Internet...
Lindo no?
Bueno, despues te diré lo que dice telnet.
Una última cosa, el número de IP que me indicas, lo tengo como Puerta de Enlace. Está bien?

muchas gracias

---

### Post by Vero1 on 2007-08-21
> **Vero1 said:**
> Hola factorqm y gracias por tenerme paciencia.

El modem está conectado a la Tarjeta de Red.
En Windows tengo el ícono de Speedy en el escritorio, donde hay que hacer click y te sale la pantallita para pedir conexión. Marcar nada de nada porque tengo Banda Ancha.
Imposible en modo router ya que no se puede cambiar. Ahora está en bridge y no permite el cambio, aun metiéndome en el DSL Manager.
Por eso traté de usar la opción de Configurar ADSL para Linux pero las instrucciones vienen para Mandrake, no para Feisty.
Probaré lo que indicas pero habrá que copiar todo lo que dice porque ni siquiera me funciona la impresora por falta de controlador, que tendría que bajar por Internet...
Lindo no?
Bueno, despues te diré lo que dice telnet.
Una última cosa, el número de IP que me indicas, lo tengo como Puerta de Enlace. Está bien?

muchas gracias

Acabo de probar Telnet y me dice NO CONECTADO?????

---

### Post by faktorqm on 2007-08-21
Hola, bueno, tenes el modem con ethernet. HAsta ahi vamos bien.
Lo que yo llamo "marcar" es lo mismo a lo que vos llamas "hacer doble click en el iconito de speedy y esperar a que te diga conectado". Asi que hasta ahi tambíen estamos bien. 
Que tengas la ip del router como puerta de enlace, eso tambien es correcto.
Lo que me llama la atencion es lo del dsl manager, yo suspuse desde el vamos que algo no andaba, por eso te dije lo del telnet.
Bueno, hagamos una cosa, si configuras el router en modo router, desde linux o windows es lo mismo. Si en windows tenes internet, PARA HABILITAR EL MODO ROUTER _NO_ TENES QUE ESTAR CONECTADA CON EL ICONITO DE SPEEDY. y ahi le das al dsl manager con el tutorial de speedy (que hace 5 minutos tuviste la viveza de grabar en el disco.... xDxDxDxD :D:D:D) y paso a paso y trankila le das.
S te sirve, resetea el router, y pone tu pc en windows, y ponele a la conexion dhcp. Anda a inicio -> ejecutar, escribi "cmd" (sin comillas) y ahi te abre una pantalla negra. escribis "ipconfig /all" (sin comillas) y te fijas el ip de la puerta de enlace. ahi tirale un telnet, sino entra, proba con el dsl manager y el tuto al lado. no te puede no-funcionar. presta atencion, y hacelo trankila, que vos podes ;) Salu2!!:popcorn:

---

### Post by Vero1 on 2007-08-22
:( Hola,
Fracaso total. No vá.
Te digo lo que hice:
Cambié la configuración de TCP/IP poniendo los valores correspondientes y acepté.
Me desconecté de Speedy, corrí el DSLManager y me dice que NO encuentra ningun router/bridge.
Tambien corrí ipconfig /all y lo de LAN está todo como lo configuré pero ni conecta ni se reconoce.
No sé qué más puedo hacer...

saludos

---

### Post by Vero1 on 2007-08-22
> **Vero1 said:**
> :( Hola,
Fracaso total. No vá.
Te digo lo que hice:
Cambié la configuración de TCP/IP poniendo los valores correspondientes y acepté.
Me desconecté de Speedy, corrí el DSLManager y me dice que NO encuentra ningun router/bridge.
Tambien corrí ipconfig /all y lo de LAN está todo como lo configuré pero ni conecta ni se reconoce.
No sé qué más puedo hacer...

saludos

ah, y Telnet sigue diciendo NO CONECTADO:mad:

---

### Post by faktorqm on 2007-08-22
1) no t des x vencida
2) Qué configuración pusiste?

mira, te cuento como sería una configuración típica.

en tu pc sería:

ip: 192.168.1.2
mascara de subred: 255.255.255.0
puerta de enlace: 192.168.1.1

el ip de la puerta de enlace debe ser igual que el ip del router.
por lo tanto tu router tendria que ser:

ip: 192.168.1.1
mascara: 255.255.255.0

Bue, siguiendo con esto, alguna manera de entrar en la configuracion debe haber, por web, por ftp, por telnet o con el programa ese feo. sino mira, llama a los de speedy y que te guien ellos con el dsl manager, deciles que no lo podes configurar con el tutorial Q ELLOS MISMOS SUBIERON a internet, una vez que puedas, el resto es historia. salu2!

EDITO:

Vos leiste no el tuto de los de speedy?!? te lo pego por las dudas:

 PASOS PREVIOS

    * Su PC deberá tener configurado un IP comprendido entre los valores 192.168.1.2 y 192.168.1.254, con máscara de red 255.255.255.0
    * Si bien para el proceso de configuración no es necesario tener definida una puerta de enlace predeterminada, ni DNS primario, ni DNS secundario, estos parámetros serán necesarios en el momento de intentar utilizar internet con el módem configurado como router.

despues te manda a unos links por si no sabes configurar el ip en tu computadora con windows, y te lo explica para 3 versiones. supongo que te vas a portar bien y lo vas a leer y a seguir al pie de la letra no? ^_^ xD salu2!!

---

### Post by Vero1 on 2007-08-22
Hay algo que no entiendo. Decis que la configuración debe ser la misma tanto en Windows como en el router, pero me ponés 192.168.1.2 para la PC y 192.168.1.1 para el router???? Es así?

A los de Speedy los he llamado ya cuando quise hacer el cambio a router hace un tiempo y lo que me dijeron fue que ellos NO dan soporte para el módem. Que pida ayuda a un técnico particular. Qué tal?
Y no es que no lo puedo configurar, directamente no me deja entrar porque no reconoce el bridge/router y eso que bajé una versión mas nueva de la que tengo en el CD que me entregaron cuando todavía tenía USB, que es la versión 5.2.
La versión que bajé de Internet es 5.6.
Sí leí lo de Speedy e inclusive imprimí todo.
Despues de cenar voy a probar configurar como vos me decís a ver si tengo suerte. La verdad es que no es nada alentador, pero no me daré por vencida, siempre y cuando me sigas ayudando:)

saludos

---

### Post by faktorqm on 2007-08-22
Hola, obvio que te ayudo, espero que me veas hoy, asi mañana te contesto ya. 
Me entendiste mal creo, yo te dije que la configuracion tienen que ser la misma tanto en windows como en linux, y que tenes que tener cierta concordancia (estar en la misma red) con el router.
Ahora, la IP del router no lo podes cambiar, por que no podes acceder, asi que RESETEA el router, y asegurate de haber apretado el boton correcto para que efectivamente se resetee. 
La ip por defecto del router es 192.168.1.1, por lo tanto tu pc debe tener esta configuracion: (en windows, por que en linux no debe andar el dsl manager, y no lo emules, por que si no no sabes donde esta la falla)

ip: 192.168.1.2
mascara: 255.255.255.0
puerta de enlace: 192.168.1.1
dns: 192.168.1.1

supongo que tenes XP. anda a la consola de xp, (cmd en inicio -> ejecutar)
y pone "ping 192.168.1.1" (sin comillas)
Ahi te tiene que responder SI o SI, sino lo hace me voy a tu casa y dejo el ccna. ;);)
Si no te responde, revisa los cables, desactiva el firewall de xp, los firewalls que tengas instalados, el antivirus, y volve a probar.
Si te responde, entonces lo que pasa es que es la compu ve al router, y le responde lo mas bien. eso es bueno. ahi probas el dsl manager. si no te reconoce nada, proba con otro, que se yo! deberia andar!
suerte con eso, no bajes los brazos! salu2!! :D

p.d.: son unos hijos de re mil ******** estos de speedy, por que te dan ese modem de ********* y soporte para una sola pc, si queres ponerlo en modo router por que sos una persona normal y sabes de computacion, te dan el tutorial y no te dan soporte. gracias telefonica! cada vez te kiero mas.
Encima no se si prestaste atencion, pero en la pagina dice en todos lados que no llames al soporte tecnico por que no te dan soporte, que llames a uno particular si queres modo router. No importa, ojalá haya mucha gente que ayude a otra gente y de a poquito todos sepamos y les vayamos metiendo el dedo en el ****** a esta manga de **********. he dicho. (yo tb tengo speedy :()

---

### Post by Vero1 on 2007-08-23
Hola factorqm,

Raro pero tu respuesta la leí en Google, ya que no me llegó el aviso de e-mail.
Hice la configuración según me indicaste y luego hice ping. Me respondió perfectamentel, pero el DSL Manager sigue sin reconocer el módem.

Desenchufé el cable de plástico blanco y probé otra vez, ya que alguien me había dicho que lo hiciera, pero sin éxito. Ya no sé por donde agarrar.
Voy a ver en Internet si hay un DSL Manager posterior al que tengo y si no hay, voy a llamar a Speedy, les guste o no y les diré lo que estamos penando.

A vos gracias y te tendré al tanto.

saludos:)

---

### Post by Vero1 on 2007-08-23
> **Vero1 said:**
> Hola factorqm,

Raro pero tu respuesta la leí en Google, ya que no me llegó el aviso de e-mail.
Hice la configuración según me indicaste y luego hice ping. Me respondió perfectamentel, pero el DSL Manager sigue sin reconocer el módem.

Desenchufé el cable de plástico blanco y probé otra vez, ya que alguien me había dicho que lo hiciera, pero sin éxito. Ya no sé por donde agarrar.
Voy a ver en Internet si hay un DSL Manager posterior al que tengo y si no hay, voy a llamar a Speedy, les guste o no y les diré lo que estamos penando.

A vos gracias y te tendré al tanto.

saludos:)

Bueno factorqm,
Hablé con Speedy, pero no valió de nada. Siguen insistiendo que consulte a un técnico particular.
Estoy que estallo de la bronca. Me hicieron probar con la dirección en números que conectó con DSL Manager pero oh! surprise, no me acepta el usuario y la contraseña que tengo. O sea...

Ahora, una pregunta: 
No se puede configurar la conexión directamente en Ubuntu, tal como lo hago en Windows?

saludos

---

### Post by por100pre1 on 2007-08-23
> **Vero1 said:**
> Bueno factorqm,
Hablé con Speedy, pero no valió de nada. Siguen insistiendo que consulte a un técnico particular.
Estoy que estallo de la bronca. Me hicieron probar con la dirección en números que conectó con DSL Manager pero oh! surprise, no me acepta el usuario y la contraseña que tengo. O sea...

Ahora, una pregunta: 
No se puede configurar la conexión directamente en Ubuntu, tal como lo hago en Windows?

saludos

En una ventana de terminal copia, pega, dale ENTER a esto:

```
gksu network-admin
```

---

### Post by faktorqm on 2007-08-23
si se puede, pero es mas bardo innecesariamente. mi respuesta en google? no entendi. sali en google yo o viste lo mismo que te escribi yo en otro lado?
bue, pppoeconf es el paquete que tenes que instalar (esta en el cd ;)) y ahi configurar todo. mientras tenes internet en ubuntu, contame, como es eso que no te reconoce el user y el pass? 
los users de speedy por lo general son tu numero de telefono, seguido de arroba seguido de speedy o speedy1m. por lo general, hay otros.
ejemplo: 43879548@speedy
y el password, en el 90% de los casos es 123456, que es el que te dan por defecto cuando te lo instalan. 
ahh y también contame por fa como entraste al dsl manager. salu2!!

---

### Post by Vero1 on 2007-08-23
> **por100pre1 said:**
> En una ventana de terminal copia, pega, dale ENTER a esto:

```
gksu network-admin
```

Muchas gracias. Probaré.

saludos

---

### Post by Vero1 on 2007-08-23
> **faktorqm said:**
> si se puede, pero es mas bardo innecesariamente. mi respuesta en google? no entendi. sali en google yo o viste lo mismo que te escribi yo en otro lado?
bue, pppoeconf es el paquete que tenes que instalar (esta en el cd ;)) y ahi configurar todo. mientras tenes internet en ubuntu, contame, como es eso que no te reconoce el user y el pass? 
los users de speedy por lo general son tu numero de telefono, seguido de arroba seguido de speedy o speedy1m. por lo general, hay otros.
ejemplo: 43879548@speedy
y el password, en el 90% de los casos es 123456, que es el que te dan por defecto cuando te lo instalan. 
ahh y también contame por fa como entraste al dsl manager. salu2!!

Te explico. Buscando en Google DSLManager posterior al que tengo, salieron todos nuestros posts, escritos hasta ahora. (Somos populares ja).
No me reconoce el pass cuando pongo en la Barra de Direcciones el número que me dieron en Speedy para conectarme directamente con el Manager.
NO entré en el Manager ya que no me aceptó el pass.
Voy a probar lo que me recomienda Por siempre 1 y comento. Si no funciona, pruebo lo del CD.

saludos

---

### Post by elrengo79 on 2007-08-23
pppoeconf se instala por defecto, por lo menos en mi pc, ejecutando en consola sudo pppoeconf se lanza el wizard para configurar tu conexion, primero detecta el modem y te pide usuario y contraseña, te pregunta si keres ke se conecte al inicio y listo, conexion configurada ke se marca sola cuando inicias la pc

---

### Post by Vero1 on 2007-08-23
> **Vero1 said:**
> Muchas gracias. Probaré.

saludos

Hola,
Lo hice y me salió la ventana de configuración, pero nada mas.
Era éso?

saludos

---

### Post by Vero1 on 2007-08-23
> **Vero1 said:**
> Te explico. Buscando en Google DSLManager posterior al que tengo, salieron todos nuestros posts, escritos hasta ahora. (Somos populares ja).
No me reconoce el pass cuando pongo en la Barra de Direcciones el número que me dieron en Speedy para conectarme directamente con el Manager.
NO entré en el Manager ya que no me aceptó el pass.
Voy a probar lo que me recomienda Por siempre 1 y comento. Si no funciona, pruebo lo del CD.

saludos

factorqm,
el paquete de pppoeconf  estaba ya  instalado...

sin novedades, seguimos igual:(

saludos

---

### Post by faktorqm on 2007-08-23
si te entiendo lo que pasa, el modem tiene pass, pero el de abrica... si lo reseteaste como te dije......
proba: 1234, 123456, tasatasa, <nada>, admin
son las contraseñas tipicas de esos aparatos. donde dice <nada> le das enter ;) :P salu2!

---

### Post by Vero1 on 2007-08-24
El módem no tiene ningun botón para prender o apagar. Lo hice varias veces y tambien desenchufé y volví a enchufar sus 3 cables.

Los números y demas que me decís, los escribo en una terminal?

salu3:)

---

### Post by Vero1 on 2007-08-24
> **elrengo79 said:**
> pppoeconf se instala por defecto, por lo menos en mi pc, ejecutando en consola sudo pppoeconf se lanza el wizard para configurar tu conexion, primero detecta el modem y te pide usuario y contraseña, te pregunta si keres ke se conecte al inicio y listo, conexion configurada ke se marca sola cuando inicias la pc


Hola elrengo79,

Éso es lo que hice primero pero no funcionó...

---

### Post by Gideon26 on 2007-08-24
Hola que tal recien acabo de leer los post de tu problema, te hago una consulta no probaste entrando por el mozilla al arescom? seria colocar en la barra de direcciones .  [http://192.168.1.1](http://192.168.1.1)   se supone como la mayoria de los router o modem router como el tuyo que deberia cargarte una pantalla que esta escrita en html como cualquier pagina y te permitiria por alli configurar el modem. intentalo y me cuentas. En cuanto a la clave de arescom 1000 la clave de fabrica es atc123 esa es la que trae de fabrica [http://www.esnips.com/nsdoc/554a2070-b0b4-41cd-8dbe-20044d72b7d7/?action=forceDL](http://www.esnips.com/nsdoc/554a2070-b0b4-41cd-8dbe-20044d72b7d7/?action=forceDL)
en esa pagina tengo puesto el manual de ese modem por si te sirve

---

### Post by Vero1 on 2007-08-24
> **elrengo79 said:**
> pppoeconf se instala por defecto, por lo menos en mi pc, ejecutando en consola sudo pppoeconf se lanza el wizard para configurar tu conexion, primero detecta el modem y te pide usuario y contraseña, te pregunta si keres ke se conecte al inicio y listo, conexion configurada ke se marca sola cuando inicias la pc

Hola de nuevo,
Acabo de probar otra vez. Salieron todas las ventanas con las preguntas. Terminé de configurar todo y luego puse plog para ver el estado.

Sale un error: PAP authentication failed. Connection terminated.

Qué puede ser?

Gracias y saludos.

---

### Post by faktorqm on 2007-08-25
Fijate en el tipo de autenticacion, debe tener 2, CHAP y PAP. revisa eso. que bueno que pudiste!! salu4! :P

---

### Post by Vero1 on 2007-08-25
> **Gideon26 said:**
> Hola que tal recien acabo de leer los post de tu problema, te hago una consulta no probaste entrando por el mozilla al arescom? seria colocar en la barra de direcciones .  [http://192.168.1.1](http://192.168.1.1)   se supone como la mayoria de los router o modem router como el tuyo que deberia cargarte una pantalla que esta escrita en html como cualquier pagina y te permitiria por alli configurar el modem. intentalo y me cuentas. En cuanto a la clave de arescom 1000 la clave de fabrica es atc123 esa es la que trae de fabrica [http://www.esnips.com/nsdoc/554a2070-b0b4-41cd-8dbe-20044d72b7d7/?action=forceDL](http://www.esnips.com/nsdoc/554a2070-b0b4-41cd-8dbe-20044d72b7d7/?action=forceDL)
en esa pagina tengo puesto el manual de ese modem por si te sirve

Hola Gideon26 y gracias por interesarte en mi problemón:(
Lo malo es que cualquier cosa que escriba en la Barra de Direcciones de Mozilla me dice que no puede encontrar al servidor. Lo de la clave de fábrica lo sabía, gracias.

De todas formas lo intentaré una vez mas.

saludos

---

### Post by Vero1 on 2007-08-25
> **faktorqm said:**
> Fijate en el tipo de autenticacion, debe tener 2, CHAP y PAP. revisa eso. que bueno que pudiste!! salu4! :P

Me fijaría pero donde?
Si me dijeras, sería una gran cosa faktorqm:)

salud-os

---

### Post by faktorqm on 2007-08-25
hola, perdoname, es que en realidad estaba en otro lado, y supuestamente no podia escribir mucho.
En el tutorial de speedy, en la parte que tiene una ventana que dice "PPP Configuration", ahi tenes un combobox que se llama "Authentication type". No está mal que esté en automático, (yo lo tengo asi) pero si no lo tenés en automático, ponelo. si lo tenes en CHAP, ponelo en PAP. 
Otra cosa, si te dice que no te conecta, en esta misma ventana, pusiste bien tu nombre de usuario y contraseña? te fijaste que sean identicos a los que vos tenes en el iconito en windows? Sino estas segura, podes llamar a tus amigos de speedy :lolflag:
Bueno, dentro de todo fuimos progresando.
Lo que te dijo Gideon26 es lo que pasa en los modem/routers normales, pero hay que tener un solo cuidado, hay que asegurarse que la puerta de enlace y el dns este seteado en el mismo ip que el modem. es decir, la puerta de enlace debe ser 192.168.1.1, el dns primario debe ser 192.168.1.1 y el ip del modem debe ser tambien 192.168.1.1, todo con mascara 255.255.255.0.
Yo no pude entrar al link que dejaste vos, me pide usuario y contraseña :( capaz soy yo... no sé.
Acá te dejo el link de uno que encontre yo que esta lindo y en castellano.

[http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf](http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf)

MIRROR:

[http://rapidshare.com/files/51313801/Instalacion_Modem_Arescom_1000.pdf](http://rapidshare.com/files/51313801/Instalacion_Modem_Arescom_1000.pdf)

Bue, el manual no lei, si encuentro algo que te sirva te lo comento. Es sabado y son las 11pm:guitar:. salu2!!

---

### Post by Hei Ku on 2007-08-26
me parece que el dns primario deberia ser un dns de speedy, y no el router. Seria raro que el router tuviera un servidor dns incorporado.
Aunque no conozco el modelo de router especifico, asi que podria estar equivocado.

Toda la suerte con la instalacion. La vengo siguiendo en detalle y me sorprende la garra que le estan poniendo. Sigan asi!

---

### Post by Vero1 on 2007-08-26
> **Vero1 said:**
> Hola Gideon26 y gracias por interesarte en mi problemón:(
Lo malo es que cualquier cosa que escriba en la Barra de Direcciones de Mozilla me dice que no puede encontrar al servidor. Lo de la clave de fábrica lo sabía, gracias.

De todas formas lo intentaré una vez mas.

saludos

Hola de nuevo,
Se me ocurrió bajar el Mozilla vía Windows y lo instalé y algo más, pude entrar en la configuración del router(todo gracias a vos:)  ).
Pero yo tengo impreso el manual de Speedy que difiere de las opciones del Arescom en forma directa.
De todas formas me pregunto si toco algo allí o inclusive si trato de seguir las instrucciones de Speedy, no haré algun tipo de desastre que despues no me permita conectarme.
faktorqm me indicó que me fijara en la configuración de Speedy donde habla de PAP, porque el error que me sale en Ubuntu indica un fallo en esa configuración y la comunicación se corta por éso.
Veré si encuentro el famoso PAP.
A vos muchas gracias por la sugerencia del Mozilla:)

saludos

---

### Post by Vero1 on 2007-08-26
> **faktorqm said:**
> hola, perdoname, es que en realidad estaba en otro lado, y supuestamente no podia escribir mucho.
En el tutorial de speedy, en la parte que tiene una ventana que dice "PPP Configuration", ahi tenes un combobox que se llama "Authentication type". No está mal que esté en automático, (yo lo tengo asi) pero si no lo tenés en automático, ponelo. si lo tenes en CHAP, ponelo en PAP. 
Otra cosa, si te dice que no te conecta, en esta misma ventana, pusiste bien tu nombre de usuario y contraseña? te fijaste que sean identicos a los que vos tenes en el iconito en windows? Sino estas segura, podes llamar a tus amigos de speedy :lolflag:
Bueno, dentro de todo fuimos progresando.
Lo que te dijo Gideon26 es lo que pasa en los modem/routers normales, pero hay que tener un solo cuidado, hay que asegurarse que la puerta de enlace y el dns este seteado en el mismo ip que el modem. es decir, la puerta de enlace debe ser 192.168.1.1, el dns primario debe ser 192.168.1.1 y el ip del modem debe ser tambien 192.168.1.1, todo con mascara 255.255.255.0.
Yo no pude entrar al link que dejaste vos, me pide usuario y contraseña :( capaz soy yo... no sé.
Acá te dejo el link de uno que encontre yo que esta lindo y en castellano.

[http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf](http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf)

MIRROR:

[http://rapidshare.com/files/51313801/Instalacion_Modem_Arescom_1000.pdf](http://rapidshare.com/files/51313801/Instalacion_Modem_Arescom_1000.pdf)

Bue, el manual no lei, si encuentro algo que te sirva te lo comento. Es sabado y son las 11pm:guitar:. salu2!!

Hola faktorqm,
Tal vez hayas leído lo que le escribí a Gideon26, pero si no, te digo que él me sugirió probar entrar a Arescom con el Mozilla y pude:)
Pero no toqué nada porque es diferente al instructivo de Speedy y tuve miedo de meter la pata en algo.
Voy a ver lo que me decís del PAP y despues les informo.
Gracias de nuevo y saludos:)

---

### Post by Vero1 on 2007-08-26
Hola Hei Ku,

Efectivamente, me están ayudando entre unos cuantos, cosa que agradezco mucho, ya que hace rato que trato de conectarme a Internet pero sin suerte. Espero que esta vez pueda.

Gracias tambien por tu aporte.

saludos

---

### Post by faktorqm on 2007-08-26
> **Vero1 said:**
> Hola faktorqm,
Tal vez hayas leído lo que le escribí a Gideon26, pero si no, te digo que él me sugirió probar entrar a Arescom con el Mozilla y pude:)
Pero no toqué nada porque es diferente al instructivo de Speedy y tuve miedo de meter la pata en algo.
Voy a ver lo que me decís del PAP y despues les informo.
Gracias de nuevo y saludos:)

ya se, por eso te puse el manual del arescom que te explica paso a paso como configurarlo entrando como te dijo gideon. salu2!

---

### Post by Vero1 on 2007-08-26
> **Vero1 said:**
> Hola faktorqm,
Tal vez hayas leído lo que le escribí a Gideon26, pero si no, te digo que él me sugirió probar entrar a Arescom con el Mozilla y pude:)
Pero no toqué nada porque es diferente al instructivo de Speedy y tuve miedo de meter la pata en algo.
Voy a ver lo que me decís del PAP y despues les informo.
Gracias de nuevo y saludos:)

Acá, de nuevo.
Como te dije pude entrar en Arescom, desde Mozilla pero no encontré nada sobre PAP...

y ahora solamente me queda :guitar:  ??

qué opinás?

salu2 y mucho :popcorn:

---

### Post by faktorqm on 2007-08-26
Te cuento: 

En este link, te explica, cómo resetear el router a valores de fábrica, cómo configurar correctamente tu xp para que te puedas comunicar con el router, como ponerlo en modo router desde cero, esta en español, y perfectamente explicado paso por paso, y es exactamente tu modelo de modem/router, hasta la instalación de los cables, todo explicado por la misma empresa.

[http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf](http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf)

Te dejo acá por las dudas, los datos de la conexión de speedy, para evitarte que los llames y les preguntes:

Encapsulacion: PPPoE

Multiplexacion: LLC

VPI: 8

VCI: 35

user: tu_telefono@speedy

pass: 123456

WAN IP: Automatica

LAN IP: 192.168.1.1
mascara: 255.255.255.0

Si no lo podes tener "en la mano" mientras lo haces, imprimilo. salu2!!:lolflag:

---

### Post by Vero1 on 2007-08-26
> **Vero1 said:**
> Acá, de nuevo.
Como te dije pude entrar en Arescom, desde Mozilla pero no encontré nada sobre PAP...

y ahora solamente me queda :guitar:  ??

qué opinás?

salu2 y mucho :popcorn:

ALELUYA!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Hola a todos los que me han ayudado. Les estoy escribiendo desde Ubuntu. La verdad es que no toqué nada solamente borré un host que encontré que estaba con mi nombre. Despues de éso me pude conectar:):guitar::lolflag:
Pero no crean que ya terminaron mis problemas eh? Diria que ahora viene una seguidilla de preguntas a Uds. que saben.

Agradecería me indiquen de dónde saco los drivers que necesito, como por ejemplo de la tarjeta gráfica Nvidia Gforce X(no recuerdo la otra letra)5200.
Tambien el driver para Impresora Epson Stylus C79.
Son los dos mas urgentes porque la pantalla parece borracha y no puedo imprimir nada.
Tampoco pude configurar el correo, me dice que no reconoce a Speedy y van...
Desde ya un millón de gracias por todo.

saludos:)

---

### Post by Vero1 on 2007-08-26
> **faktorqm said:**
> Te cuento: 

En este link, te explica, cómo resetear el router a valores de fábrica, cómo configurar correctamente tu xp para que te puedas comunicar con el router, como ponerlo en modo router desde cero, esta en español, y perfectamente explicado paso por paso, y es exactamente tu modelo de modem/router, hasta la instalación de los cables, todo explicado por la misma empresa.

[http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf](http://soporte.terra.cl/descargas_folder/Manuales/Instalacion%20Modem%20Arescom%201000.pdf)

Te dejo acá por las dudas, los datos de la conexión de speedy, para evitarte que los llames y les preguntes:

Encapsulacion: PPPoE

Multiplexacion: LLC

VPI: 8

VCI: 35

user: tu_telefono@speedy

pass: 123456

WAN IP: Automatica

LAN IP: 192.168.1.1
mascara: 255.255.255.0

Si no lo podes tener "en la mano" mientras lo haces, imprimilo. salu2!!:lolflag:

Hola amigo, porque ya a esta altura te considero amigo:)

Gracias por tu esfuerzo, pero como verás en mi otro post, ya solucionado el asunto de la conexión.  Los milagros existen:)

saludos y gracias de nuevo.

---

### Post by Hei Ku on 2007-08-26
Realmente me alegro ver que pudieron solucionar el problema. Podrias aclarar dónde fue que borraste el nombre de host. Creo que esta thread le puede servir a muchos otros. Ademas que, como dije antes, es un esfuerzo de persistencia.

En cuanto a los problemas que tenes ahora, te recomiendo armar threads por separado para cada tema. Ambos creo que son solucionables rapidamente. 

En el caso de los drivers de NVidia, creo que con Envy o los drivers de los repositorios restringidos podes instalarlos sin problemas. Y en cuanto a la impresora, proba configurarla como Stylus C68.

---

### Post by bake7221 on 2007-08-26
Does anyone else think it's cool we have a multi-linguistic group of people here... and that no matter what language you speak someone can help?

---

### Post by faktorqm on 2007-08-26
No entendi un soto de lo que dijo, encima los tradutores me tiran 4 cosas distintas..... estimo que lo que dijo es: "no estaria bueno que haya un grupo de personas que ayude sin importar el idioma en que habla?"
O dijo: "Acá hay un grupo de personas que ayuda sin importar el idioma que habla y eso esta bueno!"
ohh........ snif snif :( :(:(
we... alguno que entienda mas que el conteste, por que si le contesto yo le tengo que decir que lo vuelva a decir pero con otras palabras jajajajajaj

vero1: amiga nueva! ^_^ :):)):P):P:biggrin:

---

### Post by Vero1 on 2007-08-27
> **Hei Ku said:**
> Realmente me alegro ver que pudieron solucionar el problema. Podrias aclarar dónde fue que borraste el nombre de host. Creo que esta thread le puede servir a muchos otros. Ademas que, como dije antes, es un esfuerzo de persistencia.

En cuanto a los problemas que tenes ahora, te recomiendo armar threads por separado para cada tema. Ambos creo que son solucionables rapidamente. 

En el caso de los drivers de NVidia, creo que con Envy o los drivers de los repositorios restringidos podes instalarlos sin problemas. Y en cuanto a la impresora, proba configurarla como Stylus C68.

Hola Hei Ku,
Gracias por tu alegría:)
En cuanto al host que borré, entré en Red-Anfitriones y allí lo borré.
Tienes razón, debo abrir nuevos posts por los diferentes problemas.
Lo tendré en cuenta.
Lo de Nvidia ya lo solucioné tambien. Bajé 118 actualizaciones y se ve que éso cambió algunas opciones y pude instalarlo, pero me dice que estoy usando un driver que no es compatible. A pesar de éso la pantalla ya está bien.
Voy a probar con el Stylus C-68 a ver qué pasa.
Muchas gracias y saludos.

---

### Post by Vero1 on 2007-08-27
> **faktorqm said:**
> No entendi un soto de lo que dijo, encima los tradutores me tiran 4 cosas distintas..... estimo que lo que dijo es: "no estaria bueno que haya un grupo de personas que ayude sin importar el idioma en que habla?"
O dijo: "Acá hay un grupo de personas que ayuda sin importar el idioma que habla y eso esta bueno!"
ohh........ snif snif :( :(:(
we... alguno que entienda mas que el conteste, por que si le contesto yo le tengo que decir que lo vuelva a decir pero con otras palabras jajajajajaj

vero1: amiga nueva! ^_^ :):)):P):P:biggrin:

Hola faktorqm,

Lo que dijo se acerca mas a lo segundo que interpretaste.
Dijo que está muy bueno(cool) que aquí haya gente políglota y que puede ayudar  en cualquier idioma(más o menos).
Bueno, yo me arreglo en inglés pero para explicar computación, hm, lo veo un poco dificultoso je

No me dijiste nada con respecto a que me pude conectar...

No puedo enviar mas imágenes aquí porque el máximo es 8 y con los tuyos me paso, así que vaya una sonrisa escrita eh?

salu2

---

### Post by Vero1 on 2007-08-27
Hi bake 7221,

It would be cool endeed but I cannot imagine how could I explain, for example, how to solve certain problems in english:)

regards

---

### Post by Vero1 on 2007-08-27
> **Hei Ku said:**
> Realmente me alegro ver que pudieron solucionar el problema. Podrias aclarar dónde fue que borraste el nombre de host. Creo que esta thread le puede servir a muchos otros. Ademas que, como dije antes, es un esfuerzo de persistencia.

En cuanto a los problemas que tenes ahora, te recomiendo armar threads por separado para cada tema. Ambos creo que son solucionables rapidamente. 

En el caso de los drivers de NVidia, creo que con Envy o los drivers de los repositorios restringidos podes instalarlos sin problemas. Y en cuanto a la impresora, proba configurarla como Stylus C68.

Hola Hei Ku,
Muchas gracias. Configuré la impresora como me dijiste y ya funciona:)

saludos

---

### Post by leo_rockway on 2007-08-27
> **bake7221 said:**
> Does anyone else think it's cool we have a multi-linguistic group of people here... and that no matter what language you speak someone can help?

"No les parece copado que aca haya un grupo multi-linguistico... y que sin importar el idioma que hables alguien te puede ayudar?"

Rosetta... ALLA VOY! :lolflag:

---

### Post by Gideon26 on 2007-08-30
Hola vero1 que bueno que pudiste conectarte con ubuntu, perdon por no haber seguido contestando pasa que no me eh podido conectar recien ahora me eh conectado estuve algo ataradeado de trabajo. en cuanto a los otros drivers. postealos por separado y te ayudamos en cuanto a los de nvidia te diria que copiles los que te nvidia funcionan bastante bien sino bueno usa los de envy. aunque yo prefiero los de nvidia. 


----------------------------------------
por el momento posteando desde biowindows hasta que que baje por completo la gutsy gibbon y ahi estare de nuevo desde un ubuntu hice algunos cambios de particion y deje winchot por el momento. :P biowindows/gutsy /a futuro solaris10 (Unix)

---

### Post by Vero1 on 2007-08-30
Hola Gideon26

No tenés por qué pedir perdón. Uno tiene cosas que hacer.
Lo de la conexión fue pura suerte al haber eliminado un host al voleo:)
Te diré que lo de Nvidia ya se arregló. La pantalla es una pinturita ahora.
Por el momento no sé qué drivers pueden faltarme. Pienso que con el correr del tiempo iré viendo. 

Gracias por todo.

saludos:)

---

### Post by brus_fer on 2008-11-25
Hola gente , tengo el mismo problema pero nose como arreglarlo , tengo ubuntu 8.10 o algo asi , soy re nuw en esto
si alguien me puede ayudar... ah el problema es que no me puedo conectar a internet... nose por que lo configuro pero no se conecta....tengo un modem Huawei startAX MT882 y servicio arnet...

---

### Post by faktorqm on 2008-11-26
Acá explican todo [http://ubuntuforums.org/showthread.php?t=781918&highlight=huawei+882](http://ubuntuforums.org/showthread.php?t=781918&highlight=huawei+882)

---

