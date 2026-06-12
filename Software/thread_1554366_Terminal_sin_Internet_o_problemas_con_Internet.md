---
title: "Terminal sin Internet o problemas con Internet"
date: 2010-08-16
forum: Software
---

### Post by jpoeta on 2010-08-16
Hace un par de dias les comente el rpoblema que tenia instalando los repositorios de medibuntu el cual persiste, pues no lograr conectar nunca. 
Es extrano pues hay veces que funcionan otros reposiztorios y cosas que instalo pero por ejemplo esto tampoco funciona:

eric@eric-desktop:~$  wget [https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf](https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf)
--2010-08-16 15:10:06--  [https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf](https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf)
Resolviendo svn.torproject.org... 1.0.0.0
Conectando a svn.torproject.org|1.0.0.0|:443... falló: Expiró el tiempo de conexión.
Reintentando.

--2010-08-16 15:10:28--  (intento: 2)  [https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf](https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf)
Conectando a svn.torproject.org|1.0.0.0|:443... falló: Expiró el tiempo de conexión.
Reintentando.

--2010-08-16 15:10:51--  (intento: 3)  [https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf](https://sv&#8203;n.torproje&#8203;ct.org/svn&#8203;/torbrowse&#8203;r/trunk/bu&#8203;ild-script&#8203;s/config/p&#8203;olipo.conf)
Conectando a svn.torproject.org|1.0.0.0|:443...


Lo más raro es que yo en alemania no tuve ningun problema en bajar e instalar el programa para navegar anonimo en ubuntu. Bueno gracias y espero vuestras sugerencias y ayuda. Gracias de Antemano Aguante el Argentina Loco Team

[http://www.taringa.net/posts/linux/5663209/navegar-anonimo-en-ubuntu-10_04-guia-completa.html](http://www.taringa.net/posts/linux/5663209/navegar-anonimo-en-ubuntu-10_04-guia-completa.html)

Saludos JPOETA =);)

---

### Post by jpoeta on 2010-08-17
Aqui lo que me pasa con medibuntu:

