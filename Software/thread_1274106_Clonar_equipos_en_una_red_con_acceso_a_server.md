---
title: "Clonar equipos en una red con acceso a server"
date: 2009-09-24
forum: Software
---

### Post by electronpositivo on 2009-09-24
Buenas fenómenos.

He clonado los equipos de una red que acceden a un server mediante ldap/nfs. Están configurados con IP fija. Tras cada clonado solamente he modificado las ip manualmente y los ficheros /etc/hosts /etc/hostname.

Cuando enciendo varios a la vez el acceso a la red es muy lento. ¿Debería modificar algún fichero de configuración además de estos? :confused:

---

### Post by Hei Ku on 2009-09-24
No, deberias encenderlas por turnos. O agrandar el ancho de banda del servidor. ;)

---

### Post by guillermolisi on 2009-09-24
Que caracteristicas tiene la LAN que estas usando ?
Que ancho de banda maneja el/los servers ?

Normalmente los servidores deberian estar en un backbone con mas ancho de banda que el resto de los clientes ya que estos acceden concurrentemente a los servidores.

---

### Post by electronpositivo on 2009-09-24
> **guillermolisi said:**
> Que caracteristicas tiene la LAN que estas usando ?
Que ancho de banda maneja el/los servers ?

Normalmente los servidores deberian estar en un backbone con mas ancho de banda que el resto de los clientes ya que estos acceden concurrentemente a los servidores.

Se trata de una LAN a 100 MBs en un aula con 20 ordenadores y 1 server conectados a un switch. 

Con sólo 1 ordenador en marcha (además del server) la velocidad es bastante buena. Pero a partir del segundo ordenador que se encienda funciona todo más lento. Por este motivo me planteo que haya algún conflicto en la red con IP, nombre del PC... A veces no conecta

---

### Post by Hei Ku on 2009-09-24
Que recursos de la red estan usando? las carpetas /home?

Que pasa con el ping? Empezas a perder paquetes o se mantiene estable?

---

### Post by electronpositivo on 2009-09-24
> **Hei Ku said:**
> Que recursos de la red estan usando? las carpetas /home?


Este es el resultado del comando mount en un cliente:

```
192.168.1.254:/home on /home/users type nfs (rw,nolock,addr=192.168.1.254)
192.168.1.254:/opt/jclic/projects_server on /opt/jclic/projects type nfs (rw,nolock,addr=192.168.1.254)
192.168.1.254:/usr/share/fonts/truetype/aula on /usr/share/fonts/truetype/aula type nfs (rw,nolock,addr=192.168.1.254)
192.168.1.254:/etc/skel-clients on /etc/skel type nfs (rw,nolock,addr=192.168.1.254)
192.168.1.254:/etc/pam.d-clients on /etc/pam.d type nfs (rw,nolock,addr=192.168.1.254)

```

192.168.1.254 es la IP del server.
En /home/users los usuarios solamente tienen algunos documentos que guardan allí para hacer entregas de trabajos (no todo el contenido de su home).

> **Hei Ku said:**
> Que pasa con el ping? Empezas a perder paquetes o se mantiene estable?

Al poner en marcha varias máquinas (aunque no intente hacer login en ningún cliente) se pierde la conexión con el server, y el ping falla totalmente. Esto también me ha hecho pensar en algún conflicto en la red.

---

### Post by Hei Ku on 2009-09-24
Cómo es la actividad en el switch? Hace pensar en una tormenta de broadcast, que no es una situacion normal.
Por otro lado, si hubiera IPs en conflicto generalmente la interfaz de red se deshabilita.

---

### Post by electronpositivo on 2009-09-24
> **Hei Ku said:**
> Cómo es la actividad en el switch? Hace pensar en una tormenta de broadcast, que no es una situacion normal.

¿Cómo lo puedo saber? ¿Mejoraría conectando con menos directorios remotos al inicio?

---

### Post by guillermolisi on 2009-09-24
> **electronpositivo said:**
> ¿Cómo lo puedo saber? ¿Mejoraría conectando con menos directorios remotos al inicio?
Se podria deducir conociendo que bloques de IPs se usan en la red y con que mascara de subred, server incluido.

Luego, seria de mucho valor conocer que servicios se publican en esa red. Si hay uno descontrolado y la mascara no esta adecuadamente definida terminas teniendo una tormenta de broadcast, por ejemplo y entre otras causas posibles.

