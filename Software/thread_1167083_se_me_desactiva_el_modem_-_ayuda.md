---
title: "se me desactiva el modem - ayuda"
date: 2009-05-22
forum: Software
---

### Post by pacovilla on 2009-05-22
que tal, soy nuevo en esta comunidad y espero compartir con ustedes gratos momentos, mi problema es el siguiente, tengo Ubuntu 8.10 instalado en mi equipo con un modem amigo que logre instalarlo y hacerlo funcionar sin muchos incovenientes, gracias a las muchas guias que hacen ustedes. La maquina esta compartida en red con otra cuyo sistema es el win xp.

El problema surgio cuando quise que Ubuntu comparta su conexion a internet con la maquina de windows xp, basandome en un manual instale el paquete bridge-util y una ves instalado cree el archivo Iniciarbridge con el comando sudo gedit /etc/init.d/iniciar bridge

lo que le agregue a ese archivo fue

 *echo"Iniciando Bridge..." *[I][FONT=&quot]
*/usr/sbin/brctl addbr br0 //creo el bridge *
*/usr/sbin/brctl addif br0 eth0 //agrego la eth0 y eth1 al bridge *
*/usr/sbin/brctl addif br0 eth1 *
*/sbin/ifconfig eth0 0.0.0.0 //dejo la eth0 y eth1 sin ip asignado *
*/sbin/ifconfig eth1 0.0.0.0 *
*/sbin/ifconfig br0 192.168.0.1 up //le asigno ip al bridge y levanto el bridge con up //*[/FONT][/I]


Bueno el tema es que me arme un quiilombo y debi haber hecho algo que no era porque simplemente se me desactiva el modem, me voy a red y me sale la red, que si esta activada y funcionando y el modem que cada vez que lo activo se desactiva solo.

el tema es que probe desinstalando bridge-utils y borrandole iniciarbridget para volver a como estaba antes, pero se me sigue desactivando el modem cuando lo veo en red.

Nota: fisicamente las luces del modem amigo funciona perfecto, lo que se me desactiva es el icono del modem cuando accedo al archivo red, y cada vez que lo activo pasan dos segundos y se vuelve a desactivar.

Aclado que recien me estoy iniciando asi que por favor les pido paciencia jaja, reinstalar ubuntu no es una opcion.

---

### Post by gmunioz on 2009-05-22
Hola pac...:

Pon mas datos:

1- ¿Cómo y dónde esta conectado el modem, usb, ethernet?

2- ¿Cómo y de qué manera esta configurada la red, hub, switch, router?

3- ¿Qué cables estas usando, utp5 directo, cruzado?

Saludos.

---

### Post by guillermolisi on 2009-05-22
En una terminal/consola ingresa ```
route
``` y mostranos que te da como salida.

Sospecho que siguen vigentes los ruteos producidos por haber usado reglas para bridge-utils.

---

### Post by pacovilla on 2009-05-22
> **gmunioz said:**
> Hola pac...:

Pon mas datos:

1- ¿Cómo y dónde esta conectado el modem, usb, ethernet?

2- ¿Cómo y de qué manera esta configurada la red, hub, switch, router?

3- ¿Qué cables estas usando, utp5 directo, cruzado?

Saludos.

Que tal, el modem adsl amigo que tengo esta conectada a la computadora con ubuntu con cable usb, esta computadora esta compartida con un cable de red utp cruzado a otra con windows XP (de placa de red a placa de red)
Andaba perfecto tanto la red como internet en mi maquina con ubuntu, con la de windows andaba perfecta la red no asi internet.
Al instalar el bendito *Bridge *y modificar lo que te digo INternet ya no me anduvo mas, pero sigo teniendo red perfectamente, incluso tengo archivos compartidos entre las dos maquinas.

---

### Post by gmunioz on 2009-05-23
Hola pac...:

Ahora, sabiendo como estan instalados los dispositivos, es posible

comenzar el intento de averiguar que ocurre.

1- Desconecta el cable de red del ordenador con Ubuntu, reinicia el sistema

y controla que ocurre con el modem, ¿está activo? ¿puedes acceder a 

internet?

2- Con el cable de red nuevamente conectado, reinicia el sistema, si las 

respuestas a las preguntas anteriores son afirmativas, controla nuevamente

que ocurre.

Además ejecuta en consola los comandos

sudo ifconfig

sudo route

3- Pega en el post las salidas de los comandos y los resultados de las 

constataciones.

Sugerencia: terminator, es una consola bastante útil para estos 

procedimientos, solo funciona en modo gráfico, pero con un simple click

permite divirla en forma vertical u horizontal en multiples terminales, en

las cuales se pueden ejecutar distintos comandos, para asi poder copiar 

y/o compara sin problemas sus múltiples salidas.

Saludos.

---

### Post by pacovilla on 2009-05-26
Que tal gmunioz y guillermo, desde ya agradezco su tiempo pero probe en desenchufar tanto la red como el modem reiniciando cada vez y no ha tenido ninguna solucion.

En la terminal, tanto el route como el ifconfig me da de la ste manera.

   > 
    root@sistema-desktop:/home/sistema# route
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0

root@sistema-desktop:/home/sistema# ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:13:8f:59:c3:6f  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:18 Dirección base: 0xec00 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1693 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:86688 (84.6 KB)  TX bytes:86688 (84.6 KB)

  
aparte cuando en la terminal quiero configurarlo con sudo br2684ctl -b -c 0 -a 1.33
me dice esto.


>  br2684ctl[8184]: Interface "nas0" created sucessfully
br2684ctl[8184]: Communicating over ATM 0.1.33, encapsulation: LLC
br2684ctl[8184]: Fatal: failed to connect on socket
Les recuerdo que en red, activo el modem y se me desactiva solo, desactivo la red, y se me activa sola. si estuviera en windows diria que es un virus pero no lo creo posible, el unico virus debo ser yo jaja.


Aca les dejo algunas capturas de pantalla de lo que me dice pppoeconf cuando lo quiero configurar y lo que me hace cuando entro a Administración y a red.


[http://s3.subirimagenes.com/imagen/2610081pantallazo.png](http://s3.subirimagenes.com/imagen/2610081pantallazo.png)


[http://www.subirimagenes.com/imagen-pantallazo1-2610123.html](http://www.subirimagenes.com/imagen-pantallazo1-2610123.html)


[http://www.subirimagenes.com/imagen-pantallazo3-2610144.html](http://www.subirimagenes.com/imagen-pantallazo3-2610144.html)


Las dejo en forma de links para no cargar la web
Desde ya muchisimas gracias.


PD: de ultima quisiera saber si se puede reiniciar las configuraciones de red que vienen de fabrica en ubuntu 8.04, o como hacerlo. Pero sin reinstalar, de ultima nomas, prefiero antes intentar cualquier cosita.
Gracias

[URL="http://www.subirimagenes.com/imagen-pantallazo1-2610123.html"]
[/URL]

---

