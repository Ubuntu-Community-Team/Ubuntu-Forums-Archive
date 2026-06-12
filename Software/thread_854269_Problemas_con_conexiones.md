---
title: "Problemas con conexiones"
date: 2008-07-09
forum: Software
---

### Post by ML982 on 2008-07-09
Hola. Al terminar de instalar Ubuntu 8.04 me he encontrado con la desagradable sorpresa de que no tengo internet. Más que eso, no me reconoce la dirección de enlace del router con el cual antes no tenía problemas. Tengo una conexión nueva con speedy y no sé si eso podría estar generando el problema.
La conexión es mediante el modem smartAX mt880. A éste se conecta el router. Hay una computadora con windows xp conectada a la red y un segundo router inalambrico al cual se conectan otras dos computadoras, también con windows. La mía no tiene conexión inalambrica.
Cuando intento configurar ethernet, me sale un aviso de que la interfaz no existe.
Cuando intento configurar la conexión con el comando pppoeconf, me arroja el siguiente cartel. 

     NO CONECTADO
     Lo siento, se consultaron 1 interface, pero no respondió el concentrador de   acceso de su proveedor. Por favor, verifique sus cables de red y de modem. Otra razón de fallo puede ser también que esté ejecutándose otro proceso pppoe y que este esté controlando el módem.

Ifconfig me tira la siguiente información: 

Link encap:Ethernet  direcciónHW 00:17:31:23:12:fd  
          dirección inet6: fe80::217:31ff:fe23:12fd/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:9618 (9.3 KB)  TX bytes:468 (468.0 B)
          Interrupción:18

Ayuda! ML

---

### Post by faktorqm on 2008-07-09
Hola, este no es un problema de software, es de hardware.
Acá en el post nro. 19 un chabón pone como se configura el modem. ([http://ubuntuforums.org/showthread.php?t=779717&page=2](http://ubuntuforums.org/showthread.php?t=779717&page=2))
Si sigue sin funcionar, postea que placa de red tenes, por que no lo pusiste. (tambien lo podes averiguar con "lspci" o "lshw").
La interfaz que pusiste ahi no es la de loopback? pone el comando completo por favor y entre tags de code... Salu2!!!

---

