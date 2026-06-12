---
title: "problemas de red entre 2 pc's ubuntu"
date: 2009-01-11
forum: Software
---

### Post by totolinux on 2009-01-11
hola mi problema es que solo tengo la posibilidad de navegar o compartir archivos pero nunca puedo hacer las dos cosas en el mismo momento el escenario es el siguiente 
1º pc 1 hace de servidor de internet y tiene dos placas etho y eth1
eth1 es la de  la conección a internet con ip fija 
eth0 es la que se conecta con un cable cruzado a la otra pc 2
ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:e0:7d:e1:8d:3a  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::2e0:7dff:fee1:8d3a/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:44221 (43.1 KB)  TX bytes:491654 (480.1 KB)
          Interrupción:11 Dirección base: 0xd000 

eth1      Link encap:Ethernet  direcciónHW 00:11:5b:44:bf:1b  
          inet dirección:192.168.110.197  Difusión:192.168.110.255  Máscara:255.255.255.0
          dirección inet6: fe80::211:5bff:fe44:bf1b/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:41422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37901 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:26275666 (25.0 MB)  TX bytes:11657019 (11.1 MB)
          Interrupción:11 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1777 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:91320 (89.1 KB)  TX bytes:91320 (89.1 KB)
para poder compartir internet tengo que arrancar firestarter 
y para poder compartir archivos tengo que apagar firestarter y colocar en difusión 192.168.0.1 lo mismo que en la ip.
en la pc 2 tengo solo una eth0 ip 192.168.0.2 mascara 255.255.255.0 dif 192.168.0.1 
si alguien me puede ayudar le estaría muy agradecido.

---

### Post by totolinux on 2009-01-11
agrego resultado etc/network/interfaces para que quede claro
auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.110.197
netmask 255.255.255.0
gateway 192.168.110.1

auto eth1

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0



auto eth0

---

### Post by KaKuS on 2009-01-12
Una solución definitiva es comprarte un router, no son tan caros, conectas a ese tu conexión de internet. Le clonas los datos para que navegue y te olvidas.

PROS: 
es un pedaso de fierro que anda y anda y anda.....
no tenes que tener siempre una pc encendida para que la otra navegue
te hace de firewall
podes, pensado a futuro, agregar pcs sin que te duela la cabeza

CONTRAS:
como mucho comprando uno de marca U$S 50,00 menos en el bolsillo (hay de u$S 20,00)


Se que no es una solución directa a tu problema, pero como ya sufrí lo que estás viviendo va como opción para tu sanidad mental.

---

### Post by totolinux on 2009-01-12
Te doy gracias por tu respuesta. y es verdad las dos pc's me dan mas que un dolor de cabeza. la verdad es que arranqué con dos pc's viejas y varatitas y con eso y gracias a linux tengo toda la funcionalidad a pesar de que eran de descarte ( es mas una de las placas de red la encontre tirada en la calle) o sea a porfiado no me gana nadie y se que en linux no hay que preguntar si se puede, sino como. 
o espero a que alguien tire a la calle algun ruter viejito saludos:D

---

### Post by guillermolisi on 2009-01-12
> **totolinux said:**
> hola mi problema es que solo tengo la posibilidad de navegar o compartir archivos pero nunca puedo hacer las dos cosas en el mismo momento el escenario es el siguiente 
1º pc 1 hace de servidor de internet y tiene dos placas etho y eth1
eth1 es la de  la conección a internet con ip fija 
eth0 es la que se conecta con un cable cruzado a la otra pc 2
ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:e0:7d:e1:8d:3a  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::2e0:7dff:fee1:8d3a/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:44221 (43.1 KB)  TX bytes:491654 (480.1 KB)
          Interrupción:11 Dirección base: 0xd000 