---

### Post by Hei Ku on 2009-09-24
Forma simple de diagnostico, cuando prendas las PCs te vas al switch y te fijas cómo estan las lucecitas. ;)
Si te podes loguear remoto al switch y ver como esta el trafico, mejor.
Si podes poner un analizador de protocolo, mucho mejor. Pero supongo que no.

---

### Post by electronpositivo on 2009-09-24
El switch no tiene login remoto, pero lucecitas sí :lolflag:

Creo que esto se me va de las manos.](*,)

---

### Post by scrooge_74 on 2009-09-24
Cuál es la especificación de tu servidor? No será que son demasiadas PCs conectandose a él y que el servidor no tiene suficiente capacidad?

---

### Post by Hei Ku on 2009-09-24
Fijate el trafico de red en el servidor, a ver a cuánto esta cuando se inician las pcs.

---

### Post by scrooge_74 on 2009-09-24
Se me ocurre que el switch no esté aguantando la carga también, abría que ver qué modelo es.

Hoy por ejemplo mi router wifi decidió que no podía con la carga de la red y a la vez manejar la encriptación de la seguridad.

Así que hay que ver todos esos aspectos

---

### Post by electronpositivo on 2009-09-25
Voy a hacer unas pruebas teniendo en cuenta vuestros consejos y en unos días os comento si doy con algo.

---

### Post by electronpositivo on 2009-09-28
Bueno, estoy haciendo progresos.

Resulta que la red tiene un enlace inalámbrico (2 routers Linksys wrt54gs con firmware dd-wrt) y al parecer lo que se colapsa es esta conexión.

Lo he comprobado colocando el server al otro lado de la red inalámbrica provisionalmente y ahora que está conectada con cable-switch a los clientes el acceso es inmediato, y funciona perfectamente.

Así es que queda confirmado que la re-configuración de la red tras el clonado no está produciendo problemas.

Por tanto voy a intentar lo siguiente:
[LIST]
[*]Colocar un servidor secundario en este lado de la red.
[*]Sincronizar el contenido de los directorios compartidos del server primario con el secundario (¿rsync?).
[*]Configurar los clientes para que se conecten al server que esté a su lado de la red, sin que deban pasar a través de los routers wifi.
[/LIST]

Supongo que el acceso para autenticación ldap no será problema que pase a través de wifi... esto lo tengo que comprobar.

Si tenéis sugerencias, os estaré muy agradecido.

---

### Post by Hei Ku on 2009-09-28
Fijate que los puertos correspondientes esten abiertos en el router.

---

### Post by scrooge_74 on 2009-09-28
Cambia de routers

---

### Post by electronpositivo on 2009-09-29
> **scrooge_74 said:**
> Cambia de routers

¿Tan malos son estos?

---

### Post by electronpositivo on 2009-09-29
> **Hei Ku said:**
> Fijate que los puertos correspondientes esten abiertos en el router.

Si me permite conectar, supongo que estarán abiertos. Creo que el problema es ante la avalancha de logins y conexiones simultáneas.

---

### Post by z37a on 2009-09-29
Algo que me llama la atención también, que tipo de switch estas usando? marca, modelo, cantidad de bocas 10/100 y giga?

Puede ser también que el switch este saturado, algunos switch cuando se saturan empiezan a funcionar como hubs, repitiendo todo y eso te saturaría la red. Igualmente tomando en cuenta que el server esta a 100M y tenés 20 equipos tenés que pensar que hay una transferencia(en simultaneo) de 5M por equipo, esto hay que dividirlo por 8(ya que son Mbits y no Mbytes) y te deja menos de 1M de transferencia.

---

### Post by electronpositivo on 2009-09-29
> **z37a said:**
> Algo que me llama la atención también, que tipo de switch estas usando? marca, modelo, cantidad de bocas 10/100 y giga?

Puede ser también que el switch este saturado, algunos switch cuando se saturan empiezan a funcionar como hubs, repitiendo todo y eso te saturaría la red. Igualmente tomando en cuenta que el server esta a 100M y tenés 20 equipos tenés que pensar que hay una transferencia(en simultaneo) de 5M por equipo, esto hay que dividirlo por 8(ya que son Mbits y no Mbytes) y te deja menos de 1M de transferencia.

El switch es un conceptronic 10/100 (de giga nada de nada). Pero sigo sospechando de los routers wifi.

---

