---
title: "Escritorio Remoto - Inconveniente (?)"
date: 2010-11-22
forum: Software
---

### Post by sebasthian777 on 2010-11-22
Hola que tal gente!
Vengo usando distros de Ubuntu hace ya unos añitos. Y hace poco con un proyecto que tengo con un amigo, se nos ocurrio contratar un servidor dedicado... El tema es que nos ofrecen tanto Guindows como linux, obviamente me gusto la idea de linux, por lo que consulte a la empresa prestadora y me comunicaron que para sistemas linux no brindaban soporte a escritorio remoto... lo cual me sono medio raro... ahora bien, me dijeron que solo me brindaban soporte con PLESK (que es mas para web por lo que les entendi) y SSH.... ahora bien, mi pregunta:
¿yo desde SSH puedo lanzar y configurar un cliente VNC o ejecutar el escritorio remoto que viene con el 9.10 por defecto?
¿Tengo alguna otra posibilidad?
¿Alguien lidio con algo asi alguna vez?

Les agradesco infinitamente de antemano todos los consejos y opiniones que me den.
Un saludo grande Chicos! Desde ya mil gracias :P:)

---

### Post by guillermolisi on 2010-11-23
Cuales son las condiciones de servicio, concretamente, que te ofrecen para el hosting con Linux ?
Tenes administracion total de la maquina o solamente algunas tareas ?
La instalacion del SO la hace el proveedor o la podes hacer vos ?
Que uso le daran a esa maquina ? (servicios, procesos, etc.)

Y por ultimo, por que quieren usar escritorio grafico en un servidor ?

---

### Post by sebasthian777 on 2010-11-23
> **guillermolisi said:**
> Cuales son las condiciones de servicio, concretamente, que te ofrecen para el hosting con Linux ?
Tenes administracion total de la maquina o solamente algunas tareas ?
La instalacion del SO la hace el proveedor o la podes hacer vos ?
Que uso le daran a esa maquina ? (servicios, procesos, etc.)

Y por ultimo, por que quieren usar escritorio grafico en un servidor ?


Hola Guillermo,

Me estan ofreciendo un servicio tanto de servidor Cloud como uno dedicado (todabia no me decidi a cual).
Teoricamente tengo administracion total de la misma, y la instalacion la realizan ellos si no me equivoco (ya les acabo de mandar un mail pero tardan mas de una semana en responder...)

La maquina ejecutara un servicio que se ejecuta constantemente, que actua como un servidor para un juego, mas precisamente el ultima online emulado por sphere... Yo soy medio ignorante en estos aspectos de linux, siempre lo utilice mas para el lado de uso hogareño y no tanto con ssh.
Te comento como funciona,
Cuando yo ejecuto este servicio desde la terminal, el mismo ocupa la terminal y hasta que no lo cierro no me permite volver a utilizarla, entonces si quiciera realizar alguna otra accion en el servidor, segun lo que tengo entendido (que puede que este equivocado) no podria hasta no matar el susodicho servicio...
Y desde un entorno grafico podria habrir varias terminales para ejecutar otras acciones.

Ademas, en el grupo, mi compañero tiene 0 conocimiento sobre linux, y le seria mas facil moverse en un entorno grafico que bajo una terminal.

te hago una copia de lo que me respondieron al mail:

> - El acceso al servidor se realiza por Panel de Plesk (en caso de que opte por esta opción) y SSH. El acceso por escritorio remoto es exclusivo de los packs de Windows.


---

### Post by guillermolisi on 2010-11-23
Administracion total significa que vos tambien podrias instalar lo que necesites. Si ellos instalan el SO les tendrias que pasar especificaciones para que sepan como queres que sea esa instalacion y por lo que me decis sobre la experiencia que tienen con Linux, no pareceria que esten en condiciones de tal cosa (y el proveedor hara lo que tenga dispuesto como servicio, sin apartarse de eso, posiblemente).

Si lo que necesitan correr en ese server es un servicio no hay indisponibilidad de recursos.

Si es un proceso que no puede correr sin interactividad vas a necesitar entorno grafico, de minima X11. Si toma en esclusividad el entorno grafico siempre tenes la alternativa de usar alguna de las consolas de Linux (tenes 8 por defecto de las cuales 2 son para el entorno grafico), asi que a traves de alguna de las otras seis algo podras ahcer para administrar el servidor.

Si tenes administracion total deberias poder instalar y desinstalar lo que te plazca, VNC-server incluido aunque si es un servidor publico nunca recomendaria esa alternativa por cuestiones de seguridad. Y hablando de seguridad, no mencionas como y que tienen pensado hacer al respecto y que les ofrece el proveedor para securizar el server.

