---
title: "Ayuda Access Point y Destination Host Unreachable"
date: 2013-02-03
forum: Software
---

### Post by MeduZa on 2013-02-03
Hola a Todos, tengo un problema medio raro, me pasa en Ubuntu Server y también probe en Debian.

Básicamente lo que tengo es un server casero con dos placas de red y un wifi

eth0 conectada a Internet
eth1 conectada a un switch de 16 bocas
wlan0 se encarga del WIFI con un chip Atheros
el server tiene los siguientes servicios andando correctamente:
BIND9, DHCP3 (isc-dhcp-server), hostapd y otros servicios secundarios que no vienen al caso

Hasta acá todo perfecto todo anda por separado, lo que hice fue crear un bridge entre el eth1 y wlan0 para que eso sea una sola red y se vean entre los diferentes clientes conectados.

El problema surge solo cuando levanto el br0
Lo que puedo hacer:
* el DNS resuelve los IP correctamente (internos y externos)
* puedo conectar varios clientes por WIFI, reciben su IP pueden acceder la LAN pero no a Internet.
* eth0 no tiene acceso a Internet pero si a la LAN (puedo conectarme por SSH a eth0)
ejemplo desde el server:
```
poseidon# ping google.com
PING google.com (173.194.37.37) 56(84) bytes of data.
From 192.168.0.108 icmp_seq=1 Destination Host Unreachable
From 192.168.0.108 icmp_seq=2 Destination Host Unreachable
....

```
si apago el br0 todo vuelve a la normalidad (pero pierdo eth1 y wlan0 porque ahora los controlo por br0)

Por el lado de BIND y DHCP no veo problemas, los clientes se conectan y obtienen su ip, el DHCP crea el registro en el BIND9, dos ejemplos sacados de la tabla de DNS:
```
android-cde10a3b388c5d0e A	192.168.16.103
			TXT	"310950ce2faf4c85aea7b5fdff58ddc382"
BLACKBERRY-1A7F		A	192.168.16.101
			TXT	"316833f310fc33955c68ddf12216208135"
```

Yo no se si el problema es de route, bridge o hostapd, pero no doy con la tecla.

Acá dejo mis configs a ver si alguno me tira una idea ya probe de todo.

/etc/interfaces
```

auto lo eth0 br0

# The loopback network interface
iface lo inet loopback

# The primary network Interface connected to the Wan
allow-hotplug eth0
iface eth0 inet dhcp
  post-up sh /home/poseidon/router.sh

# The second network Interface Connected to the Lan
allow-hotplug eth1
iface eth1 inet manual

#The Wireless network connecting WIFI clients to the LAN
allow-hotplug wlan0
iface wlan0 inet manual

# Bridge interface
iface br0 inet static
  address 192.168.16.1
  netmask 255.255.255.0
  gateway 192.168.16.1
  dns-nameservers 192.168.16.1
  bridge_ports wlan0 eth1
  up /sbin/ifconfig br0 up
  post-up /bin/sleep 10 ; /usr/sbin/hostapd -B /etc/hostapd/hostapd.conf
  post-up service isc-dhcp-server restart
  pre-down /usr/bin/killall hostapd
  down /sbin/ifdown br0
```

