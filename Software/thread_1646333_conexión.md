---
title: "conexión"
date: 2010-12-15
forum: Software
---

### Post by Vero1 on 2010-12-15
Hola

Tengo un problema serio. Como cada vez que reiniciaba se me borraba la configuración de ifconfig y tambien me quedaba sin conexión, alguien me sugirió eliminar pppoeconf para reinstalarlo despues. Claro que no reflexioné que me quedaría sin conexión y por ende no podría reinstalar nada.

Conclusión, no sé cómo hacer para tener conexión de nuevo y poder reinstalar pppoeconf y configurarlo.

Desapareció tambien el ícono del Network Manager de los paneles y cuando quiero agregar Area de notificación, no me responde.

Si corro ifconfig me aparece solamente "lo", pero si edito "etc/network/interfaces" me sale toda la configuración del pppoeconf.

Agradezco desde ya su ayuda.

saludos

---

### Post by EnriqueK on 2010-12-16
supongo que a pesar de no tener internet debes de tener los índices de repositorios actualizados, o sea no creo que  los hayas borrado. por lo que tabién vas a poder instakar todo lo que quieras mientras se encuentre vigente tu última actualización de repositorios, por lo tanto, intenta instalar el pppoeconf usando Synaptic , al no tener internet te va a mostrar un mensaje de alerta indicando la imposibilidad de poder realizad las descargas requeridas, pero también te va a mostrar las URLs de los paquetes a descargar, toma nota de ellos, los descargas en otro equipo, luego los pones en /var/cache/apt/archives , seguidamente repite el intento de instalar, pero como los paquetes los tendrá ya en el cache, no va a ir a buscarlos a internet, por lo que procederá a instalarlos.

---

### Post by Vero1 on 2010-12-16
Muchas gracias, lo pondré en práctica.

saludos

---

### Post by Vero1 on 2010-12-16
Enrique K,

Te diré que reinstalé Lucid y por supuesto recuperé pppoeconf, pero al instalar actualizaciones, se me fue el applet del NM y tambien la configuración y conexión.
La conexión la pude restablecer al agregar a resolv.conf las dos direcciones DNS que tenía cuando había conexión y con éso vuelvo a tenerla, pero en cada reinicio la pierdo.

Podrìas decirme cómo evitar ésto y que la configuración no se pierda?

Desde ya gracias.

---

### Post by guillermolisi on 2010-12-16
Vero1

Podrias mostrarnos el contenido de /etc/network/interfaces ?

Es que las IP de los DNSs deberian definirse cada vez que te conectas y segun lo que vos mencionas pareceria que esto no sucede (o te asigna DNSs que no funcionan). Este mecanismo es natural y propio de una conexion con IP dinamica (DHCP) a un ISP.

Si queres usar otros DNSs, tenes que abrir una consola/terminal e ingresar ```
sudo nano /etc/dhcp3/dhclient.conf
```
Ahi veras una linea comentada (un # al principio de la misma) que debe ser descomentada (removiendo el signo #, y donde colocas las direcciones IP de los DNS que queres usar ANTES que los que te asigne tu ISP:
```

...
...
...
send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="Red"]#prepend domain-name-servers 127.0.0.1;[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
...
...
...
```

Suponiendo que utilices los DNS de Google, deberia quedarte asi:
```
prepend domain-name-servers 8.8.8.8,8.8.4.4;
```

De esta forma cada vez que reinicies tu maquina y te conectes antepondra esos DNS a los de tu ISP.

---

### Post by Vero1 on 2010-12-16
Hola Guillermo Lisi,

acá está lo que pedís:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
iface eth0 inet manual

Yo tengo IP dinámica pero las DNS no sé quien las proporciona. Una vez tomé nota de las DNS que agregué a resolv.conf y son éstas:

200.63.155.178 y 200.63.155.50 y con éstas funciona.

Te diré que con las distros anteriores ésto no me pasaba. No sé si es la distro o es mi nuevo motherboard que tiene tarjeta de Red Realtek(si no me equivoco), que dicen trae problemas.

Nada tienen que ver con las DNS que tiene Windows.

Lo que sale cuando no tengo conexión es la puerta de enlace que sí es común con Windows y es 192.168.1.1 o 2.1.

En lo que respecta a lo que decís: "Si queres usar otros DNSs, tenes que abrir una consola/terminal e ingresar
Code:

sudo nano /etc/dhcp3/dhclient.conf

Ahi veras una linea comentada (un # al principio de la misma) que debe ser descomentada (removiendo el signo #, y donde colocas las direcciones IP de los DNS que queres usar ANTES que los que te asigne tu ISP:" Es que realmente no sé si mi ISP asigna o no alguna DNS...


Cuando no tengo conexión a Internet, el resolv.conf tiene solamente la puerta de enlace y sin las DNS no me conecta.

Configuro la conexión con pppoeconf y no hay otro modo.

Edito el comando que me dijiste porque no sé donde debo poner las DNS

  GNU nano 2.2.2                      Archivo: /etc/dhcp3/dhclient.conf                                                      

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;


Perdón por la extensión del post.

saludos

---

### Post by EnriqueK on 2010-12-17
Cuando tengo problemas de los DNS de mi proveedor de Internet , uso los de Google. para facilitar las tareas de habilitarlos, creé un pequeño scripr que estimo que te puede servir
[B]#!/bin/sh
echo 'nameserver 8.8.8.8' >> /etc/resolv.conf
echo 'nameserver 8.8.4.48' >> /etc/resolv.conf[/B]
Luego creo un lanzador que puede estar en el menú de aplicaciones, en el escritorio o en el panel 
Tipo -->Aplicación en terminal
Nombre --> cualquiera
Comando --> sudo sh ruta_al script

---

### Post by guillermolisi on 2010-12-17
> **Vero1 said:**
> Hola Guillermo Lisi,

Edito el comando que me dijiste porque no sé donde debo poner las DNS

Perdón por la extensión del post.

saludos

Las IPs de los DNS van en la linea que marque en color rojo y sobre la cual despues di el ejemplo de como deberia verse al usar los DNS de Google. Tambien hay que descomentarla (quitarle el simbolo # del principio de linea).

---

### Post by Vero1 on 2010-12-17
Gracias a los dos.

Hoy, por milagro no se borró la configuración. De repetirse usaré sus sugerencias.

saludos

---

