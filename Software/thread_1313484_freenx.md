---
title: "freenx"
date: 2009-11-03
forum: Software
---

### Post by capcabgue on 2009-11-03
Hola a todos, aún con mi problema de control remoto del PC.

Les cuento, que ppor eso de seguridad y rapidez he decidido hacer la instalación mediante freenx. instalé el servidor en el PC de mi casa y en el notebook el cliente, pero cuando trato de conectarme me dice que la conexión fue rechazada. Me arroja estos errores:
NX> 203 NXSSH running with pid: 13716
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.100 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Ahora que escribo supongo que es porque no he configurado el servidor (mi PC), bueno traté de instalarlo bajando desde nomachine el cliente node y server. Los 2 primeros sin problemas, pero cuando instale el server, me arroja varios errores 704:

NX> 704 ERROR: can not add user:nx
NX> 704 ERROR: User :nx already exists
NX> 704 to fix the problem, you may try to completely uninstall NX
NX> 704 Server and install it from scratch. If this is not enough,
NX> 704 please delete the nx user by using the system command and
NX> 704 proceed with a new instalationof NXServer
dpkg: error processing nx server (--install):
 Subprocess post-intalation script returned error exist status 1
Errors were encountered while processing:
nxserver:

Entiendo lo que dice, pero como solucionarlo,.....ni idea.

Alguien me puede ayudar con esto. Yo creo que el error se debe a que instale primero por consola y luego por manager... y quizas hay un conflicto..

Gracias nuevamente

---

### Post by Maciett on 2009-11-04
Según lo que te dice no son varios errores 704, es uno que en vez de escribirlo como parráfo continua en la línea que sigue, dice: "no puedes crear un usuario nx por que ya existe, para arreglar el problema intenta desintalar completamente el server nx y lo instalas de cero. Si esto no funciona por favor borra el usuario nx desde la consola y procede a reinstalar la aplicación."

Ojalá te sirva

Saludos

---

### Post by capcabgue on 2009-11-05
> **Maciett said:**
> Según lo que te dice no son varios errores 704, es uno que en vez de escribirlo como parráfo continua en la línea que sigue, dice: "no puedes crear un usuario nx por que ya existe, para arreglar el problema intenta desintalar completamente el server nx y lo instalas de cero. Si esto no funciona por favor borra el usuario nx desde la consola y procede a reinstalar la aplicación."

Gracias por el dato, lo que decía en ingles lo había entendido, pero lo que no se hacer es como desisntalar completamente el server nx.
Hice un dpkg -r nxserver y me dice que no esta instalado (me parece que mientras instalaba openvpn lo borre por sinaptic. Bueno aqui despues de esto busqué nx y sólo me aparece el nxclient, el cual lo desinstale.

Como me puedo asegurar que no me queda nada del server de nx??

Gracias

---

