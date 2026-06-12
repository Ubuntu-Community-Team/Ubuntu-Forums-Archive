---
title: "Tratando de conectar mi PC a un LCD con un cable cruzado"
date: 2010-09-23
forum: Software
---

### Post by Air23 on 2010-09-23
Hola!

Estoy intentado conectar poner en red mi PC y un TV LCD Samsung LN32C550 [1] para luego reproducir archivos desde la PC en el LCD usando un servidor DLNA (Media Tomb, miniDLNA, etc)

Tengo 2 placas de red, una de ellas (eth0) es la cual esta conectada a internet y la otra (eth2) esta conectada al LCD mediante un cable cruzado.

Este es mi archivo /etc/network/interfaces:

```
# The loopback network interfaceauto loiface lo inet loopback
auto lo
iface lo inet loopback

# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp

# eth2
auto eth2
iface eth2 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.1
```
En la configuracion de la red en el LCD puse

IP Adress 192.168.1.2
Subnet Mask 255.255.255.0
Gateway 192.168.1.1

Ahora viene el problema... cuando activo la conexión eth2 (ya sea desde el NetworkManager o con un sudo ifup eth2) dejo de tener acceso a internet en la PC.
Al ir a la utilidad Prueba de red del LCD que tiene 4 items:
- Dirección Mac
- Dirección IP, Subred, Puerta de enlace, Servidor DNS
- Ping puerta de enlace
- Prueba del servicio de Internet

Cuando realizo la prueba con la conexión eth2 activada (y por ende sin internet en la PC) pasa satisfactoriamente los primeros 3 items mientras que si hago la prueba con eth2 desconectada solo pasa los items 1 y 2.

¿Que estoy haciendo mal? ¿Que mas tengo que hacer?

Dejo la salida de algunos comandos por si pueden ser útiles.

ifconfig
```
eth0      Link encap:Ethernet  direcciónHW 00:1b:11:11:0c:e7  
          Direc. inet:186.19.10.148  Difus.:255.255.255.255  Másc:255.255.252.0
          Dirección inet6: fe80::21b:11ff:fe11:ce7/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1582591 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:376693 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:839364798 (839.3 MB)  TX bytes:33863664 (33.8 MB)
          Interrupción:18 Dirección base: 0xc800 

eth2      Link encap:Ethernet  direcciónHW 00:e0:43:cb:00:71  
          Dirección inet6: fe80::2e0:43ff:fecb:71/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:21 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:653 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1290 (1.2 KB)  TX bytes:51593 (51.5 KB)
          Interrupción:17 Memoria:febffc00-febffcff 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:315 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:315 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:35525 (35.5 KB)  TX bytes:35525 (35.5 KB)
```

route -n con eth2 desconectada

```
juan@HAL-9000:~$ route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
186.19.8.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         186.19.8.1      0.0.0.0         UG    0      0        0 eth0
0.0.0.0         186.19.8.1      0.0.0.0         UG    100    0        0 eth0
```

route -n con eth2 conectada

```
juan@HAL-9000:~$ route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2
186.19.8.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
0.0.0.0         186.19.8.1      0.0.0.0         UG    100    0        0 eth0
```

Saludos y muchas gracias de antemano.


[1] El manual del LCD puede bajarse de [http://www.samsung.com/us/support/downloads/LN32C550J1FXZA](http://www.samsung.com/us/support/downloads/LN32C550J1FXZA)

---

### Post by guillermolisi on 2010-09-23
De una rapida lectura me surgen las siguientes observaciones:

eth2 no deberia tener definicion de gateway ya que seria la eth0 pero esta tiene IP dinamica y publica (la que le asigne el DHCP server del ISP.
Si la dejas sin gateway y al tener IP privada, cuando requieras algo con IP publica automaticamente saldra via eth0 por ser esta placa la unica con IP publica.
Cuando activas esta placa eth2 te quedas sin Internet porque la definicion de gateway que le diste es autoreferencial, por lo tanto nunca saldra de ella misma.
Te deberia quedar algo asi (adecuando los bloques IP a tu red):

```
auto eth0
iface eth0 inet dhcp

# The primary network interface
auto eth1
iface eth1 inet static
        address 90.0.0.2
        netmask 255.255.255.0
        network 90.0.0.0
        broadcast 90.0.0.255
```

Conta como te fue con los cambios.

---

### Post by Air23 on 2010-09-23
¡Muchas gracias Guillermo!

Ya puedo activar eth2 sin quedarme sin internet. :P

¿Ahora lo que debo hacer es seguir esta tutorial [http://ubuntuforums.org/showpost.php?p=5923017&postcount=4](http://ubuntuforums.org/showpost.php?p=5923017&postcount=4), no? Pregunto para estar seguro y no mandarme ninguna "macana".

---

### Post by guillermolisi on 2010-09-23
Esas instrucciones que dio Gabriel son para activar el forwarding y NATting en una red que usa una maquina como gateway.

Primero adecua la configuracion de la placa de red del monitor definiendole el gateway para que apunte a 192.168.1.1 (la IP que le diste a eth2 en la PC).

Despues proba si en la PC podes navegar y acceder a los servicios de Internet. Luego proba desde el monitor (si aplica la navegacion en Internet tambien para el monitor).

Si en la PC no tenes navegacion, cosa que dudo, entonces posiblemente haya que trabajar el forwarding en iptables, pero vayamos por partes (dijo Dr. Jekyll).

Si vas a necesitar navegacion en el monitor (no se me ocurre como seria eso tratandose de un monitor - no lei el link :) ) entonces habria que habilitar forwarding + NATting.

---

### Post by Air23 on 2010-09-23
Ya configure 192.168.1.1 como gateway en la TV.

En la PC tengo internet sin problemas. Si bien en el LCD no hay navegación, este de alguna manera chequea si tiene acceso a internet mediante una utilidad llamada Prueba de red y el cuarto item (Prueba del servicio de Internet) da mal (todos los demás están ok).

¿Para hacer streaming de video con un servidor DLNA (Mediatomb o miniDLNA) hara falta habilitar forwarding + NATting?

---

### Post by guillermolisi on 2010-09-23
Depende de donde este el servidor de streaming. Si esta en Internet, si deberas habilitar esas caracteristicas.
Si la PC oficia de servidor de streaming para el monitor, entonces no haria falta ya que entiendo que entre los dos se ven sin problemas.

---

### Post by Air23 on 2010-09-23
Es solo para reproducir archivos que están en la PC así que doy el tema por concluido. Ya instale miniDLNA y funciona todo muy bien.

Gracias por la ayuda :P

Saludos

---

