---
title: "Servido Squid impide navegar en internet, en el mismo server.."
date: 2010-04-01
forum: Software
---

### Post by Darth_Berthold on 2010-04-01
Hola Muchachos.....

La cosa es como sigue:

Tengo 2 Tarjetas de Red eth0 donde esta conectado al Modem
y eth1 (ip 10.0.0.1) que se conecta al switch

La situación es que si conecto la red eth1, el servidor proxy se queda sin internet...
los usuarios no tienen internet tampoco.

Este es el Firewall...

iptables -t nat -F
iptables -t nat -X
iptables -t nat -Z
iptables -F
iptables -X
iptables -Z

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A PREROUTING -s 10.0.0.0/8 -p tcp --dport 80 -j REDIRECT --to-port 10.0.0.1:3128
iptables -t nat -A POSTROUTING -o eth0 -s 10.0.0.0/8 -j MASQUERADE
# SSL
iptables -A FORWARD -s 10.0.0.0/8 -i eth0 -p tcp --dport 993 -j ACCEPT
iptables -A FORWARD -s 10.0.0.0/8 -i eth0 -p tcp --dport 995 -j ACCEPT
# POP3
iptables -A FORWARD -s 10.0.0.0/8 -i eth0 -p tcp --dport 110 -j ACCEPT
# Consultas de Correo
iptables -A FORWARD -s 10.0.0.0/8 -i eth0 -p tcp --dport 465 -j ACCEPT
# SMTP
iptables -A FORWARD -s 10.0.0.0/8 -i eth0 -p tcp --dport 25 -j ACCEPT
--------------------------------------------------------------------------------------------
Este es el Squid.conf
http_port 10.0.0.1:3128
cache_mem 256 mb
cache_dir ufs /var/spool/squid 2048 16 256
cache_access_log /var/log/squid/access.log
cache_log /var/log/cache.log

acl SSL_ports port 443 563 8074
acl Safe_ports port 8002
acl Safe_ports port 21 # ftp
acl Safe_ports port 80 8074 # http
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
#acl Safe_ports port 8074 # Registro de Pcientes
acl CONNECT method CONNECT


#listas de control de acceso
acl all src 0.0.0.0/0.0.0.0
acl localhost src 127.0.0.1/255.255.255.255
acl ip_permitido src 'etc/squid/ip_permitido'
acl no_permitido url_regex 'etc/squid/no_permitidos'

#control de acceso
http_access allow ip_permitido
http_access deny no_permitido !localhost
http_access allow all

error_directory /usr/share/squid/errors/es

----------------------------------------------------------------------------------------------

Cualquier ayuda es bien recibida....

---

### Post by Darth_Berthold on 2010-04-01
ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:50:ba:16:e3:a9  
          Direc. inet:200.104.58.159  Difus.:200.104.58.255  Másc:255.255.255.0
          Dirección inet6: fe80::250:baff:fe16:e3a9/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:574496 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3474 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:38578372 (38.5 MB)  TX bytes:569470 (569.4 KB)
          Interrupción:19 Dirección base: 0xd000 

eth1      Link encap:Ethernet  direcciónHW 00:40:f4:53:f0:fd  
          Dirección inet6: fe80::240:f4ff:fe53:f0fd/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:143 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:226 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:13661 (13.6 KB)  TX bytes:18605 (18.6 KB)
          Interrupción:16 Dirección base: 0xd400 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:154 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:154 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:15806 (15.8 KB)  TX bytes:15806 (15.8 KB)

-----------------------------------------------------------------------------------------
route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
200.104.58.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         200.104.58.1    0.0.0.0         UG    0      0        0 eth0

---

### Post by CdK1 on 2010-04-03
Si paras el servidor squid, el problema persiste?

---

### Post by Darth_Berthold on 2010-04-05
Desconecte la tarjeta que daba servicio a la lan interna de ahi me daba internet de nuevo....

RARISIMO...

---

### Post by moreback on 2010-04-05
Puede ser que tu configuración esté activando dos puertas de enlace (gateways). Con todas las interfaces activadas, ¿qué tienes en tu tabla de rutas?

Ejecuta **ip route** en una consola y péganos el resultado.

Saludos.

---

### Post by Darth_Berthold on 2010-04-06
AAAAAARRRRRRRGGGGG !!!!

Suicidio colectivo con la maquina, jajajaj, le di formato, estoy jugando con ebox, jajjaja

alguien tiene manual APH (A prueba de Hue...)...

---

### Post by Darth_Berthold on 2010-04-12
Uff a la carga de nuevo....

IP ROUTE....

192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.166  metric 1 
default via 192.168.2.1 dev eth1  proto static 

Espero que le sirva maestro....

---

### Post by Darth_Berthold on 2010-04-12
Ya cabros !!!!

Cache cual era el problema....

Me costo peeeeero la cosa ya se que era...

**** !!!

El problema era la tarjeta de red que daba el permiso a la red local...

Lo cambie y SANTO REMEDIO !!!!


jajajajaja

Gracias a todos por la ayuda....

Thankiu thankiu...:lolflag:

Como pongo el tema RESUELTO ?

jajajaja.

---

### Post by Carlos C on 2010-04-13
Eso lo hace un moderador, así que... solved!

---

