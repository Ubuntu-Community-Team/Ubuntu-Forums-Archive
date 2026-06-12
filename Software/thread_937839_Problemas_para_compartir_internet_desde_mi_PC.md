---
title: "Problemas para compartir internet desde mi PC"
date: 2008-10-04
forum: Software
---

### Post by Nikosnob on 2008-10-04
Hola gente este es mi primer mensaje, bueno le paso a comertar mi problema, yo quiero compartir internet desde mi pc hacia otra (la otra tambien tiene ubuntu). Yo me conecto a internet desde un modem USB pero el problema es que cuando conecto el cable de red en mi pc para conectar a la otra, dejo de tener internet. Si sirve de algo tengo arnet y el modem es el Huawei MT810.

Trate de configurarlo con firestarter pero me dice que el dispositivo no esta listo (osea el modem que me aparece como nas0).

Saludos

---

### Post by faktorqm on 2008-10-06
Hola y bienvenido al foro. No entiendo la verdad por que cuando enchufas te quedas sin internet... ¿Como tenes configurada la placa de red? ¿Que cable estas usando para conectarte a la otra pc? Con firestarter hacer eso que necesitas vos es tan facil como 1-2-3 ¿Te fijaste algun tutorial por internet o te mandaste solo? Salu2!

---

### Post by santiagofrias on 2008-10-06
Creo que el problema puede ser el modem, ya que no es un modem router sino un modem USB, el MT810 (la hamburguesa)siempre dio algunos problemas y no solo con linux.
Creo que deberías ver de conseguir que te presten un modem-router y ver que pasa antes de comprar uno, pero me parece que el problema pasa por allí.
Yo tengo conectada así la red:
[http://fdntga.bay.livefilestore.com/y1p67IW8-LVKMdqK-S0zRgwlJYO6HDetK_ru0Ra_1bDnui7RIIKVd0RP6hie-mgJQJvimJ8D-oT1zc/Red.png](http://fdntga.bay.livefilestore.com/y1p67IW8-LVKMdqK-S0zRgwlJYO6HDetK_ru0Ra_1bDnui7RIIKVd0RP6hie-mgJQJvimJ8D-oT1zc/Red.png)

---

### Post by gmunioz on 2008-10-07
Hola nik....:
Estimo que no es que te quedas sin internet, sino que al conectar la placa de red, cambian los dns en resolv.conf y las aplicaciones no encuentran la salida.
Lo que puedes hacer es:
1) Habilitar definitivamente el forwarding en el kernel, ejecutando en consola, (Aplicaciones - Accesorios - Terminal):

sudo gedit /etc/sysctl.conf

Buscar las líneas que dicen:

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

Y dejarlas asi, sin almohadilla en la segunda:

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Guardar el archivo.

2) Estando en gedit (editor de texto) pulsar en nuevo y previo copiar el siguiente contenido, pegarlo en el archivo.


#!/bin/sh
# Script para habilitar conexión compartida de internet

# Limpieza de las reglas
iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

# Habilitación de compartición
iptables -A INPUT -i eth0 -j ACCEPT
iptables -t nat -A POSTROUTING -s eth0 -o nas0 -j MASQUERADE
iptables -A FORWARD -i eth0 -j ACCEPT


Guardar el archivo como /etc/init.d/firewall
Cerrar gedit

3) Ejecutar las siguientes ordenes:
sudo chmod +x /etc/init.d/firewall
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall

Reiniciar la pc

4) En la pc cliente
Lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la máquina que acabas de configurar.

Saludos. Gabriel.** 22 Mad **Intrepid User

---

### Post by Nikosnob on 2008-10-22
Bueno hice lo que me dijo gmunioz; lo de habilitar definitivamente el forwarding en el kernel e hice el sript, ahora si tengo internet en mi pc cuando las pc estan conectadas en red, pero no logro tener internet en la otra (con la que quiero comparir).

