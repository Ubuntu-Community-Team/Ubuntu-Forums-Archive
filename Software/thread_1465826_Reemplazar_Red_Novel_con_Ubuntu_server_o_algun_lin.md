---
title: "Reemplazar Red Novel con Ubuntu server o algun linux?"
date: 2010-04-29
forum: Software
---

### Post by NickCis on 2010-04-29
Hola, en donde trabajo mantienen una red novel para compartir archivos. Todos los clientes son windows 98 (maquinas viejas, ejecutan programas que se encuentras sobre el server, es un sistema de administracion de ventas/compras, etc).

Mi pregunta era si es conveniente y/o posible reemplazar la red novel por algun derivado libre?.

Que ventajas tendria y qe desventajas?

Saludos.

---

### Post by alfplayer on 2010-04-29
Un buen sistema moderno puede ofrecer mucho más, aprovechando los avances de hardware y software.

---

### Post by NickCis on 2010-04-29
Alguna pista sobre como montar un sistema de este tipo?

Saludos.

---

### Post by anarko on 2010-04-29
Hola NickCis, te cuento lo que podes hacer, mantener la red novell no creo, pero podes reemplazar ( con paciencia y con saliva ) por una red en samba, poniendo en el server cualquier Linux que sea de tu agrado y configurando el samba para que haga las veces se domain server, así los win98 pueden usar el servicio de autenticación desde el server. Con esto podes mantener carpetas separadas para los usuarios y grupos sin que puedan acceder a donde no deben. 
El tema de tener unidades compartidas se maneja de manera igual que en novell. Si lo querés de una forma mase seria/segura también podes decirle que usuarios pueden acceder a que compartición del samba.

Por si no lo sabes el samba es el sistema de compartición de archivos que usa Microsoft en sus windows ( por  lo menos hasta el 2000 que yo sepa ) simula ser un servidor de dominio ( si así lo requerís vos ) windows. También puede funcionar como un servidor de archivos abierto sin restricciones si no te querés hacer embrollo con los permisos de los usuarios. 

Cualquier consulta no dudes en preguntar, tengo vasta experiencia en este tipo de servidores. 

Saludos

---

### Post by NickCis on 2010-04-30
Si, la solucion, supongo qe seria esa.
Me gustaria que se pueda mantener mas o menos la misma disposicion de las cosas. Paso explicar como funciona actualmente:

El server (Novell) esta constantemente prendido. 

Las computadoras (windows 98), al prenderse te muestra un cartel de red novell para que pongas usuario y contraseña (este cartel guarda el ultimo usuario con su contraseña que pusiste, esto deberia siguir estando, incluido la opcion de recordar). Despues de ingresar correctamente, entra  al computadora normal.
Las unidades del server son montadas como una unidad de disco "Z".

Las computadoras tienen accesos directos a programas exe que se encuentran en el server, y ejecutan estos programas localmente.

Nececitaria que me expliquen como lograr eso.

Se puede mantener el login de novell o tiene qe ser reemplazado por otro?.

Como es el manejo de usuarios con sus respectivos permisos? (actualmente todas las computadoras montan las mismas carpetas como unidad Z y tienen todos permiso para leer y escribir, pero me gustaria seguir teniendo la posibilidad de cambiar los privilegios).

Que distro conviene usar para el server? Ubuntu?, 64 bits o 32bits? (El server tiene procesador compatible con 64bits)

Alguna otra cosa qe tenga qe tener al respecto?.

Desde ya, muchas gracias :P

---

### Post by z37a on 2010-04-30
Si realmente te interesa mantener todo lo Novell peor desde Linux mandame un mp, por que no correspondería que lo postee acá ya que debería hablar de otra distro!

Ahora si tu intención es otra y el uso que se le da en especifico es otro tal vez lo del samba te funcione mejor!

---

### Post by alfplayer on 2010-04-30
> **z37a said:**
> Si realmente te interesa mantener todo lo Novell peor desde Linux mandame un mp, por que no correspondería que lo postee acá ya que debería hablar de otra distro!

Ahora si tu intención es otra y el uso que se le da en especifico es otro tal vez lo del samba te funcione mejor!

No creo que haya dificultad para seguir la conversación aunque sea mejor hacerlo con otra distro. Este tema está relacionado con software para Ubuntu.

