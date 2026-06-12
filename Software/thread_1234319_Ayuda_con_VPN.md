---
title: "Ayuda con VPN"
date: 2009-08-07
forum: Software
---

### Post by jcoronelc on 2009-08-07
Es posible poder levantar una VPN usando WICD???  he buscado info, pero solo encuentro referentes a network manager  alguna ayuda?

---

### Post by Humanum on 2009-08-07
> **jcoronelc said:**
> Es posible poder levantar una VPN usando WICD???  he buscado info, pero solo encuentro referentes a network manager  alguna ayuda?

Hola,

No estoy seguro que alguien pudiera responder porque probablemente todos hablan Ingles... sera preferible buscar si existe la espanola version de Ubuntu forum pero boy a intentar traducir para ti en ingles...

Translation of the post : "Is it possible to have a VPN using WICD ??? I have tried to check every where but only could come up with references about Network manager... Anyone to help ???

---

### Post by Carlos C on 2009-08-08
> **Humanum said:**
> Hola,

No estoy seguro que alguien pudiera responder porque probablemente todos hablan Ingles... sera preferible buscar si existe la espanola version de Ubuntu forum pero boy a intentar traducir para ti en ingles...

Translation of the post : "Is it possible to have a VPN using WICD ??? I have tried to check every where but only could come up with references about Network manager... Anyone to help ???
La verdad es que el post fue publicado en el foro de la comunidad local chilena, en donde el idioma utilizado por la mayoría es castellano.
Saludos!

---

### Post by jcoronelc on 2009-08-11
Nadie que tenga el caso que me comente alguna solucion?

_**montar VPN con Wicd instalado**_

---

### Post by Carlos C on 2009-08-12
No, no es posible. Se tiene la idea de habilitar conexiones por VPN en la versión 2.0, pero falta bastante para eso:

[http://wicd.net/punbb/viewtopic.php?id=588](http://wicd.net/punbb/viewtopic.php?id=588)

Así que no, no podrás hacerlo, por el momento.
Saludos.

---

### Post by jcoronelc on 2009-08-13
> **Carlos C said:**
> No, no es posible. Se tiene la idea de habilitar conexiones por VPN en la versión 2.0, pero falta bastante para eso:

[http://wicd.net/punbb/viewtopic.php?id=588](http://wicd.net/punbb/viewtopic.php?id=588)

Así que no, no podrás hacerlo, por el momento.
Saludos.


lata... despues de arto buscar ya daba por sentado eso.


a la finale, volvi a network-manager y de ahi quiero realizar la conexion vpn a la of.

ha sido infructuoso... fome pensar que tendria que volver a windows porque no puedo realizar una conexion vpn...

no hay caso... buscando y buscando se presenta el mismo problema en muchos usuarios... describen soluciones sin sentido y la porqueria de vpn no quiere andar...

ya no se que hacer.

no hay otro gestor de redes que tenga ademas conexiones vpn???

saludos

---

### Post by Carlos C on 2009-08-13
Puedes mirar acá:

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

Saludos.

---

### Post by jcoronelc on 2009-08-13
Instale el Kvpnc
Funciona, se conecta, y usa chap para autentificar... pero a la hora de desconectar... se cuelga.
solucion, a la mala bajar el ppp0 con ifconfig y matar el kvpnc con killall

fome, pero funca...


con el network-manager, viendo el log aparece lo siguiente

Aug 13 16:49:29 emma NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Aug 13 16:49:29 emma NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5208 
Aug 13 16:49:29 emma NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Aug 13 16:49:30 emma NetworkManager: <info>  VPN plugin state changed: 3 
Aug 13 16:49:30 emma pppd[5211]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug 13 16:49:30 emma pppd[5211]: pppd 2.4.5 started by root, uid 0
Aug 13 16:49:30 emma pptp[5213]: nm-pptp-service-5208 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Aug 13 16:49:30 emma pppd[5211]: Using interface ppp1
Aug 13 16:49:30 emma pppd[5211]: Connect: ppp1 <--> /dev/pts/2
Aug 13 16:49:30 emma NetworkManager: <info>  VPN connection 'SANTIAGO' (Connect) reply received. 
Aug 13 16:49:30 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Aug 13 16:49:30 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 13 16:49:30 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Aug 13 16:49:31 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Aug 13 16:49:31 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 13 16:49:31 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 97). 
Aug 13 16:49:31 emma pppd[5211]: CHAP authentication failed: Authentication failed.
Aug 13 16:49:31 emma pppd[5211]: CHAP authentication failed
Aug 13 16:49:31 emma pppd[5211]: Connection terminated.
Aug 13 16:49:31 emma NetworkManager: <info>  VPN plugin failed: 1 
Aug 13 16:49:31 emma NetworkManager: <info>  VPN plugin failed: 1 
Aug 13 16:49:31 emma pptp[5213]: nm-pptp-service-5208 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Aug 13 16:49:31 emma pptp[5213]: nm-pptp-service-5208 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Aug 13 16:49:31 emma pppd[5211]: Exit.
Aug 13 16:49:31 emma pptp[5223]: nm-pptp-service-5208 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Aug 13 16:49:31 emma pptp[5223]: nm-pptp-service-5208 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Aug 13 16:49:31 emma pptp[5223]: nm-pptp-service-5208 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Aug 13 16:49:31 emma NetworkManager: <info>  VPN plugin state changed: 6 
Aug 13 16:49:31 emma NetworkManager: <info>  VPN plugin state change reason: 0 
Aug 13 16:49:31 emma NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Aug 13 16:49:31 emma NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Aug 13 16:49:31 emma NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 

con PAP, CHAP y MSCHAP es el mismo error...

asi es que asumo que es problema o del nm o del plugin.

alguna idea de como arreglarlo? o es un bug sin solucion?

saludos.

---

### Post by moreback on 2009-08-13
Yo creo que sería bueno que revisaras el software que tienes de VPN en la oficina, por ahí también tienen que existir problemas, no necesariamente son todos de Network-Manager.

Sld.s

---

### Post by jcoronelc on 2009-08-14
> **moreback said:**
> Yo creo que sería bueno que revisaras el software que tienes de VPN en la oficina, por ahí también tienen que existir problemas, no necesariamente son todos de Network-Manager.

Sld.s

mmmm...

es que ahi esta lo extraño.

soy el único con ubuntu en la of... el resto, todos winxp, cualquiera con una cuenta puede conectarce via vpn a la of sin problemas.

probe el ubuntu con el kvpnc y se conectó sin problemas, pero se cuelga a la hora de desconectar.

nm simplemente tira error y no conecta ni a palos... auduce errora la hora de auntentificar con chap o ms-chap, incluso con pap...

asi que creo que la cosa va por ahi.

---