En la otra pc como me dijiste puse como puerta de enlace la pc que configure (la que se conecta a internet) y los dns de mi proovedor pero sigo sin internet.

Saludos

---

### Post by hictio on 2008-10-22
No entendi si tenes internet Ok al final en tu ult. post.

Tenes 2 maqs.:
- Maq A el firewall que comparte internet (con dos tarjetas de red, o una tarjeta de red, y la otra a traves de USB).

- Y Maq B que esta detras de Maq B que llega a internet a traves de Maq A.

Maq A tiene el DHCP activo? Como obtiene direccion IP Maq B? La asignas en forma manual? Con que settings?


Tests para ir viendo donde puede estar el prob: (con todo conectado y funcionando, es decir, prendido :) )

Desde Maq B:
- ping al loopback (127.0.0.1)
- ping a la direccion IP interna que tiene asignada esa misma maq.
- ping a la direccion de IP Maq A (tiene que ser a la direccion IP de la tarjeta interna, la misma que Maq A usa como Default Gateway)

Desde Maq A:
- ping al loopback (127.0.0.1)
- ping a la direccion IP interna que tiene asignada esa misma maq.
- ping a Maq B
- ping a la direccion externa (publica) que tiene esa maq. la que te el ISP.

Si esto funciona:

Desde Maq A & B:
- ping 209.85.171.83 (uno de los IPs de gmail.com)

Si esto funciona:
- ping gmail.com

---

### Post by Nikosnob on 2008-10-22
1) - Perdon por mi falta de expreción. Como tengo las cosas:

PC 1 (La que se conecta a internet):
-Una sola placa de red.
-Conexion a internet a través de modem USB.
La configure llendo a Sistema/Administracion/Red y en las propiedades de eth0 de la siguiente manera:
Configuracion: Dirección de IP estática
Direccion de IP: 192.168.1.3
Mascara de sub-red: 255.255.255.0
Dirección de la puerta de enlace: -

PC 2 (Cliente, con la que quiero compartir)
-Una sola placa de red.
La configure llendo a Sistema/Administracion/Red
 -En las propiedades de eth0 de la siguiente manera:
  Configuracion: Dirección de IP estática
  Direccion de IP: 192.168.1.5
  Mascara de sub-red: 255.255.255.0
  Dirección de la puerta de enlace: 192.168.1.3
 -La pestaña donde dice DNS le puse los de mi proovedor (Arnet)

Es asi como le tengo conectado
[http://i34.tinypic.com/5dkk9g.png](http://i34.tinypic.com/5dkk9g.png)

2)-hictio perdona pero no entiendo lo que me decis de ping ni como verlo/configurarlo, es que soy muy novato en esto

---

### Post by hictio on 2008-10-22
Excelente, ahora esta mucho mas claro todo.
Hace los siguientes tests:

Desde PC 1:
- ping al loopback (127.0.0.1)
- ping a la direccion IP interna que tiene asignada esa misma maq.
- ping a PC 2
- ping a la direccion externa (publica) que tiene esa maq. la que te asigna el ISP.

Desde PC 2:
- ping al loopback (127.0.0.1)
- ping a la direccion IP interna que tiene asignada esa misma maq.
- ping a la direccion IP de PC 1 (tiene que ser a la direccion IP de la tarjeta interna, la misma que PC 1 usa como Default Gateway)

Si esto funciona:

Desde PC 1 & PC 2:
- ping 209.85.171.83 (uno de los IPs de gmail.com), si esto funciona:

- ping gmail.com


