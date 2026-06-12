---
title: "Puente de red con ubuntu 9.04"
date: 2009-10-29
forum: Software
---

### Post by benja22 on 2009-10-29
Hola
Tengo 3 PCs, 2 con windows y uno con ubuntu(con conexión Internet). Quiero hacer un puente de red en el PC con ubuntu, este tiene Internet y lo quiero compartir con los otros 2 computadores con windows. Tengo 2 tarjetas de red y conexión a Internet

---

### Post by Carlos C on 2009-10-30
¿Lo que quieres es tener los tres computadores conectados a internet? Lo más fácil es usar un router. Dinos si cuentas con uno.


Saludos

---

### Post by benja22 on 2009-10-30
> **Carlos C said:**
> ¿Lo que quieres es tener los tres computadores conectados a internet? Lo más fácil es usar un router. Dinos si cuentas con uno.


Saludos

No tengo router. quiero conexión a Internet en los 3 computadores.
El computador con ubuntu tiene la conexión a Internet, este le debe mandar Internet a los 2 PCs con windows.
Ademas quiero conectividad entre los 3 PCs, como para intercambiar archivos por red y cosas así.
Saludos

---

### Post by Tomito on 2009-11-02
Me sumo al pedido del amigo, sería interesante aprender como hacerlo

---

### Post by Carlos C on 2009-11-02
Pueden mirar acá:

[http://php.apsique.com/ecal/routing](http://php.apsique.com/ecal/routing)

---

### Post by benja22 on 2009-11-10
Lo hice!

Instalar el packete Bridge-utils en el gestor de packetes synaptic o escribir en el terminal:

sudo aptitude install bridge-utils

Con sudo y gedit crear un archivo llamado puente en /etc/init.d

Estaciones: 
IP 192.168.0.X donde X= 2,3 u otros
Gateway 192.168.0.1
Subred 255.255.255.0
DNS: 208.67.222.222 o 208.67.220.220 u otro Servidor

**dentro de él poner**:
donde br0 será el puente, wlan0 es donde llega la internet y eth0 y eth1 son las 2 tarjetas para el puente

#!/bin/bash

#Creacion del Puente
 [COLOR=Black]brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
ifconfig eth0 down
ifconfig eth1 down
ifconfig eth0 0.0.0.0 up
ifconfig eth1 0.0.0.0 up
ifconfig br0 192.168.0.1 netmask 255.255.255.0 up
route add default gateway 192.168.0.1[/COLOR]

#Compartiendo internet
iptables --flush
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i br0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

PD: gracias igual por la respuesta del router

---

