---
title: "Ayuda! Sin Internet despues de Actualizar a Ubuntu 9.04 beta"
date: 2009-03-08
forum: Software
---

### Post by alanlionheart on 2009-03-08
Hola gente, les comento que ayer a la noche me puse a acutualizar el 9.04 beta de Ubuntu desde los repositores. Hasta ahi lo mas bien, pero como tenia qe instalar el Envy para que me instale el software de mi placa de video NVidia me di cuenta de que estaba sin conexion a internet. Les cuento que ya trate con el Network Manager y me detecta la conexion (eth0) pero asi mismo desconectandola y volviendola a conectar no pasa nada. 
Tambien intente desconectar el modem, o el cable a la placa de red, pero no pasa nada, sigue todo igual.

Aca les tiro lo qe tengo en el /etc/network/interfaces

> auto lo
iface lo inet loopback


googleando por ahi tmb vi opciones como ver qe me muestra el "ifconfig", pero como de redes y esas cosas no entiendo mucho no supe que hacer con eso, pero igual se los muestro

> ifconfig

eth0      Link encap:Ethernet  direcciÃ³nHW 00:17:31:a5:48:bc  
          direcciÃ³n inet6: fe80::217:31ff:fea5:48bc/64 Alcance:VÃ*nculo
          ARRIBA DIFUSIÃ“N CORRIENDO MULTICAST  MTU:1500  MÃ©trica:1
          RX packets:9394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:565672 (565.6 KB)  TX bytes:1184 (1.1 KB)
          InterrupciÃ³n:23 DirecciÃ³n base: 0xe000 

lo        Link encap:Bucle local  
          inet direcciÃ³n:127.0.0.1  MÃ¡scara:255.0.0.0
          direcciÃ³n inet6: ::1/128 Alcance:AnfitriÃ³n
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  MÃ©trica:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:2088 (2.0 KB)  TX bytes:2088 (2.0 KB)

virbr0    Link encap:Ethernet  direcciÃ³nHW b2:2b:92:7a:a0:8b  
          inet direcciÃ³n:192.168.122.1  DifusiÃ³n:192.168.122.255  MÃ¡scara:255.255.255.0
          direcciÃ³n inet6: fe80::b02b:92ff:fe7a:a08b/64 Alcance:VÃ*nculo
          ARRIBA DIFUSIÃ“N CORRIENDO MULTICAST  MTU:1500  MÃ©trica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:7871 (7.8 KB)

Despues me meti con el pppoeconf y me tiro esto

> Lo siento, se consultaron 3 interface(s), pero no         
respondio el concentrador de acceso de su proveedor.     
Por favor, verifique sus cables de red y del modem.
Otra razon del fallo puede ser tambien que esta
ejecutandose otro proceso pppoe y que este esta
controlando el modem.    


Tambien por aca encontre una manera que a un chabon le hacia tener conexion pero cuando reiniciaba la volvia a perder, intente hacer lo siguiente: 
> sudo ifconfig eth0 192.168.0.132 netmask 255.255.255.0 up
pero no paso nada.

La verdad es qe andube buscando, y bastante, antes de poner un thread aca, pero no encontre solucion alguna que me funcione. Se tmb que podria iniciar desde el LiveCD, pero la verdad es qe queria tratar de arreglarlo por otras vias asi tmb me podia meter un poco en todo eso. Muchas gracias desde ya, saludos!


P.D:ya se que no tendria que haber actualizado a la 9.04 hasta que este terminada, pero queria problarla, creo que fue un error no esperar hasta Abril :P

---

### Post by luks911 on 2009-03-08
Una duda: ¿cómo te conectás a internet? ¿Te conectás directo a un router o  tenés que marcar por pppoe?

---

### Post by alanlionheart on 2009-03-08
Del Modem al Switch y de este a mi placa de red

---

### Post by luks911 on 2009-03-08
No sé si tendrá que ver, pero mi archivo interfaces tiene al final la siguiente línea:
```
auto eth0
```
El resto, igual.

Por otra parte, no entiendo qué es el dispositivo virbr0, que ahora veo que es el que recibió una IP.

---

### Post by alanlionheart on 2009-03-08
Gracias luks911, voy a probar lo que dijiste. En cuanto al vibr0, cuando corro pppoeconf es una de las interfaces que se consultan, otra cosa no sabria decirte.

---

### Post by gmunioz on 2009-03-08
Hola ala...:

1- jaunty aun no es beta, es alfa, a pesar de ello corre muy bien.
2- tienes conflictos porque has instalado xen
   virbr0 es un bridge del kernel con xen como virtualizador.
3- Instala la correcta versión de Jaunty o si eres usuario xen
   configuralo como corresponde, respecto de el ignoro todo.
4- No instales drivers de video mediante Envy, hazlo mediante los
   controladores de hardaware.
5- para no correr riesgos al actualizar, se actualizan aproximadamente
   entre 100 y 200 megas diarios, inicia en modo recovery, elige netroot
   del submenu emergente y actualiza mediante:
   apt-get update
   apt-get upgrade
   No Uses Synaptic
Saludos.
Gabriel.
Solo doy soporte para Ubuntu - 22 - Mad Jaunty User.

---