Y que pasa con los backups ? Los administran Ustedes o el proveedor ? Como ?

Que Linux instalan ?

Como ves, no es solamente contratar un servicio y nada mas.

---

### Post by sebasthian777 on 2010-11-23
> **guillermolisi said:**
> Administracion total significa que vos tambien podrias instalar lo que necesites. Si ellos instalan el SO les tendrias que pasar especificaciones para que sepan como queres que sea esa instalacion y por lo que me decis sobre la experiencia que tienen con Linux, no pareceria que esten en condiciones de tal cosa (y el proveedor hara lo que tenga dispuesto como servicio, sin apartarse de eso, posiblemente).

Si lo que necesitan correr en ese server es un servicio no hay indisponibilidad de recursos.

Si es un proceso que no puede correr sin interactividad vas a necesitar entorno grafico, de minima X11. Si toma en esclusividad el entorno grafico siempre tenes la alternativa de usar alguna de las consolas de Linux (tenes 8 por defecto de las cuales 2 son para el entorno grafico), asi que a traves de alguna de las otras seis algo podras ahcer para administrar el servidor.

Si tenes administracion total deberias poder instalar y desinstalar lo que te plazca, VNC-server incluido aunque si es un servidor publico nunca recomendaria esa alternativa por cuestiones de seguridad. Y hablando de seguridad, no mencionas como y que tienen pensado hacer al respecto y que les ofrece el proveedor para securizar el server.

Y que pasa con los backups ? Los administran Ustedes o el proveedor ? Como ?

Que Linux instalan ?

Como ves, no es solamente contratar un servicio y nada mas.

Hola Guillermo.

Mira, justo me respondieron el mail:
> Libertad total de acceso y configuración para especialistas en Linux * Para servidores web, servidores de desarrollo, bases de datos, gaming, etc.* Acceso root para el control total de tu máquina Sistema operativo preinstalado * CentOS 5 con Parallels Plesk Panel 9 Sistemas operativos alternativos * openSUSE 11 minimal* openSUSE 11 con Parallels Plesk Panel 9 (64-Bits)* CentOS 5 minimal* Debian 4.0 (etch) minimal* Ubuntu 8.04 LTS minimal* Ubuntu 6.06 LTS minimal

Con lo que me dijiste de las consolas (que realmente no lo sabia) creo que se me habren unas cuantas puertas. Realmente me voy a poner a averiguar estas cosas que me comentas, en una primera instancia es de mucha ayuda. 
Lo que voy a hacer es generar una maquina virtual en mi casa, instalar un linux de estas caracteristicas y probar esto que me decis. Lo que me interesa es lo siguiente (lo explico con un ejemplo):
1) Yo abro una terminar desde SSH, y ejecuto el servicio... (el servicio se queda constantmente actualizando y reflejando datos de lo que acontece sobre el, en dicha terminar. a su vez, me permite introducir comandos para administrar este programa)
2) cierro el cliente SSH.
3) en el servidor se continua ejecutando el servicio bajo esa terminal
4) me vuelvo a conectar bajo SSH y tomo control/visualizacion de esta terminal
5) veo lo que se refleja y sigo interactuando nuevamente con la terminal
6) repito los paso anteriores salvo el primero.

paralelamente a esto, acceder por otra terminal en caso que quiera administrar alguna otra caracteristica de mi servidor dedicado en linux.

Estoy delirando con los pasos que puse anteriormente o esto funciona asi?

Creo que si desde SSH puedo acceder a varias terminales no tendria problema alguno.


Mil y un gracias por tu tiempo Guillermo. =)

---

### Post by juancarlospaco on 2010-11-23
Depende como este armado el Hosting, 
no siempre que tengas root y SSH podes tener un escritorio grafico completo por mas que sepas instalarlo,
por ejemplo yo armo un LXC, soy root y tengo SSH, pero ese contenedor jamas tendra placa de video...

Por que realmente necesitas tener un escritorio grafico completo en un servidor???

---

### Post by sebasthian777 on 2010-11-23
> **juancarlospaco said:**
> Depende como este armado el Hosting, 
no siempre que tengas root y SSH podes tener un escritorio grafico completo por mas que sepas instalarlo,
por ejemplo yo armo un LXC, soy root y tengo SSH, pero ese contenedor jamas tendra placa de video...

Por que realmente necesitas tener un escritorio grafico completo en un servidor???

Hola, ya estoy descartando la opcion de escritorio grafico remoto. y la razon por la que queria encontrar eso, es mas que nada por mi compañero, por si yo algun dia de emergencia no podia meterme al host, como para que el pudiera o le fuera mas facil.

