---
title: "Problemas para conectarse a internet por Lan"
date: 2009-08-21
forum: Software
---

### Post by hatredx on 2009-08-21
Bueno antes que todo los saludo a todos.
Les presento mi problema, en mi casa tengo una conexion por telefonica, me conecto muy bien por la conexion adsl de telefonica, la wifi anda muy bien pero en mi trabajo al momento de conectar el cable de red no me navega y la cosa es que un compañero, tambien utiliza ubuntu y le navega de lo mas bien.
Mi conclusion es que tal vez con la conexion adsl se bloqueo la lan, ahora la pregunta es:
¿como vuelvo a habilitar la conexion LAN?
:confused::confused::confused::confused::confused:
De ante manos mucha gracias saludos y bendiciones

---

### Post by Carlos C on 2009-08-21
Bastante extraño. Dinos que te muestra al escribir en el terminal:
```
ifconfig
```

Saludos.

---

### Post by hatredx on 2009-08-22
ok bueno ahora estoy en mi casa, asi que estoy via adsl asi k por ahora  no hay problema, pero el comando me tira esto 
```
eth0      Link encap:Ethernet  direcciónHW 00:24:81:67:cc:c3  
          Dirección inet6: fe80::224:81ff:fe67:ccc3/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:44639 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:28349 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:64582364 (64.5 MB)  TX bytes:2519553 (2.5 MB)
          Interrupción:19 

eth1      Link encap:Ethernet  direcciónHW 00:21:00:da:68:f9  
          Dirección inet6: fe80::221:ff:feda:68f9/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:86 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:86 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:5864 (5.8 KB)  TX bytes:5864 (5.8 KB)

pan0      Link encap:Ethernet  direcciónHW 32:de:10:1c:67:3a  
          Dirección inet6: fe80::30de:10ff:fe1c:673a/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:540 (540.0 B)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:186.104.64.196  P-t-P:10.52.114.3  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:44517 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:28179 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:64220413 (64.2 MB)  TX bytes:1893473 (1.8 MB)

```

realmente les digo con suerte se configurar la conexion adsl

---

### Post by moreback on 2009-08-24
En general no debieras tener problemas para hacer esos cambios de redes si es que hiciste la configuración ADSL usando Network-Manager. Los problemas aparecen cuando haces configuraciones manuales que Network-Manager no tocará y eso deja la escoba posteriormente.

Cuéntanos cómo hiciste la conexión ADSL, en qué guía te basaste, etc.

---

### Post by hatredx on 2009-08-25
Ok, al parecer deje la escoba con el comando que ocupe, por que ya ni siquiera me conecta por adsl asi que creo que estoy en un predicamento un tanto dificil, bueno el comando que utilise fue:
```
$ sudo pppoeconf
```
el cual por una semana funco
este comando me lo dio un tecnico de telefonica, me dijo que serviria pues lo hiso pero me dejo la grande en mi ubuntu.
Creo que tendre que reinstalarlo si es que no ahi alguna solucion y si la hay, por favor enzeñenme como configurar bien la adsl sin que provoque un conflicto con las otras conexiones.

---

### Post by moreback on 2009-08-25
¿Qué archivos has modificado? Si hiciste algo manual, trata de recordar qué cosas cambiaste, ya que por ahí habrá que empezar a arreglar.

---

### Post by hatredx on 2009-08-25
En realidad no cambie nada de forma manual, pero un amigo se metio como ROOT
con el comando:
 ```
$ sudo nautilus
```y borro un archivo, cual? no se
creo que fue el...
no recuerdo se que era uno que se encuentra en 
Sistema de archivos/etc/ppp/peers
pero eso fue despues del problema con la lan
el problema de la lan surgio despues de usar el comando que puse en el post anterior

EDITO: se me fue algo muy extraño que paso hoy el modem estaba conectado a otro pc y ejecute el comando pppoeconf obviamente no funciono pero mientras detectaba las interfaces de red fui a conectar el cable y ahora funciono la adsl pero no se me parece bastante raro

---

