---
title: "Intento conectar notebook por cable a router"
date: 2010-07-12
forum: Software
---

### Post by zaladquiel on 2010-07-12
Saludos. 
Tengo un Notbook con Ubuntu 9.04 instalado. El problema es que intento conectarlo a un router TENDA por cable para obtener internet pero no funciona. El router está conectado y configurado con un PC de escritorio con Ubuntu 9.10. Como la señal wifi es inestable quiero conectar el notebook al router con un segundo cable de red, pero no parece detectar la coneccion en forma automática. Agradecería me detallaran los pasos a seguir.

---

### Post by Carlos C on 2010-07-12
Hola. En el terminal puedes escribir el comando "ifconfig" para ver el estado de tus puertos y conexión. Creo que lo mejor es partir por eso.


Saludos.

---

### Post by zaladquiel on 2010-07-12
> **Carlos C said:**
> Hola. En el terminal puedes escribir el comando "ifconfig" para ver el estado de tus puertos y conexión. Creo que lo mejor es partir por eso.


Saludos.

Gracias acá va el resultado...

rafael@rafael-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1e:68:36:05:03  
          Dirección inet6: fe80::21e:68ff:fe36:503/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:10 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:744 (744.0 B)  TX bytes:748 (748.0 B)
          Interrupción:252 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:20 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:20 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:1f:3a:b0:18:e1  
          Direc. inet:192.168.0.100  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::21f:3aff:feb0:18e1/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1460  Métrica:1
          Paquetes RX:11 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:28 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1902 (1.9 KB)  TX bytes:5155 (5.1 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1F-3A-B0-18-E1-00-00-00-00-00-00-00-00-00-00  
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

rafael@rafael-laptop:~$

---

