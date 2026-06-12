---
title: "Solucion para hacer un puente de red en ubuntu"
date: 2009-11-09
forum: Software
---

### Post by benja22 on 2009-11-09
Instale el packete Bridge-utils en el gestor de packetes synaptic o escriba en el terminal:

sudo aptitude install bridge-utils

Con sudo y gedit crear un archivo llamado puente en /etc/init.d

Estaciones: 
IP 192.168.0.X donde X= 2,3 u otros
Gateway 192.168.0.1
Subred 255.255.255.0
DNS: 208.67.222.222 o 208.67.220.220 u otro Servidor

dentro de él poner:
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

---

### Post by Bunnybugs on 2009-11-09
This is an english forum, if you want help, i'd recommend to speak english...

well, I can't help you right now!

---

### Post by benja22 on 2009-11-09
> **Bunnybugs said:**
> This is an english forum, if you want help, i'd recommend to speak english...

well, I can't help you right now!

emm, This is the chilean comunity, in chile the people speak spanish.
well, I did not want an answer, I was giving the answer for make an network bridge, some people needs this answer.

---

### Post by Bunnybugs on 2009-11-10
Em, the chile community isn't here on Ubuntuforums.org?

---

### Post by Carlos C on 2009-11-11
> **Bunnybugs said:**
> Em, the chile community isn't here on Ubuntuforums.org?

Bunnybugs, I remind you:

[COLOR=DarkRed]
[/COLOR]> [COLOR=DarkRed][SIZE=3]Ubuntu Forums Code of Conduct[/SIZE][/COLOR]        [URL="http://www.ubuntu.com/community/conduct"]
[/URL]
 **[SIZE=4]Posting to the Forums:[/SIZE]**
 **Section I - General Policy:**

9. Please strive to communicate with other users as effectively as possible:

[LIST]
[*]Please try to write your posts in English **unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff**.
[/LIST]
This is the Chile Team Forum and we speak in spanish.


benja22: por favor evita publicar dos veces la misma información. Esto lo publicaste en otro thread que tú mismo iniciaste [aquí]("http://ubuntuforums.org/showthread.php?t=1305049").

Te sugiero que antes de publicar leas [esto]("http://ubuntuforums.org/showthread.php?t=1162750").

Cierro el thread para que la discusión continúe en el hilo original.

Saludos.

---

