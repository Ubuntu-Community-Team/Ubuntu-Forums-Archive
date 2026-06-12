---
title: "Duda Migrando BrazilFW a Ubuntu Server"
date: 2009-09-10
forum: Software
---

### Post by jawifi01 on 2009-09-10
Hola, envie este mail a la lista y no aparece y tampoco recibi respuestas, espero que por este medio aparezca mi consulta a fin de poder solucionar esta duda, gracias de antemano y perdon por la repeticion si a alguien le llego el otro mensaje.

Gente, buenas noches, los molesto porque estoy tratando de mudar el Router Wifi / Acces Point (se me confunden los términos) que tengo armadito en una pentium III con brazilfw.
Quiero hacer esto porque con es distribucion me siento un poco acotado, ya que no tiene bash y muchas otras cosas, entonces decidi pasarlo a Ubuntu Server para de paso tener todo un poco mas homogeneo.

El tema es que me hice un embrollo cpn la configuracion y no se como salir de el, ya que yo tengo un servicio de internet comunitario que dan unos chicos de la zona donde vivo, y ellos me dan ina ip y los demas datos de configuracion, para acceder a internet, que son:

IP Fija: 192.168.1.XX
DNS: 200.51.211.7 / 192.168.1.2
GW: 192.168.1.2
Mask: 255.255.255.0

Yo tengo mi red en BFW con:
IP: 192.168.0.254
Mask:255.255.255.0

y ahora lo quiero pasar a ubuntu server y no se como configurarlo, tengo la maquina con 3 placas de red, 2 ethernet y una wifi (que despues usare para que funcione como AP).
Por eso es que hago esta consulta, a ver si me pueden tirar alguna idea sobre como asignar estos datos al servidor, o si hay algun script en algun lado, para poder configurarlo y que haga lo que necesito, ya que el BFW se instala con un menu paso a paso y es sencillo, pero no se aprene nada, ya que hace todo solo y quiero afinarlo.

Gracias

---

### Post by pablo.s on 2009-09-10
```
man route
```

y lo demás te lo dejo a vos
porque querés aprender.

---

### Post by jawifi01 on 2009-09-10
> **pablo.s said:**
> ```
man route
```y lo demás te lo dejo a vos
porque querés aprender.


Gracias, pensé que consultaba a personas un poquito más solidarias!! quiero aprender, pero necesito elementos, esta respuesta me suena a cargada.

Si sabia que me iban a cargar no preguntaba nada.

Saludos

---

### Post by guillermolisi on 2009-09-10
> **jawifi01 said:**
> Hola, envie este mail a la lista y no aparece y tampoco recibi respuestas, espero que por este medio aparezca mi consulta a fin de poder solucionar esta duda, gracias de antemano y perdon por la repeticion si a alguien le llego el otro mensaje.

Gente, buenas noches, los molesto porque estoy tratando de mudar el Router Wifi / Acces Point (se me confunden los términos) que tengo armadito en una pentium III con brazilfw.
Quiero hacer esto porque con es distribucion me siento un poco acotado, ya que no tiene bash y muchas otras cosas, entonces decidi pasarlo a Ubuntu Server para de paso tener todo un poco mas homogeneo.

El tema es que me hice un embrollo cpn la configuracion y no se como salir de el, ya que yo tengo un servicio de internet comunitario que dan unos chicos de la zona donde vivo, y ellos me dan ina ip y los demas datos de configuracion, para acceder a internet, que son:

IP Fija: 192.168.1.XX
DNS: 200.51.211.7 / 192.168.1.2
GW: 192.168.1.2
Mask: 255.255.255.0

Yo tengo mi red en BFW con:
IP: 192.168.0.254
Mask:255.255.255.0

y ahora lo quiero pasar a ubuntu server y no se como configurarlo, tengo la maquina con 3 placas de red, 2 ethernet y una wifi (que despues usare para que funcione como AP).
Por eso es que hago esta consulta, a ver si me pueden tirar alguna idea sobre como asignar estos datos al servidor, o si hay algun script en algun lado, para poder configurarlo y que haga lo que necesito, ya que el BFW se instala con un menu paso a paso y es sencillo, pero no se aprene nada, ya que hace todo solo y quiero afinarlo.

