---
title: "No puedo navegar en internet ubuntu 9.04"
date: 2009-07-30
forum: Software
---

### Post by orlan2y3 on 2009-07-30
hola
tengo un problemita con ubuntu 9.04
lo instale en mi trabajo, aqui hay como 50 maquinas con windows en la red, el internet es T1 bien bueno y rapido, ahora bien mi problema es que no puedo navegar en internet..
a las maquinas que tienen windows hay que poner ip fija para navegar en internet..
a mi ubuntu le he pues la ip fija de tal manera>:
direccion 10.0.0.24
mascara de red 255.255.255.0
puerta de enlace 10.0.0.1
servidores DNS: 196.3.81.132, 200.88.127.22
dominios de busqueda: codetel.net.do
 
mi rengo de ip es 10.0.0.......
 
de esta forma es que se configura en windows y entra a internet,
pero en ubuntu no entra ni a palo..
que hago?
que esta mal?
ayudaaaaaa.......

---

### Post by robertor on 2009-07-30
Puedes hacer ping a tu gateway?
```
ping 10.0.0.1
```

Puedes hacer ping a google?
```
ping www.google.cl
```
Debiera responder algo asi:
```
roberto@bender python$ ping www.google.cl
PING www.l.google.com (74.125.65.99) 56(84) bytes of data.
64 bytes from gx-in-f99.google.com (74.125.65.99): icmp_seq=1 ttl=54 time=135 ms
^C
--- www.l.google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 135.244/135.244/135.244/0.000 ms

```
Prueba tambien hacer ping directo a la ip de google.
```
ping 74.125.65.99
```

Para hacer ping, tienes que abrir una consola y escribir el comando.

Cosas que sospecho, que la configuración de red no este bien, que no estés resolviendo nombres y que finalmente te esten filtrando en la red.
Saludos!
Roberto

---

### Post by orlan2y3 on 2009-07-30
si
gracias
mira puedo hacerle ping al 10.0.0.1
pero no puedo hacer ping a google ni a la direccion ip de google..
pensando un poco en lo que dices ya tengo tres dias intentando navegar y nada quisas activando el dhcp del router funcione... pero lo raro es que no funcione con ip statica...
todas mis maquinas con windows funcionan bien con sus ip estaticas o manuel como dice ubuntu...
entonces????
doy ping a otras maquinas que estan en la red..
doy ping al router...
puedo ver otros equipos con windows en la red y puedo ver las redes de windows...
estoy en un grupo de trabajo de windows...
todo bien....
 
peroooooooo nooo puedo navegar en internet.... esto me tiene malll:confused:

---

### Post by robertor on 2009-07-30
> **orlan2y3 said:**
> si
doy ping a otras maquinas que estan en la red..
doy ping al router...
puedo ver otros equipos con windows en la red y puedo ver las redes de windows...
estoy en un grupo de trabajo de windows...
todo bien....

Todo eso desde Ubuntu? Entonces no es problema de red propiamente tal. Estas seguro que no estas filtrando la salida a inet por mac address o algo así?[/QUOTE]
Saludos!
Roberto

---

### Post by orlan2y3 on 2009-07-30
te refieres al internet? 
porque como te explique aqui esta todo directo, el router conectado a un switch y todas las pc conectadas a ese switch y ya por hay corre el internet. aqui no hay proxi ni servidores nada de eso... solo maquinas con windows...
dime algo que me ayude..
porfavor
lo unico que te puedo decir es que las maquinas con windows todas tien la ip manual porque si no no entran a internet..
el problema esta en mi maquina con ubuntu o en el router de internet?
o ubuntu no esta asimilando los dns o algo asi?
no se
que me dices?

---

### Post by Carlos C on 2009-08-01
Hola. Por favor publica tus dudas en el subforo adecuado. Si no sabes dónde hacerlo te sugiero entres a un subforo y leas el post "ATENCIÓN: Qué puedes publicar en este Sub Foro". Moví el thread y dejé un enlace que se borrará luego de 24 horas.

Sobre tu problema, para descartar que sea un asunto de DNS puedes probar usando opendns:

[http://ubuntuforums.org/showthread.php?t=1165288](http://ubuntuforums.org/showthread.php?t=1165288)

no pierdes nada con probar, sin embargo creo que el asunto no va por ahí, ya que dices que tampoco obtienes respuesta si escribes el ip de google.
Saludos.

---

### Post by ffjgonzalez on 2010-03-12
Yo tengo el mismo problema que tuviste vos, incluso la configuracion y la cantidad de maquinas es similar. Tambien puedo navegar en la red, y ver los recursos compartidos de la Red Microsoft, pero no puedo navegar en Internet. 
Probe configurando la red en forma manual, modificando los archivos /etc/resolv.conf y 
/etc/network/interfaces, y reiniciando la red con /etc/init.d/networking restart, pero no hay modo, no navega en internet
Que mas puedo probar?
En Windows tiene la misma configuracion y anda bien, pero con ubuntu no hay caso.
Muchas gracias x la ayuda


> **orlan2y3 said:**
> hola
tengo un problemita con ubuntu 9.04
lo instale en mi trabajo, aqui hay como 50 maquinas con windows en la red, el internet es T1 bien bueno y rapido, ahora bien mi problema es que no puedo navegar en internet..
a las maquinas que tienen windows hay que poner ip fija para navegar en internet..
a mi ubuntu le he pues la ip fija de tal manera>:
direccion 10.0.0.24
mascara de red 255.255.255.0
puerta de enlace 10.0.0.1
servidores DNS: 196.3.81.132, 200.88.127.22
dominios de busqueda: codetel.net.do
 
mi rengo de ip es 10.0.0.......
 
de esta forma es que se configura en windows y entra a internet,
pero en ubuntu no entra ni a palo..
que hago?
que esta mal?
ayudaaaaaa.......

---

### Post by Carlos C on 2010-03-13
> **ffjgonzalez said:**
> Tambien puedo navegar en la red, y ver los recursos compartidos de la Red Microsoft, pero no puedo navegar en Internet. 


Verifica primero si tienes salida al exterior o si es un problema de DNS. Haz primero un ping a algún sitio conocido:
```
ping www.google.cl
```Si no obtienes respuesta intenta con su ip, en el caso de google.cl es
```
ping 209.85.195.104
```Si tampoco tienes respuesta al menos sabes que no es problema de DNS.

---

### Post by asterix77 on 2010-03-14
No sé si estarán de más estas preguntas, pero

a) ¿puedes ingresar a la intranet con ubuntu?. Porque si puedes hacerlo, tal vez el acceso a internet lo tengan filtrado por mac.

y si no puedes ingresar ni siquiera a la intranet

b) ¿no será que la intranet esté bajo un grupo de trabajo o de un dominio?. En tal caso creo que tienes qe editar el archivo de configuración de samba, para integrarte al grupo


Saludos

---

### Post by CdK1 on 2010-03-16
Lo primero es dar información relevante, ejemplo, configuración de la red, etc y por sobretodo un lindo "ifconfig", para ver como seteaste, además la IP que le diste, no la está usando ningún PC con Windows verdad? supongo que tomaste en cuenta eso?...


Postea estos dos comandos; ifconfig y route -n


Caturra:/# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:37:15:28:ca  
          inet addr:190.45.224.15  Bcast:190.45.224.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fe15:28ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20937262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5869897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1197238430 (1.1 GiB)  TX bytes:2959447204 (2.7 GiB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:457394 (446.6 KiB)  TX bytes:457394 (446.6 KiB)

Caturra:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
190.45.224.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         190.45.224.1    0.0.0.0         UG    0      0        0 eth0
Caturra:/#

---

