---
title: "[SOLVED] compartir internet (bridge?)"
date: 2008-05-30
forum: Software
---

### Post by MeduZa on 2008-05-30
tengo 2 computadoras corriendo linux, mi desktop con Ubuntu 8.04 y mi querida IPAQ con GPE-Familiar

Mi pc se conecta a internet por eth0 que tiene el ip 192.168.0.100 al router que tiene el 192.168.0.1
Mi pc se conecta a la IPAQ por usb0 con el ip 192.168.1.100
Mi IPAQ se conecta a mi pc por usb0 con el ip 192.168.1.102

si hago ping desde cualquiera de las 2 se ven sin problemas.

Ahora mi pregunta es, como le doy internet a mi Ipaq (o a mi red USB)

Realmente encuentro cosas en google pero no me funcan, la ultima que hice fue poner el firestarter y que me natee pero tampoco anda :P
leo por todos lados de hacer un bridge pero no entiendo como

Gracias

---

### Post by oktubrer on 2008-05-30
Teoricamente, calculo que tu pc tendría que funcionar como un router que una las dos redes (la 192.168.0.0 que funciona entre el modem adsl y tu pc, y la 192.168.1.0 que funciona entre la ipaq y la pc)

Y configurar el modem adsl para que haga nat con la ip de la ipaq también... :confused:

Mejor dejo que conteste alguien que esté seguro, en cuanto pueda sinó me pongo a buscar info.

---

### Post by faktorqm on 2008-05-30
no entendi que necesitas. Pero vos ahi tenes 2 redes distintas, eso es lo que no entiendo. tenes 192.168.0.0 y 192.168.1.0. Supongo que metiste cada pc a una boca del router separada, y que programaste el router de tal manera que te rutea internet a las 2, necesitas natear si o si con firestarter desde eth0 a usb0. Pero en ese caso tengo entendido que usb0 debe estar en otra red distinta que la pc, si no estas nateando en la misma red, o, mejor dicho, no estas nateando nada. 
Pone tu ipaq en 192.168.2.1 y natea con esas direcciones. 

Te aviso que considero que en todos los casos que tu mascara de subred es 255.255.255.0 y el dns y gateway en la pc ""sola"" es el router, en la pc con la ipaq enchufada tambien es el router y en la ipaq es la pc a la cual esta enchufada.

La guia del kernel pa cuando? :lolflag:

edito:


oktubrer: en realidad, si fueran 3 pc's separadas, basta con un switch para hacerlo, y te natea el router mismo. Acá la unica manera de hacerlo es con nat desde el linux, para que ""compartan"" la conexion.

---

### Post by MeduZa on 2008-05-30
es porque una red es ethernet (eth0) y la otra "red" es USB (usb0) cada una le pongo ips diferentes porque sino no me anda nada :(

entonces tengo mi red asi:

INTERNET---->ROUTER---->PC---->IPAQ.........< equipos
............Cable.............eth......USB...............< portadoras

hagan de cuenta que tengo 2 NIC, se supone que tengo que hacer algo en mi pc para que la red usb sea parte de la red eth no?

mi pc no rutea, el que rutea es el Router pero esta en otra red (eth) y la IPAQ esta en la red USB :S
Cualquiera que se conecte a mi router (es de 8 bocas) adquiere internet y red local, pero la ipaq esta conectada a mi pc (es como una sanguijuela chupadatos)

---

### Post by MeduZa on 2008-05-30
> **faktorqm said:**
> 

La guia del kernel pa cuando? :lolflag:



jajaja cuando repare la ca**da que me mande (no me anda el escaner) -.-

---

### Post by MeduZa on 2008-05-30
adjunto mas datos:

```
meduza@Xenoid:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:d8:b1:b0:90  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feb1:b090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32121369 (30.6 MB)  TX bytes:1362484 (1.2 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19846 (19.3 KB)  TX bytes:19846 (19.3 KB)

usb0      Link encap:Ethernet  HWaddr 3e:54:6c:5c:1e:64  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3c54:6cff:fe5c:1e64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:292 (292.0 B)  TX bytes:7058 (6.8 KB)

```

y la ipaq no queda otra que foto :P

---

### Post by faktorqm on 2008-05-30
Esta todo bien configurado, estas nateando mal en el firestarter por algun motivo. ahora me tengo ke ir, a la noche lo miro mejor. Salu2!

---

### Post by MeduZa on 2008-05-30
> **faktorqm said:**
> Esta todo bien configurado, estas nateando mal en el firestarter por algun motivo. ahora me tengo ke ir, a la noche lo miro mejor. Salu2!

si eso es lo raro, capas el browser de la ipaq q es medio chotex, voy a seguir probando, de todas maneras gracias espero mas respuestas ^_^

---

### Post by Mister X on 2008-05-30
Lo que vos queres se puede hacer con iptables. Tengo un script hecho en algun lado, pero no lo encuentro, esto te deberia funcionar (no lo probé)

borras las reglas anteriores
```
iptables --flush
```

permitis las conecciones entrantes de la IPAQ (sea lo que sea:) )
```
iptables -A INPUT -i usb0 -j ACCEPT
```