Ahora simplemente tengo que aprender como es el manejo correcto de SSH y como utilizar varias terminales (es tan simple como establecer nuevas conexiones?).

Tambien si alguno podria responderme si los pasos que enumere anteriormente son logicos y estan correctos.
De paso, si pueden tirar algun link guia por donde empezar a buscar info (porfavor, no les estoy pidiendo que me resuelvan nada, simplemente me interesa el tema y quiero aprender :D :) )

Desde ya mil gracias chicos! Cada vez que tuve una duda aqui me han ayudado =).

---

### Post by guillermolisi on 2010-11-23
> **sebasthian777 said:**
> Hola Guillermo.

Lo que me interesa es lo siguiente (lo explico con un ejemplo):
1) Yo abro una terminar desde SSH, y ejecuto el servicio... (el servicio se queda constantmente actualizando y reflejando datos de lo que acontece sobre el, en dicha terminar. a su vez, me permite introducir comandos para administrar este programa)
No es lo mismo servicio que proceso y una de las caracteristicas que los diferencia es que el servicio se inicia (normalmente) cuando se pone en marcha el servidor y solo se detiene cuando el sysadmin lo requiera o cuando se apaga el server.
Un servicio bien configurado no requiere que alguien se conecte con el server para iniciarlo y se puede monitorear remotamente, no hace falta que su contenido ("actualizando y reflejando datos") sea mostrado permanentemente en una pantalla para que funcione .... a menos que estemos hablando de un proceso en lugar de un servicio, y que este proceso sea exclusivamente interactivo (los servicios no son interactivos, solo se monitorean).

> 2) cierro el cliente SSH.
3) en el servidor se continua ejecutando el servicio bajo esa terminal
4) me vuelvo a conectar bajo SSH y tomo control/visualizacion de esta terminal
5) veo lo que se refleja y sigo interactuando nuevamente con la terminal
6) repito los paso anteriores salvo el primero.

paralelamente a esto, acceder por otra terminal en caso que quiera administrar alguna otra caracteristica de mi servidor dedicado en linux.

Estoy delirando con los pasos que puse anteriormente o esto funciona asi?

Creo que si desde SSH puedo acceder a varias terminales no tendria problema alguno.


Mil y un gracias por tu tiempo Guillermo. =)

Verifica bien que caracteristicas operativas posee lo que quieren usar en ese server.

AL margen de las potentisimas facilidades de ssh, hay mas herramientas que junto con ssh logran hacer la vida mas facil para quienes necesitan administrar servidores. Una de ellas es "screen" que, llegado el caso que si o si tengas que dejar interactuar lo que llamas "servicio" con una terminal, podes desconectarte del server sin que el proceso que estas viendo se interrumpa.

---

### Post by sebasthian777 on 2010-11-23
> **guillermolisi said:**
> No es lo mismo servicio que proceso y una de las caracteristicas que los diferencia es que el servicio se inicia (normalmente) cuando se pone en marcha el servidor y solo se detiene cuando el sysadmin lo requiera o cuando se apaga el server.
Un servicio bien configurado no requiere que alguien se conecte con el server para iniciarlo y se puede monitorear remotamente, no hace falta que su contenido ("actualizando y reflejando datos") sea mostrado permanentemente en una pantalla para que funcione .... a menos que estemos hablando de un proceso en lugar de un servicio, y que este proceso sea exclusivamente interactivo (los servicios no son interactivos, solo se monitorean).



Verifica bien que caracteristicas operativas posee lo que quieren usar en ese server.

AL margen de las potentisimas facilidades de ssh, hay mas herramientas que junto con ssh logran hacer la vida mas facil para quienes necesitan administrar servidores. Una de ellas es "screen" que, llegado el caso que si o si tengas que dejar interactuar lo que llamas "servicio" con una terminal, podes desconectarte del server sin que el proceso que estas viendo se interrumpa.

Ok, Con estos datos creo que tengo para empezar a probar.

Mil Gracias po ahora!!!!

---

### Post by alfplayer on 2010-11-24
1. Con vncserver no es necesario hardware de video y se puede crear un escritorio completo, aunque puede ser inconveniente tener instalado (y ejecutando) un escritorio porque usa recursos como espacio en disco.

2. Se puede usar el comando nohup para dejar ejecutando un comando "que ocupa la terminal" en una sesión ssh, para que siga en ejecución después de terminar la sesión ssh (o sea, para que siga después de desloguearse de ssh y también cuando vuelvas a loguearte).

---