bridge output (no tengo nada conectado en eth1 en este momento):
```
bridge name	bridge id		STP enabled	interfaces
br0		8000.0023cdcb2fea	no		eth1
							wlan0
port no	mac addr		is local?	ageing timer
  1	00:23:cd:cb:2f:ea	yes		   0.00
  2	00:30:48:85:0c:dd	yes		   0.00
  1	4c:bc:a5:4e:f6:02	no		   1.62
br0
 bridge id		8000.0023cdcb2fea
 designated root	8000.0023cdcb2fea
 root port		   0			path cost		   0
 max age		  20.00			bridge max age		  20.00
 hello time		   2.00			bridge hello time	   2.00
 forward delay		  15.00			bridge forward delay	  15.00
 ageing time		 300.01
 hello timer		   0.72			tcn timer		   0.00
 topology change timer	   0.00			gc timer		   2.72
 flags			


eth1 (2)
 port id		8002			state		       disabled
 designated root	8000.0023cdcb2fea	path cost		 100
 designated bridge	8000.0023cdcb2fea	message age timer	   0.00
 designated port	8002			forward delay timer	   0.00
 designated cost	   0			hold timer		   0.00
 flags			

wlan0 (1)
 port id		8001			state		     forwarding
 designated root	8000.0023cdcb2fea	path cost		 100
 designated bridge	8000.0023cdcb2fea	message age timer	   0.00
 designated port	8001			forward delay timer	   0.00
 designated cost	   0			hold timer		   0.00
 flags			

```
ifconfig:
```
br0       Link encap:Ethernet  HWaddr 00:23:cd:cb:2f:ea  
          inet addr:192.168.16.1  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::223:cdff:fecb:2fea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15206 (14.8 KiB)  TX bytes:53353 (52.1 KiB)

eth0      Link encap:Ethernet  HWaddr 00:30:48:85:0c:dc  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe85:cdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905 errors:65 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:109 txqueuelen:1000 
          RX bytes:85243 (83.2 KiB)  TX bytes:979164 (956.2 KiB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:30:48:85:0c:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70835 (69.1 KiB)  TX bytes:70835 (69.1 KiB)

mon.wlan0 Link encap:UNSPEC  HWaddr 00-23-CD-CB-2F-EA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20924 (20.4 KiB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:cd:cb:2f:ea  
          inet6 addr: fe80::223:cdff:fecb:2fea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20412 (19.9 KiB)  TX bytes:79596 (77.7 KiB)

```
```
 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.16.0    *               255.255.255.0   U     0      0        0 br0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         localhost       0.0.0.0         UG    0      0        0 br0
default         localhost       0.0.0.0         UG    0      0        0 eth0

```
```
dig google.com

; <<>> DiG 9.7.3 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43369
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		49	IN	A	173.194.37.72
google.com.		49	IN	A	173.194.37.73
google.com.		49	IN	A	173.194.37.78
google.com.		49	IN	A	173.194.37.64
google.com.		49	IN	A	173.194.37.65
....bla bla bla (funciona)

```
las reglas del firewal:
> #! /bin/sh

# Firewall rules.

################################
#   eth0: connected to WAN     #
#   br0: connected to LAN      #
#   eIP: external IP           #
################################

IPTABLES=/sbin/iptables
EXTIF="eth0"
INTIF="br0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
EXTIP="`/sbin/ifconfig $EXTIF | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
echo "   External IP:  $EXTIP"

echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -t nat -F

echo "   Setting loopback"

$IPTABLES -A OUTPUT -o lo -j ACCEPT
$IPTABLES -A INPUT -i lo -j ACCEPT

echo "   Setting INPUT"
### State tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# SSH
$IPTABLES -A INPUT -i $INTIF -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
$IPTABLES -A INPUT -i $EXTIF -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP

# Ping
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

echo "   Setting FOREWARD"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state NEW -d 192.168.16.100 -j ACCEPT
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
#bridge
$IPTABLES --append FORWARD --in-interface $EXTIF -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -p all -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -p all -j ACCEPT
#$IPTABLES -A FORWARD -j LOG 
#$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP

echo "   Setting SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

echo "   Setting OUTPUT"
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP

echo "   Enabling Security rules"
#$IPTABLES -A INPUT -o eth0 -p tcp -dport 10000 -j DROP

echo "\nfirewall-iptables done.\n"

Reitero si seteo todo por separado, funciona bien, pero los equipos no se ven entre ellos (wlan0 con los eth1) y quiero que se vean por eso creo el br0.

lo raro es que puedo hacer un dig pero no un ping :S
saludos ):P

---

### Post by guillermolisi on 2013-02-04
Y no es mas sencillo que las dos interfaces eth1 y wlan0 esten con IPs asignadas en la misma red en lugar de toda la parafernalia de un bridge ?

---

### Post by MeduZa on 2013-02-04
> **guillermolisi said:**
> Y no es mas sencillo que las dos interfaces eth1 y wlan0 esten con IPs asignadas en la misma red en lugar de toda la parafernalia de un bridge ?

no entiendo tu punto, como seria eso?

---

### Post by guillermolisi on 2013-02-04
Si eth1 esta en la red 192.168.16.x y wlan0 en la red 192.168.16.y, ambas con mascara 255.255.255.0, vas a poder lograr que ambos tramos se vean entre si simplemente porque estan en la misma red.
Es decir, no importa si los clientes se conectan via cable o inalambricamente, estaran usando una IP 192.168.16.z/255.255.255.0 que les permitira llegar a las demas maquinas en esa red.

Lo que no se es cual es la razon para manejar dos subredes: la 192.168.0.x (eth0) y la 192.168.16.x (eth1/wlan0/br0). En principio si eth0 es la interface que esta conectada a Internet (directamente o a un router provisto por un ISP) deberia tener una IP publica y configurar NAT en el firewall para que todas las maquinas de la LAN (decir esto implica una sola red interna, mas alla de los dispositivos que se utilicen en ella) consuman esa misma IP publica.

