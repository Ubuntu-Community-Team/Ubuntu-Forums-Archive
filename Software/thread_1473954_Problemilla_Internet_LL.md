---
title: "Problemilla Internet LL"
date: 2010-05-05
forum: Software
---

### Post by aleperno on 2010-05-05
Buenas gente, les comento un par de problemas que tengo:

1) El dia de hoy cometi el "error" de hacer un pppoeconf, a lo que luego de esto, el iconito de conexiones de red [IMG]http://i41.tinypic.com/25iag50.png[/IMG] desaparecio quiero que vuelva a aparecer, y deshacer lo del pppoeconf ya que conecta a inet automaticamente.

2) La segunda cosa es que quiero acceder al modem para configurar unas cosas, del modo que hacia en Win que ponia en firefox "192.168.1.1" y entraba y ahi configuraba, recuerdo del JJ que podia hacerlo pero no recuerdo como.

Puse ifconfig y no logro visualizar cual es la ip de mi modem para acceder a el.

```
eth0      Link encap:Ethernet  direcciónHW 90:e6:ba:92:02:3e  
          Dirección inet6: fe80::92e6:baff:fe92:23e/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:132937 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:96672 errores:0 perdidos:0 overruns:0 carrier:5
          colisiones:0 long.colaTX:1000 
          Bytes RX:158802778 (158.8 MB)  TX bytes:10981480 (10.9 MB)
          Interrupción:30 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:69257 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:69257 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:23483377 (23.4 MB)  TX bytes:23483377 (23.4 MB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:190.174.47.***  P-t-P:200.51.241.***  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:132465 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:96218 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:155859131 (155.8 MB)  TX bytes:8837276 (8.8 MB)

```

Disculpen si es una preguntonta, supongo que son gajes del amateurismo jaja.

Saludos!

---

### Post by guillermolisi on 2010-05-08
El icono de red esta inserto en un applet. Fijate [en este thread]("http://ubuntuforums.org/showthread.php?t=1472304") que se habla del tema.

Por lo demas, primero tenes que remover _completamente_ el paquete pppoe y si te sigue metiendo ruido en la conexion, editar el archivo /etc/network/interfaces para borrar y adecuar su contenido.

No ves ninguna IP asignada a eth0 porque esta interviniendo pppoe en la conexion que mostras.
Resuelto esto deberias poder conectarte al modem como hacias antes.

---

### Post by aleperno on 2010-05-09
> **guillermolisi said:**
> El icono de red esta inserto en un applet. Fijate [en este thread]("http://ubuntuforums.org/showthread.php?t=1472304") que se habla del tema.

Por lo demas, primero tenes que remover _completamente_ el paquete pppoe y si te sigue metiendo ruido en la conexion, editar el archivo /etc/network/interfaces para borrar y adecuar su contenido.

No ves ninguna IP asignada a eth0 porque esta interviniendo pppoe en la conexion que mostras.
Resuelto esto deberias poder conectarte al modem como hacias antes.

Guille disculpa que te moleste xD pero como elimino el paquete PPPOE?
con apg-get remove pppeconf se ve que no, dentro de pppoeconf no encontre una opcion tampoco..

Perdon por las molestias :D

---

### Post by guillermolisi on 2010-05-09
El man de apt-get dice (en Ingles porque lo uso en ese idioma):
> remove
           remove is identical to install except that packages are removed
           instead of installed. Note the removing a package leaves its
           configuration files in system. If a plus sign is appended to the
           package name (with no intervening space), the identified package
           will be installed instead of removed.
O sea que lo desinstala pero deja su configuracion intacta, cosa que no es buena para esta circunstancia.

Luego dice:
> purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).
Que es lo que estas necesitando para eliminar todo rastro de pppoe.

Tambien se lo puede hacer via Synaptic (remover completamente) y Aptitude.

Proba y conta como te fue.

---

### Post by aleperno on 2010-05-09
Bueno, elimine eso, asi es como quedaron los paquetes ppp: [IMG]http://img210.imageshack.us/img210/549/pantallazoms.png[/IMG]  La cuestion es que sigue conectandose automaticamente a internet solo magicamente jaja. Si voy a Conexiones de Red no aparece nada, ni el Aut0 en cableada, ni el "Speedy" en DSL. y si apreto alt+f2 y pongo nm-applet no me aparece el applet..  Pero bueno, nuc que mas puedo hacer, conectado a internet sigo estando... asi que no se jaja.  Ah y lo de la IP del modem sigue igual.

[QUOTE=/etc/network/interfaces]auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual[/QUOTE]

---

### Post by guillermolisi on 2010-05-10
>  					Originally Posted by **/etc/network/interfaces** 					 				
 				[I]auto lo
iface lo inet loopback


[COLOR=Red]auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider[/COLOR]

auto eth0
iface eth0 inet manual[/I]

Edita el archivo /etc/network/interfaces y borra el bloque marcado en color. Despues proba y decinos como te fue.

---

