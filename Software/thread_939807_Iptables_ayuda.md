---
title: "Iptables ayuda"
date: 2008-10-06
forum: Software
---

### Post by ramiro_md on 2008-10-06
Bueno gente, hoy me dieron ganas de desarrollar un script para el firewall.
Anduve leyendo un pocquitín sobre el tema, y tengo entendido que hay dos maneras de programar el script:
1)Bloquear todas las conexiones como política principal. Y luego ir creando excepciones.
2)Aceptar todas las conexiones como política principal y luego ir creando excepciones.
Yo opté por la opción 1, basandome en que cuanto menos puertos abiertos haya mejor :). Entonces cerré todos los puertos:

iptables -A INPUT -p TCP -j DROP

Bien, luego comencé a crear excepciones quedandome algo así:

iptables -A INPUT -p TCP -j DROP
iptables -A INPUT -s xx.xxx.xxx.xxx -p TCP --dport xxx -j ACCEPT 
[...]

Lo que hice en esa útlima línea, creo que algunos ya se habrán dado cuenta igual, es aceptar toda conexión entrante  del source xxx.xxx.xxx.xxx al puerto xxx.

Mi duda es la siguiente, si eso que propongo en ese script es correcto. O hay alguna falla. Porque lo noto algo contradictorio xD.
Bueno espero que me den una mano y me orienten un poco más con respecto a esto. Un saludo.

---

### Post by faktorqm on 2008-10-06
Hola, mirá acá te posteo uno que lo hice yo linea por linea, estuve un mes leyendo cosas sonre iptables y como se manejan los paquetes, asi que si te metes con esto, vas a tener que leer y leer y leer. Yo te dejo aca uno con lo que hice, yo lo que necesitaba cuando lo arme, era, de una red, que solo se pueda conectar a un determinado ip y a un determinado puerto, y que todo el resto lo tire, ni siquiera responda error. (reject y drop)
O sea, que desde la red "interna", tenes todos los puertos bloqueados, y solo accedes a internet por una ip y por un puerto (un proxy). Si te queres conectar a otro ip que no sea el del proxy, tira el paquete. (drop)

```

#!/bin/sh

# Esta placa va a tener la conexión a la red que para mi es el "externo"
# Evidentemente respeto género...
DISPOSITIVO_EXTERNO=eth1
IP_EXTERNO=157.0.6.27
MASCARA_EXTERNA=255.255.255.0
BROADCAST_EXTERNO=157.0.6.255

# Esta placa va a tener la conexión a la red que para mi es el "interno"
DISPOSITIVO_INTERNO_AUL=eth0
IP_INTERNA_AUL=192.168.0.1
MASCARA_INTERNA_AUL=255.255.255.0
BROADCAST_INTERNO_AUL=192.168.0.255
RED_INTERNA_AUL=192.168.0.0

# EStos son los datos para poder conectarme afuera
PUERTA_ENLACE=157.0.6.99
IP_PROXY=157.0.89.4
PUERTO_PROXY=8080
DNS_EXTERNO_UNO=157.0.47.1
DNS_EXTERNO_DOS=157.0.47.1

# Asigno IP, mascara, puerta de enlace, proxy, y dns para cada interfaz y las dejo activadas
ifconfig lo 127.0.0.1
ifconfig $DISPOSITIVO_INTERNO_AUL $IP_INTERNA_AUL netmask $MASCARA_INTERNA_AUL broadcast $BROADCAST_INTERNO_AUL up
ifconfig $DISPOSITIVO_EXTERNO $IP_EXTERNO netmask $MASCARA_EXTERNA broadcast $BROADCAST_EXTERNO up
route add default gw $PUERTA_ENLACE metric 1
echo "nameserver $DNS_EXTERNO_UNO
nameserver $DNS_EXTERNO_DOS" | tee /etc/resolv.conf
export http_proxy=http://$IP_PROXY:$PUERTO_PROXY/

# Desactivo el reenvio (lo vuelvo a activar al final)
echo "0" > /proc/sys/net/ipv4/ip_forward

# Limpio todas las configuraciones existentes
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

# Rechazo todo para las reglas input, output y forward
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# Protecciones contra inundaciones SYN
iptables -N syn-flood
iptables -A INPUT -i $DISPOSITIVO_EXTERNO -p tcp --syn -j syn-flood
iptables -A syn-flood -m limit --limit 1/s --limit-burst 4 -j RETURN
iptables -A syn-flood -j DROP

# Me aseguro de que las conexiones tcp nuevas sean paquetes SYN
iptables -A INPUT -i $DISPOSITIVO_EXTERNO -p tcp ! --syn -m state --state NEW -j DROP

# Habilito el enmascaramiento
iptables -t nat -A POSTROUTING -s $RED_INTERNA_AUL/$MASCARA_INTERNA_AUL -o $DISPOSITIVO_EXTERNO -j MASQUERADE

# Reenvio el puerto 8080 de la red interna al 8080 del proxy y habilito la vuelta
iptables -A PREROUTING -t nat -p tcp -d $RED_INTERNA_AUL/$MASCARA_INTERNA_AUL --dport 8080 -j DNAT --to $IP_PROXY:$PUERTO_PROXY
iptables -A FORWARD -p tcp -d $IP_PROXY --dport 8080 -o $DISPOSITIVO_INTERNO_AUL -j ACCEPT

# Esta regla salva el problema de que no podes "llegar" al proxy desde la red interna
iptables -A POSTROUTING -t nat -p tcp -d $IP_PROXY --dport 8080 -s $RED_INTERNA_AUL/$MASCARA_INTERNA_AUL -j SNAT --to $IP_EXTERNO

# Mantener el estado y/o abrir para conexiones salientes
iptables -A FORWARD -m state --state NEW -i $DISPOSITIVO_INTERNO_AUL -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state NEW,INVALID -i $DISPOSITIVO_EXTERNO -j DROP

# Bloqueo NetBIOS y Samba
iptables -t nat -A PREROUTING -p tcp --dport 135:139 -j DROP
iptables -t nat -A PREROUTING -p udp --dport 137:139 -j DROP
iptables -t nat -A PREROUTING -p tcp --dport 445 -j DROP
iptables -t nat -A PREROUTING -p udp --dport 445 -j DROP

# Acepto para poder pedir nombres
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Acepto paquetes ICMP (ping y amigos...) a ambos lados
iptables -A OUTPUT -p icmp -j ACCEPT
iptables -A INPUT  -p icmp -j ACCEPT

# Rechazo cualquier cosa desde el interior

iptables -A INPUT -i $DISPOSITIVO_INTERNO_AUL -j DROP
iptables -A OUTPUT -o $DISPOSITIVO_INTERNO_AUL -j DROP

# Me acepto a mi mismo
iptables -A INPUT -i lo -j ACCEPT

# Freno las peticiones ARP desde las otras interfaces
for i in /proc/sys/net/ipv4/conf/*
do
 echo "1" > $i/arp_filter
done

echo "7" > /proc/sys/net/ipv4/ip_dynaddr
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
echo "1" > /proc/sys/net/ipv4/conf/default/rp_filter
echo "1" > /proc/sys/net/ipv4/conf/all/rp_filter
echo "0" > /proc/sys/net/ipv4/conf/default/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/all/accept_redirects

# Habilito el reenvio de vuelta
echo "1" > /proc/sys/net/ipv4/ip_forward

# Habilito la proteccion contra el error de mensaje "malo"
echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses

```