eth1      Link encap:Ethernet  direcciónHW 00:11:5b:44:bf:1b  
          inet dirección:192.168.110.197  Difusión:192.168.110.255  Máscara:255.255.255.0
          dirección inet6: fe80::211:5bff:fe44:bf1b/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:41422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37901 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:26275666 (25.0 MB)  TX bytes:11657019 (11.1 MB)
          Interrupción:11 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1777 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:91320 (89.1 KB)  TX bytes:91320 (89.1 KB)
para poder compartir internet tengo que arrancar firestarter 
y para poder compartir archivos tengo que apagar firestarter y colocar en difusión 192.168.0.1 lo mismo que en la ip.
en la pc 2 tengo solo una eth0 ip 192.168.0.2 mascara 255.255.255.0 dif 192.168.0.1 
si alguien me puede ayudar le estaría muy agradecido.
Por lo ultimo que comentas sobre Firestarter me da la impresion de que te faltan habilitar reglas para que permita compartir archivos mientras accedes a Internet o, y esto es mas probable aun, cuando configuras Firestarter se define una de las placas de red como la que posee acceso a Internet y la otra para LAN cuando deberia ser al reves, por eso bloquea un servicio y habilita otro.

Como para ubicarnos mejor en la situacion que comentas:

En cual de las dos maquinas corres Firestarter ?

Que protocolo estas usando para compartir archivos entre las dos PCs ?

Que ISP tenes contratado para Internet ? (por que usas IP fija y no dinamica ?)

La IP fija que decis usas para Internet NO es publica, es una IP privada y es una subred de la LAN interna formada por ambas maquinas (creo que esto es una buena parte del problema).

---

### Post by totolinux on 2009-01-12
1) En cual de las dos maquinas corres Firestarter ?
2)Que protocolo estas usando para compartir archivos entre las dos PCs ?
3)Que ISP tenes contratado para Internet ? (por que usas IP fija y no dinamica ?)

La IP fija que decis usas para Internet NO es publica, es una IP privada y es una subred de la LAN interna formada por ambas maquinas (creo que esto es una buena parte del problema).
__________________
mira soy medio nuevito pero voy a tratar de contestar...
1) solo corro firestarter en la que es servidora  la pc 1º la de las dos placas eth.
2)cuando coloque la opción compartir carpetas se instalaron automaticamente creo que es (SMB).
3)contratè un servicio wireless aparentemente estoy conectado en la misma antena con otros vecinos y me dieron ip fija y en la otra eth asigné de la misma manera ip fija.
En firestarter en la pestaña eventos conexiones bloqueadas esta a full 
me indica por ejemplo(hit from 10.0.11.210 detected).
cualquier dato que falte pedimelo que este tema quiero solucionarlo gracias por tu interés:confused:

---

### Post by sergiom99 on 2009-01-14
antes de que se vaya el foro al cuerno, me habia preguntado en voz alta:
no hace falta hacer un "bridge" entre las dos redes para que una salga por la otra? algun tipo de regla?

---

### Post by guillermolisi on 2009-01-14
Por lo que veo, las dos PCs estan en la misma red (192.168.0 con mascara 255.255.255.0) con lo cual deberian verse entre si.

Proba de editar y modificar el archivo /etc/network/interfaces de la segunda maquina y cambiarle el siguiente parametro:
```
gateway = 192.168.110.197 (ya que es esta maquina la que posee la pasarela a Internet y resuelve los DNS del ISP)
```

Reinicia los servicios de red de esa segunda PC con
```
sudo /etc/init.d/networking restart
```

Y proba y comenta como te fue (con y sin Firestarter).

---

### Post by totolinux on 2009-01-14
Gracias gillermo pero no nos entendemos o no te entendí:
la pc1 es la de las dos placas y en la que da internet a la otra (pc2).

(Pc1):
auto lo
iface lo inet loopback

iface eth1 inet static (Internet)
address 192.168.110.197
netmask 255.255.255.0
gateway 192.168.110.1
auto eth1
iface eth0 inet static (red Hogareña)
address 192.168.0.1
netmask 255.255.255.0
auto eth0
(Pc2):
iface eth0 inet static 
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
esta es la config solo tengo acceso a internet desde la Pc2 con firestarter activado pero no puedo ver o compartir carpetas desde ninguna de ellas.

