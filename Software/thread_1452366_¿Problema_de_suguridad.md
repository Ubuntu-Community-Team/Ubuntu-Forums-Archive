---
title: "¿Problema de suguridad?"
date: 2010-04-11
forum: Software
---

### Post by condes on 2010-04-11
Hola!!! Yo se que Ubuntu es bastante seguro. Sin embargo me surgió una duda. Yo tenía adsl y varias veces verifiqué el monitor de sistema, para saber, si la pc enviaba o recibía información de internet, sin mi consentimiento. Y la verdad nunca hubo grandes desajustes, hasta que cambié mi proveedor de internet. Saqué el adsl y me puse banda ancha (o sea por cable de Tv) y a partir de ahí, noto que, el monitor de sistema, se la pasa recibiendo información de internet. Tengo miedo que los técnicos que vinieron me hayan instalado algo en la pc, porque si me guío por sus caras, la verdad no parecían de fiar. Mi pregunta es:

¿La banda ancha genera recepción constante de información o lo que cuento no es normal?
¿Puedo tener un problema de seguridad?
¿Es posible instalar algún programa espía desde la pc?

SALUDOS

---

### Post by bichopro on 2010-04-12
es muy dificil, si tienes dudas instala Gufw para que puedas activar graficamente el firewall, pero para mi que otra cosa esta conectada a internet, un plugin de rhythmbox o algo asi

---

### Post by condes on 2010-04-15
Te agradezco por tu respuesta. Hoy me comuniqué con mi proveedor y me dijeron (sin que yo le diga nada) que puedo tener un programa espía. Existe algún programa del terminal de Ubuntu que permita la salida de datos o información? 

SAludos

---

### Post by alfplayer on 2010-04-16
> **condes said:**
> Te agradezco por tu respuesta. Hoy me comuniqué con mi proveedor y me dijeron (sin que yo le diga nada) que puedo tener un programa espía. Existe algún programa del terminal de Ubuntu que permita la salida de datos o información? 

SAludos

Los de soporte técnico normalmente no conocen el tráfico de las computadoras de los clientes, no pueden saber si hay un espía en tu computadora.

No hay una forma simple de averiguarlo con certeza, pero con tiempo y con conocimiento de linux se pueden buscar espías por ejemplo con comandos como "ps" o "netstat" para ver procesos y conexiones. En general, se recomienda tomar medidas de seguridad preventivamente.

---

### Post by condes on 2010-04-16
Si, tengo una idea de lo que tratan esos comandos y me voy a poner en órbita con ellos. Pero mi pregunta es... si yo quiero activar un programa espía en la compu de otro, usando Ubuntu, ¿existe algun otro comando como el netcat? Pregunto esto no para hacer daño a otra compu sino porque, los técnicos, toquetearon el terminal y no se que escribieron. O sea, ¿Existe algun comando de Ubuntu que se comporte como un espía permitiendo la trasmisión de información, dejando abierto un puerto o algo por el estilo?

SAludos

---

### Post by alfplayer on 2010-04-16
> **condes said:**
> Si, tengo una idea de lo que tratan esos comandos y me voy a poner en órbita con ellos. Pero mi pregunta es... si yo quiero activar un programa espía en la compu de otro, usando Ubuntu, ¿existe algun otro comando como el netcat? Pregunto esto no para hacer daño a otra compu sino porque, los técnicos, toquetearon el terminal y no se que escribieron. O sea, ¿Existe algun comando de Ubuntu que se comporte como un espía permitiendo la trasmisión de información, dejando abierto un puerto o algo por el estilo?

SAludos

No entiendo cuál es la necesidad. Puede ser que estés buscando un key logger, que se puede combinar con un programa como netcat para trasmitir los datos.

---

### Post by condes on 2010-04-16
Exacto. Mi pregunta es. Si el netcat esta abierto ¿COmo lo detecto?

¿Hay otro comando que permita eso? ¿Como lo detecto?

SAludos

PD: Ya instale la barrera de fuego y me instale un programa para monitorizar la red (etherap). Hay alguno mejor de este ultimo?

---

### Post by alfplayer on 2010-04-16
> **condes said:**
> Exacto. Mi pregunta es. Si el netcat esta abierto ¿COmo lo detecto?

¿Hay otro comando que permita eso? ¿Como lo detecto?

SAludos

PD: Ya instale la barrera de fuego y me instale un programa para monitorizar la red (etherap). Hay alguno mejor de este ultimo?

Un programa para trasmitir datos simples se puede hacer con unas líneas de código, debe haber miles que hagan eso. "socat" es parecido a netcat y está en los repositorios.

Para ver si está netcat o cualquier proceso en ejecución se podría usar el monitor de sistema (con la opción de ver los procesos de todos los usuario), o desde terminal con monitores como "top" o "htop", o con una línea de comandos como por ejemplo "ps aux | grep nc" (nc es el ejecutable de netcat).

---

### Post by moreback on 2010-04-17
mhh... el tiempo que estuve con vtr llegaban muchos paquetes de broadcast, arp y cosas raras por la interfaz del modem. Con Wireshark se puede ver el tráfico.

Al final pusimos un router d-link y asunto solucionado. :-)

---

### Post by condes on 2010-04-18
Bueno... les comento. Instalé el firestarter (cortafuegos) y el wareshark (monitor de red). También compré un router. Pero con solo instalar este último, la máquina dejó de recepcionar información. En cualquier caso verifiqué con el monitor de red (sin el router). Solo estaba recibiendo ataques pero no emitiía paquetes nocivos. Por último con el comando top verifiqué si existían programas nocivos. Revisé de dos listas que encontré en internet de procesos comunes, y por suerte eran todos normales. 


Gracias por la ayuda, saludos

---

### Post by Carlos C on 2010-04-19
¿lo damos por solucionado?

---

### Post by condes on 2010-04-28
Si, seguro. SOLUCIONADO!!!

---

