---
title: "Ayuda con UbuntuFirewall"
date: 2009-01-19
forum: Software
---

### Post by leo_liet on 2009-01-19
Hola amigos de ubuntu, quería preguntarles como hay que configurar el firewall.
 No tengo ofresco ningun servicio (telnet, ftp, http, etc) asi que, que opinan acerca de que puertos tendria que permitir, etc.
 
 Espero que puedan ayudarme gracias :D

---

### Post by AliTabuger7 on 2009-01-19
Lo siento por la traducción automática
¿Qué uso?

Samba (Windows acciones) son populares. Torrents también son populares.

Si usted no está actuando como un servidor, estas son las más frecuentemente utilizadas. que son alrededor de 140 y alrededor de 7000, respectivamente.

Probablemente no hace daño a algo que el firewall y ver lo que no funciona, entonces permitir que.

---

### Post by guillermolisi on 2009-01-20
> **leo_liet said:**
> Hola amigos de ubuntu, quería preguntarles como hay que configurar el firewall.
 No tengo ofresco ningun servicio (telnet, ftp, http, etc) asi que, que opinan acerca de que puertos tendria que permitir, etc.
 
 Espero que puedan ayudarme gracias :D
En principio y considerando que mencionas no ofrecer algun servicio en la red, yo no tocaria nada, particularmente si esta funcionando todo bien.

La pregunta es, como sabes que no estas ofreciendo algun servicio ?
Que tenes instalado y en uso/corriendo a nivel servicios (MySQL, Samba, Apache, etc.) ?

---

### Post by leo_liet on 2009-01-20
> En principio y considerando que mencionas no ofrecer algun servicio en la red, yo no tocaria nada, particularmente si esta funcionando todo bien.

 Esta funcionando todo bien, pero queria bloquear el trafico de salida y tambien el de entrada, para estar mas "seguro".

> 
La pregunta es, como sabes que no estas ofreciendo algun servicio ?

 Se que no estoy ofreciendo porque los desactive :D.

---

### Post by guillermolisi on 2009-01-20
> **leo_liet said:**
> Esta funcionando todo bien, pero queria bloquear el trafico de salida y tambien el de entrada, para estar mas "seguro".



 Se que no estoy ofreciendo porque los desactive :D.