---

### Post by z37a on 2010-04-30
> **alfplayer said:**
> No creo que haya dificultad para seguir la conversación aunque sea mejor hacerlo con otra distro. Este tema está relacionado con software para Ubuntu.

Bueno les comento entonces, alguien me dio el pie y comento!!!

Novell tenia planeado para el 2010 dejar de dar soporte para Netware, lo extendio a 2015, peor no va a salir nada nuevo. El reemplazo fue una distro Linux con TODOS los servicios y mas de Novell, se llama OES(Open Enterprise Server), van por la OES2 SP2, es nada mas y nada menos que un SLES(SuSe Linux Enterprise Server) 10 SP3 con un addon con TODOS los servicios de netware y mas cosas. De abierto no tiene mucho, si bien el kernel es libre la mayoria de los paquetes no, pero es la evolución de netware y la verdad esta bueno, espero que a futuro Novell libere codigo sobre esto y asi se logre utilizar en otras distros peor por ahora no hay forma.

Dentro de lo nuevo vos podes tener terminales SLED(SuSe... Desktop) con cliente de Novell, iPrint y muchas cosas mas, aparte de tener los windows como antes.

Si realmente hay interés en el tema preferiría me manden PM, o mail, se los contesto sin dramas, peor no quiero mezclar a Ubuntu con SuSe o las cosas de Novell.

PD: Cualquier cosa no duden en consultar en serio, si bien no certifique tengo lso cursos de Novell hechos!!!!! Por tanto puedo darles datos y como conseguir las cosas y demas.

---

### Post by alfplayer on 2010-05-02
> **z37a said:**
> Bueno les comento entonces, alguien me dio el pie y comento!!!

Novell tenia planeado para el 2010 dejar de dar soporte para Netware, lo extendio a 2015, peor no va a salir nada nuevo. El reemplazo fue una distro Linux con TODOS los servicios y mas de Novell, se llama OES(Open Enterprise Server), van por la OES2 SP2, es nada mas y nada menos que un SLES(SuSe Linux Enterprise Server) 10 SP3 con un addon con TODOS los servicios de netware y mas cosas. De abierto no tiene mucho, si bien el kernel es libre la mayoria de los paquetes no, pero es la evolución de netware y la verdad esta bueno, espero que a futuro Novell libere codigo sobre esto y asi se logre utilizar en otras distros peor por ahora no hay forma.

Dentro de lo nuevo vos podes tener terminales SLED(SuSe... Desktop) con cliente de Novell, iPrint y muchas cosas mas, aparte de tener los windows como antes.

Si realmente hay interés en el tema preferiría me manden PM, o mail, se los contesto sin dramas, peor no quiero mezclar a Ubuntu con SuSe o las cosas de Novell.

PD: Cualquier cosa no duden en consultar en serio, si bien no certifique tengo lso cursos de Novell hechos!!!!! Por tanto puedo darles datos y como conseguir las cosas y demas.

Me parece que no se está mezclando.

¿Qué le puede ofrecer reemplazar el servidor con una nueva versión de SuSe o Novell que no le puede ofrecer una solución libre con Ubuntu, con la posibilidad de modernizar también los terminales?

En general, mantener una combinación de sistemas antiguos y modernos es una mala situación.

---

### Post by z37a on 2010-05-02
> **alfplayer said:**
> Me parece que no se está mezclando.

¿Qué le puede ofrecer reemplazar el servidor con una nueva versión de SuSe o Novell que no le puede ofrecer una solución libre con Ubuntu, con la posibilidad de modernizar también los terminales?

En general, mantener una combinación de sistemas antiguos y modernos es una mala situación.

No obvio, que si quiere puede migrar todo a Samba y otras soluciones, pero lamentablemente no encontré hasta ahora un buen reem,plazo libre y gratuito de los servicios de Netware. Se complica bastante y no suelen tener interfaces tan amigables como las de Novell, es una pena en realidad, no quiere decir que apoye a Novell pero la verdad no hay mucho para buscar, como file server si se puede reemplazar, pero por ejemplo el cliente de Novell y demás tecnologías de red Novell no encontré forma alguna, Zenwork tampoco encontré como y hay muchas cosas mas. Por eso dije, todo depende de que funciones de netware quieran reemplazar.

---

