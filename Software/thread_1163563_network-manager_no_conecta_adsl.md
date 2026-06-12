---
title: "network-manager no conecta adsl"
date: 2009-05-18
forum: Software
---

### Post by negrotuxero on 2009-05-18
tengo el siguiente problema
cuando quiero conctarme a internet network-manager me deja agregar la coneccion adsl 
pero no figura en la lista cuando haces click para conectar i tampoco conecta automaticamente... la unica manera de conectarme es por pppoeconf luego de reiniciar dos veces

la conecciones via red esa que tiene la fichitas onda las del telefono pero mas grandles dejo la respuesta ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:1e:90:00:72:04  
          dirección inet6: fe80::21e:90ff:fe00:7204/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:10884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12618 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:9046458 (9.0 MB)  TX bytes:2368620 (2.3 MB)
          Interrupción:221 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1292 (1.2 KB)  TX bytes:1292 (1.2 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:192.168.34.39  P-t-P:192.168.34.254  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1488  Métrica:1
          RX packets:10458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12388 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:8766974 (8.7 MB)  TX bytes:2082090 (2.0 MB)

ya instale knetworkmanager y wicd pero ninguna de las dos me sirvio


espero respuestas :D gracias....


conecte con pppoeconf

igual ya fue reinstale i a la m*****!!

GRACIAS RASO...:p

---

### Post by guillermolisi on 2009-05-18
> **negrotuxero said:**
> tengo el siguiente problema
cuando quiero conctarme a internet network-manager me deja agregar la coneccion adsl 
pero no figura en la lista cuando haces click para conectar i tampoco conecta automaticamente... la unica manera de conectarme es por pppoeconf luego de reiniciar dos veces

la conecciones via red esa que tiene la fichitas onda las del telefono pero mas grandles dejo la respuesta ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:1e:90:00:72:04  
          dirección inet6: fe80::21e:90ff:fe00:7204/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:10884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12618 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:9046458 (9.0 MB)  TX bytes:2368620 (2.3 MB)
          Interrupción:221 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1292 (1.2 KB)  TX bytes:1292 (1.2 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:192.168.34.39  P-t-P:192.168.34.254  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1488  Métrica:1
          RX packets:10458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12388 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:8766974 (8.7 MB)  TX bytes:2082090 (2.0 MB)

ya instale knetworkmanager y wicd pero ninguna de las dos me sirvio


espero respuestas :D gracias....
Que version de Ubuntu estas usando ?
Que marca y modelo es el modem ADSL ?

Despues de ejecutar pppoeconf probaste de ingresar a algun sitio web, como para confirmar que realmente no tenes activo el enlace ?

Me llama la atencion que tanto eth0 como ppp0 han enviado y recibido paquetes, por eso me parece que la conexion esta establecida solo que el NM te "miente" haciendote creer que no se conecto.

Ademas ppp0 tiene asignada una IP privada que posiblemente surgio del enlace con el modem (o se la pusiste manualmente ?)

---

### Post by emiliano_raso on 2009-05-19
Negro negro... Te dije que formatees la maquina xD Es mas facil xD jaja...

> **guillermolisi said:**
> Que version de Ubuntu estas usando ?
Que marca y modelo es el modem ADSL ?

Despues de ejecutar pppoeconf probaste de ingresar a algun sitio web, como para confirmar que realmente no tenes activo el enlace ?

Me llama la atencion que tanto eth0 como ppp0 han enviado y recibido paquetes, por eso me parece que la conexion esta establecida solo que el NM te "miente" haciendote creer que no se conecto.

Ademas ppp0 tiene asignada una IP privada que posiblemente surgio del enlace con el modem (o se la pusiste manualmente ?)

- Tiene Intrepid Ibex.
- Si probó.
- No puso manualmente la IP

Probá desinstalar knetworkmanager y network-manager con:
sudo aptitude remove knetworkmanager
sudo aptitude purge knetworkmanager
Y lo mismo con network-manager. Asi sacas TODO... y despues instalá kpowersave desde Synaptic.
Eso me faltó decirte que pruebes u.u

Welcome to the foro Negro...

---