Ok. Una prueba determinante seria hacer un scanning de tu maquina para saber a ciencia cierta si los puertos que estan abiertos son los que deberian estarlo. Para esto suele usarse nmap habiendo otras herramientas similares (en [http://www.sismonda.com.ar](http://www.sismonda.com.ar) hay un tutorial sobre su uso).

Suponiendo que esta todo bien, si cerras los puertos de salida no vas a poder navegar ni intercambiar e-mail, entre otras cosas. Esos ports se abren cuando inicias un cliente de e-mail, mensajeria, web, etc.

Los puertos de entrada vienen cerrados por defecto y se abren si asi lo configuras en el FW o si algun servicio esta disponible para ser consumido por alguien externo a tu red (Internet por ejemplo).

---

### Post by leo_liet on 2009-01-20
> Ok. Una prueba determinante seria hacer un scanning de tu maquina para saber a ciencia cierta si los puertos que estan abiertos son los que deberian estarlo. Para esto suele usarse nmap habiendo otras herramientas similares (en [http://www.sismonda.com.ar](http://www.sismonda.com.ar) hay un tutorial sobre su uso).

Suponiendo que esta todo bien, si cerras los puertos de salida no vas a poder navegar ni intercambiar e-mail, entre otras cosas. Esos ports se abren cuando inicias un cliente de e-mail, mensajeria, web, etc.

Los puertos de entrada vienen cerrados por defecto y se abren si asi lo configuras en el FW o si algun servicio esta disponible para ser consumido por alguien externo a tu red (Internet por ejemplo).

 Gracias por tu respuesta. Si ya se usar nmap, pero lo que quiero saber es, como se que aplicacion esta usando determinado puerto, para poder saber por ejemplo que ese puerto esta siendo usado por firefox y no por un backdoor por ejemplo.
 Otra cosa, los puertos no son de entrada o de salida. Las CONEXIONES son las que pueden ser de entrada (alguien se conecta a tu PC) o CONEXIONES de salida (cuando por ejemplo te conectas con firefox al server de google por http)

 Saludos

---

### Post by Hei Ku on 2009-01-20
Hmmm, creo que Guille sabe la diferencia. Las canas son por algo. :rolleyes:

Para ver qué conexiones tenés abiertas usa el netstat. Y despues divertite con el iptables.

---

### Post by leo_liet on 2009-01-30
> Hmmm, creo que Guille sabe la diferencia. Las canas son por algo. 
 Jajaja

 Bueno, después de fijarme con netstat que puertos tenia abiertos, empecé a trabajar con el firewall, pero ahora que estoy en ello tengo un par de dudas, que aparecieron luego de hacer un rápido escáner de puertos con nmap. 

 - ¿Por qué tengo abierto el puerto tcp 631 (ipp), que es el usado para trabajos de impresión, si desactive el servicio Miniaplicación de la cola de impresión? ¿Qué otro servicio tengo que desactivar para que ese puerto este cerrado? No tengo impresora, así que no tendría que dejarlo abierto, por ahora lo estoy filtrando con el firewall, para que nadie que no este en mi red interna tenga acceso a el.

 - ¿Para qué están abiertos los puertos udp 55850 y udp 5353 (mdns)?

 - Y por último ¿qué puertos usan el firefox y emesene?, o para poder controlar esto tendría que abrir un puerto para el firefox y en el firefox especificar que uso un proxy en localhost (con el puerto que abrí)

 Y otra cosa que me llamo la atención, es que probando el firewall firestarter, este me mostraba en tiempo real las conexiones establecidas. Se puede configurar el ufw para que me muestre esto? Y sino a donde puedo ver los logs (que supongo que guardan los intentos de conexiones a los puertos que estan filtrados)

 Bueno, muchas gracias desde ya. Espero que no piensen que soy un paranoico de la seguridad jeje y tambien espero que puedan ayudarme :D

 Saludetes y AGUANTE RIVER!!! :D

---

### Post by Hei Ku on 2009-01-30
tenes instalado y andando CUPS?

emesene usa varios puertos. fijate en google por los puertos del protocolo del msn.

firefox, a ver, dificil responder, sobre todo despues del comentario anterior sobre las conexiones. busca los puertos de http, https, ftp, por empezar. ;)

si tenes un proxy local, utilizalo, aunque no le veo la utilidad si solo cumple la funcion de proxy para esa maquina. de todas maneras vas a tener que abrir los puertos para el proxy.

me parece que te falta algunos conceptos claves de tcp/ip y redes. y eso es clave para seguridad. Tenes que no solo saber como utilizar las herramientas, sino el concepto subyacente y todos los distintos mecanismos.

Lo primero que haria en tu lugar es agarrar el libro de Tanenbaum, y despues de ese, el manual de iptables.

---

### Post by guillermolisi on 2009-01-30
> **Hei Ku said:**
> tenes instalado y andando CUPS?

emesene usa varios puertos. fijate en google por los puertos del protocolo del msn.

firefox, a ver, dificil responder, sobre todo despues del comentario anterior sobre las conexiones. busca los puertos de http, https, ftp, por empezar. ;)

si tenes un proxy local, utilizalo, aunque no le veo la utilidad si solo cumple la funcion de proxy para esa maquina. de todas maneras vas a tener que abrir los puertos para el proxy.

me parece que te falta algunos conceptos claves de tcp/ip y redes. y eso es clave para seguridad. Tenes que no solo saber como utilizar las herramientas, sino el concepto subyacente y todos los distintos mecanismos.

Lo primero que haria en tu lugar es agarrar el libro de Tanenbaum, y despues de ese, el manual de iptables.

Agrego: para poder aconsejar sobre que puerto abrir o cerrar en un entorno LAN habria que conocer que servicios se consumen en esa LAN por sus usuarios.

En general, cuando hay un puerto abierto es porque existe corriendo un servicio/programa que lo activo de esa forma. Cerrarlo o no depende fundamentalmente de lo que dije en el parrafo anterior.
Entonces si queres saber porque tenes abiertos los puerto 'x' e 'y' busca que servicios y aplicaciones los usan y ahi tendras la respuecta contundente.

> firefox, a ver, dificil responder, sobre todo despues del comentario anterior sobre las conexiones. busca los puertos de http, https, ftp, por empezar. ;)
Bien ahi, HeiKu :)

---

### Post by leo_liet on 2009-01-30
CUPS lo tengo instalado, pero como hago para detenerlo :S
 El emesene ya lo solucione (encontre los puertos), en cuanto a firefox ¿se puede configurar el ufw para que permita que ese proceso pueda tener acceso a la red, es decir, puedo seleccionar yo que programas quiero que tengan acceso a la red (como en win xp).
 En cuanto a los puertos 55850 y 5353, sigo esperando una respuesta.

> me parece que te falta algunos conceptos claves de tcp/ip y redes. y eso es clave para seguridad. Tenes que no solo saber como utilizar las herramientas, sino el concepto subyacente y todos los distintos mecanismos.

 ?_? a que te refieres, porque creo que aunque no soy un guru de tcp/ip me desempeño bastante bien en el tema (a pesar de mi corta edad)

---

### Post by Hei Ku on 2009-01-30
El 5353 se usa para multicast DNS.

El otro puede ser sospechoso, pero tendrias que hacer un netstat para ver mas detalles.

