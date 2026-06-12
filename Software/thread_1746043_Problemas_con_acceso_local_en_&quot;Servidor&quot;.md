---
title: "Problemas con acceso local en &quot;Servidor&quot;"
date: 2011-05-01
forum: Software
---

### Post by ramiro_md on 2011-05-01
Buenas, les comento que arme un servidor local en casa con Ubuntu Server 10.10.
En mi casa poseemos 2 routers wireless, uno en planta alta (el cual recibe la señal del modem) y otro en planta baja que recibe la señal del router de planta alta por cable de red.
El tema es: yo conecto el server al router de planta baja (Deimos) y las computadoras de la casa pueden usar el FTP y el SSH sobre el servidor solo si están conectadas al router que esta conectado el servidor.
Lo cual me sirve y no me sirve. Porque si estoy en mi pieza en la planta alta de la casa, no podría tener acceso al servidor porque me conecto por el otro router (Fobos).
La sección de Virtual Servers de ambos routers esta así:
> 
Service Port------IP Address------Protocol------Status
21---------------192.168.1.117-----ALL----------Enabled

En qué le estoy pifiando ?.
Saludos y gracias.

---

### Post by gmunioz on 2011-05-01
[I]"....Un router wireless en planta alta,recibe la señal del modem y un router wireless en planta baja que recibe la señal del router de planta alta por cable de red.
Conecto el server al router de planta baja y las computadoras de la casa pueden usar el FTP y el SSH sobre el servidor solo si están conectadas al router que esta conectado el servidor..."[/I]
Esto es así porque todos los ordenadores estan dentro del mismo rango de ip en la red generada por este router.

*"...Si estoy en la planta alta de la casa, no podría tener acceso al servidor porque me conecto por el otro router...."*
Esto es así porque estan este ordenador y el anterior router en otro rango de ip en la otra red generada por este router.

Para tener acceso al servidor:
El router de planta baja debería de conectar por cable al de planta alta no por su wlan sino por un port lan y tener desactivado su servidor dhcp, así funcionaría como switch y todos los ordenadores estarian dentro del mismo rando de ip, en la red generada por el router de planta alta, el único que estaría funcionando como router y asignando por dhcp las ips.

---

