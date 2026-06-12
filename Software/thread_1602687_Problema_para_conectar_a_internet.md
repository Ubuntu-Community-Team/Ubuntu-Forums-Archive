---
title: "Problema para conectar a internet"
date: 2010-10-21
forum: Software
---

### Post by Rinay on 2010-10-21
Hola
Soy nueva con este sistema operativo, empece hace 5 dias cuando  me baje ubuntu 10.10, pero todavia no pude conectarme a internet.
Les  cuento mi problema: Un amigo me dijo que cuando tuviera instalado  ubuntu, podria conectame directamente, pero no fue asi, me aparecia el  simbolo (esas flechitas) diciendo "la conexion de red cableada  automatica etho esta activa", pero al entrar a mozilla no abria ninguna  pagina, preguntando me dijeron que tenia que actualizar el sistema, pero  tampoco porque no tenia conexion. Despues que desactive ipv6, editando  el grub2, tampoco. Me fije que estuviera todo bien en editar conexiones,  y estaba todo bien, pero sigo sin poder conectarme [IMG]http://linux-cd.com.ar/foro2/Smileys/default/sad.gif[/IMG]
Uso  ubuntu 10.10, compartido con windows xp (la opcion instalar dentro de  windows) con 25gb para ubuntu, y tengo un modem ethernet zyxel.
AH y  si cambio de ignorar a automatico en ipv6 las flechitas se transforman  en un signo de exclamacion rojo que dice "sin conexion de red", y cuando  hice la instalacion reinicie la pc y el modem.
Ayuda! [IMG]http://linux-cd.com.ar/foro2/Smileys/default/sad.gif[/IMG]

---

### Post by hectorivand on 2010-10-21
Hola, bienvenida al mundo Ubuntu :D

a ver... vamos por parte, contame que tipo de conexión tenes? discas alguna conexión en XP o apenas entras ya estas conectada sin tener que hacer más nada?

Aparte de que me respondas esto de arriba por favor, copia y pega el resultado del siguiente comando. ifconfig

Lo ejecutas de la siguiente manera.: vas a aplicaciones, accesorios, terminal, se abre una ventanita y ahi escribis ifconfig. apretas enter.

busca eth0, copia y pega acá todo lo que venga después de eso.

Saludos
Nacho

---

### Post by Rinay on 2010-10-22
> **hectorivand said:**
> Hola, bienvenida al mundo Ubuntu :D

a ver... vamos por parte, contame que tipo de conexión tenes? discas alguna conexión en XP o apenas entras ya estas conectada sin tener que hacer más nada?

Aparte de que me respondas esto de arriba por favor, copia y pega el resultado del siguiente comando. ifconfig

Lo ejecutas de la siguiente manera.: vas a aplicaciones, accesorios, terminal, se abre una ventanita y ahi escribis ifconfig. apretas enter.

busca eth0, copia y pega acá todo lo que venga después de eso.

Saludos
Nacho
Gracias por la bienvenida Nacho ^^

Si, tengo que poner un nombre de usuario y contraseña para conectarme desde windows xp (haciendo clic en el icono del escritorio)
 
Y el resultado fue este

eth0      Link encap:Ethernet  direcciónHW 00:18:f3:c3:76:05  
                 Direc. inet:192.168.1.2  Difus.:192.168.1.255  Másc:255.255.255.0
                 Dirección inet6: fe80::218:f3ff:fec3:7605/64 Alcance:Enlace
                 ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
                 Paquetes RX:15 errores:0 perdidos:0 overruns:0 frame:0
                 Paquetes TX:42 errores:0 perdidos:0 overruns:0 carrier:0
                 colisiones:0 long.colaTX:1000 
       Bytes RX:1555 (1.5 KB)  TX bytes:8562 (8.5 KB)
                 Interrupción:20 Dirección base: 0xa000 

lo    Link encap:Bucle local  
       Direc. inet:127.0.0.1  Másc:255.0.0.0
                 Dirección inet6: ::1/128 Alcance:Anfitrión
       ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
                 Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
                 Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
                 colisiones:0 long.colaTX:0 
                 Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by marcelo_bur on 2010-10-22
> **Rinay said:**
> Gracias por la bienvenida Nacho ^^

Si, tengo que poner un nombre de usuario y contraseña para conectarme desde windows xp (haciendo clic en el icono del escritorio)
 
Y el resultado fue este

eth0      Link encap:Ethernet  direcciónHW 00:18:f3:c3:76:05  
                 Direc. inet:192.168.1.2  Difus.:192.168.1.255  Másc:255.255.255.0
                 Dirección inet6: fe80::218:f3ff:fec3:7605/64 Alcance:Enlace
                 ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
                 Paquetes RX:15 errores:0 perdidos:0 overruns:0 frame:0
                 Paquetes TX:42 errores:0 perdidos:0 overruns:0 carrier:0
                 colisiones:0 long.colaTX:1000 
       Bytes RX:1555 (1.5 KB)  TX bytes:8562 (8.5 KB)
                 Interrupción:20 Dirección base: 0xa000 

