---
title: "Deluge, puertos, router y otros misterios..."
date: 2009-05-11
forum: Software
---

### Post by aledruetta on 2009-05-11
Hola comunidad! 
 
Tengo un problema que no sé si es un problema. Ese es el problema. 
 
Me explico: 
 
Instalé Deluge para bajar archivos torrents. Estuve leyendo en el foro y en otros sitios información sobre la configuración de esta aplicación, siguiendo algunas recomendaciones que iba encontrando en el camino, pero, a esta altura estoy bastante confundido. 
 
El equipo es un laptop con Ubuntu Jaunty conectado de forma inalámbrica a un router **TP-Link TL-WR542G**. El servicio de Internet, supuestamente, me brinda 3 Mb de velocidad. Tengo instalado y activado, **gufw**, el firewall de Ubuntu. 
 
Deluge está bajando "The Wall" de Pink Floyd en este momento, a una velocidad de unos 40 Kb promedio. Se me ocurre que es poco. Entonces, lo primero que hago es ver en Preferencias cuáles son los puertos que está usando Deluge, y dice, por un lado, **"puerto activo: 56468"**, por otro lado: "Utilizando puertos aleatorios: **6881 hasta 6891** - Comprobar puertos activos". Al lado de "Comprobar..." hay un símbolo de atención dentro de un triángulo amarillo. Hago clik ahí, espero que termine la comprobación, y sigue igual. 
 
Entonces interpreto que hay algún problema de apertura de puertos. Voy al firewall; abro los puertos del 6881 al 6891 y el 56468. Compruebo, y sigue todo igual. 
 
Voy al Firefox, coloco **192.168.1** y abro la configuración del router. Me dirijo a Forwarding y abro los mismos puertos, colocando como IP **192.168.1.100**. Vuelvo a comprobar en Deluge, y todo sigue igual. 
 
Entonces instalo **nmap** y **zenmap** para escanear los puertos. Hago un Intense Scan de "localhost". Me devuelve, entre otras cosas: 
 
Interesting ports on localhost (127.0.0.1): 
Not shown: 999 closed ports 
PORT    STATE SERVICE VERSION 
631/tcp open  ipp     CUPS 1.3.9

Hago un Intense Scan de "192.168.1.1" y me devuelve: 
 
Not shown: 998 filtered ports 
PORT     STATE  SERVICE VERSION 
80/tcp   open   http    TP-LINK WR541G/542G WAP http config 
1900/tcp closed upnp
 
Y, finalmente, hago un Intense Scan de "192.168.1.100", con el resultado: 
 
SCRIPT ENGINE: Aborting script scan. 
Host 192.168.1.100 appears to be up ... good. 
All 1000 scanned ports on 192.168.1.100 are closed 
Too many fingerprints match this host to give specific OS details
 
Aclaro que estoy haciendo esto un poco a ciegas, porque fui siguiendo distintos tutoriales, sitios, foros, etc. Es decir, no sabía muy bien lo que hacía mientras lo hacía. 
 
Lo que no entiendo es:  
 
[B]¿Por qué si abrí los puertos en el firewall y en el router, estos no aparecen abiertos en los scan de zenmap, y en Deluge aparece el símbolo de advertencia? 
 
¿Es esto lo que está afectando la velocidad de descarga de Deluge o es otra cosa?[/B] 
 
Bueno, confío en la ayuda de ustedes para orientarme en la maraña, 
 
Saludos y gracias, 
El Aleph.

---

### Post by Mauro22 on 2009-05-11
Por lo que tengo entendido en nmap solo te devuelve los puertos abiertos "de interes" (vaya uno a saber para que :D) o sea que si el puerto del deluge esta abierto a nmap no le interesa mucho porque no es de utilidad.


Por lo que encontre, "Deluge" es un cliente de torrent, con esto se deduce que la velocidad de bajada de un torrent depende de:

* Popularidad del Archivo en cuestion (mayor cantidad de seeds)
* Velocidad de Subida de los seeds
* Velocidad de Bajada (y subida) del leecher (o sea vos)
* De los puertos


Vos haces hincapie en los puertos nada más.

1) Desactiva el firewall, el kernel viene con iptables corriendo que configurandolo bien, no haria falta poner otro firewall.

2) Tu ip de intranet es 192.168.1.100 siempre? o el router esta en DHCP?

3) Proba con otros programas similares, onda aMule a ver si tira ID Baja aun abriendo los puertos!


Saludos!

---

### Post by guillermolisi on 2009-05-11
> **Mauro22 said:**
> Por lo que tengo entendido en nmap solo te devuelve los puertos abiertos "de interes" (vaya uno a saber para que :D) o sea que si el puerto del deluge esta abierto a nmap no le interesa mucho porque no es de utilidad.