Si eth0 hay que mantenerla con una IP privada, que sea en la misma red que el resto de las maquinas, lo que la convierte en el gateway de la red hacia y desde WAN.

Me parece que el tema pasa mas por una cuestion de topologia de red que otra cosa, para lo cual seria muy bueno contar con mas informacion al respecto.

---

### Post by MeduZa on 2013-02-04
> **guillermolisi said:**
> Si eth1 esta en la red 192.168.16.x y wlan0 en la red 192.168.16.y, ambas con mascara 255.255.255.0, vas a poder lograr que ambos tramos se vean entre si simplemente porque estan en la misma red.
Es decir, no importa si los clientes se conectan via cable o inalambricamente, estaran usando una IP 192.168.16.z/255.255.255.0 que les permitira llegar a las demas maquinas en esa red.

Lo que no se es cual es la razon para manejar dos subredes: la 192.168.0.x (eth0) y la 192.168.16.x (eth1/wlan0/br0). En principio si eth0 es la interface que esta conectada a Internet (directamente o a un router provisto por un ISP) deberia tener una IP publica y configurar NAT en el firewall para que todas las maquinas de la LAN (decir esto implica una sola red interna, mas alla de los dispositivos que se utilicen en ella) consuman esa misma IP publica.

Si eth0 hay que mantenerla con una IP privada, que sea en la misma red que el resto de las maquinas, lo que la convierte en el gateway de la red hacia y desde WAN.

Me parece que el tema pasa mas por una cuestion de topologia de red que otra cosa, para lo cual seria muy bueno contar con mas informacion al respecto.

eth0 esta conectada al módem del ISP que me da un IP 192.168.0.1 y tiene 4 bocas, solo uso una que va al eth0 del server y tiene DMZ porque el firewall lo manejo desde el server.
La verdad que voy a probar a ver que onda lo que decís, porque quiero que los que están en la wlan0 vean los servers que están en la LAN y las impresoras y a otras PC/Clientes, es por eso que había echo lo del br0 (ademas de que es mas fácil 1 rule for all :) )
voy a probar y te digo.
Gracias por el dato, como veras tengo conocimientos pero hasta ahí nomas ;)

---

### Post by guillermolisi on 2013-02-04
> **MeduZa said:**
> eth0 esta conectada al módem del ISP que me da un IP 192.168.0.1 y tiene 4 bocas, solo uso una que va al eth0 del server y tiene DMZ porque el firewall lo manejo desde el server.
La verdad que voy a probar a ver que onda lo que decís, porque quiero que los que están en la wlan0 vean los servers que están en la LAN y las impresoras y a otras PC/Clientes, es por eso que había echo lo del br0 (ademas de que es mas fácil 1 rule for all :) )
voy a probar y te digo.
Gracias por el dato, como veras tengo conocimientos pero hasta ahí nomas ;)
Ah, ok. Entonces llevaria la LAN a 192.168.0.x y listo ! (tal vez sea mas laborioso que ingresar en la administracion del router para cambiarle la IP para la LAN; tal vez sea el unico camino dependiendo del nivel de servicio que brinde el ISP)

---

### Post by MeduZa on 2013-02-04
> **guillermolisi said:**
> Ah, ok. Entonces llevaria la LAN a 192.168.0.x y listo ! (tal vez sea mas laborioso que ingresar en la administracion del router para cambiarle la IP para la LAN; tal vez sea el unico camino dependiendo del nivel de servicio que brinde el ISP)

eso ultimo que dijiste me confundió, te explico como es la topologia:

MODEM <-- eth0 (WAN) <-- SERVER ---> eth1 (192.168.16.0) ---> SWITCH ---> x100 clientes (192.168.16.101 al 200)
[COLOR="White"] . . . . . . . . . . . . . . . . . . . . . . . . . . . .[/COLOR] |
[COLOR="White"] . . . . . . . . . . . . . . . . . . . . . . . . . . . . [/COLOR]|---> wlan0 (192.168.16.0) 10 clientes (192.168.16.201 al 210)

y como lo puse ahora:
MODEM <-- eth0 (WAN) <-- SERVER ---> br0 (192.168.16.0) ---> eth1 y wlan0 ---> x110 clientes (192.168.16.101 al 210)

el moden solo da internet, no es router o gateway, el server es el router, gateway, firewall, DNS server, DHCP, NTP

Ademas del Switch van a estar colgados otros Servers (NAS, Print, file, etc) que tienen que ser accesibles desde wlan0.

