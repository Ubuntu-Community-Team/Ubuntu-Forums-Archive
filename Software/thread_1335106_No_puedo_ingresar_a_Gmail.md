---
title: "No puedo ingresar a Gmail"
date: 2009-11-21
forum: Software
---

### Post by lopulus on 2009-11-21
hola gente! Yo tengo un problema en el cual no puedo ingresar a gmail... Si entro a otras paginas como esta por ejemplo.
cuando coloco en un terminal "ping gmail.com" me aparece lo siguiente:
ping: unknown host gmail.com
Tengan en consideracion que soy novato en ubuntu... (9.10)
Saludos y abrazos

---

### Post by oktubrer on 2009-11-23
Para poder ayudarte harían falta algunos datos más. ¿Cuando queres ingresar a la página que error aparece en el navegador? ¿que navegador usas? ¿como estás conectado a internet (red local, atrás de un proxy, etc).
Ejecutá en una consola ifconfig y copiá la salida, asi tenemos de donde arrancar.

---

### Post by staar on 2009-11-23
la dirección es [http://mail.google.com]("http://mail.google.com") ;-)

---

### Post by oktubrer on 2009-11-23
> **staar said:**
> la dirección es [http://mail.google.com]("http://mail.google.com") ;-)

Mmm estimo que tendría que acceder de ambas formas sin problemas, mail.google.com o [www.gmail.com](www.gmail.com).  El ping responde de todas formas.

---

### Post by alfplayer on 2009-11-23
> **staar said:**
> la dirección es [http://mail.google.com](http://mail.google.com) ;-)

gmail.com es válida (redirige a mail.google.com) y responde a pings.

---

### Post by guillermolisi on 2009-11-23
Por las dudas de que estes sufriendo algun problem de DNS fallidos/desactualizados de parte de tu ISP, proba poniendo la direccion IP de gmail.com en lugar de la URL y comenta que pasa.

---

### Post by lopulus on 2009-11-24
> **oktubrer said:**
> Para poder ayudarte harían falta algunos datos más. ¿Cuando queres ingresar a la página que error aparece en el navegador? ¿que navegador usas? ¿como estás conectado a internet (red local, atrás de un proxy, etc).
Ejecutá en una consola ifconfig y copiá la salida, asi tenemos de donde arrancar.
 aca esta la salida del ifconfig...


Link encap:Ethernet  direcciónHW 00:e0:4d:73:52:a6  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:27 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:74 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:74 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:8858 (8.8 KB)  TX bytes:8858 (8.8 KB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:186.12.230.201  P-t-P:10.64.64.64  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2541 errores:6 perdidos:0 overruns:0 frame:0
          Paquetes TX:2749 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:2565961 (2.5 MB)  TX bytes:324016 (324.0 KB)
Luego, lo que estoy usando es mozila firefox con un modem huawei E160 de claro 3G

No aparece ningun error, queda en la pagina de google (uso el link de esa pagina y tambien lo tipeo) como cargando indefinidamente...

Es  suficiente?

Gracias...

---

### Post by lopulus on 2009-11-24
> **alfplayer said:**
> gmail.com es válida (redirige a mail.google.com) y responde a pings.


Cuando puse gmail.com aparecio lo siguiente:

64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=1 ttl=49 time=417 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=2 ttl=49 time=428 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=3 ttl=49 time=427 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=4 ttl=49 time=425 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=5 ttl=49 time=415 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=6 ttl=49 time=425 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=7 ttl=49 time=425 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=8 ttl=49 time=409 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=9 ttl=49 time=424 ms
ju64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=10 ttl=49 time=434 ms
  y seguia sucesivamente....

---

### Post by lopulus on 2009-11-24
> **guillermolisi said:**
> Por las dudas de que estes sufriendo algun problem de DNS fallidos/desactualizados de parte de tu ISP, proba poniendo la direccion IP de gmail.com en lugar de la URL y comenta que pasa.

si la ip de gmail es 209.85.147.19 entonces lo que me aparecio fue solamente


PING 209.85.147.19 (209.85.147.19) 56(84) bytes of data.


gracias nuevamente...

---

### Post by oktubrer on 2009-11-24
Guillermo se refería a que pruebes ingresando en el navegador la IP de gmail.  ¿Por casualidad estás navegando con el Konqueror?  Porque históricamente la versión normal de Gmail no funcionaba con este navegador, había que pasar a la versión HTML, o cambiar la configuración de Konqueror para que ante Gmail se identifique como otro browser.

---

### Post by guillermolisi on 2009-11-24
> **lopulus said:**
> Cuando puse gmail.com aparecio lo siguiente:

64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=1 ttl=49 time=417 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=2 ttl=49 time=428 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=3 ttl=49 time=427 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=4 ttl=49 time=425 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=5 ttl=49 time=415 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=6 ttl=49 time=425 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=7 ttl=49 time=425 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=8 ttl=49 time=409 ms
64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=9 ttl=49 time=424 ms
ju64 bytes from ey-in-f83.1e100.net (74.125.79.83): icmp_seq=10 ttl=49 time=434 ms
  y seguia sucesivamente....
BTW, 400ms de lag me parece algo elevado.

---

### Post by guillermolisi on 2009-11-24
> **oktubrer said:**
> Guillermo se refería a que pruebes ingresando en el navegador la IP de gmail.  ¿Por casualidad estás navegando con el Konqueror?  Porque históricamente la versión normal de Gmail no funcionaba con este navegador, había que pasar a la versión HTML, o cambiar la configuración de Konqueror para que ante Gmail se identifique como otro browser.
Exactamente, gracias por la aclaracion, me interpretaste perfectamente bien.

---

### Post by lopulus on 2009-11-25
> **guillermolisi said:**
> Exactamente, gracias por la aclaracion, me interpretaste perfectamente bien.

Hola: El navegador que uso es el mozilla-firefox 3.5.5

---

### Post by alfplayer on 2009-11-25
Ese valor de ping puede estar muy elevado, y esto puede ser a causa de un modem o router fallando parcialmente. Se puede probar haciendo la prueba de ping nuevamente después de resetear el o los modems o routers según corresponda. También se puede probar reseteando switches si se están usando.

---

### Post by lopulus on 2009-11-26
Hola Gente: En principio quiero agradecerles las respuestas y la preocupacion. Quiero comentarles que ayer pude ingresar solo por una vez. Cuando sali y quis volver a ingresar ya no pude. No se si esto Complica o favorece la situacion.
Con respecto a lo que dicen de resetear el modem... No se como hacerlo....
Gracias nuevamente.

---

### Post by alfplayer on 2009-11-26
> **lopulus said:**
> Hola Gente: En principio quiero agradecerles las respuestas y la preocupacion. Quiero comentarles que ayer pude ingresar solo por una vez. Cuando sali y quis volver a ingresar ya no pude. No se si esto Complica o favorece la situacion.
Con respecto a lo que dicen de resetear el modem... No se como hacerlo....
Gracias nuevamente.

Algunos modems tienen un botón o pulsador de reset. Si no se hace con el botón se puede desconectar la alimentación (el cable de power) y volver a conectarlo después de unos segundos.

---

### Post by lopulus on 2009-11-26
> **alfplayer said:**
> Algunos modems tienen un botón o pulsador de reset. Si no se hace con el botón se puede desconectar la alimentación (el cable de power) y volver a conectarlo después de unos segundos.

El tema es que tengo un modem claro3G usb. Supongo que al sacarlo del puerto se deconecta la alimentacion. Si esto es así, ya lo he intentado y todo sigue igual...

---

### Post by Mauro22 on 2009-11-26
Esto es de Peru: [Hay mas]

[http://caminante.wordpress.com/2009/02/25/no-funciona-modem-internet-de-claro-3g-peru/](http://caminante.wordpress.com/2009/02/25/no-funciona-modem-internet-de-claro-3g-peru/)


Pero dice que claro 3g se lleva mal con Google y todo lo relacionado. Me parece que no es un problema de configuracion ni nada.

---

### Post by alfplayer on 2009-11-26
> **lopulus said:**
> El tema es que tengo un modem claro3G usb. Supongo que al sacarlo del puerto se deconecta la alimentacion. Si esto es así, ya lo he intentado y todo sigue igual...

Sí, al desconectarlo se apaga. Si calienta mucho se puede dejar un momento desconectado para esperar a que se enfríe. No creo que pueda ayudar más porque no tengo experiencia con 3G.

Sería bueno saber con qué otras páginas falla (si falla con alguna más), y también podría ser útil saber si hay antecedentes de problemas de conexión como el tuyo con Claro 3G en tu región.

---

### Post by guillermolisi on 2009-11-26
Si es un problema vinculado con como configura Claro su red, lo mejor es usar el comando "tracert <ip_de_gmail>" para ver por donde pasa y cuanto tarda, si llega a destino.

Por otra parte no vi comentarios sobre haber probado de poner la IP de Gmail en el browser en lugar de su URL (para verificar si es una cuestion relacionada con DNS).

---

### Post by emiliano_raso on 2009-11-26
Internet 3G de Claro tiene problema tambien con Google Earth aparte de Gmail.
Parece que tuviera un problema personal con Google
Lo vi antes de ayer y justo veo este thread.

Es por eso...

---

### Post by lopulus on 2009-11-27
> **guillermolisi said:**
> Si es un problema vinculado con como configura Claro su red, lo mejor es usar el comando "tracert <ip_de_gmail>" para ver por donde pasa y cuanto tarda, si llega a destino.

Por otra parte no vi comentarios sobre haber probado de poner la IP de Gmail en el browser en lugar de su URL (para verificar si es una cuestion relacionada con DNS).

hola! si el IP de Gmail es 72.14.205.83 me hace exactamente lo mismo, figura cargando en la solapa del navegador pero no accede a la pagina de  logging de gmail... ( recuerden que hsta hace un tiempo podia ingresar sin problemas...

Con respecto a tracert... Que debo hacer?

Saludos

---

### Post by guillermolisi on 2009-11-27
Para correr "tracert" abris una consola/terminal e ingresas ```
tracert <url/IP_de_destino>
``` (puede pedir que lo hagas con sudo).

Mostranos la salida que te brinde esa corrida.

Si te dice que no existe ese programa lo podes instalar desde los repositorios (el paquete se llama "traceroute").

---

### Post by lopulus on 2009-11-27
hola! esto es lo que me salio

[I]traceroute to 209.85.147.19 (209.85.147.19), 30 hops max, 60 byte packets
 1  192.168.17.1 (192.168.17.1)  3801.111 ms  3812.237 ms *
 2  * * *
 3  * * *
 4  * * host25.190-224-15.telecom.net.ar (190.224.15.25)  637.171 ms
 5  host25.200-117-124.telecom.net.ar (200.117.124.25)  696.341 ms  739.740 ms  2729.569 ms
 6  host166.190-225-252.telecom.net.ar (190.225.252.166)  2766.376 ms  2779.537 ms *
 7  * * *
 8  * * 209.85.254.70 (209.85.254.70)  349.718 ms
 9  216.239.43.94 (216.239.43.94)  539.708 ms * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * 209.85.251.182 (209.85.251.182)  843.820 ms 209.85.251.158 (209.85.251.158)  1003.745 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
[/I]

---

### Post by guillermolisi on 2009-11-27
Esa IP publica que pusiste, *209.85.147.19, *no es la de Gmail (que en definitiva es Tu Destino para la prueba con este comando).

Te muestro como ejemplo, como lo corri en una de las maquinas que uso y tambien pdras ver los tiempos de respuesta de cada salto en el camino hasta el destino (gmail.com)
```
guille@guillepc:~$ sudo tracert gmail.com
traceroute to gmail.com (74.125.79.83), 30 hops max, 60 byte packets
 1  hephaestus (192.168.0.10)  0.152 ms  0.128 ms  0.112 ms
 2  host1.190-139-97.telecom.net.ar (190.139.97.1)  2.080 ms  2.145 ms *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  209.85.252.6 (209.85.252.6)  30.839 ms  31.328 ms *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * 209.85.255.130 (209.85.255.130)  223.597 ms *
14  ey-in-f83.1e100.net (74.125.79.83)  224.154 ms * *
```

---

### Post by lopulus on 2009-11-27
Cual es la ip de gmail? y que deberia hacer para solucionarlo?

---

### Post by alfplayer on 2009-11-27
Ejecutando el comando que mostró Guillermo en el post anterior se podría tener más información. Igualmente, si el problema es el que señala Emiliano no tendría solución hasta que las empresas responsables lo resuelvan.

---

### Post by guillermolisi on 2009-11-27
> **lopulus said:**
> Cual es la ip de gmail? y que deberia hacer para solucionarlo?
Le tenes a la vista:
> traceroute to gmail.com (**74.125.79.83**), 30 hops max, 60 byte packets
Si es una cuestion de implementacion de infraestructura de red del ISP, habla con ellos.
Si el problema esta en otro lado, primero hay que determinar donde es y despues ver que se hace.

---

### Post by Mauro22 on 2009-11-27
> **guillermolisi said:**
> Esa IP publica que pusiste, *209.85.147.19, *no es la de Gmail (que en definitiva es Tu Destino para la prueba con este comando).

Pertenece a Google, pero no responde a PING...

Para mi que Claro lo redirecciona a esa que está muerta.

```
blackice@blackice-paradise:~$ whois 209.85.147.19

OrgName:    Google Inc. 
OrgID:      GOGL
Address:    1600 Amphitheatre Parkway
City:       Mountain View
StateProv:  CA
PostalCode: 94043
Country:    US

NetRange:   209.85.128.0 - 209.85.255.255 
CIDR:       209.85.128.0/17 
NetName:    GOOGLE
NetHandle:  NET-209-85-128-0-1
Parent:     NET-209-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.GOOGLE.COM
NameServer: NS2.GOOGLE.COM
NameServer: NS3.GOOGLE.COM
NameServer: NS4.GOOGLE.COM
Comment:    
RegDate:    2006-01-13
Updated:    2006-06-01

OrgTechHandle: ZG39-ARIN
OrgTechName:   Google Inc. 
OrgTechPhone:  +1-650-318-0200
OrgTechEmail:  arin-contact@google.com

# ARIN WHOIS database, last updated 2009-11-26 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.
```

---

### Post by lopulus on 2009-11-29
Ya no se que mas probar y que hacer...
Aconsejenme!

Recien acabo de ingresar a gmail desde W$ y no tuve ningun problema, inclusive lo ha hecho como lo hacia de igual manera que en ubuntu antes que tenga problemas. De ahi supongo que el problemas es en Ubuntu. Cuando hice un ping en "simbolo de sistema" lo termino en solo tres pasos. 
No se si esto puede ayudar en algo...

---

### Post by guillermolisi on 2009-11-29
> **lopulus said:**
> Ya no se que mas probar y que hacer...
Aconsejenme!
Desde mi punto de vista hubo cantidad de consejos y pruebas para realizar pero no vi que resutados obtuviste y tampoco que hayas repetido algunas pruebas con datos que se modificaron (como la IP de Gmail.com) para ver sus nuevas salidas que son de vital importancia para los que estan siguiendo el tema ya que en base a ellas surgiran otras pruebas o conclusiones.

Si algunos puntos te resultan dificiles de entender, no tenes mas que preguntar para que se te explique mejor.

La solucion la logras vos, nosotros ayudamos.

---

### Post by lopulus on 2009-11-29
> **guillermolisi said:**
> Esa IP publica que pusiste, *209.85.147.19, *no es la de Gmail (que en definitiva es Tu Destino para la prueba con este comando).

Te muestro como ejemplo, como lo corri en una de las maquinas que uso y tambien pdras ver los tiempos de respuesta de cada salto en el camino hasta el destino (gmail.com)
```
guille@guillepc:~$ sudo tracert gmail.com
traceroute to gmail.com (74.125.79.83), 30 hops max, 60 byte packets
 1  hephaestus (192.168.0.10)  0.152 ms  0.128 ms  0.112 ms
 2  host1.190-139-97.telecom.net.ar (190.139.97.1)  2.080 ms  2.145 ms *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  209.85.252.6 (209.85.252.6)  30.839 ms  31.328 ms *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * 209.85.255.130 (209.85.255.130)  223.597 ms *
14  ey-in-f83.1e100.net (74.125.79.83)  224.154 ms * *
```

guillermo:  aca esta el tracert para gmail:

lopulus@Lopulus:~$ sudo tracert gmail.com
traceroute to gmail.com (74.125.79.83), 30 hops max, 60 byte packets
 1  192.168.17.13 (192.168.17.13)  1185.465 ms  1185.402 ms *
 2  * * *
 3  * * *
 4  * * host25.190-224-15.telecom.net.ar (190.224.15.25)  1646.289 ms
 5  host25.200-117-124.telecom.net.ar (200.117.124.25)  1646.209 ms  1677.170 ms *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * 209.85.249.199 (209.85.249.199)  1017.113 ms  1109.438 ms
11  * * *
12  * * *
13  * * *
14  209.85.255.126 (209.85.255.126)  1774.287 ms * 209.85.255.118 (209.85.255.118)  1774.203 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * ey-in-f83.1e100.net (74.125.79.83)  1123.287 ms


Ahora para la ip que sale a continuacion...(74.125.79.83)

me sale:

lopulus@Lopulus:~$ sudo tracert 74.125.79.83
traceroute to 74.125.79.83 (74.125.79.83), 30 hops max, 60 byte packets
 1  192.168.17.13 (192.168.17.13)  3248.259 ms  3269.629 ms *
 2  * * *
 3  * * *
 4  * * host25.190-224-15.telecom.net.ar (190.224.15.25)  905.834 ms
 5  host25.200-117-124.telecom.net.ar (200.117.124.25)  1078.501 ms  1078.492 ms  1461.198 ms
 6  cog01ri-pos16-0-0.tasf.telecom.net.ar (200.3.32.134)  1763.740 ms  1923.671 ms  1923.586 ms
 7  host146.190-225-248.telecom.net.ar (190.225.248.146)  2121.090 ms  2121.083 ms  2121.078 ms
 8  209.85.254.70 (209.85.254.70)  2111.356 ms  2121.063 ms  709.760 ms
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * 209.85.255.166 (209.85.255.166)  3406.748 ms
14  209.85.255.130 (209.85.255.130)  3406.566 ms * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * ey-in-f83.1e100.net (74.125.79.83)  2469.499 ms  2490.710 ms

---

### Post by Mauro22 on 2009-11-29
Llegar, llega, pero puede ser que te "desconecte" por el tiempo en llegar... 224 ms de Guillermo vs 2400 tuyos... HAY diferencia.

---

### Post by lopulus on 2009-11-29
> **Mauro22 said:**
> Llegar, llega, pero puede ser que te "desconecte" por el tiempo en llegar... 224 ms de Guillermo vs 2400 tuyos... HAY diferencia.

Ok, supongo que ese es el tiempo que tarda en cargar la pagina.... Ahora bien. En  W$$$ lo carga rapidisimo con google Chrome. Ahora aqui con Chromiun y con Galeon  hace lo mismo que con mozilla....

Desconcierto total....

---

### Post by guillermolisi on 2009-11-29
Me llama poderosamente la atencion esta primera linea porque desde el vamos hay mucha demora y no deberia ser asi:
> lopulus@Lopulus:~$ sudo tracert gmail.com
traceroute to gmail.com (74.125.79.83), 30 hops max, 60 byte packets
 1  192.168.17.13 (192.168.17.13) ** 1185.465 ms  1185.402 ms** *

Si no interpreto mal, es la demora que tenes para salir de tu LAN por la placa de red hacia tu gateway (que podria ser un router o directamente el modem ADSL).

Para mi, ahi ya tenes algun inconveniente. El resto es consecuencia de ello.

Fijate la diferencia con el ejemplo que paso en donde el lag para la misma situacion (llegar a un gateway). Estamos hablando de una diferencia de 1000 contra casi cero milisegundos !

Pasanos el contenido de tu archivo /etc/network/interfaces asi vamos viendo como tenes configurada la red.

---

### Post by lopulus on 2009-11-29
> **guillermolisi said:**
> Pasanos el contenido de tu archivo /etc/network/interfaces asi vamos viendo como tenes configurada la red.


en un terminal coloque lo siguiente: gksudo gedit /etc/network/interfaces y me salio esto

[I]auto lo
iface lo inet loopback
[/I]

Esta bien?

---

### Post by guillermolisi on 2009-11-29
> **lopulus said:**
> en un terminal coloque lo siguiente: gksudo gedit /etc/network/interfaces y me salio esto

[I]auto lo
iface lo inet loopback
[/I]

Esta bien?
Podrias ahora ingresar en una consola/terminal el comando "ifconfig -a" (sin las comillas) y mostrarnos su salida ?

Disculpa que el tema venga como con cuentagotas pero con cada resultado van surgiendo distintas cosas.

La LAN que estas usando esta compuesta por una PC y un modem ADSL ? Hay mas componentes ? El modem esta como router o como bridge ?

---

### Post by oktubrer on 2009-11-29
Tendríamos que ver también que DNS estás usando en Ubuntu y cuales en W$, por las dudas de que sean distintos.  Con el comando que te pasó Guillermo tenemos la primer mitad, para ver la configuración en W$ desde una ventana de DOS (vas a Inicio - Ejecutar y escribis "cmd" sin comillas) ejecutá ipconfig.

---

### Post by mama21mama on 2009-11-30
A mi me anda todo perfecto, debo mencionar que uso [OpenDNS]("http://mamalibre.eshost.com.ar/?q=node/128").

> mama@mama-desktop:~$ ping gmail.com
PING gmail.com (74.125.127.83) 56(84) bytes of data.
64 bytes from pz-in-f83.1e100.net (74.125.127.83): icmp_seq=1 ttl=49 time=249 ms
64 bytes from pz-in-f83.1e100.net (74.125.127.83): icmp_seq=2 ttl=49 time=249 ms
64 bytes from pz-in-f83.1e100.net (74.125.127.83): icmp_seq=3 ttl=49 time=250 ms


Saludos

---

### Post by lopulus on 2009-11-30
> **guillermolisi said:**
> Podrias ahora ingresar en una consola/terminal el comando "ifconfig -a" (sin las comillas) y mostrarnos su salida ?

Disculpa que el tema venga como con cuentagotas pero con cada resultado van surgiendo distintas cosas.

La LAN que estas usando esta compuesta por una PC y un modem ADSL ? Hay mas componentes ? El modem esta como router o como bridge ?


aca esta lo que me tiro. Lo de cuentagotas no importa...jejeje, yo soy mas lento
eth0      Link encap:Ethernet  direcciónHW 00:e0:4d:73:52:a6  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:27 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:82 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:82 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:9759 (9.7 KB)  TX bytes:9759 (9.7 KB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:186.13.158.243  P-t-P:10.64.64.64  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:980 errores:11 perdidos:0 overruns:0 frame:0
          Paquetes TX:997 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:933784 (933.7 KB)  TX bytes:153744 (153.7 KB)

---

### Post by guillermolisi on 2009-11-30
Aqui tenes algo que no esta funcionando bien:
> ppp0      Link encap:razz:rotocolo punto a punto  
          Direc. inet:186.13.158.243  P-t-P:10.64.64.64  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1500  Métrica:1
          **[COLOR=Red]Paquetes RX:980 errores:11[/COLOR]** perdidos:0 overruns:0 frame:0
          Paquetes TX:997 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:933784 (933.7 KB)  TX bytes:153744 (153.7 KB)

---

### Post by lopulus on 2009-11-30
Hola! esto es lo que me salio en W$


adapatdor ethernet conexion de area local
	Estado de los medios ....: medios desconectados
Adaptador PPP Calro AR
	Subfijo de conexion especifica:
	Direccion ip...................: 186.12.76.75
	Mascara de subred..............: 255.255.255.255
	Puerta de enlace predeterminada: 186.12.76.75

Espero que sea de ayuda

---

### Post by lopulus on 2009-11-30
> **guillermolisi said:**
> Aqui tenes algo que no esta funcionando bien:


Al fin encontramos algo!!!

Eso que significa y que debo hacer

---

### Post by guillermolisi on 2009-11-30
> **lopulus said:**
> Al fin encontramos algo!!!

Eso que significa y que debo hacer
Eso significa que ese modem tiene problemas en la recepcion de paquetes y eso hace que reintente la transmision de cada paquete fallido hasta que confirma una buena recepcion del otro lado de la conexion con la consecuente demora.

Me llama la atencion que en el post #7 de este thread tambien muestra errores en la recepcion de paquetes (lo vi releyendo todo el thread de nuevo).

EDIT: Windows viene con tracert de fabrica ? Porque seria muy bueno correrlo mientras usas Windows para comparar lags.

---

### Post by lopulus on 2009-11-30
hola: si se puede ejecutar el tracert, va por lo menos yo probe y anduvo. aca van los datos
H:\Documents and Settings\Administrador>tracert [www.gmail.com](www.gmail.com)

Traza a la dirección googlemail.l.google.com [74.125.159.19]
sobre un máximo de 30 saltos:

  1   388 ms   410 ms   380 ms  192.168.17.13
  2   370 ms   429 ms   429 ms  170.51.254.53
  3   337 ms   410 ms   389 ms  170.51.254.54
  4   359 ms   380 ms   399 ms  host25.190-224-15.telecom.net.ar [190.224.15.25]

  5   368 ms   419 ms   439 ms  host137.190-225-249.telecom.net.ar [190.225.249.
137]
  6   348 ms   399 ms   419 ms  host166.190-225-252.telecom.net.ar [190.225.252.
166]
  7   426 ms  1540 ms   989 ms  host146.190-225-248.telecom.net.ar [190.225.248.
146]
  8  2414 ms   588 ms  1159 ms  209.85.251.28
  9   369 ms   200 ms   199 ms  216.239.43.86
 10     *        *        *     Tiempo de espera agotado para esta solicitud.
 11   232 ms   239 ms   240 ms  72.14.236.173
 12   269 ms   269 ms   289 ms  209.85.254.252
 13   247 ms   249 ms   249 ms  72.14.232.213
 14   268 ms   249 ms   279 ms  209.85.254.14
 15   328 ms   349 ms   370 ms  yi-in-f19.1e100.net [74.125.159.19]

Traza completa.


Espero que sea de ayuda...

---

### Post by alfplayer on 2009-11-30
> **lopulus said:**
> Hola! esto es lo que me salio en W$


adapatdor ethernet conexion de area local
    Estado de los medios ....: medios desconectados
Adaptador PPP Calro AR
    Subfijo de conexion especifica:
    Direccion ip...................: 186.12.76.75
    Mascara de subred..............: 255.255.255.255
    Puerta de enlace predeterminada: 186.12.76.75

Espero que sea de ayuda

dirección IP igual a la puerta de enlace ? :shock:

---

### Post by oktubrer on 2009-11-30
> **alfplayer said:**
> dirección IP igual a la puerta de enlace ? :shock:

Creo recordar que en W$ si estableces la conexión directo desde la pc (no con un router o lan) siempre te establece por defecto el gateway con la ip, no sería un error.

---

### Post by guillermolisi on 2009-12-01
Los resultados del tracert bajo Windows tambien me parecen malos. De hecho en algun momento la demora crece hasta que da "tiempo de espera agotado".

Otra cosa que me llama la atencion es que entiendo estas usando un modem 3G de Claro pero la conexion a Internet sale a traves de Telecom. Es correcto esto ?

---

### Post by lopulus on 2009-12-01
Si, eso parece. No se como trabaja todo esto... en los dos tracert da lo mismo

---

### Post by guillermolisi on 2009-12-01
> **lopulus said:**
> Si, eso parece. No se como trabaja todo esto... en los dos tracert da lo mismo
Tenes posibilidad de probar con otro modem 3G de Claro y que sea del mismo modelo o, alternativamente, probar tu modem en otra maquina y repetir los tracert para gmail y tomar nota de los valores que arrojen ?

Como para determinar si es el modem u otra cosa.

---

### Post by lopulus on 2009-12-01
Si, Creo que puedo hacer las dos cosas. Ahora, el tracert lo tengo que voy a probar en otra maquina sera bajo W$ ya que esa no tiene ubuntu, pero supongo que es lo mismo ya que el problema es similar tanto en ubuntu como en W$...
Eso me llevara un par de dias ya que tengo que pedir prestada una notebook...

Saludos...

---

### Post by lopulus on 2009-12-02
Hola: Aca van los datos que logre obtener

[COLOR="Red"]Con otro modem en W$ en mi pc[/COLOR]



Microsoft Windows XP [Versión 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.
H:\Documents and Settings\Administrador>tracert gmail.com
Traza a la dirección gmail.com [74.125.79.83]
sobre un máximo de 30 saltos:
  1   178 ms   189 ms   160 ms  192.168.17.234
  2   159 ms   159 ms   159 ms  10.2.6.205
  3   158 ms   199 ms   199 ms  10.2.2.2
  4   178 ms   189 ms   159 ms  170.51.254.53
  5   168 ms   199 ms   189 ms  170.51.254.54
  6   188 ms   200 ms   189 ms  host25.190-224-15.telecom.net.ar [190.224.15.25]
  7   178 ms   190 ms   160 ms  host29.200-117-124.telecom.net.ar [200.117.124.29]
  8   189 ms   159 ms   160 ms  cog01ri-pos16-1-0.tasf.telecom.net.ar [200.3.32.138]
  9   188 ms   170 ms   188 ms  host142.190-225-248.telecom.net.ar [190.225.248.142]
 10   177 ms   160 ms   159 ms  209.85.251.28
 11   197 ms   199 ms   200 ms  209.85.251.25
 12   309 ms   420 ms   340 ms  209.85.249.199
 13   370 ms   430 ms   369 ms  209.85.250.55
 14   408 ms   409 ms   400 ms  72.14.232.149
 15   399 ms   439 ms   399 ms  209.85.255.143
 16   388 ms   439 ms   440 ms  209.85.255.122
 17   399 ms   400 ms   400 ms  ey-in-f83.1e100.net [74.125.79.83]

Traza completa.

_________________________________________________________________________

[COLOR="Red"]Otro modem en ubuntu[/COLOR]

lopulus@Lopulus:~$ sudo tracert gmail.com

[sudo] password for lopulus: 

traceroute to gmail.com (209.85.225.83), 30 hops max, 60 byte packets
 1  192.168.17.122 (192.168.17.122)  342.199 ms  529.336 ms *
 2  * * *
 3  * * *
 4  * * 170.51.254.53 (170.51.254.53)  753.796 ms
 5  170.51.254.54 (170.51.254.54)  883.658 ms * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * 209.85.251.28 (209.85.251.28)  654.220 ms 209.85.254.70 (209.85.254.70)  654.157 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  209.85.241.22 (209.85.241.22)  477.070 ms  834.433 ms *
17  * * *
18  * * *
19  * * iy-in-f83.1e100.net (209.85.225.83)  821.891 ms
__________________________________________________________________________

[COLOR="Red"]con otro modem en una notebook y W$[/COLOR]

Microsoft Windows XP [Versión 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\0jito>tracert gmail.com
Traza a la dirección gmail.com [74.125.79.83]
sobre un máximo de 30 saltos:

  1   572 ms   389 ms   609 ms  192.168.17.13
  2   378 ms   600 ms   429 ms  170.51.254.53
  3   368 ms   739 ms   409 ms  170.51.254.54
  4   378 ms   449 ms   429 ms  host25.190-224-15.telecom.net.ar [190.224.15.25]
  5   440 ms   469 ms   479 ms  host25.200-117-124.telecom.net.ar [200.117.124.25]
  6   358 ms   429 ms   430 ms  ret01rt-pos16-0-0.tasf.telecom.net.ar [200.3.32.118]
  7   379 ms   439 ms   440 ms  host146.190-225-248.telecom.net.ar [190.225.248.146]
  8   465 ms   429 ms   439 ms  209.85.251.28
  9   428 ms   469 ms   479 ms  209.85.251.25
 10   517 ms   599 ms   570 ms  209.85.249.199
 11   869 ms  2309 ms   729 ms  209.85.250.55
 12   676 ms   409 ms   399 ms  72.14.232.149
 13   438 ms   409 ms   619 ms  209.85.255.166
 14  1167 ms   442 ms   396 ms  209.85.255.130
 15   305 ms   299 ms   309 ms  ey-in-f83.1e100.net [74.125.79.83]

Traza completa.

---

### Post by lopulus on 2009-12-02
No se si sirve de dato pero desde pidgin me aparecen los correos no leidos... obviamente si los quiero abrir no los abre...

Saludos

---

### Post by guillermolisi on 2009-12-02
Indudablemente y en base a los que acabas de aportar el modem original algo malo tiene.
Fijate los valores en milisegundos que registraron las corridas con tracert antes y ahora, con las ultimas pruebas, tanto en Win como en Ubuntu.

Que les parece a los demas ? Ven algun dato mas ?

---

### Post by Mauro22 on 2009-12-02
> **guillermolisi said:**
> Que les parece a los demas ? Ven algun dato mas ?

El tiempo bajó, poco pero bajó.


Dos cosas veo:

1) En los 3 casos, Ventanas tarda "menos" en llegar. 

2) En los 3 casos, tarda en salir de la pc... el primer salto es a una red intranet:

192.168.17.234
192.168.17.122
192.168.17.13

Tarda mucho, promedio de 300ms cuando debe ser mucho menos (estamos hablando de pcs en la misma red.

Luego los DNS:

170.51.254.53
170.51.254.54

Pertenecen a LAWRENCIO.CTIMOVIL.COM.AR 

esos tienen demora...

lo demas es consecuencia de esto.

Mala getaway + malos DNS... 


Por lo que veo.

---

### Post by lopulus on 2009-12-03
> **guillermolisi said:**
> Indudablemente y en base a los que acabas de aportar el modem original algo malo tiene.
Fijate los valores en milisegundos que registraron las corridas con tracert antes y ahora, con las ultimas pruebas, tanto en Win como en Ubuntu.

Que les parece a los demas ? Ven algun dato mas ?

Quiero aclarar que cuando probe el otro modem en ubuntu, tampoco pude ingresar a Gmail....

Con respecto a lo que dice mauro ¿que debo hacer con respecto al getaway y a los dns?

---

### Post by mama21mama on 2009-12-03
Repito:

[OpenDNS]("http://mamalibre.eshost.com.ar/?q=node/128") es un servicio gratuito de DNS, las DNS que usamos por defecto es la que nos da nuestro proveedor ISP, que nos siempre funciona como deberia, OpenDNS nos da un servicio gratuito, mas seguro, mas rapido, mas estable y con algunas caracteristicas que la mayoria de proveedores ISP no dan como Anti-Phising o paginas con malware, y hasta nos corrigue si escribimos mal alguna direccion.


[Instalar en Ubuntu]("http://mamalibre.eshost.com.ar/?q=node/128")

---

### Post by lopulus on 2009-12-03
hola gente: Aca de nuevo. hice el tuto de dns de mama21 y el tracert de gmail.com quedo asi

lopulus@Lopulus:~$ sudo tracert gmail.com
traceroute to gmail.com (74.125.79.83), 30 hops max, 60 byte packets
 1  192.168.17.161 (192.168.17.161)  319.397 ms  479.347 ms *
 2  * * *
 3  * * *
 4  * * *
 5  host29.200-117-124.telecom.net.ar (200.117.124.29)  909.694 ms  1027.130 ms  1099.729 ms
 6  host14.200-117-124.telecom.net.ar (200.117.124.14)  1167.071 ms  1227.101 ms  1707.007 ms
 7  host142.190-225-248.telecom.net.ar (190.225.248.142)  1756.966 ms  1856.988 ms *
 8  * * 209.85.254.70 (209.85.254.70)  489.744 ms
 9  209.85.251.25 (209.85.251.25)  689.685 ms * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * 209.85.255.122 (209.85.255.122)  946.790 ms 209.85.255.130 (209.85.255.130)  1134.142 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  ey-in-f83.1e100.net (74.125.79.83)  711.689 ms  784.122 ms *



Cuando puedo acceder de vez en cuando a la pagina de registracion de gmail, me logeo y despues trabaja normalmente, puedo ver correos y todo lo que implica ingresar a la casilla de correo...
Gracias nuevamente.,

---

### Post by lopulus on 2009-12-05
Hola: Alguna otra prueba para hacer o algo para cambiar?

---

### Post by guillermolisi on 2009-12-05
> **lopulus said:**
> Hola: Alguna otra prueba para hacer o algo para cambiar?
Yo cambiaria de proveedor.

Tenes la conexion con Claro y cuando te conectas utilizas la infraestructura de Telecom (porque Telmex no tiene la misma infraestructura de red que las telefonicas que "compraron" ENTEL).

Ser cliente de Telecom o Telefonica es tan malo como serlo de Telmex, pero por lo menos poseen infraestructura de red propia.

---