Te comento, este script que vos haces solo te sirve para cuando lo corres, si no lo ejecutas cada vez que arrancas no sirve. Y de hecho, todas estas configuraciones las podes poner en archivos distribuidos por varios lugares del gnu/linux, pero justamente te sacan la facilidad de cambiar una cosa y de un solo lugar.
Ojo con lo que tocas! lee primero! 

PINCHA TE LLEVO EN EL ALMA!!! Y CADA DIA, TE QUIERO MAS!!!! VAMO!!!!

---

### Post by ramiro_md on 2008-10-06
GRacias faktorqm, voy a tener en cuenta tu ejemplo. La verdad es que tenés razón es bastante engorroso el tema, hay muchisima información y para tener un par de reglas me estoy volviendo loco :(
Para que cargue al incio puse el script en la carpeta "/etc/init.d/".
Voy a seguir indagando sobre iptables y espero poder generar mi propio script pronto :).
Un saludo hermano pincharrata y gracias.


...sin lógica sin razón te sigo desde desde el tablón...( 8 )

---

### Post by ramiro_md on 2008-10-06
Cuando ponés:
```
# Rechazo todo para las reglas input, output y forward
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

```
¿estás bloqueando todos los puertos?. ¿Si quiero navegar por internet bloqueando las descargas directas sería?:
```

iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j DROP

```
Un saludo. Gracias por la paciencia.

---

### Post by faktorqm on 2008-10-07
No entiendo que queres hacer, pero te explico, vos cuando bloqueas bloqueas todo lo que es de afuera hacia adentro, si bloqueas de adentro hacia afuera no te anda nada despues!! (por eso te decia que ojo con lo que tocas...) 
Digamos, vos para bloquear todos los puertos, pones las instrucciones, pero son de afuera hacia adentro, (asi nadie te "ve"). Vos cuando pedis una pagina web, no sale por tu puerto 80, vos te conectas por cualquier puerto al puerto 80 del otro o sea del servidor, no del tuyo! 
En el caso contrario, del emule por ejemplo, si elegis abrir un puerto de afuera hacia adentro. pero todos los demas los tenes bloqueados (siempre hablando de afuera hacia adentro). Salu2!

---

### Post by ramiro_md on 2008-10-07
ENtendido :) muchas gracias. Voy a seguir probando.
Che por qué cuando pongo el script en la carpeta /etc/init.d/ cuando inicia gnome me tira un error de que no puede cargar las preferencias y tarda en cargarme los themes e iconos mios ?? re flayero :confused:

---