[Ping](http://en.wikipedia.org/wiki/Ping) es un comando para hacer pruebas de conexion basicas de red. Abri un terminal (Applications -> Accessories -> Terminal) y tipeas ping seguido del hostname o de la direccion IP para testear.
Cuando lo ejecutas, se ve algo asi:
```

esteban@tango:~$ ping gmail.com
PING gmail.com (64.233.161.83) 56(84) bytes of data.
64 bytes from od-in-f83.google.com (64.233.161.83): icmp_seq=1 ttl=242 time=155 ms
64 bytes from od-in-f83.google.com (64.233.161.83): icmp_seq=2 ttl=242 time=156 ms
64 bytes from od-in-f83.google.com (64.233.161.83): icmp_seq=3 ttl=242 time=156 ms

--- gmail.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 155.496/156.132/156.596/0.566 ms

```

A diferencia de el de Windows, el ping de linux por default continua ejecutnadose hasta que lo matas, para matarlo, dale Ctrl + C, y volves al prompt.

A menos que haya algo raro, desde PC 1 tendrias que tener acceso a internet sin problemas.

---

### Post by Nikosnob on 2008-10-22
Bueno los datos que recolecte fueron estos:

PC 1:

```
nico@nico-desktop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.129 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.105 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.110 ms
--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.105/0.114/0.129/0.016 ms


nico@nico-desktop:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
--- 192.168.1.3 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 6999ms


nico@nico-desktop:~$ ping 192.168.1.5 (IP PC 2)
PING 192.168.1.5 (192.168.1.5) 56(84) bytes of data.
--- 192.168.1.5 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 6999ms


nico@nico-desktop:~$ ping 190.31.31.70 (IP QUE ASINGA EL ISP)
PING 190.31.31.70 (190.31.31.70) 56(84) bytes of data.
64 bytes from 190.31.31.70: icmp_seq=1 ttl=64 time=0.138 ms
64 bytes from 190.31.31.70: icmp_seq=2 ttl=64 time=0.151 ms
64 bytes from 190.31.31.70: icmp_seq=3 ttl=64 time=0.125 ms
--- 190.31.31.70 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.125/0.138/0.151/0.010 ms


nico@nico-desktop:~$ ping 209.85.171.83 (IP GMAIL)
PING 209.85.171.83 (209.85.171.83) 56(84) bytes of data.
64 bytes from 209.85.171.83: icmp_seq=1 ttl=242 time=217 ms
64 bytes from 209.85.171.83: icmp_seq=2 ttl=242 time=216 ms
--- 209.85.171.83 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 1999ms
rtt min/avg/max/mdev = 216.571/217.140/217.710/0.735 ms


```

PC 2:
```
agustina@agustina-desktop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.096 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.073 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.074 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.077 ms
--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.073/0.080/0.096/0.009 ms



agustina@agustina-desktop:~$ ping 192.168.1.5 (IP PC 2)
PING 192.168.1.5 (192.168.1.5) 56(84) bytes of data.
64 bytes from 192.168.1.5: icmp_seq=1 ttl=64 time=0.097 ms
64 bytes from 192.168.1.5: icmp_seq=2 ttl=64 time=0.074 ms
64 bytes from 192.168.1.5: icmp_seq=3 ttl=64 time=0.078 ms
64 bytes from 192.168.1.5: icmp_seq=4 ttl=64 time=0.074 ms
64 bytes from 192.168.1.5: icmp_seq=5 ttl=64 time=0.074 ms
--- 192.168.1.5 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.074/0.079/0.097/0.012 ms


agustina@agustina-desktop:~$ ping 192.168.1.3 (IP PC 1)
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=1 Destination Host Unreachable
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable
From 192.168.1.5 icmp_seq=4 Destination Host Unreachable
From 192.168.1.5 icmp_seq=5 Destination Host Unreachable
From 192.168.1.5 icmp_seq=6 Destination Host Unreachable
From 192.168.1.5 icmp_seq=7 Destination Host Unreachable
From 192.168.1.5 icmp_seq=8 Destination Host Unreachable
From 192.168.1.5 icmp_seq=9 Destination Host Unreachable
--- 192.168.1.3 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9024ms
, pipe 3


agustina@agustina-desktop:~$ ping 209.85.171.83 (IP GMAIL)
PING 209.85.171.83 (209.85.171.83) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=1 Destination Host Unreachable
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable
--- 209.85.171.83 ping statistics ---
6 packets traansmitted, 0 received, +3 errors, 100% packet loss, time 5018ms

```

No entiendo bien cuando decis "tiene que ser a la direccion IP de la tarjeta interna, la misma que PC 1 usa como Default Gateway" Donde busco esa IP?

---

### Post by chalito on 2008-10-22
Osea que tenes internet sin problemas en PC1, pero las maquinas no se ven entre si (ping entre PC1 y PC2 no anda).
Lo que me llamó la atención es esto:
nico@nico-desktop:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
--- 192.168.1.3 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 6999ms

PC1 no está viendo su propia IP? Algo está mal ahi...

Podrías postear el resultado de los siguientes comandos (en ambas maquinas):

route -n
ifconfig -a

viendo un poco el grafico de como tenes armada la conexion.. eso que tenes armado es un router inalambrico o un modem? Si es un modem dudo que le puedas conectar las 2 pc (una por cable y otra por wifi.. el wifi es solo para usar como alternativa al cable, no al mismo tiempo), y lo que necesitarias es ya sea un router wifi (recomiendo linksys) o poner internet solo en PC1, y compartirla desde esta para poder usarla desde PC2. Para esto necesitarias a) dejar PC1 prendida, y b) conectar PC1 a PC2 ya sea por un cable de red cruzado o por wifi. 
Como wifi me parece que no tenes en PC1, la opción evidente es conectar PC2 a PC1 via un cable ethernet cruzado... 