haces nat en la interfaz de salida a internet
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

haces el bridge entre las 2 interfaces (fowarding)
```
iptables -A FORWARD -i usb0 -j ACCEPT
```

activas el soporte para IP forwarding en el kernel
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

### Post by MeduZa on 2008-05-30
> **Mister X said:**
> 
haces el bridge entre las 2 interfaces (fowarding)
```
iptables -A FOWARD -i usb0 -j ACCEPT
```


este paso me dice:

meduza@Xenoid:~$ sudo iptables -A FOWARD -i usb0 -j ACCEPT
iptables: No chain/target/match by that name

---

### Post by sergiom99 on 2008-05-30
Creo que va asi:

```
sudo iptables -A FORWARD -i usb0 -j ACCEPT 
```

```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward 
```

forward es con R intermedia. tal vez por eso sea el error.

---

### Post by MeduZa on 2008-05-31
funco!! despues de eso agregue el DNS y WALAAAAAAAAAA internet por usb cosa que en windows XP + windows Mobile no se podia (se podia pero era una truchada a travez del sync de m$)
la verdad me saque las reestricciones por software que tenia, ahora si el unico limite que tengo es el hard :)

la pagina de ubuntuforum me anda hasta que trato de entrar a los foros xD
asi que mejor primero hago un update ^_^

---

### Post by faktorqm on 2008-05-31
Hola, bueno veo que ya te ayudaron. El único problema que veo es que eso cuando reinicias se borra todo. para el iptables, te hacés un script con las lineas correspondientes y que cargue al inicio, pero para activar el forwarding en el kernel hacés:

```
sudo gedit /etc/sysctl.conf
```

y buscás la línea que dice:

```

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

```

y la descomentás. (le borras el # adelante)

el script te deberia quedar algo asi:

```

#!/bin/sh

iptables -A INPUT -i usb0 -j ACCEPT
iptables -t nat -A POSTROUTING -s usb0 -o eth0 -j MASQUERADE
iptables -A FORWARD -i usb0 -j ACCEPT

```

Con el tema de la limpieza de reglas, difiero con Mister X, yo para limpiar las reglas uso:

```

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

```

Vos usa el que quieras, o simplemente fijate cual te anda y agregalo como primera linea del script. Acordate de ponerle al script chmod +x script.sh y de ejecutarlo con sudo. Espero que te haya servido, Salu2!

---

### Post by MeduZa on 2008-05-31
llegaste antes, jajaja venia a preguntar eso jajajaja

yo no use ninguna, las reglas las tengo bien, asi que no las borre (al menos las entiendo asi como estan xD )

---

### Post by Mister X on 2008-05-31
Me morfé las R de forward, perdon :lolflag:

me alegro que te funcione, saludos

---