---

### Post by guillermolisi on 2009-01-14
> **totolinux said:**
> Gracias gillermo pero no nos entendemos o no te entendí:
la pc1 es la de las dos placas y en la que da internet a la otra (pc2).

(Pc1):
auto lo
iface lo inet loopback

iface eth1 inet static (Internet)
address 192.168.110.197
netmask 255.255.255.0
gateway 192.168.110.1
auto eth1
iface eth0 inet static (red Hogareña)
address 192.168.0.1
netmask 255.255.255.0
auto eth0
(Pc2):
iface eth0 inet static 
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
esta es la config solo tengo acceso a internet desde la Pc2 con firestarter activado pero no puedo ver o compartir carpetas desde ninguna de ellas.
Ok. Entonces el tema de acceder a Internet desde PC2 no es un problema.

Ahora, que se vean los recursos compartidos de las dos PCs con Firestarter activado requiere que me digas que definiciones/reglas tiene configuradas.

Al Firestarter tenes que decirle que las dos PCs se pueden ver. Te paso un screenshot de parte de las definiciones del que uso en mi casa (cuatro maquinas reales, varias virtuales, Ubuntu y WinXP) como para que veas a que me refiero (90.0.0.1 es la PC que en tu caso denominas PC1 y esa IP es la interna. La otra placa de red que posee esa maquina tiene IP publica dinamica asignada por mi ISP.

---

### Post by totolinux on 2009-01-15
Gracias Guillermo !capo¡ ahora si lo logramos el problema fué este
Aquí te paso las difiniciones que fuí poniendo al leer algunos tuturiales 
EN: PERMITIR LAS CONEXIONES DESDE EL HOST
192.168.0.2
192.168.0.1

EN: PERMITIR SERVICIO - PUERTO  - PARA 
BitTorrent            6881-6889  everyone
Samba (SMB)             138      everyone

EN: REENVIAR SERVICIO ETC ETC ETC 
   NADA...

copié las reglas de  (PERMITIR SERVICIO - PUERTO  - PARA)  de tu PC y listo!!! Saludos :D

---

### Post by guillermolisi on 2009-01-15
> **totolinux said:**
> Gracias Guillermo !capo¡ ahora si lo logramos el problema fué este
Aquí te paso las difiniciones que fuí poniendo al leer algunos tuturiales 
EN: PERMITIR LAS CONEXIONES DESDE EL HOST
192.168.0.2
192.168.0.1

EN: PERMITIR SERVICIO - PUERTO  - PARA 
BitTorrent            6881-6889  everyone
Samba (SMB)             138      everyone

EN: REENVIAR SERVICIO ETC ETC ETC 
   NADA...

copié las reglas de  (PERMITIR SERVICIO - PUERTO  - PARA)  de tu PC y listo!!! Saludos :D

Una acotacion. En Permitir Servicio - Samba (smb) no le des permisos a Everyone sino solo a las maquinas de tu LAN, asi si alguien de afuera quiere conectarse por ese protocolo desde Internet no podra.

Me alegro que funcione todo.

Ah ... si el tema esta finiquitado, marca el thread como SOLVED, por favor.

---

### Post by totolinux on 2009-01-15
Si, lo puse tal cual a lo de tu config. asi que todo listo.
perdon pero no se donde tengo que cliquear para poner SOLVED :oops:

---

### Post by guillermolisi on 2009-01-15
> **totolinux said:**
> Si, lo puse tal cual a lo de tu config. asi que todo listo.
perdon pero no se donde tengo que cliquear para poner SOLVED :oops:

Mira, si no recuerdo mal, esta dentro de la seccion Thread Tools, abajo a la izquierda de la lista de mensajes o como una opcion (abajo a la izquierda) de los mensajes que enviaste dentro de este hilo.

---

