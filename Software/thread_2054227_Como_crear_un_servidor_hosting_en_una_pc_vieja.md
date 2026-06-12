---
title: "Como crear un servidor hosting en una pc vieja?"
date: 2012-09-06
forum: Software
---

### Post by sergioc on 2012-09-06
Hola, yo tengo instalado W7 y Ubuntu ultima versión, pero no se usar Linux, soy usuario nuevo por lo que sigo usando W7, tengo algunas dudas en cuanto Linux y lo que es posible en el, me gusta practicar códigos como html y css, crear webs o instalar plantillas y editarlas, siempre usé hosting gratuito debido a que nunca me causó problemas y no tuve la necesidad de pagar uno, actualmente estoy intentando aprender a usar joomla y me encuentro que esta vez si me trajo algunos problemas el host ya que no me permite la configuración del php.ini y otras cosas, según leí dicen que es por el host pero no estoy seguro de eso.

Yo quería saber si con Linux puedo crear un servidor y usarlo de host para montar mis webs y que se puedan ver desde cualquier pc como en cualquier host, leí en [este tutorial]("http://www.forat.info/2008/07/07/servidor-en-linux-ubuntu-server-vol-2-sistema-operativo/") que decía algo como esto pero no entendí ya que decía que esto quedaría instalado en la red local (si no mal interpreto esto quiere decir que no puede ser visto por el publico) y ademas es del 2008 con lo que no se si es correcto actualmente y por otro lado vi en  [este tutorial]("http://www.youtube.com/watch?v=w5daQTBSQPA") donde si se puede ver desde cualquier pc, la verdad me confundí con esto.

Quería preguntarles a ustedes, si es posible reemplazar a un host con la instalación de un servidor en otra pc que tengamos en des-uso para crear nuestro propio host, que opinan y que me recomiendan.

Es ubuntu server la base para que esto funcione o cual distro?

Que posibilidades tengo y cual es el mejor tutorial para esto.

Características de la pc en des-uso:
Micro: Pentium 4 Dual core
Disco duro: 160 gb
Memoria: 1024 mb DDR2
Placa de video: Nvidia GeForce 512 gb

Conexion: 1 Mb :confused:

Disculpen mi ignorancia, soy nuevo como pueden ver.

Gracias, saludos!

---

### Post by sergioc on 2012-09-08
Finalmente instale ubuntu server 12.04 lts

Luego quice seguir lo del tutorial y me quede en el [paso 4]("http://www.forat.info/2008/07/13/servidor-en-linux-ubuntu-server-vol-4-web-server-lamp/") ya que dice de abrir un navegador y como hago si no tengo escritorio solo veo la terminal a pantalla completa?

---

### Post by granjero on 2012-09-08
Hola, podés usar el webmin desde cualquier pc conectada en la misma red. 

En el navegador pones la ip de la pc que hace de server...

salud!

---

### Post by hictio on 2012-09-08
> **granjero said:**
> Hola, podés usar el webmin desde cualquier pc conectada en la misma red. 

En el navegador pones la ip de la pc que hace de server...

salud!

Usualmente, Webmin usa el puerto TCP 10000 para accederlo via webrowser.
Asi que para accederlo tendrías que tipear en tu navegador:

```

http://direccion.ip.servidor:10000

```

Y también es muy común que el Webmin esté funcionando sólo a través de una conexión segura via SSL, asi que la dirección que tendrías que tipear sería:

```

https://direccion.ip.servidor:10000

```

Y es muy probable que tengas una advertencia de tu browser, porque el certificado no está autenticado por ninguna CA.