Lo que no me queda claro es como los clientes consumiendo por wlan0 van a ver a los conectados a eth1, inclusive en el mismo nivel de ip, tengo entendido que voy a necesitar algo en el medio para enlazarlos, no creo que sea tan facil como ponerlos al mismo IP level.

---

### Post by guillermolisi on 2013-02-04
> **MeduZa said:**
> eso ultimo que dijiste me confundió, te explico como es la topologia:

MODEM <-- eth0 (WAN) <-- SERVER ---> eth1 (192.168.16.0) ---> SWITCH ---> x100 clientes (192.168.16.101 al 200)
[COLOR="White"] . . . . . . . . . . . . . . . . . . . . . . . . . . . .[/COLOR] |
[COLOR="White"] . . . . . . . . . . . . . . . . . . . . . . . . . . . . [/COLOR]|---> wlan0 (192.168.16.0) 10 clientes (192.168.16.201 al 210)

y como lo puse ahora:
MODEM <-- eth0 (WAN) <-- SERVER ---> br0 (192.168.16.0) ---> eth1 y wlan0 ---> x110 clientes (192.168.16.101 al 210)

el moden solo da internet, no es router o gateway, el server es el router, gateway, firewall, DNS server, DHCP, NTP

Ademas del Switch van a estar colgados otros Servers (NAS, Print, file, etc) que tienen que ser accesibles desde wlan0.

Lo que no me queda claro es como los clientes consumiendo por wlan0 van a ver a los conectados a eth1, inclusive en el mismo nivel de ip, tengo entendido que voy a necesitar algo en el medio para enlazarlos, no creo que sea tan facil como ponerlos al mismo IP level.
Si tenes a todas las maquinas cliente en la misma red y con una mascara de subred adecuada deberian poder verse entre si, de minima con un ping. No importa si hay switches en el medio o mas de una placa de red sirviendo a una misma red.

A efectos de definir correctamente el gateway, tenes que elegir una IP en la misma red LAN que identifique al server que oficia de router/firewall. Ejemplo:

> MODEM <-- eth0 (WAN) 192.168.0.1 <-- SERVER ---> eth1 (192.168.0.2) ---> SWITCH ---> x100 clientes (192.168.0.101 al 200)
[COLOR="White"] . . . . . . . . . . . . . . . . . . . . . . . . . . . .[/COLOR] |
[COLOR="White"] . . . . . . . . . . . . . . . . . . . . . . . . . . . . [/COLOR]|---> wlan0 (192.168.0.3) 10 clientes (192.168.0.201 al 210)
La IP del Gateway seria 192.168.0.1 y tenes que generar, si es que no existe, las reglas de NATting para que todo entre y salga de la LAN con la misma IP publica. 192.168.0.1 deberia rutear todo el trafico al modem (que es el que posee la IP publica) a traves de 192.168.0.1.

Si tiras un ping desde 192.168.0.1 deberias poder ver cualquier maquina que este en la misma red (192.168.0.2-200) siempre que esten con la mascara 255.255.255.0

---

### Post by MeduZa on 2013-02-05
ok encontré el error :D, no me peguen :(

Resulta que cuando ingrese las entradas en el archivo /etc/hosts puse al ip del model como localhost, se ve que lo hice sin darme cuenta y seguí.

me di cuenta mientras trataba de setear la tabla de rutas a mano, el default gateway en vez de decir el nombre del modem decía localhost, ahí fue que me di cuenta

ya anda todo no tuve que modificar el bridge ni tocar nada

De todas maneras Guillermo te estoy muy agradecido por ayudarme en este momento de desesperación hahhaha no soy de postear en el foro hasta que resuelvo o descubro algo nuevo, y me queda por probar eso de la topologia como vos dijiste, pero ya sabes que dicen que si anda no se toda ;)

---

### Post by guillermolisi on 2013-02-05
:) Y si todo esto permitio que vieras la equivocacion y pudieras adecuarla, buenisimo.

---

### Post by MeduZa on 2013-02-05
se me olvido, también había un problema con las tablas de ruteo, el Linux admin de donde trabajo me dijo que no se pueden tener 2 default gateway así que removí el del br0, hice un:
ip route del default dev br0

y todo empezó a andar de 10.
de esto:
```
 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.16.0    *               255.255.255.0   U     0      0        0 br0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         localhost       0.0.0.0         UG    0      0        0 br0
default         localhost       0.0.0.0         UG    0      0        0 eth0

```
a esto :
```

 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.16.0    *               255.255.255.0   U     0      0        0 br0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         chAdmin         0.0.0.0         UG    0      0        0 eth0

```

---