Me refiero a que si sabes sobre TCP/IP no podes preguntar que puerto abrir para Firefox. Solamente te falta entender algunas cosas de redes y tcp/ip. Por eso te recomende el libro de Tanenbaum sobre redes, que es de lo mejor en el tema para iniciarse. Nadie nace sabiendo.

---

### Post by guillermolisi on 2009-01-30
Googleando los TCP ports, en particular el 55850, encontre esto entre muchas info:

[http://ist.uwaterloo.ca/security/howto/2000-10-02/compromise.html](http://ist.uwaterloo.ca/security/howto/2000-10-02/compromise.html) (en Ingles)

---

### Post by leo_liet on 2009-01-31
Gracias por la ayuda, en cuanto pueda pongo la captura del netstat, para que opinen que puede ser.
 Creo que no tiene nada que ver saber tcp/ip y saber el puerto que utiliza un navegador, pero bueno. respeto su opinion

 Espero que no sea lo que dice guille. alguien sabe como desactivo cups?

 saludetes

---

### Post by Hei Ku on 2009-01-31
Un navegador utiliza varios protocolos diferentes. HTTP, HTTPS, FTP, y otros puertos para funciones especificas. Por ej: los app servers locales en java generalmente se ponen en el 9080, 9081, etc.
Entonces, en realidad no tenes que preguntar por la aplicacion, sino por el protocolo que queres usar, y despues abrir los puertos correspondientes, y ademas podes utilizar esos mismos protocolos en puertos no standard. Por ej: si queres habilitar ssh en una pc, lo recomendable es no hacerlo en el port standard, sino en un port alto, para reducir un poco, y digo solo un poco, la posibilidad de que lo detecten con un escaneo de puertos.

Para deshabilitar CUPS, podes editar el archivo /etc/cups/cupsd.conf

---

### Post by leo_liet on 2009-02-01
Gracias Hei. Pero tambien querria saber si es posible configurar el firewall como en win xp, en la parte de excepciones, en la el firewall bloquea las conexiones entrantes a excepcion de los progrmas especificados.

 Gracias y saludos

---

### Post by guillermolisi on 2009-02-01
> **leo_liet said:**
> Gracias Hei. Pero tambien querria saber si es posible configurar el firewall como en win xp, en la parte de excepciones, en la el firewall bloquea las conexiones entrantes a excepcion de los progrmas especificados.

 Gracias y saludos
Por defecto, el FW de Linux bloquea todas las conexiones entrantes que no tengan un origen interno. Por ejemplo, no podrias recibir un requerimiento por el port 80 a menos que tengas un Apache que este escuchando en ese port.

Por aplicaciones .... mmmm ... creo que no. Si por puertos (y con una referencia a la aplicacion que habitualmente lo utiliza, caso Apache y port 80, en caso que uses Firestarter).

---

### Post by leo_liet on 2009-02-06
> **guillermolisi said:**
> Por defecto, el FW de Linux bloquea todas las conexiones entrantes que no tengan un origen interno. Por ejemplo, no podrias recibir un requerimiento por el port 80 a menos que tengas un Apache que este escuchando en ese port.

Por aplicaciones .... mmmm ... creo que no. Si por puertos (y con una referencia a la aplicacion que habitualmente lo utiliza, caso Apache y port 80, en caso que uses Firestarter).

 
 Ok, gracias. Entonces no voy a poder "seleccionar" que programas quiero que puedan establecer conexiones :(

---

### Post by Hei Ku on 2009-02-06
No, tenes que saber que puertos abrir de acuerdo al protocolo que vayas a utilizar. Y configurar la aplicacion para que escuche en ese puerto, si elegiste uno no standard.

---

### Post by faktorqm on 2009-02-09
Hola, aclaro algo que creo que no lo puso nadie, si es asi perdon. 

Cuando vos queres cerrar las conexiones entrantes por tal o cual puerto, las cerras con iptables. Si tenes algun servicio corriendo, podes probar en principio de desactivarlo temporalmente haciendo ```
sudo /etc/init.d/cupsys stop
```
y ahi notar la diferencia. (usar netstat -a o combinaciones similares)

Cuando usas firefox o cualquier otro programa que se conecte afuera agarra el primer puerto libre que se le ocurre al sistema operativo y manda la peticion al puerto 80 pero del servidor, no de tu maquina. Vos podes estar saliendo por cualquiera, pero llegas al otro lado al 80.

Asi mismo pasa con varios programas, no asi con emule o algun cliente de la red BT, que especificas por que puertos entran y salen las conexiones y a que protocolo pertenecen.

Yo el Ubuntu Firewall no lo uso, va de hecho no se ni que hace, uso iptables exclusivamente. si queres pasate por aca si queres ver un par de reglas de seguridad, capaz te sirven. [http://ubuntuforums.org/showpost.php?p=6209693&postcount=56](http://ubuntuforums.org/showpost.php?p=6209693&postcount=56)

Cualquier duda pregunta, Salu2!

---