Gracias
Por las dudas, esta NO es la lista de e-mail de Ubuntu-ar, es el foro y no estan vinculados mas alla de quienes pueden estar suscriptos a uno y otro medio.

Hecha la aclaracion va otra.
Una cosa es un router, sea o no inalambrico, y otra distinta es un acces point.
Para hacerla sintetica, los Acces Point no tienen posiblidad de ruteos, cosa que los primeros si pueden.

No conozco el producto que estas usando, pero en general, todos terminan generando reglas para que sean tratadas en el verdadero firewall, en el kernel de Linux, comunmente conocido como iptables.

Ya revisaste el contenido de su foro de tutoriales en Español ? [http://www.brazilfw.com.br/forum/viewforum.php?f=40](http://www.brazilfw.com.br/forum/viewforum.php?f=40)

---

### Post by guillermolisi on 2009-09-10
> **jawifi01 said:**
> Gracias, pensé que consultaba a personas un poquito más solidarias!! quiero aprender, pero necesito elementos, esta respuesta me suena a cargada.

Si sabia que me iban a cargar no preguntaba nada.

Saludos
Gente, ambos:

Si bien la respuesta de Pablo.s no es de lo mas logrado que he visto de su parte, tus comentarios jawifi01 tampoco ayudan a focalizarse en la solucion sino en generar otro problema.

Por lo tanto sean y muestrense inteligentes haciendo que lo mejor de cada uno salga a luz.

Disculpas aceptadas de ambos (para Ustedes mismos y para los demas) porque confio en que no tendran inconveniente en exponerlas, asi como tampoco el conocimiento que se pueda aportar al tema.

---

### Post by guillermolisi on 2009-09-10
Podrias especificar que datos forman parte de la configuracion de cada placa de red que posee la maquina ?

---

### Post by jawifi01 on 2009-09-11
> **guillermolisi said:**
> Podrias especificar que datos forman parte de la configuracion de cada placa de red que posee la maquina ?

Pido disculpas por lo anterior, quizá me extralimité, pero si fuera técnico no preguntaria y la respuesta realmente no me aclaraba nada.

Te respondo lo que me consultas:

yo tengo en el BrazilFW lo siguiente:
eth0
IP Fija: 192.168.1.38
DNS: 200.51.211.7 / 192.168.1.2
GW: 192.168.1.2
Mask: 255.255.255.0

y eth1
IP: 192.168.0.254
Mask:255.255.255.0

La configuración de eth0 me la da mi ISP y recibo internet por antena, que entra a esa placa de red, de ahi la saco por DHCP o ips fijas a mi lan desde la placa eth1 que va a un switch al cual conecto las demas pcs y asi tengo internet en todas las maquinas.
lo que quier hacer ahora es cambiar el SO de esa pc que hace de Router+Firewall por Ubuntu Server, y como esta distribución no es "dedicada" para eso se que voy a tener que configurar las cosas "a mano" para eso le agregué un rigido a esa maquina y le puse ubuntu SIN x, ahora me falta configurarlo, el problema es que no se como identificar que placa es eth0 y cual eth1, no se como definir el ruteo y quiero agregar un bridge a la placa wifi que tiene la maquina, que es una TPLink que funciona en master para tambien "sacar" wifi de ahi y usarlo con la notebook.

Gracias

Juan

---

### Post by gmunioz on 2009-09-11
Hola jaw....:

En Ubuntu, la configuración de las tarjetas de red

se realiza en el archivo /etc/network/interfaces

para tus dos tarjetas de red, sería:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.38
gateway 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

auto eth1
iface eth1 inet static
address 192.168.0.254
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

```

Respecto del bridge, pon otro post
previo leer en el foro al respecto,
si lo posteado es insuficiente

---