Por lo que encontre, "Deluge" es un cliente de torrent, con esto se deduce que la velocidad de bajada de un torrent depende de:

* Popularidad del Archivo en cuestion (mayor cantidad de seeds)
* Velocidad de Subida de los seeds
* Velocidad de Bajada (y subida) del leecher (o sea vos)
* De los puertos


Vos haces hincapie en los puertos nada más.

1) Desactiva el firewall, el kernel viene con iptables corriendo que configurandolo bien, no haria falta poner otro firewall.

2) Tu ip de intranet es 192.168.1.100 siempre? o el router esta en DHCP?

3) Proba con otros programas similares, onda aMule a ver si tira ID Baja aun abriendo los puertos!


Saludos!
El UFW no es "el firewall" en si mismo, es una interface de configuracion para no tener que lidiar directamente con las primitivas de IP-Tables.

El firewall propiamente dicho esta dentro del kernel de Linux y no se puede desactivar, solo configurar para que deje salir y deje entrar todo el trafico que reciba.

Nunca use Deluge pero si tiene un opcion para encriptar los paquetes, mejor activarla,  asi el ISP no los detecta y dropea, disminuyendo el rendimiento de la conexion con otros peers.

---

### Post by guidito73 on 2009-05-11
Puede ser también que tu ISP esté bloqueando puertos...

Y para descartar todo eso, podés bajar alguna versión de Ubuntu en torrent un ratito para ver la velocidad (suelen tener velocidades bastante altas).

Como dijo el amigo, un firewall me parece medio al dope estando en linux...

---

### Post by aledruetta on 2009-05-12
> **Mauro22 said:**
> 2) Tu ip de intranet es 192.168.1.100 siempre? o el router esta en DHCP?

3) Proba con otros programas similares, onda aMule a ver si tira ID Baja aun abriendo los puertos!


Saludos!

Hola Mauro,

Probé con aMule y me tira ID Baja.

Y la ip es esa siempre. Esta es la única máquina conectada al router (inalambrico). Francamente, no sé qué es DHCP.

Gracias por tu colaboración,
Alejandro.

---

### Post by aledruetta on 2009-05-12
> **guillermolisi said:**
> Nunca use Deluge pero si tiene un opcion para encriptar los paquetes, mejor activarla,  asi el ISP no los detecta y dropea, disminuyendo el rendimiento de la conexion con otros peers.

Hola Guillermo,

Tiene encriptación y está activada.

Gracias por tu colaboración,
Alejandro.

---

### Post by Mauro22 on 2009-05-12
Si tenes un router inalambrico tenes que tener un modem (configurado como router) que le da señal de internet al router y este a las pcs no?


En ese caso tenes que abrir los puertos en el modem tambien, para que pasen al router y luego a la pc.

---

### Post by aledruetta on 2009-05-13
> **Mauro22 said:**
> Si tenes un router inalambrico tenes que tener un modem (configurado como router) que le da señal de internet al router y este a las pcs no?


En ese caso tenes que abrir los puertos en el modem tambien, para que pasen al router y luego a la pc.

Gracias Mauro,

No se me había ocurrido eso. Es un cablemodem Motorola SBV5121. Pero ahí, sí que no tengo la más mínima idea de cómo acceder a él para abrir sus puertos.

Saludos,
Alejandro.

---

### Post by dirty fingers on 2009-05-13
El deluge y tiene soporte upnp así que si tu router tiene la opción habilitada se abren solos los puertos.

En el deluge si pones puerto aleatorio tira cualquiera(es impredecible, imposible usar esta opcion junto a un firewall). 
Así desactiva la opción, pone un rango en la opción de abajo (ej:6881-6891) (va a tomar el primero libre) y en el gufw vas a preconfigurado y agregas las reglas de deluge.
[[IMG]http://img217.imageshack.us/img217/8616/pantallazohmx.th.png[/IMG]]("http://img217.imageshack.us/my.php?image=pantallazohmx.png")

---

### Post by aledruetta on 2009-05-13
> **dirty fingers said:**
> El deluge y tiene soporte upnp así que si tu router tiene la opción habilitada se abren solos los puertos.

En el deluge si pones puerto aleatorio tira cualquiera(es impredecible, imposible usar esta opcion junto a un firewall). 
Así desactiva la opción, pone un rango en la opción de abajo (ej:6881-6891) (va a tomar el primero libre) y en el gufw vas a preconfigurado y agregas las reglas de deluge.
[[IMG]http://img217.imageshack.us/img217/8616/pantallazohmx.th.png[/IMG]]("http://img217.imageshack.us/my.php?image=pantallazohmx.png")

Magia!!! Ahora sí, aparentemente esa fue la solución.

Saludos y muchas gracias,
Alejandro.

---