### Post by ramiro_md on 2011-05-02
> **gmunioz said:**
> [I]
Para tener acceso al servidor:
El router de planta baja debería de conectar por cable al de planta alta no por su wlan sino por un port lan y tener desactivado su servidor dhcp, así funcionaría como switch y todos los ordenadores estarian dentro del mismo rando de ip, en la red generada por el router de planta alta, el único que estaría funcionando como router y asignando por dhcp las ips.
Compañero, gracias porla respuesta.
Es así como lo tengo configurado. :(

---

### Post by alfplayer on 2011-05-02
Probá hacer ping al router de arriba desde las computadoras conectadas al router de abajo y al revés (ping al router de abajo desde las conectadas al router de arriba).

---

### Post by ramiro_md on 2011-05-02
> **alfplayer said:**
> Probá hacer ping al router de arriba desde las computadoras conectadas al router de abajo y al revés (ping al router de abajo desde las conectadas al router de arriba).

Desde Deimos (abajo) a Fobos (arriba):
> 
rama@rastrojero:~$ ping -a 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=6.71 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.92 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.33 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=2.86 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=1.58 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=2.86 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=2.86 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=1.37 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=1.40 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=2.13 ms
64 bytes from 192.168.1.1: icmp_req=11 ttl=64 time=3.05 ms
64 bytes from 192.168.1.1: icmp_req=12 ttl=64 time=3.11 ms
^Z
[1]+  Detenido                ping -a 192.168.1.1


Desde Fobos (arriba) a Deimos (abajo):
> 
daniela@daniela-laptop:~$ ping -a 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_req=1 ttl=64 time=6.13 ms
64 bytes from 192.168.1.2: icmp_req=2 ttl=64 time=1.36 ms
64 bytes from 192.168.1.2: icmp_req=3 ttl=64 time=1.66 ms
64 bytes from 192.168.1.2: icmp_req=4 ttl=64 time=1.60 ms
64 bytes from 192.168.1.2: icmp_req=5 ttl=64 time=1.46 ms
64 bytes from 192.168.1.2: icmp_req=6 ttl=64 time=1.18 ms
64 bytes from 192.168.1.2: icmp_req=7 ttl=64 time=1.27 ms
64 bytes from 192.168.1.2: icmp_req=8 ttl=64 time=1.29 ms
^Z
[1]+  Detenido                ping -a 192.168.1.2


A todo esto, creo que hay un dato importante que no he mencionado en la explicación del problema. El servidor tiene ip fija, le puse 192.168.1.117, un número alto porque por lo general el router que asigna las IP no asigna un número tan alto. Puede influir ?

---

### Post by alfplayer on 2011-05-02
Tienen todos los equipos/computadoras la misma máscara de red? Podés hacerle ping al servidor desde tu pieza ? Recordá que ping es una herramienta muy básica y simple de usar para resolver problemas de conectividad, muchas veces lo primero que se hace cuando se sospecha un problema de red.

---

### Post by ramiro_md on 2011-05-02
Ping al servidor desde una máquina conectada al router de la planta alta:
> 
daniela@daniela-laptop:~$ ping -a 192.168.1.117
PING 192.168.1.117 (192.168.1.117) 56(84) bytes of data.
64 bytes from 192.168.1.117: icmp_req=1 ttl=64 time=166 ms
64 bytes from 192.168.1.117: icmp_req=2 ttl=64 time=47.0 ms
64 bytes from 192.168.1.117: icmp_req=3 ttl=64 time=5.35 ms
64 bytes from 192.168.1.117: icmp_req=4 ttl=64 time=28.3 ms
64 bytes from 192.168.1.117: icmp_req=5 ttl=64 time=148 ms
64 bytes from 192.168.1.117: icmp_req=6 ttl=64 time=47.6 ms
64 bytes from 192.168.1.117: icmp_req=7 ttl=64 time=77.5 ms
64 bytes from 192.168.1.117: icmp_req=8 ttl=64 time=41.8 ms
64 bytes from 192.168.1.117: icmp_req=9 ttl=64 time=124 ms
64 bytes from 192.168.1.117: icmp_req=10 ttl=64 time=30.4 ms
^Z
[1]+  Detenido                ping -a 192.168.1.117


Las computadoras tienen la misma máscara de red.

---

### Post by alfplayer on 2011-05-02
Lo que estaría quedando es problema de firewall. Tenés alguno?

---

### Post by ramiro_md on 2011-05-03
> **alfplayer said:**
> Lo que estaría quedando es problema de firewall. Tenés alguno?

No, solo el de los routers. En el comienzo del thread lo comenté.
Saludos.

---

### Post by alfplayer on 2011-05-03
> **ramiro_md said:**
> No, solo el de los routers. En el comienzo del thread lo comenté.
Saludos.

Lo que comentaste en el primer post es lo de virtual servers que no es para paquetes dentro de la LAN. Con algunos routers es posible controlar todo el firewall (ej.: con DD-WRT) aunque por defecto se permite el tráfico dentro de la LAN.

> Se puede probar en el servidor con netstat que esté escuchando en 192.168.1.117 o en 0.0.0.0.

 ```
sudo netstat -anop | grep ssh
```EDIT: Ups, esto ya está chequeado

También podés ejecutar esto para ver que no hay firewall funcionando en el servidor y si son GNU/Linux en las computadoras que están fallando conectadas a Fobos (si son de otro sistema operativo también podés verificar si hay firewall).

 ```
sudo iptables --list --verbose
```

---

### Post by ramiro_md on 2011-05-03
alfplayer, gracias por el tiempo invertido!. Recién llego a casa y volví a probar las conexiones y anda todo :o.
No entiendo por qué no andaba antes ni por qué anda ahora. Pero anda.
Una lástima no poder dejado bien documentado el problema y despedirse con un "ahora se le cantó andar".
Saludos y gracias!.

---

