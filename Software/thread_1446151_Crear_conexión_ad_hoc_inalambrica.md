---
title: "Crear conexión ad hoc inalambrica"
date: 2010-04-03
forum: Software
---

### Post by chulelinux on 2010-04-03
Que tal, desde hace ya un tiempo me vengo quemando el coco tratando de hacer funcionar una red ad hoc entre la pc de escritorio (SO Karmic con speedy) y la notebook con xp. Primero me costo hacer andar la placa enlwi-g2 que solo me funcionó con ndiswrapper. Luego di cuenta que solo logro conectar las dos pc con network manager. Wicd no conecta nunca.
El tema es que me aparecen como que están conectadas pero no puedo compartir internet ni archivos. Ni siquiera devuelve un ping. La conexión es con ip estáticas y cifrado wep;tengo instalado firestarter y samba (este último no se muy bien usarlo) y lo que más me importa es compartir la conexión a internet.

Leí un montón de cosas pero nada me sirvió, y di cuenta que si la red la hago abierta y sin cifrado anda a veces y comparte internet aunque nunca pude hacer que se vean. Envio mi sistema y gracias por cualquier ayuda:

ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1b:fc:3e:85:ed  
          Dirección inet6: fe80::21b:fcff:fe3e:85ed/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:4370 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3396 errores:0 perdidos:0 overruns:0 carrier:2
          colisiones:0 long.colaTX:1000 
          Bytes RX:3507894 (3.5 MB)  TX bytes:518446 (518.4 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:97 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:97 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:10896 (10.8 KB)  TX bytes:10896 (10.8 KB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:201.255.44.55  P-t-P:200.63.148.51  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:4192 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3221 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:3404776 (3.4 MB)  TX bytes:436916 (436.9 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:08:54:94:e2:39  
          Direc. inet:192.168.0.1  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::208:54ff:fe94:e239/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:483 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:50951 (50.9 KB)
          Interrupción:18 Memoria:febff800-febff825 


route

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
ERCUY01-Lb1.mrs *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         *               0.0.0.0         U     0      0        0 ppp0

---

### Post by totolinux on 2010-04-04
Hola. mirá yo no se mucho de redes pero he logrado compartir internet entre pc y notebook las dos con ubuntu y xp pero ahora solo las uso con ubuntu 9.04 y comparten internet en forma aceptable.
Te cuento que en la pc que hace de servidor desinstalé networkmanager y la configuré en forma manual. iptables antes lo configuraba con firestarter (es un firewall que permite hacer la compartición a internet) pero ahora lo he configurado con un script que saqué de un tutorial muy piola. [http://www.ubuntu-es.org/index.php?q=node/98722](http://www.ubuntu-es.org/index.php?q=node/98722)
Al inicio habla de la forma de hacer funcionar su hardware que no viene al caso pero creo que tendrías que seguirlo desde el punto 6 o 7.
Esto me quemó la cabeza pero lo logré y ya lo he hecho de varias maneras y esta, que te indico es la mas cómoda. suerte y saludos camarada.

---

### Post by chulelinux on 2010-04-06
Muchas gracias totolinux... lo voy a probar. Como la cuestión es compartir entre dos máquinas no quiero sumar un router. Como consulta: ¿como se le puede poner una clave a la red? porque estoy en un edifio y si no le pongo alguna seguridad no va a andar la cosa...

Saludos

---

### Post by totolinux on 2010-04-06
Yo te recomiendo que trates de crear la red primero abierta y puedas compartir internet. para que tengas la menor cantidad de factores a la hora de chequear la conexión  luego se agregan un par de lineas a el archivo /etc/network/interfaces 
ejemplo: 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.110.197
netmask 255.255.255.0
network 192.168.110.0
broadcast 192.168.110.255
gateway 192.168.110.1

auto wlan0
iface wlan0 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
wireless_mode ad-hoc
wireless-essid ubuntuservidor
[COLOR="Red"]wireless_key s:mi_clave[/COLOR]

este es mi archivo de configuración de el servidor "escritorio"
solo esta agregado en rojo la clave
yo la uso sin clave total no tengo gran señal fuera de mi casa y en realidad no me importa si alguien quiere usar mi conexión. Pero se van a tener que romper la cabeza como me la rompí yo:lolflag:

---

### Post by chulelinux on 2010-04-07
Camarada Toto, con el tema de la clave me ha hecho sentir un mezquino egoista je je pero si no le pongo un mínimo de "seguridad" se conecta hasta el perro del vecino. En cambio con una clavecita al menos va a tener que tener ganas...

En buena hora... ANDUVO¡¡¡¡, con clave y todo sin ningún inconveniente. Muchas gracias, muchas, pues me cansé de instalar y desinstalar aplicaciones sin que funque la cosa.

Para quien tenga el mismo problema comento la configuración a modo de mini tutorial:

- Pc escritorio con Ubuntu 9.10 (Placa wireless Enlwi-g2) y notebook (placa atheros) con innombrable XP. Internet de Speedy gestionada por pppo
- Driver en linux puesto con ndiswrapper (bajado de la página de encore el último de realtek no me andaba tan bien)
- Iptables todavía gestionadas por Firestarter.
- Wireles gestionado de la manera que señaló Totolinux: solo sume al archivo /etc/network/interfaces  la configuración de la wlan, quedando así: (lo rojo es lo que simplemente sumé y anduvo)

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

[COLOR="Red"]auto wlan0
iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
wireless_mode ad-hoc
wireless-essid ubuntuservidor
wireless_key s:mi_clave[/COLOR]

El protocolo pppo que aparece como interface cuando uno hace ifconfig me complica un poco la cosa para entender el tema de las iptables y el modo de configurar todo esto manualmente... Entiendo que lo hecho con auto wlan0 es haber establecido la puerta para una red que ahora por medio de firestarter (en mi caso) se comunica con la gran red internet. En fin, puedo compartirme internet aunque todavía no compartir carpetas.... pero eso es otro tema y ya saldrá.

Muchas gracias nuevamente 
Slds

---

### Post by totolinux on 2010-04-07
Que bueno me alegro:D, que lo disfrutes y gracias por el mini tutorial que nunca viene mal para otros con las mismas dudas.  Saludos

---