lo    Link encap:Bucle local  
       Direc. inet:127.0.0.1  Másc:255.0.0.0
                 Dirección inet6: ::1/128 Alcance:Anfitrión
       ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
                 Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
                 Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
                 colisiones:0 long.colaTX:0 
                 Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

Hola. Fijate si tenes lo que se ve en la captura de pantalla que adjunto completado en tu conección ADSL.

Saludos

---

### Post by marcelo_bur on 2010-10-22
Aclaración: A mi no me aparece nada porque la conección se establece mediante un router. Pero si vos solo usas modem tendrían que aparecer alli los mismos datos que usas para conectarte desde Window$.
Saludos

---

### Post by hectorivand on 2010-10-22
> **Rinay said:**
> Gracias por la bienvenida Nacho ^^

Si, tengo que poner un nombre de usuario y contraseña para conectarme desde windows xp (haciendo clic en el icono del escritorio)
 
Y el resultado fue este

eth0      Link encap:Ethernet  direcciónHW 00:18:f3:c3:76:05  
                 Direc. inet:192.168.1.2  Difus.:192.168.1.255  Másc:255.255.255.0
                 Dirección inet6: fe80::218:f3ff:fec3:7605/64 Alcance:Enlace
                 ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
                 Paquetes RX:15 errores:0 perdidos:0 overruns:0 frame:0
                 Paquetes TX:42 errores:0 perdidos:0 overruns:0 carrier:0
                 colisiones:0 long.colaTX:1000 
       Bytes RX:1555 (1.5 KB)  TX bytes:8562 (8.5 KB)
                 Interrupción:20 Dirección base: 0xa000 

lo    Link encap:Bucle local  
       Direc. inet:127.0.0.1  Másc:255.0.0.0
                 Dirección inet6: ::1/128 Alcance:Anfitrión
       ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
                 Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
                 Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
                 colisiones:0 long.colaTX:0 
                 Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

Barbaro, tenes una conexión de ADSL normal que usa PPoE para conectarse. Busque algún tutorial fácil para pasarte pero no encontre nada, asi que hice uno y de paso cañaso lo publique en mi blog.

Vídeo, muy corto que te indica donde tienes que hacer clic básicamente :D

[http://www.techdays.com.ar/2010/10/22/video-tutorial-crear-una-conexion-adsl-en-ubuntu-10-10/](http://www.techdays.com.ar/2010/10/22/video-tutorial-crear-una-conexion-adsl-en-ubuntu-10-10/)

Saludos y contame si te sirvió

Nacho

---

### Post by Rinay on 2010-10-23
> **hectorivand said:**
> Barbaro, tenes una conexión de ADSL normal que usa PPoE para conectarse. Busque algún tutorial fácil para pasarte pero no encontre nada, asi que hice uno y de paso cañaso lo publique en mi blog.

Vídeo, muy corto que te indica donde tienes que hacer clic básicamente :D

[http://www.techdays.com.ar/2010/10/22/video-tutorial-crear-una-conexion-adsl-en-ubuntu-10-10/](http://www.techdays.com.ar/2010/10/22/video-tutorial-crear-una-conexion-adsl-en-ubuntu-10-10/)

Saludos y contame si te sirvió

Nacho
GRACIAS GRACIAS GRACIAS MIL NACHO!!!! :)
Por fin me pude conectar! actualice el sistema baje varios pack navegue y hasta pude activar los efectos! me encanta!

Me quedaron dos preguntitas nada mas por hacer
1- En youtube no puedo ver videos, me dice an error occurred please try again later" con la pantalla del video en negro (tengo todos los plugin de mozilla).
2- Si yo quisiera instalar ubuntu 10.10 particionando el disco, como tendria que hacer? particionar el disco es muy dificil? igual todavia no lo voy a hacer, soy muy novata :tongue: voy a seguir explorando y despues si. Pero me gustaria ir sabiendolo

---

### Post by hectorivand on 2010-10-23
> **Rinay said:**
> GRACIAS GRACIAS GRACIAS MIL NACHO!!!! :)
Por fin me pude conectar! actualice el sistema baje varios pack navegue y hasta pude activar los efectos! me encanta!

Me quedaron dos preguntitas nada mas por hacer
1- En youtube no puedo ver videos, me dice an error occurred please try again later" con la pantalla del video en negro (tengo todos los plugin de mozilla).
2- Si yo quisiera instalar ubuntu 10.10 particionando el disco, como tendria que hacer? particionar el disco es muy dificil? igual todavia no lo voy a hacer, soy muy novata :tongue: voy a seguir explorando y despues si. Pero me gustaria ir sabiendolo

Buenisimo que lo hayas podido solucionar.:

1 - Seguramente te esta faltando adobe Player, así que para matar varios pajaros de un tiro, abri el centro de software de ubuntu y busca "restricted codecs for ubuntu" ese te instala Flash Player, soporte para Mp3 y un par de formatos más.

2 - La partición la haces muy fácil con Gparted, también lo encontras en el centro de software de Ubuntu. De todos modos, si tenes 10.04, podes actualizar directamente a 10.10, si no lo queres hacer por miedo a que te deje de funcionar algo, create un live cd y proba todo.

Saludos
Nacho

---