salu2

---

### Post by hictio on 2008-10-22
Mhhh.. Otra opcion, un poco mas cara que un cruzado, pero mas barata que un router WiFi es un switch entre PC1 & PC2, pero claro, PC1 va a tener que estar prendida para que la PC2 llegue a internet.
A la larga, lo mas barato para una casa, me parece que es siempre comprar un WiFi que no gasta mucha electricidad, y no hacen nada de ruido (iria entre el modem y las PCx que que quieras)

Ahora si tenes necesidades especiales, o queres tener un firewall dedicado, podrias ver de poner una maq con dos tarjetas de red (una al modem del ISP y otra al switch o router WiFi), no tiene porque ser una maquina muy potente, para esto, en mi opinion, lo mas facil de instalar y usar en una casa es [IPCop](http://www.ipcop.org/)

---

### Post by Nikosnob on 2008-10-22
Aca tengo los resultados de los comandos

PC 1:

```
nico@nico-desktop:~$ route -n

Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
200.3.60.12     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
nico@nico-desktop:~$ ifconfig -a
br0       Link encap:Ethernet  direcciónHW 00:0d:87:82:28:8a  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  
          Máscara:255.255.255.0
          dirección inet6: fe80::20d:87ff:fe82:288a/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:18708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:6081893 (5.8 MB)  TX bytes:5799 (5.6 KB)


eth0      Link encap:Ethernet  direcciónHW 00:0d:87:82:28:8a  
          dirección inet6: fe80::20d:87ff:fe82:288a/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:18728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:6350653 (6.0 MB)  TX bytes:3626 (3.5 KB)
          Interrupción:11 Dirección base: 0xae00 


lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:3707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3707 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:191251 (186.7 KB)  TX bytes:191251 (186.7 KB)


nas0      Link encap:Ethernet  direcciónHW 00:73:05:0c:e4:d0  
          dirección inet6: fe80::273:5ff:fe0c:e4d0/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:97846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79060 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:115691918 (110.3 MB)  TX bytes:8709094 (8.3 MB)


ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.31.31.70  P-t-P:200.3.60.12          
          Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST MTU:1492          
          Métrica:1
          RX packets:96485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77717 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:114860944 (109.5 MB)  TX bytes:6166434 (5.8 MB)
```

PC 2:
```
agustina@agustina-desktop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.1.3     0.0.0.0            UG    100    0        0 eth0 

agustina@agustina-desktop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:48:54:1F:8A:84  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::248:54ff:fe1f:8a84/64 Scope:Link 
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1 
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:1000 
          RX bytes:9696 (9.4 KB)  TX bytes:22456 (21.9 KB) 
          Interrupt:10 Base address:0xa000 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1 
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:0 
          RX bytes:5936 (5.7 KB)  TX bytes:5936 (5.7 KB)

```

---

### Post by hictio on 2008-10-22
Nikosnob, el cable de red que conecta PC1 & PC2 es un cable cruzado?

---

### Post by chalito on 2008-10-23
Ok, ahora me queda un poco mas claro. 

Primero: según lo que posteaste ahí, la IP de tu PC1 no es 192.168.1.3 sino 192.168.0.1. Partiendo de eso, es normal que no se vea con 192.168.1.5 usando una máscara de 24bits(255.255.255.0), o que no responda el ping a 192.168.1.3, que no existe.

Segundo, no se como conectás las 2 PC entre ellas, pero si es con un cable de red directo de una a otra, TENÉS que usar un cable cruzado (o cross-over). No te va a servir un cable de red común. [Acá tenés]("http://www.pasarlascanutas.com/cable_cruzado/cable_cruzado.htm") info sobre el tema, pero si no te animás a hacerte un cable cruzado vos, deberías poder comprar uno baratito en cualquier casa de computación.

Si es con un Hub o Switch, no necesitás un cable cruzado.

Entonces. Lo más sencillo de probar es ponerle a PC2 la IP: 192.168.0.2 netmask 255.255.255.0, y default gateway 192.168.0.1, ponerle los mismos DNS que figuren en PC1 y probar primero si haciendo ping de PC2 a PC1 funciona.

Con eso la dejás configurada para que esté en la misma red que PC1, y que salga por ésta a Internet.

En PC1, tenés que activar el forwarding y NAT, creo que ya lo explicaron en un post anterior. una vez hecho eso deberías poder navegar desde PC2 pasando a través de PC1.

---

### Post by mgaldeano on 2009-04-09
Hola. Tengo un problema similar. Tengo 2 maquinas. La maq 1 con Ubuntu intrepid, conectada a Internet con un modem Huawei E226. La segunda con Win xp. Quiero compartir la conexión de internet, pero no lo logro.
Por favor ayuda.
Copio las salidas de los comandos que pueden ayudar a resolver.
Saludos
Martín

---

### Post by staar on 2009-04-09
tengo la misma misma configuracion que vos, lo que yo hice es esto:

en ubuntu puse la conexion cableada (todo con el network-manager, gráficamente) con ip fija 192.168.0.1, mascara de red 255.255.255.0 y puerta de enlace 0.0.0.0 (si al reiniciar el network-manager no te guarda estas configuraciones, lo que hay que hacer es cambiarle el nombre a la conexión por el que se te ocurra)...

después instalé firestarter ```
sudo aptitude install firestarter 
``` que te permite compartir la conexión, con un asistente gráfico muy sencillo, poniendo como interfaz conectada a internet a ppp0 y como interfaz de área local a eth0 (ojo, existe un bug en firestarter que te avisa que un dispositivo no esta preparado, pero Hei-Ku explicó como solucionarlo [_acá_]("http://ubuntuforums.org/showthread.php?t=1006277"))...

en windos tenes que ir a conexiones de red, y configurar la conexión con una ip fija (dentro del rango 192.168.0.2 - 192.168.0.255, por ejemplo 192.168.0.4), con la misma máscara de red que en ubuntu, pero con puerta de enlace 192.168.0.1 (es decir, la maquina con ubuntu) y configurar los dns, tambien estáticos, con los dns de tu conexión a internet (buscalos en el network-manager, en la conexion de banda ancha móvil)...

y creo que eso es todo, fijate y contanos...

saludos

---

### Post by mgaldeano on 2009-04-09
Gracias. 
Se solucionó (aparentemente me faltaba en eth0 la puerta de enlace 0.0.0.0)
Saludos
M

---

### Post by manolito1976 on 2010-01-09
hola a todos,

quiero unir dos ordenadores para compartir internet, he seguido las instrucciones punto por punto y no se cual es el problema, pero no hay manera. Explico el caso a ver si podeis ver algun error:(la conexion entre los dos ordenadores es mediante cable cruzado)

PC1: Ubuntu 9.04, conectado a internet por wifi (wlan1) a un router inalambrico.
direccion ip asignada por el router: 192.168.1.129
direccion ip de mi eth0 (red local): 192.168.0.1
mascara de subred: 255.255.255.0
puerta de enlace: 0.0.0.0

PC2: Xubuntu 9.10, conectado al PC1 mediante un cable cruzado
direccion ip de la red local: 192.168.0.2
mascara de subred: 255.255.255.0
puerta de enlace: 192.168.0.1

Como configuracion del firestarter en el PC1 he puesto como normativa que permita las conexiones de la ip: 192.168.0.2

como asi no me conectaba a internet el PC2, (en el PC1 no hay ningun problema, aunque la señal no es muy buena, no se si esto tiene algo que ver), hice las pruebas de ping que recomendabais al iniciador de este hilo:

Desde PC 1:
- ping al loopback (127.0.0.1) **(ok!)**
- ping a la direccion IP interna que tiene asignada esa misma maq. **(ok!)**
- ping a PC 2 **(ok!)**
- ping a la direccion externa (publica) que tiene esa maq. la que te asigna el ISP. **(este no entiendo muy bien que es pero me imagino que sera al router, y ese ping me le hace sin problemas)**

Desde PC 2:
- ping al loopback (127.0.0.1) **(ok!)**
- ping a la direccion IP interna que tiene asignada esa misma maq. **(ok!)**
- ping a la direccion IP de PC 1 (tiene que ser a la direccion IP de la tarjeta interna, la misma que PC 1 usa como Default Gateway) **(ok!)**

Si esto funciona: [B](como veis hasta aqui todo funciona)
[/B] 
Desde PC 1 & PC 2:
- ping 209.85.171.83 (uno de los IPs de gmail.com), si esto funciona:

**Aqui viene el problema, pues el ping desde PC1 fnciona, pero el ping desde PC2 no, se queda colgado esperando respuesta que nunca llega, lo he intentado un monton de veces y ya me he decidido a postear aqui a ver si era algo que no llego a entender**

- ping gmail.com


[B]este ultimo ping me funciona solamente desde el PC1, como os podeis imaginar.

[/B]Bueno, eso es todo, si me podeis dar alguna idea os lo agradeceria mucho ya que no tengo forma de actualizar el xubuntu desde el otro ordenador, y tampoco instalar programas como no sea buscando los deb y buscando las dependencias que no se cumplen una a una, lo cual es muy engorroso.

bueno, salud, espero vuestra respuesta

---

### Post by gmunioz on 2010-01-09
Hola man....:

Prueba esto:

Habilitar definitivamente el forwarding en el kernel, 
ejecutando en consola, (Aplicaciones - Accesorios - Terminal):

```
sudo gedit /etc/sysctl.conf
```

Buscar las líneas que dicen:

```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1
```

Y dejarlas asi, sin almohadilla en la segunda:

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
```

Guardar el archivo.

Estando en gedit (editor de texto) pulsar en nuevo y previo copiar 
el siguiente contenido, pegarlo en el archivo a guardar como script:

```
#!/bin/sh
# Script para habilitar conexión compartida de internet
# Red local 192.168.0.0/24 por eth1

# Limpieza de las reglas
iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

# Habilitar NAT
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -d 0.0.0.0/0 -j MASQUERADE

# Dejar pasar los paquetes ICMP
iptables -A INPUT -i eth1 -p ICMP -j ACCEPT

# Permitir conexiones al puerto 80 (HTTP)
iptables -A INPUT -i eth1 -p TCP –dport 80 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 25 (SMTP)
iptables -A INPUT -i eth1 -p TCP –dport 25 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 10000 (Webmin)
iptables -A INPUT -i eth1 -p TCP –dport 10000 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 53 (DNS)
iptables -A INPUT -i eth1 -p TCP –dport 53 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 22 (SSH)
iptables -A INPUT -i eth1 -p TCP –dport 22 -m state –state NEW -j ACCEPT

# Aceptar paquetes de conexiones ya establecidas
iptables -A INPUT -p TCP -m state –state RELATED -j ACCEPT

# Rechazar paquetes de conexiones nuevas
iptables -A INPUT -i eth1 -m state –state NEW,INVALID -j DROP

# Rechazar paquetes de forwarding de conexiones no establecidas
iptables -A FORWARD -i eth1 -m state –state NEW,INVALID -j DROP
```

---

### Post by manolito1976 on 2010-01-11
hola gabriel!

gracias por la pronta respuesta!!

la linea comentada de marras ya la habia descomentado pues habia visto por ahi que habia que hacerlo, auqnue no entendia bien por que, ya ves que soy novato en estos temas de redes...
si he entendido bien hago un script con el texto que me has dado y lo ejecuto, verdad? todo en el PC1, si no me equivoco, o tambien en el PC2?
bueno, voy a probarlo en el PC1 y ya te cuento si me funciona.
salud!!

---

### Post by manolito1976 on 2010-01-11
bueno, paso a explicar lo que me ha ocurrido...

he creado un script con el texto que me has pasado,
en principio me daba muchos errores al ejecutarlo, asi que he pasado a ejecutarlo como sudo, y ha pasado lo siguiente:

> Bad argument `&#8211;dport'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;dport'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;dport'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;dport'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;dport'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;state'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;state'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `&#8211;state'
Try `iptables -h' or 'iptables --help' for more information.

seguidamente me he quedado sin internet en el PC1, lo que solo he vuelto a recuperar corriendo el firestarter (buff, he sudado por momentos, pero parece que algo aprendi)

asi que ahora no se muy bien que pasa, me da la sensacion que he desconfigurado el iptables porque solo se ha ejecutado una parte del script, pero no estoy seguro. 
he vuelto a probar todos los pings de antes y me sigue yendo exactamente igual, solo que si corto el firestarter creo que se me va de internet.

hay algo que me falta por ahi??

bueno, ya me diras, saludos!

PD: edito y añado por si sirve, tengo la version de iptables 1.4.1.1, lo digo porque la primera vez que ejecute el script sin sudo me decia que quizas tenioa que "upgrade" el iptables.

---

### Post by manolito1976 on 2010-01-11
bueno, he estado haciendo unas pruebas, y ahora estoy un poco mas confundido, l verdad.
por un lado el script que me habias mandado, no se muy bien por que al copiarlo a mi gedit, me cambio los dos guiones -- por un guion largo, que fue lo que me dio el error primero. asi que me use a revisar las paginas de man de iptables y encontre que habia la opcion --dport y --state, asi que lo cambie y ya no me daba error.
segundo, una vez resuelto este error, me dije, ya esta!, pero no, ahora no me deja hacer el ping desde PC2 a PC1 a menos que encienda el firestarter en PC1, lo que me lleva a pensar que he desconfigurado el iptables con no muy buena fortuna...
no se como lo veis...

mmmmmm ahora no se que pasa, pero me vuelve a dejar hacer todos los pings excepto el que no me dejba desde el principio, o sea, de PC2 hasta internet (esto despues de encender firestarter en los dos PCs y depsues apagarlo)

bueno, ahi queda eso, si me podeis echar una mano, algo que probar , nose , lo agradeceria, un saludo

---