Para más data, la documentación -en inglés- de [Ubuntu Server](https://help.ubuntu.com/12.04/serverguide/) es buenísima.

---

### Post by sergioc on 2012-09-08
Antes que nada, me parece que la pc con ubuntu server no esta conectada a internet, intente hacer una actualización de prueba y falló, acá dejo unas fotos:

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/2012-010.jpg[/IMG]
[IMG]http://i30.servimg.com/u/f30/15/10/51/07/2012-011.jpg[/IMG]
[IMG]http://i30.servimg.com/u/f30/15/10/51/07/2012-012.jpg[/IMG]

Cuando instalé ubuntu server lo hice desde la otra pc poniendo el disco duro en ella y luego una vez instalado lo puse de nuevo en la pc que corresponde, lo hice asi para que no se pinche o reinicie al ser que esta media baqueteada , haberlo instalado asi me trae problemas de configuraciones?

Ambas computadoras están conectadas a un router con cables (pero también tiene wi-fe) y de ahí al moden, para que esten conectadas en red esta bien asi?

---

### Post by hictio on 2012-09-08
Si, pareciera que no se puede conectar a internet, o bien tiene un problema de DNS.
Conectate al servidor Ubuntu Server, y hacé estos tests:

1- Tiene una dirección IP asignada?
Tipeá: ifconfig ENTER

2- Si tiene dirección IP, testeá de hacer ping a su propia dirección.
Tipeá: ping direccion.ip.Ubuntu.Server ENTER
Tiene que responder, lo terminás con Ctrl + C.

3- Fijate si podés hacer ping al gateway de tu red, usualmente el router que te conecta a internet.
Tipeá: ping direccion.ip.gateway ENTER
Lo terminás con Ctrl + C.

4- Si el ping contra el gateway funcionó, fijate si podés llegar a una dirección IP en internet.
Tipeá: ping 8.8.4.4 ENTER
Lo terminás con Ctrl + C.

5- Si el ping hacia internet funcionó, testeá lo mismo, pero sin usar una dirección IP.
Tipeá: ping [www.yahoo.es](www.yahoo.es) ENTER
Lo terminás con Ctrl + C.

---

### Post by sergioc on 2012-09-09
Acabo de testear, la tiene asignada y si funciona la prueba haciendo ping a mi propia IP, lo que si no se si esta bien asignada ya que eso lo hice yo en [este paso]("http://www.forat.info/2008/07/10/servidor-en-linux-ubuntu-server-vol-3-configuracion-de-red/") desde /etc/network/interfaces, como no sabia cual era mi IP de mi pc con ubuntu server puse la IP de la otra pc, supongo que eso debe estar mal y todos los demas pasos no me funciono ninguno..

Aca dejo una foto del paso 1, 2 y creo que 3 tambien:
[IMG]http://i30.servimg.com/u/f30/15/10/51/07/pingip10.jpg[/IMG]

Y no se cual es la IP de mi Ubuntu Server y cual la del Gateway, si se fijándome desde interfaces pero no son las mismas que aparecen en ifconfig.

Que haya instalado Ubuntu Server con el disco duro en la otra pc, eso esta bien?

Las DNS las copie de [OpenDNS]("http://www.opendns.com/"), tampoco se si eso lo hice bien.

Que es eso de 64 bits?

---

### Post by hictio on 2012-09-09
Un test rápido... Probá lo siguiente, desde el Ubuntu Server:

1- ping 8.8.8.8 ENTER
Si funciona, tenés que ver un resultado similar a:
```

ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=50 time=40.1 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=50 time=73.5 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=50 time=60.6 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=50 time=40.6 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=50 time=75.9 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=50 time=60.6 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=50 time=61.9 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=50 time=62.7 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=50 time=64.9 ms

```

2- ping gmail.com ENTER
Si funciona, tenés que ver un resultado similar a esto:
```

 ping gmail.com
PING gmail.com (173.194.42.21) 56(84) bytes of data.
64 bytes from eze03s05-in-f21.1e100.net (173.194.42.21): icmp_req=1 ttl=52 time=17.8 ms
64 bytes from eze03s05-in-f21.1e100.net (173.194.42.21): icmp_req=2 ttl=52 time=14.2 ms
64 bytes from eze03s05-in-f21.1e100.net (173.194.42.21): icmp_req=3 ttl=52 time=13.9 ms
64 bytes from eze03s05-in-f21.1e100.net (173.194.42.21): icmp_req=4 ttl=52 time=18.0 ms
64 bytes from eze03s05-in-f21.1e100.net (173.194.42.21): icmp_req=5 ttl=52 time=14.1 ms
64 bytes from eze03s05-in-f21.1e100.net (173.194.42.21): icmp_req=6 ttl=52 time=14.6 ms

```

Si 1 funciona y 2 no, estás saliendo a internet, pero tenés un problema con el DNS.

---

### Post by sergioc on 2012-09-09
No funciona con ninguno de los 2..

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/nocone10.jpg[/IMG]

Seguro hice mal el paso de configurar IP y DNS, las IP no deben ser las correspondientes, estuve buscando en google como saber mi IP, hay algunas explicaciones pero se necesita descargar un programa por lo visto y sin conexión no puedo hacerlo.

Esta es mi configuración:

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/interf10.jpg[/IMG]

---

### Post by hictio on 2012-09-09
Si hacés ping al gateway te responde?
ping 192.168.0.1 ENTER

---

### Post by sergioc on 2012-09-09
Me responde "network is unreachable", el tema es que esas IP las puse yo y como no sabia las de Ubuntu Server utilice las IP de esta otra pc, yo creo que tengo que cambiar los datos de la interfaces por verdaderos y no de la otra pc, pero no se como saber mi IP en Ubuntu Server y mas estando sin conexión.

Las únicas 2 que funcionan son:
127.0.0.1 y 192.168.122.1

Pero no se cual es del Server y cual del Gateway..

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/serv10.jpg[/IMG]

Que significa 64 bytes en este caso?, no tiene nada que ver con los bytes de la pc? yo instale Ubuntu 32 pensando que esta pc es de 32 pero si es de 64 instalo el de 64.

Me esta gustando mucho Linux, ni bien le agarre la mano renuncio a w7 para siempre, quiero manejar solo Linux en ambas pc.

Me voy a dormir, mañana seguimos, te agradezco por la ayuda y el interés en resolver mi problema, saludos.

---

### Post by hictio on 2012-09-10
En el otro screenshot que posteaste, el Ubuntu Server tendría la dirección IP 192.168.0.100 asignada. Si le hacés ping desde el propio Ubuntu Server responde?

---

### Post by sergioc on 2012-09-10
No, con ninguna de las que asigne responde, pero como decia esas IP no son del Ubuntu Server sino de esta otra pc. 

Con las que si responde son las que me aparecen al tipear ifconfig, pero no son las que yo asigne en interfaces:

192.168.122.1 
127.0.0.1 

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/pingip10.jpg[/IMG]

---

### Post by hictio on 2012-09-10
Okas.
No tenés dirección asignada.
Cómo se asignan las direcciones IP en esa red? Hay un router con DHCP que asigna la dirección automáticamente a quien la solicite?
Sino es asi, basado en los valores de los screenshots que posteaste, asignale una dirección en forma manual:

```

sudo /sbin/ifconfig eth0 192.168.0.167 netmask 255.255.255.0 broadcast 192.168.0.255 ENTER
sudo /sbin/route add 192.168.0.0 ENTER
sudo /sbin/route add default gw 192.168.0.1 ENTER

```

Para testear si caminó:

ifconfig
ping 192.168.0.1
ping 8.8.4.4
ping gmail.com

La dirección 192.168.0.167 se asume que está libre dentro de la red.

---

### Post by sergioc on 2012-09-10
No funciono ninguno de los 3, me salen estos errores:

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/descon10.jpg[/IMG]


No se nada sobre como asignar IP, este es mi router del cual salen 2 cables, 1 a cada pc y tambien emite wifi:

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/router10.jpg[/IMG]

En mi Ubuntu Server antes tenia w7, cuando formateaba para reinstalar el w7 luego tenia que insertar un cd e instalar los drivers necesarios, dentro de los cuales incluía para que funcione la conexión a Internet, también necesitaba instalar el driver del router cosa que no hice en Ubuntu Server aunque me parece que la ultima vez que instale w7 no hizo falta este paso, no estoy seguro.

Y en la pc que tengo usando ahora tengo una partición con Ubuntu 12.04 y para instalarlo no me pidió ningún driver, anda todo de 10 y super veloz, esto no se si es por que se auto-configura o es por que en al otra partición con w7 tengo todos los drivers instalados.

---

### Post by hictio on 2012-09-10
No funcionaron porque no el Ubuntu Server no tiene una interfaz de red llamada eth0, como decía en el archivo de configuración que posteaste antes.
Tiene tarjeta de red instalada?
Si tiene, cuando le conectás un cable de red, se enciende algún led?
Si tipeás:
```

lspci

```

Qué devuelve?

---

### Post by sergioc on 2012-09-10
Se enciende el led del router indicando que esta conectado al Ubuntu Server, 
la luz Nº3 de la foto que esta mas arriba, si desenchufo el cable desde la pc esa luz se apaga, 

No, no tengo placa de red, ahí llame a mi proveedor de hardware para comprar las placas de red,
me dijo que con el router que tengo se puede configurar para que funcione en red, pero el no sabe mucho de esto, 
vos decís que se puede configurar el router o compro placas? 

Devuelve esto:

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/ispci10.jpg[/IMG]

---

### Post by sergioc on 2012-09-11
En hora buena! :D

Ahora funciona, probé varias veces de re-instalar el cd desde mi Ubuntu Server hasta que me rendí por que siempre se colgaba en el mismo lugar y me fui a descansar, cuando regrese había pasado al siguiente paso y continuó con la instalación, en instalaciones predeterminadas solo elegi "lamp, open ssh y samba file" luego solo me salio error en un paso y tuve que omitirlo y seguir con el siguiente, el paso era algo asi como "revisar y preparar instalaciones", pero termino la instalacion, hice algunas pruebas y funcionan! pero ya me perdí, no entiendo si tengo que asignar IP o si se hizo automáticamente o que, que deberia hacer ahora? y como hago para usarla desde la otra pc, asi al Ubuntu Server le saco el mouse y teclado que molestan.

Gracias, Saludos!

[IMG]http://i30.servimg.com/u/f30/15/10/51/07/funcio10.jpg[/IMG]

Acá hay un problema, no entra al editor o no existe.. 
```
sudo nano /etc/network/interfaces
sudo: nano: command not found
```

Creo que viene de ese error que tuve en la nueva instalación, para mi que no se me instalaron los programas que vienen por defecto como hago para repararlo? 
o cuales cosas son necesarias y como instalarlas?

Solucionado, instale nano.

---

### Post by sergioc on 2012-09-13
Hola, me podrías enseñar como sigue después de haber logrado la instalación de Ubuntu Server?

Me han dicho en otro post que se puede usar la IP dinámica, también estuve buscando tutoriales en google y hasta dicen que es mejor en cuanto seguridad, vos me recomendás que use la IP dinámica como me la auto-configuró en la instalación?

Seria un placer poder poner en marcha esto.

Saludos!

---

### Post by hictio on 2012-09-14
Mirá, si entendés inglés (no es complejo, es bien técnico), lo mejor es leer el manual **oficial** de Ubuntu para su Ubuntu Server:

[Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/)

Está dividido por capítulos, si, pero por funciones que el servidor puede cumplir.

Lo importante, me parece a mi, es definir que es lo querés hacer con el Ubuntu Server, es decir, que querés que sirva.

---

### Post by sergioc on 2012-09-14
No, no se ingles, pero hoy instale google translator en chrome y eso puede ayudar algo, lo que yo quiero hacer es hostearme a mi mismo para subir webs hechas en joomla u otros scripts o plantillas, practicar códigos html, css y posiblemente estudiar javascript y php, también me gustaría poder autorizar a amigos o conocidos que puedan subir sus trabajos, si me guias cuales de [estos pasos]("https://help.ubuntu.com/12.04/serverguide/") me corresponden hacer yo los haré, si esta dentro de tus posibilidades y no te es molestia, si no es asi lo entenderé, yo busque en google pero todos los tutoriales que vi no coinciden con lo que busco o están desactualizados, ademas todos están basados en IP estática y yo voy a trabajar con IP dinámica.

---

### Post by hictio on 2012-09-15
Hola,

Te diría que arranques con esta página: [Web Servers](https://help.ubuntu.com/12.04/serverguide/web-servers.html).
Con respecto al tema de la dirección IP dinámica de tu conexión de internet, si tenés todas tus máquias detrás de un router WiFi o similar, no es un tema que tengas que settear en el propio servidor, sino en el router, y especificamente sería el Port Forwarding, para que cuando llegue un request para conectarse a un servicio en la dirección IP pública (y dinámica), sea el router el que envíe al servidor de destino el request correspondiente.
Una solución simple, para que se ocupe del tema de las direcciones de IP dinámicas, es que uses un servicio como Dynamic DNS para registrar un dominio, asi te olvidás del tema.

---

### Post by sergioc on 2012-09-15
Hola, me podrías decir como y con que programa utilizo Ubuntu Server desde mi pc general (digo pc general por que no se como se dice) usando Linux Ubuntu 12.04 que quiero comenzar a usar solo Linux en ambas pc, con Samba se hace esto? o Open Ssh? o cual programa?, gracias por la ayuda.

---

### Post by hictio on 2012-09-16
Para administrar el servidor en forma remota, lo más común es el SSH.
Es decir, conectarte via SSH desde tu máquina mediante un cliente SSH al servidor SSH que está funcionando en el Ubuntu Server.
Para hacer eso, desde una máquina Ubuntu lo único que tenés que hacer es arrancar un Terminal y tipear:
```

ssh -l usuario direccion.ip.ubuntu.server ENTER

```
Si en el Ubuntu Server tenés el mismo nombre de usuario que estás usando en la máquina Ubuntu, podés tipear directamente:
```

ssh direccion.ip.ubuntu.server ENTER

```

Sino querés usar SSH y la línea de comando, hay otras herramientas como [Webmin](http://webmin.com/), para administrar el Ubuntu Server a través de un webfront. Pero siempre vas a tener mucho más control si trabajás en la línea de comando.

---

### Post by sergioc on 2012-09-17
> ssh direccion.ip.ubuntu.server ENTER
Ah que era sencillo el ssh! 

> Una solución simple, para que se ocupe del tema de las direcciones de IP dinámicas, es que uses un servicio como Dynamic DNS para registrar un dominio, asi te olvidás del tema.
No entiendo sobre esto, como es eso de registrar un dominio, a que te referís? [www.ejemplo.com?](www.ejemplo.com?) o que? yo quería usar dominios .com.ar gratis de nic.ar es posible esto?

_Pude instalar_: 
HTTPD - Apache2 Web Server
PHP5 - Scripting Language
Apache Tomcat

_Estos n_o: 
Squid - Proxy Server:
```

david@ubuntuServer:~$ sudo apt-get install squid
[sudo] password for david: 
sudo: unable to open /var/lib/sudo/david/0: Read-only file system
W: No se utiliza bloqueos para el fichero de bloqueo de sólo lectura /var/lib/dpkg/lock
E: No se puede escribir en /var/cache/apt/
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

```
Ruby on Rails:
```

david@ubuntuServer:~$ sudo apt-get install rails
[sudo] password for david: 
sudo: unable to open /var/lib/sudo/david/0: Read-only file system
W: No se utiliza bloqueos para el fichero de bloqueo de sólo lectura /var/lib/dpkg/lock
E: No se puede escribir en /var/cache/apt/
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

```

Probé de re instalar los que si pude instalar y me sale el mismo mensaje, asi que supongo que ya estan todos instalados.

Me siento perdido, como sigo ahora?

---

### Post by hictio on 2012-09-18
> **sergioc said:**
> 
No entiendo sobre esto, como es eso de registrar un dominio, a que te referís? [www.ejemplo.com?](www.ejemplo.com?) o que? yo quería usar dominios .com.ar gratis de nic.ar es posible esto?


No, los servicios que te ofrencen la actualización de IP dinámica en un registro DNS no permiten usar cualquier dominio, sino el que ellos ofrecen; por lo menos los que son totaltmente gratuitos.
Fijate en [Dyn DNS](http://dyn.com/dns/), yo lo uso hace como diez años, pero me parece que no ofrecen más el servicio gratuito? Fijate en su página web.
Otra opción es [No-IP Free](http://www.no-ip.com/personal/)

---

### Post by sergioc on 2012-09-18
No entiendo muy bien, para que son estos dominios? se necesita uno solo para identificar mi pc? pero luego podre usar cualquier tipo de dominios para las webs que yo suba? o siempre necesitare registrar los dominios por ahí?

Yo a lo que me refería es que necesito usar dominios .com.ar para mis clientes, estos dominios los consigo gratis y vienen excelente para las webs de mis clientes.

Mi duda es si el dominio que yo registre es solo para poder acceder a mi pc pero luego podre utilizar cualquier dominios para mis scripts o como?

---

### Post by hictio on 2012-09-20
Esos servicios funcionan usando DNS y actualizando un registro (el que vos seleccionás como "host.dominio.algo" cuando te suscribís al servicio).
Lo que hace el servicio es, si registrás el dominio "sergioc.no-ip.com", por ejemplo, que esa dirección va a apuntar a la dirección IP pública y dinámica que vos tenés en tu conexión de internet.
Estos servicios usualmente ofrecen un cliente que se ejecuta o bien en tu propia máquina, o en el propio router (hay muchísimos routers hogareños que lo soportan).
Este cliente le informa a un servidor, por ejemplo no-ip.com y le informa cuando tu dirección IP cambia, y asi actualiza la dirección IP a tu registro "sergioc.no-ip.com", de esa forma todas las personas que saben la dirección siempre usan el host "sergioc.no-ip.com" independientemente de la dirección IP que te asignen.

---

### Post by sergioc on 2012-09-21
Gracias por la ayuda!

Mira me registre en [dnsdynamic.org]("www.dnsdynamic.org") y registre la IP de mi Ubuntu Server [192.168.0.101]("http://miubuntuserver.dnsdynamic.com/") por este dominio [miubuntuserver.dnsdynamic.com]("http://miubuntuserver.dnsdynamic.com/") al cual ingreso y dice ***It works!***

Mi pregunta es ese dominio en que lo usare? osea entiendo que es mi IP dinámica disfrazada de dominio pero no se que tengo que hacer con el una vez conseguido, a su vez sigo con la duda si para los script que yo vaya a subir tendrán que usar este tipo de dominios? o este dominio es solo para crear el host y luego para los script podre usar cualquier dominio como se me plazca?

Una cosita mas, si mi IP es dinámica por que cada vez que entro a ifconfig dice la misma IP?

Espero no molestarte con tanto, no quiero cansarte, cualquier cosa me avisas y lo cortamos, desde ya me diste una re mano, pero si podemos seguir mejor.

Ahora que hago?

Saludos!

---

### Post by hictio on 2012-09-21
Estás usando la dirección IP incorrecta.
El host "miubuntuserver.dnsdynamic.com" no puede apuntar a la dirección 192.168.0.101 porque esa es una [dirección IP privada](http://es.wikipedia.org/wiki/Direcci%C3%B3n_IP_privada), no acesible ni ruteable en internet.
Para determinar que dirección IP tenés que usar, usando la misma conexión de internet donde está el servidor que tiene asignado "miubuntuserver.dnsdynamic.com", entrá a la página:

[http://checkip.dyndns.org/](http://checkip.dyndns.org/)

Y te va a decir cuál es tu dirección IP pública actual.
El host "miubuntuserver.dnsdynamic.com" tiene que apuntar a esa dirección IP.

Lo importante con todo este tema es que trates de automatizarlo, fijate si tu router tiene soporte para IP dinámicos, y si lo hace, si incluye el servicio de dnsdynamic.com.
Después de esto, cuando funcione, vas a tener que hacer port forwardinf en el router que los requests lleguen a tu máquina con Ubuntu Server dentro de tu red LAN.

Tu dirección IP es siempre la misma porque estás dentro de una red privada, y es bueno que asi sea, especialmente cuando hagas port forwarding a la dirección IP interna que tiene tu máquina con Ubuntu Server.

---

### Post by sergioc on 2012-09-25
Voy a usar No-ip, mi direccion ahora es [miubuntuserver.no-ip.org]("http://miubuntuserver.no-ip.org") pero me pide user y pass y no se que poner ahi, probe con root root y no funciona, admin admin tampoco, con los datos de no-ip tampoco y con los datos de mi ubuntu tampoco..
> [http://miubuntuserver.no-ip.org](http://miubuntuserver.no-ip.org) está solicitando un nombre de usuario y una contraseña. El sitio dice: "DSL Router"

La Ip publica es la misma en cliente y servidor?

**_DDNS:_**
**DDNS:** Enable
**Service Provider:** no-ip.com	
**User Name:** mi no-ip user	
**Password:** mi no-ip pass
**Domain Name:** miubuntuserver.no-ip.org	

**_Virtual Server:_**
Forwarding: **Single Port Forwarding** o **Port Range Forwarding**, cual elijo?

Como completar estos campos?
[https://www.dropbox.com/s/heatn01ox4ukpg0/2012-09-25%2014.18.29.jpg](https://www.dropbox.com/s/heatn01ox4ukpg0/2012-09-25%2014.18.29.jpg)
[https://www.dropbox.com/s/7b1c3zr3s3vgwcx/2012-09-25%2014.18.02.jpg](https://www.dropbox.com/s/7b1c3zr3s3vgwcx/2012-09-25%2014.18.02.jpg)

**_Web Servers:_**
Todos estos programas estan instalados, pero no configurados:
HTTPD - Apache2 Web Server
PHP5 - Scripting Language
Squid - Proxy Server
Ruby on Rails
Apache Tomcat

****** Reinstale las distros, ahora tengo **Ubuntu Server 12.04.1 lts 64 bit** y en el cliente formatie todo e instale solo **Ubuntu 12.04 lts 64 bit**, adios Windows.*

Saludos!

---

### Post by hictio on 2012-09-25
El IP "miubuntuserver.dnsdynamic.com" y el que te devuelve [http://checkip.dyndns.org/](http://checkip.dyndns.org/) tiene que ser el mismo (el test de acceder a la página [http://checkip.dyndns.org/](http://checkip.dyndns.org/) tiene que estar hecho desde la misma conexión donde vas a usar "miubuntuserver.dnsdynamic.com").

Lo que tenés que hacer es que el router haga forward del tráfico que llega al router para que pase y llegue a tu máquina con Ubuntu Server.

El servicio Apache usa el puerto 80 TCP, es muy probable que tu ISP bloquee ese puerto, asi que por si las moscas usá un puerto mayor y "raro" como el 8189, por ejemplo.
Lo que tenés que hacer es configurar en tu router para que el tráfico del puerto 8189 TCP llegue a la dirección IP (interna, privada, del tipo 192.168.x.x) y al puerto 80 TCP de esa misma dirección IP interna.

Usando las opciones de configuración del screenshot de:
[https://www.dropbox.com/s/7b1c3zr3s3vgwcx/2012-09-25%2014.18.02.jpg](https://www.dropbox.com/s/7b1c3zr3s3vgwcx/2012-09-25%2014.18.02.jpg)


Completá:

En External iría: 8189
En Internal iría: 80

To IP Address:
la dirección IP que tiene el Ubuntu Server

Protocol
TCP

Enable: Habilitá la opción

En el Ubuntu Server, chequeá que el servicio Apache está funcionando:

```

sudo service apache2 restart ENTER

```

Para acceder a tu site, tipeáL

[http://miubuntuserver.dnsdynamic.com:8189](http://miubuntuserver.dnsdynamic.com:8189)

Lo mejor es que esto lo testees desde fuera de la propia red donde está "miubuntuserver.dnsdynamic.com", para ver si funciona correctamente.

---

### Post by sergioc on 2012-09-26
Hola, buen dia.

El chequeo de la Ip me sale siempre la misma Ip, no entiendo cada cuanto cambia, 
como en el Server no estaba seguro si era la misma Ip publica que en el cliente y desde el server no podía por tener solo los comandos usê curl ifconfig.me el cual me sirvió para confirmar si la Ip era la misma en ambas pc y si lo es.

Mira no entiendo por que se cambio la Ip privada del server y del cliente, el server ayer era 192.168.0.102 y hoy es 192.168.0.104 
y el cliente ayer era 192.168.0.101 y hoy es 192.168.0.103, ademas al conectarme aparece una advertencia que antes no.
```
david@ubuntu:~$ ssh 192.168.102
ssh: connect to host 192.168.102 port 22: No route to host
david@ubuntu:~$ ssh 192.168.102
ssh: connect to host 192.168.102 port 22: No route to host
david@ubuntu:~$ ssh 192.168.104
The authenticity of host '192.168.104 (192.168.0.104)' can't be established.
ECDSA key fingerprint is 78:32:cb:13:63:02:3f:69:3c:96:4a:64:87:4f:c3:df.
Are you sure you want to continue connecting (yes/no)? yes
**Warning:** Permanently added '192.168.104,192.168.0.104' (ECDSA) to the list of known hosts.
david@192.168.104's password: 
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-31-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Sep 26 13:19:02 ART 2012

  System load:  0.75               Processes:           91
  Usage of /:   1.1% of 149.29GB   Users logged in:     1
  Memory usage: 14%                IP address for eth0: 192.168.0.104
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Wed Sep 26 13:18:17 2012
```

Esto significa que esta funcionando?
```
david@ubuntuServer:~$ sudo service apache2 restart
[sudo] password for david: 
 * Restarting web server apache2                                                                       
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[ OK ]
david@ubuntuServer:~$
``` 

En Single Port Forwarding puse los datos como me indicaste, en Port Range Forwarding no va nada?

Usarê no-ip así que serâ [http://miubuntuserver.no-ip.org:8189](http://miubuntuserver.no-ip.org:8189) pero cuando entro sale la pantalla en blanco con este error..
```
¡Vaya! Google Chrome no ha podido establecer conexión con la página miubuntuserver.no-ip.org:8189.
```

Y [http://miubuntuserver.no-ip.org](http://miubuntuserver.no-ip.org) o [http://miubuntuserver.no-ip.org:80](http://miubuntuserver.no-ip.org:80) me pide usuario y contraseña.

---

### Post by hictio on 2012-09-27
Hola,

Deberías ponerle un dirección IP fija (privada, del tipo 192.168.x.x) a tu máquina con Ubuntu Server, asi te olvidás del tema.
No necesitás hacés port forwarding de rangos, porque necesitás acceder, por lo menos por ahora, solamente a un puerto determinado, el puerto 8189 en el router, y que esta a su vez llegue también sólo a un puerto en particular, el 80 de tu Ubuntu Server.

El mensaje de arranque del Apache en tu Ubuntu Server, no es raro.
Para sacarte la duda de si está funcionando o no el Apache, accedelo desde otra máquina dentro de esa misma red.
Abrí un browser cualquiera en otra máquina dentro de la misma red (que tenga dirección IP 192.168.x.x) y tipeá la dirección IP interna que tiene tu Ubuntu Server, por ejemplo:

[http://192.168.0.104](http://192.168.0.104)

La advertencia del SSH cuando te conectás, y cambió la dirección IP, es normal.

Tené en cuenta una cosa, cuando funcione el tema del port forwarding, tu máquina Ubuntu Server va a estar expuesta, visible, a internet. Mantené el servidor con todos los updates al día!

---

### Post by sergioc on 2012-09-29
Como hago esto?
> Deberías ponerle un dirección IP fija (privada, del tipo 192.168.x.x) a tu máquina con Ubuntu Server, asi te olvidás del tema.
No necesitás hacés port forwarding de rangos, porque necesitás acceder, por lo menos por ahora, solamente a un puerto determinado, el puerto 8189 en el router, y que esta a su vez llegue también sólo a un puerto en particular, el 80 de tu Ubuntu Server.

[http://192.168.0.104](http://192.168.0.104)
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

Como es mantener todo los updates al día?

---

### Post by hictio on 2012-09-29
- Si podés acceder a [http://192.168.0.104](http://192.168.0.104), el Apache de tu Ubuntu Server está funcionando Ok.
Hay que ver que pasa con el port forwarding, cuando puedas, posteá un screenshot de los settings del router actuales.


- Para settear una dirección IP fija a tu Ubuntu Server, editás el archivo de texto: **/etc/network/interfaces**, tendría que quedar así:

```

auto eth0
iface eth0 inet static
address 192.168.0.104
netmask 255.255.255.0
gateway 192.168.0.1

```


- Para mantener actualizado tu sistema, de forma manual, tipeás:

Para actualizar todos los paquetes con updates:
```

sudo apt-get update

```

Y esto para instalarlos:
```

sudo apt-get upgrade

```

---

### Post by sergioc on 2012-09-30
Hecho, no necesita dns-nameserver?
```
auto eth0
iface eth0 inet static
address 192.168.0.104
netmask 255.255.255.0
gateway 192.168.0.1
```

Lo de las actualizaciones durante la instalación elegi la opción de actualizar automaticamente, de todos modos tengo que actualizar manualmente?

> Hay que ver que pasa con el port forwarding, cuando puedas, posteá un screenshot de los settings del router actuales.
Aca te dejo unas capturas, fíjate con la flechita de abajo pasas a la siguiente imagen:
[https://www.dropbox.com/sh/r832170bgsrma2s/2l5f1PVfx2#f:%20Network%20Status.png](https://www.dropbox.com/sh/r832170bgsrma2s/2l5f1PVfx2#f:%20Network%20Status.png)

---

### Post by hictio on 2012-09-30
> **sergioc said:**
> Hecho, no necesita dns-nameserver?


El DNS usualmente se settea en un archivo de configuración diferente, el archivo **/etc/resolv.conf**.


> **sergioc said:**
> 
Lo de las actualizaciones durante la instalación elegi la opción de actualizar automaticamente, de todos modos tengo que actualizar manualmente?


Perfecto! Solamente estate atento a los mensajes en pantalla cuando te logeás al Ubuntu Server, hay updates que luego de instalados necesitan un reboot para que tomen efecto, no muchos como en Windows, pero si los de kernel, por ejemplo, que son críticos.

> **sergioc said:**
> 
Aca te dejo unas capturas, fíjate con la flechita de abajo pasas a la siguiente imagen:
[https://www.dropbox.com/sh/r832170bgsrma2s/2l5f1PVfx2#f:%20Network%20Status.png](https://www.dropbox.com/sh/r832170bgsrma2s/2l5f1PVfx2#f:%20Network%20Status.png)

No, el que decía es el de los settings de Port Forwarding, los que posteaste la vez pasada, sin estar configurados todavía.

---

### Post by sergioc on 2012-09-30
Single Port Forwarding:
[https://www.dropbox.com/s/i54auc1iltyjglq/Single%20Port%20Forwarding.png](https://www.dropbox.com/s/i54auc1iltyjglq/Single%20Port%20Forwarding.png)

Port Range Forwarding:
[https://www.dropbox.com/s/ogpv7z783spn20w/Port%20Range%20Forwarding.png](https://www.dropbox.com/s/ogpv7z783spn20w/Port%20Range%20Forwarding.png)

Aca cambio la seleccion de Ip dinamica a Ip estatica o dejo como esta?
[https://www.dropbox.com/s/p9ler9zsyn5yt3i/setup%20wizard.png](https://www.dropbox.com/s/p9ler9zsyn5yt3i/setup%20wizard.png)

Desactivo DHCP Server?
[https://www.dropbox.com/s/fiad4cqbbzw4f6c/DHCP%20Server.png](https://www.dropbox.com/s/fiad4cqbbzw4f6c/DHCP%20Server.png)

Desactivo DDNS?
[https://www.dropbox.com/s/qlf9oqb7e50qp4s/DDNS.png](https://www.dropbox.com/s/qlf9oqb7e50qp4s/DDNS.png)

Elimino mi dominio en no-ip?

> El DNS usualmente se settea en un archivo de configuración diferente, el archivo /etc/resolv.conf.
Debo hacerlo? de donde saco las DNS?

Gracias.

---

### Post by hictio on 2012-09-30
> **sergioc said:**
> Single Port Forwarding:
[https://www.dropbox.com/s/i54auc1iltyjglq/Single%20Port%20Forwarding.png](https://www.dropbox.com/s/i54auc1iltyjglq/Single%20Port%20Forwarding.png)


Se ve todo Ok. Tendría que estar funcionando Ok el acceso remoto (fuera del LAN) al Apache de tu Ubuntu Server.

> **sergioc said:**
> 
Port Range Forwarding:
[https://www.dropbox.com/s/ogpv7z783spn20w/Port%20Range%20Forwarding.png](https://www.dropbox.com/s/ogpv7z783spn20w/Port%20Range%20Forwarding.png)


Esto no lo necesitás, por lo menos para el acceso del Apache.

> **sergioc said:**
> 
Aca cambio la seleccion de Ip dinamica a Ip estatica o dejo como esta?
[https://www.dropbox.com/s/p9ler9zsyn5yt3i/setup%20wizard.png](https://www.dropbox.com/s/p9ler9zsyn5yt3i/setup%20wizard.png)


Dejalo como está. Tu ISP es el que te asigna una dirección IP dinámica (por eso todo este tema del No-IP ;) )

> **sergioc said:**
> 
Desactivo DHCP Server?
[https://www.dropbox.com/s/fiad4cqbbzw4f6c/DHCP%20Server.png](https://www.dropbox.com/s/fiad4cqbbzw4f6c/DHCP%20Server.png)


No vale la pena, lo importante es que el Ubuntu Server tenga un IP fijo dentro de tu LAN, para que los settings de Port Forwaridng en el router sean siempre constantes, y no tengas que andar editándolos si llegase a cambiar la IP que le asigna el DHCP al Ubuntu Server.
Pero para todas las otras máquinas que no tienen servicios, lo más cómodo y práctico es que tomen IP automáticamente.

> **sergioc said:**
> 
Desactivo DDNS?
[https://www.dropbox.com/s/qlf9oqb7e50qp4s/DDNS.png](https://www.dropbox.com/s/qlf9oqb7e50qp4s/DDNS.png)


Para nada! Esto hace que el cliente del propio router le avise a No-IP cuando tu dirección IP dinámica cambia! Asi no tenés que hacerlo en forma manual.

> **sergioc said:**
> 
Elimino mi dominio en no-ip?


Para nada! El host registrado en No-IP, más el cliente en tu router, se encargan que cuando cambie tu IP dinámica se actualice el registro para que apunte a la nueva dirección IP.

> **sergioc said:**
> 
Debo hacerlo? de donde saco las DNS?

Gracias.

Yo tengo Fibertel, y los DNS de ellos son medio maletas a veces, hace un par de años me pasé a los DNS de Google.
Probalo y fijate como anda la cosa...
Hacé backup del archivo actual, y editalo con estos valores:
```

nameserver 8.8.4.4
nameserver 8.8.8.8

```

---

### Post by sergioc on 2012-09-30
Listo, puse las DNS de google..

Si ya esta todo hasta acá que mas debo hacer?

Al querer entrar a [http://miubuntuserver.no-ip.org:8189](http://miubuntuserver.no-ip.org:8189) dice:
> Esta página web no está disponible
Se ha rechazado el intento de conexión de Google Chrome a miubuntuserver.no-ip.org. Es posible que el sitio web no esté disponible o que la red no esté configurada correctamente.
A continuación se detallan algunas sugerencias:
Vuelve a cargar esta página más tarde.
Comprueba tu conexión a Internet. Reinicia todos los routers, módems y otros dispositivos de red que estés utilizando.
Añade Google Chrome como programa permitido en la configuración del antivirus o del firewall. Si ya lo habías añadido a la lista de programas permitidos, prueba a eliminarlo y a volver a añadirlo.
Si utilizas un servidor proxy, comprueba la configuración de proxy o ponte en contacto con el administrador de tu red para asegurarte de que el servidor proxy funcione correctamente. Si consideras que no necesitas utilizar un servidor proxy, ajusta la configuración del proxy: Accede al menú de herramientas > Configuración > Mostrar opciones avanzadas... > Cambiar la configuración de proxy... y asegúrate de que la opción seleccionada sea sin proxy o directa.
Error 102 (net::ERR_CONNECTION_REFUSED): El servidor ha rechazado la conexión.

---

### Post by hictio on 2012-09-30
El router en si no tiene ningún firewall o similar activo?
miubuntuserver.no-ip.org resuelve a una dirección IP pública, pero ni siquiera responde a un ping.

---

### Post by sergioc on 2012-09-30
La verdad que no se, me fije pero no veo ninguna opción que incluya "firewall", si queres y no te es molestia.. yo podría descargar team viewer y darte acceso a mis pcs, no se que hacer, yo hago lo que vos me digas.

---

### Post by sergioc on 2012-09-30
Ahí arregle algo que había hecho mal, las DNS no se habían guardado, tuve que acceder como root para que me tome el cambio.

```
david@ubuntu:~$ ping miubuntuserver.no-ip.org
PING miubuntuserver.no-ip.org (190.172.66.181) 56(84) bytes of data.
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=1 ttl=63 time=1.62 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=2 ttl=63 time=1.51 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=3 ttl=63 time=1.46 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=4 ttl=63 time=1.54 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=5 ttl=63 time=1.42 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=6 ttl=63 time=1.79 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=7 ttl=63 time=1.45 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=8 ttl=63 time=1.44 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=9 ttl=63 time=1.49 ms
64 bytes from 190-172-66-181.speedy.com.ar (190.172.66.181): icmp_req=10 ttl=63 time=1.50 ms
^[^C
--- miubuntuserver.no-ip.org ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 13285ms
rtt min/avg/max/mdev = 1.428/1.527/1.799/0.109 ms

```

Si entro a [http://miubuntuserver.no-ip.org:8189](http://miubuntuserver.no-ip.org:8189) pasa esto:
```
¡Vaya! Google Chrome no ha podido establecer conexión con la página miubuntuserver.no-ip.org:8189.
```

Si entro a la dirección pero sin el :8189 pasa esto:
[https://www.dropbox.com/s/zq62nulrxh053gq/miubuntuserver.png](https://www.dropbox.com/s/zq62nulrxh053gq/miubuntuserver.png)

---

### Post by hictio on 2012-10-01
Desde afuera de tu LAN el ping a miubuntuserver.no-ip.org sigue sin responder.

---

### Post by sergioc on 2012-10-01
No queres entrar a mi pc o ya es mucho pedir?

---

### Post by hictio on 2012-10-01
Probemos otro puerto.
Siempre el externo, en lugar del 8189, poné 8081.
El router se re-inicia cuando terminás de poner los settings, verdad?

---

### Post by hictio on 2012-10-01
> **sergioc said:**
> No queres entrar a mi pc o ya es mucho pedir?

Te comento, igual, que el problema, por lo que veo, no está en tu PC con Ubuntu Server, sino en el router.
De todas formas, NO deberías ofrecer acceso asi, a alguien que no conocés de internet, es una locura :)
Una pregunta, tu router, el que estás usando con configurado con el cliente de No-IP y que está haciendo el Port Forwarding, entre los settings, no tiene uno para poner una máquina en una DMZ?

---

### Post by sergioc on 2012-10-02
En este momento me surgió otro problema por lo cual no puedo hacer mas ninguna prueba hasta que esto se solucione, simplemente no me inicia el Ubuntu Server, 
esto es un problema del hardware, traigo este problema desde que compre la pc, la hice ver varias veces y nunca pudimos saber que parte del hardware ocasiona este problema, 
de todos modos dejándola un tiempo sin tocar luego intentas y arranca, por suerte la usare de server así que una ves configurada correctamente ya no la apagare mas, 
pero no siempre pasa esto, hoy me toco vivir esto, mañana o hoy mas tarde seguro se solucionara.

Por otro lado cambie el puerto como me indicaste y si tengo DMZ..
[https://www.dropbox.com/s/lp0b9bshfzfkmw6/dmz.png](https://www.dropbox.com/s/lp0b9bshfzfkmw6/dmz.png)

Pero como te dije tengo el server apagado, te avisare cuando logre encenderlo.

Y por ultimo tienes razón en eso del acceso, pero bueno no tengo nada que perder y sos una persona que me viene ayudando pacientemente desde hace muchos días 
por otro lado si no diera acceso de todos modos cualquier usuario medio avanzado puede destruir todo de mi pc sin ningún permiso, 
cosa que me tendrás que enseñar a evitar una vez logrado el objetivo de tener el server en marcha, ah! y ademas vos no sos alguien, vos sos una maquina o por lo menos eso siempre pensé.
:|

Me da mucho gusto poder estar en contacto con vos, valoro mucho tu colaboración, Saludos!

---

### Post by sergioc on 2012-10-03
Bueno, desarme toda la pc y la arme de vuelta y veo que el cooler del micro tiene de 4 patitas 2 quebradas, lo cual no agarra bien y se mueve, ademas le faltaría gel refrigerante, voy a ver si en estos días le compro esas cosas y de paso le compro una carcasa nueva, si supiera que alguna pieza mas le este fallando se la compraría pero no lo se, voy a probar con eso que dije primero.

---

### Post by hictio on 2012-10-04
Si, resolvé todos los problemas de hardware antes. No tiene sentido configurar nada si la máquina te va a dejar a pie después :)

---