eric@eric-desktop:~$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1
eric@eric-desktop:~$ ./postlucid.sh
Aplicando Radiance Theme...
[sudo] password for eric:
--2010-08-15 11:29:04-- [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolviendo [www.medibuntu.org](www.medibuntu.org)... 1.0.0.0
Conectando a [www.medibuntu.org|1.0.0.0|:80](www.medibuntu.org|1.0.0.0|:80)... falló: Expiró el tiempo de conexión.
Reintentando.

--2010-08-15 11:29:26-- (intento: 2) [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Conectando a [www.medibuntu.org|1.0.0.0|:80](www.medibuntu.org|1.0.0.0|:80)... falló: Expiró el tiempo de conexión.
Reintentando.

--2010-08-15 11:29:49-- (intento: 3) [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Conectando a [www.medibuntu.org|1.0.0.0|:80](www.medibuntu.org|1.0.0.0|:80)...

Gracias Aguante Argentina Loco Team 

Jpoeta;)

---

### Post by guillermolisi on 2010-08-17
Lo que esta sucediendo es que no termina de resolver la URL y queda con una IP cualquiera, por eso no encuentra esos repositorios.

> --2010-08-15 11:29:04-- [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolviendo [www.medibuntu.org](www.medibuntu.org)... **1.0.0.0**

Esto normalmente esta a cargo de los DNS de la red y si funcionan mal tendras este tipo de inconvenientes (generalmente ocasionados por el ISP local).

---

### Post by jpoeta on 2010-08-17
Muchísimas gracias por la respuesta Guillermo, lo que quisiera saber es que debería hacer existe alguna forma de solucionar lo de los dns debiría llamar a Telefónica? o lo puedo hacer solo que me recomendarias. Me acuerdo que cuando era nuevo en Ubuntu( con el 6.06) Tenia que poner manualmente los dns y el ip, será que así podría solucionarlo?

Muchísimas Gracias nuevamente

Jpoeta;)

---

### Post by zeroadrenaline on 2010-08-17
> **jpoeta said:**
> Muchísimas gracias por la respuesta Guillermo, lo que quisiera saber es que debería hacer existe alguna forma de solucionar lo de los dns debiría llamar a Telefónica? o lo puedo hacer solo que me recomendarias. Me acuerdo que cuando era nuevo en Ubuntu( con el 6.06) Tenia que poner manualmente los dns y el ip, será que así podría solucionarlo?

Muchísimas Gracias nuevamente

Jpoeta;)

Tipo de coneccion (adsl - cablemodem)?
Red routeada o directa?
Salida de los siguientes comandos:

sudo route -n
sudo ifconfig
sudo cat /etc/resolv.conf

---

### Post by mama21mama on 2010-08-17
hola, 

mira por [estos lugares ]("http://www.ubuntronics.com/2010/04/repositorios-de-medibuntu-caidos.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+blogspot%2FJOzz+%28Ubuntronics%29&utm_content=Google+Reader")

o 

```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```

> 
    #mirror-1
    deb mirrors.ucr.ac.cr lucid free non-free
    deb-src mirrors.ucr.ac.cr lucid free non-free

    #mirror-2:
    deb mirror.oscc.org.my lucid free non-free
    deb-src mirror.oscc.org.my lucid free non-free

    #mirror-3:
    deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
    deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

---

### Post by jpoeta on 2010-08-20
Esto es lo que me dice el terminal de los comandos que me decis Adrenaline y disculpa porque no respondí rapido pero estaba de viaje. Gracias por tu ayuda y Gracias a todos en general quiero solucionar este problema lo mas pronto posible.

```
eric@eric-desktop:~$ sudo route -n
[sudo] password for eric: 
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
eric@eric-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:15:e9:a6:56:b8  
         ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
         Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
         Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
         colisiones:0 long.colaTX:1000 
         Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupción:16 Dirección base: 0x2400 

eth1      Link encap:Ethernet  direcciónHW 00:11:5b:c2:35:64  
         Direc. inet:192.168.1.33  Difus.:192.168.1.255  Másc:255.255.255.0
         ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
         Paquetes RX:78135 errores:0 perdidos:0 overruns:0 frame:0
         Paquetes TX:50277 errores:0 perdidos:0 overruns:0 carrier:0
         colisiones:0 long.colaTX:1000 
         Bytes RX:39564408 (39.5 MB)  TX bytes:12456507 (12.4 MB)
         Interrupción:23 Dirección base: 0x6c00 

lo        Link encap:Bucle local  
         Direc. inet:127.0.0.1  Másc:255.0.0.0
         ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
         Paquetes RX:384 errores:0 perdidos:0 overruns:0 frame:0
         Paquetes TX:384 errores:0 perdidos:0 overruns:0 carrier:0
         colisiones:0 long.colaTX:0 
         Bytes RX:15891 (15.8 KB)  TX bytes:15891 (15.8 KB)

eric@eric-desktop:~$ sudo cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
```

---

### Post by biale on 2010-08-20
Hay algo que no se entiende, para ir avanzando. 

En el lugar físico desde donde corriste los comandos, Firefox (o lo que sea) llega bien a los sitios de web? Es solo un problema con los repos de Medibuntu?

---

### Post by jpoeta on 2010-08-21
Al Principio tuve problemas con Firefox pero luego solucione el problema cambio su configuracion con about:config y luego ipv6 True
Trate de hacer lo mismo con el terminal para solucionar el problema pero no se pudo.
El problema se da con los repositorios de medibuntu, y en un par de otras cosas pero lo extrano es que no es general. 
Aparte de ello cuando trate de usar otro link para medibuntu

me sale lo siguiente luego

```
W: Error de GPG: http://ppa.launchpad.net lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2ED6BB6042C24D89
W: Error de GPG: http://ppa.launchpad.net lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 608BF7B93528AE20
W: Error de GPG: http://ppa.launchpad.net lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY D6B6DB186A68F637
W: Error de GPG: http://deb.torproject.org lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 74A941BA219EC810
W: Error de GPG: http://ppa.launchpad.net lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2E183FA1E260F5B0
W: Error de GPG: http://ppa.launchpad.net lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Error de GPG: ftp://ftp.leg.uct.ac.za lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
```

---

### Post by biale on 2010-08-21
Si FFox funciona, de alguna manera estas resolviendo DNS. Pero por otro lado desabilitar IPV6 resultó ser una necesidad y no una optimización de performance. Hay dos pruebas rápidas que podés hacer.

Tal como ya lo mensioné en tu otro thread, la primera es desabilitar IPV6 a nivel del sistema (y no solo FFox). Yo en una PC de escritorio lo tengo así.

Si el procedimiento anterior no es la solución cambiaría provisoriamente los DNS por los que provee Google y que van a funcionar en cualquier lugar, aunque no necesariamente con la velocidad optima.
Basta editar el archivo anterior (sudo gedit /etc/resolv.conf) y modificar los DNS:

# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4

Si FFox sigue operativo y ademas se resuelve al menos "uno" de los repos que fallaban, (sudo apt-get update) el problema esta encarado y en parte pasa por los DNS.

---

### Post by jpoeta on 2010-08-21
Lo de cambiar en ipv6 Para el sistema lo hice pero no resulto donde decis que encuentros los dns en google? cual debería tomar para Perú donde se encuentra mi amigo.
Muchas gracias por tu respuesta

---

### Post by biale on 2010-08-21
Los encontras en:

[http://code.google.com/intl/es-AR/speed/public-dns/](http://code.google.com/intl/es-AR/speed/public-dns/)

Pero son los que puse en mi post: 8.8.8.8 y 8.8.4.4

---

### Post by jpoeta on 2010-08-21
y efectivamente eran los DNS muchas gracias, lo que quiero saber es que si debo dejar los dns publicos luego de la instalacion o los de telefonica.
Gracias de Antemano!:guitar:

---

### Post by jpoeta on 2010-08-21
todo funciono 10 puntos cuando puse los dns hasta google earth abrio perfecto pero reiniciamos y google earth me muestra error de servidor como puedo hacer que esos dns se queden para siempre como mios.
Gracias

---

### Post by guillermolisi on 2010-08-21
Pasa eso porque cuando alteras los DNS que te ofrece tu ISP solo duran hasta el proximo reinicio salvo que edites (con sudo) el archivo /etc/dhcp3/dhclient.conf y agregues/descomentes/edites la linea que esta en negrita utilizando las IPs del servidor DNS que quieras utilizar (OpenDNS en mi caso)
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
[COLOR=Blue]**prepend domain-name-servers 208.67.222.222,208.67.220.220;**[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```Reinicias los servicios de red y deberian funcionar.

Si queres confirmar si estan operativos, fijate que contenido posee el archivo /etc/resolv.conf ya que deberia ser similar a este ejemplo
```
nameserver **208.67.222.222**
nameserver **208.67.220.220**
nameserver 200.49.130.29
#nameserver 200.49.130.28
#nameserver 200.49.130.34
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
```

---

### Post by biale on 2010-08-21
Hay dos puntos...

Fijate si anotando los DNS forma gráfica quedan fijados. O sea en el applet del panel, editar las conexiones, la conexión en uso, Ajustes de IPv4, "servidores DNS":

8.8.8.8, 8.8.4.4

El segundo punto, es que si bien estos DNS son universales y pueden quedar, no necesariamente responden a la velocidad optima.

Con tranquilidad habría que llamar al proveedor de Internet y si probando resultan mas rápidos, ajustar los DNS a "telefónica", preferentemente a nivel del router y no a nivel de la PC.

... Ahora me doy cuenta que Guillermo me ganó de mano con una propuesta muy válida.

---

### Post by guillermolisi on 2010-08-21
> **biale said:**
> Hay dos puntos...

Fijate si anotando los DNS forma gráfica quedan fijados. O sea en el applet del panel, editar las conexiones, la conexión en uso, Ajustes de IPv4, "servidores DNS":

8.8.8.8, 8.8.4.4

El segundo punto, es que si bien estos DNS son universales y pueden quedar, no necesariamente responden a la velocidad optima.

Con tranquilidad habría que llamar al proveedor de Internet y si probando resultan mas rápidos, ajustar los DNS a "telefónica", preferentemente a nivel del router y no a nivel de la PC.
Coincido respecto de la velocidad en la resolucion por parte de servidores lejanos, pero hay que considerar tambien otros aspectos como la confiabilidad en la actualizacion regular y periodica de sus registros, cosa que Fibertel (por mencionar un ejemplo conocido) no realiza. No se Telefonica como se aplica a esa tarea.

---

### Post by jpoeta on 2010-08-22
Doy el post por solucionado muchas gracias amigos por las repuestas por ahora mi amigo se piensa quedar en Ubuntu.:popcorn:
Nuevamente alguien que se pasa al Ubuntu Team y espero que se quede siempre ;)
Hasta una proxima oportunidad
Jpoeta

---

