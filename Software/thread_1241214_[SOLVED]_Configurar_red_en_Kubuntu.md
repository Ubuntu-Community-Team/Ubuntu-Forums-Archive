---
title: "[SOLVED] Configurar red en Kubuntu"
date: 2009-08-15
forum: Software
---

### Post by FB91 on 2009-08-15
Estuve leyendo muchos sitios pero ninguno solucionó mi problema.

Tengo 2 PCs en red (cableada), una con Windows XP (conectada al modem) y la mia que es la que tiene Kubuntu 9.04.

Desde Ubuntu pude configurar todo lo más bien, pero ahora en Kubuntu se me complicó :S

Les cuento lo que intenté hacer: 

Fuí a System Settings -> Network Settings -> Network Managment y en la pestaña Wired clickee en "add" y ahí puse el ip de la otra máquina, el gateway, dns, etc, etc...

eso no funcionó... alguna idea?

el comando ifconfig -a  me muestra al eth0 (supongo que lo toma) si necesitan el comando entero diganme. (si no lo necesitan mejor porque voy a tardar a transcribirlo a mano :S )

Gracias! :D

---

### Post by SLA_leandrin on 2009-08-15
Hola,

Si buscás en el foro, te vas a cansar de ver problemas con el network-manager de KDE4 para kubuntu.
Yo diría que lo mejor que podés hacer (si te anduvo bien en gnome) es desinstalar network-manager-kde e instlar network-manager-gnome.

---

### Post by FB91 on 2009-08-15
ahh no sabía que se podía hacer eso!

y como hago para instalarlo? hay algo parecido al "Añadir o quitar" de Ubuntu?

Gracias ;)

---

### Post by SLA_leandrin on 2009-08-15
Abrí la terminal en Sistema --> Terminal y elecutá lo siguiente:

```
sudo apt-get remove network-manager-kde && sudo apt-get install network-manager-gnome
```

Después que instales el  netowrk-manager-gnome tenés que ir a Preferencias del Sistema --> Avanzado --> Autoarranque --> Añadir Programa 

Y agrerar ```
nm-applet
```

Ahí tendrías que salir de la sesión y entrar de nuevo.
Espero que te sirva!!

PD: Si, hay para añadir o quitar programas, está en Sistema --> Gestión de Software

---

### Post by FB91 on 2009-08-15
el network-manager-gnome no lo tiene que bajar de internet?? porque probé correr el comando apt-get install network-manager-gonme y la respuesta es que no encuentra el paquete

quisiera aprender a hacerlo desde el network-manager de kde

PD.: no tengo internet! (perdon si no me expliqué bien :S)

---

### Post by Hei Ku on 2009-08-15
Si, tenes que bajarlo de internet, asi que estas medio en el horno.
Vas a tener que hacerlo manualmente.

Podes contar un poco mas como estan conectadas las PCs, y cual es la que estas configurando ahora?

---

### Post by guillermolisi on 2009-08-15
> **Hei Ku said:**
> Si, tenes que bajarlo de internet, asi que estas medio en el horno.
Vas a tener que hacerlo manualmente.

Podes contar un poco mas como estan conectadas las PCs, y cual es la que estas configurando ahora?
Con esa informacion y un editor de texto podrias conectarte a Internet sin necesidad del nefasto NM que con Kubuntu se lleva a las patadas.

Si tenes una conexion fija, cableada, no haria falta NM. Por lo menos no tanto como cuando tenes una notebook y usas WiFi.

---

### Post by FB91 on 2009-08-15
La que ahora estoy configurando es la que tiene Kubuntu, la otra PC (que tiene Windows XP) es la que me "comparte" internet.

> Si tenes una conexion fija, cableada, no haria falta NM

Y como hago para configurarla sin el NM ?

---

### Post by guillermolisi on 2009-08-15
> **FB91 said:**
> La que ahora estoy configurando es la que tiene Kubuntu, la otra PC (que tiene Windows XP) es la que me "comparte" internet.



Y como hago para configurarla sin el NM ?
Dando detalles de como es la red que estas usando, IPs de cada maquina, router, etc, indicando cual es la que oficia de gateway/pasarela, etc. Cuanto mas detalle, aunque abunden, mejor.

---

### Post by FB91 on 2009-08-15
Ok, aquí van los resultados de ejecutar ipconfig /all y ifconfig -a en las 2 máquinas
[B]
PC con Windows_________________________________________________[/B]

```
Configuración IP de Windows

        Nombre del host . . . . . . . . . : ESTUDIO
        Sufijo DNS principal  . . . . . . :
        Tipo de nodo . . . . . . . . . .  : desconocido
        Enrutamiento IP habilitado. . . . : Sí
        Proxy WINS habilitado. . . . .    : No

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS :
        Descripción. . . . . . . . . . .  : NVIDIA nForce 10/100 Mbps Ethernet
        Dirección física. . . . . . . . . : 00-30-67-00-EE-2E
        DHCP habilitado. . . . . . . . .  : No
        Dirección IP. . . . . . . . . . . : 192.168.0.1
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   :

Adaptador PPP Highway - Conexión ADSL               :

        Sufijo de conexión específica DNS :
        Descripción. . . . . . . . . . .  : WAN (PPP/SLIP) Interface
        Dirección física. . . . . . . . . : 00-53-45-00-00-00
        DHCP habilitado. . . . . . . . .  : No
        Dirección IP. . . . . . . . . . . : 190.231.59.84
        Máscara de subred . . . . . . . . : 255.255.255.255
        Puerta de enlace predeterminada   : 190.231.59.84
        Servidores DNS . . . . . . . . . .: 200.45.191.35
                                             200.45.48.233

```[B]PC con Kubuntu_________________________________________________
[/B]    [FONT=&quot]
[/FONT]
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:3f:c7:fb
          inet addr:192.168.0.180  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe3f:c7fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:74263 (74.2 KB)  TX bytes:85413 (85.4 KB)
          Interrupt:252 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1339 (1.3 KB)  TX bytes:1339 (1.3 KB)

pan0      Link encap:Ethernet  HWaddr ca:5a:c0:a0:5b:d2
          inet6 addr: fe80::c85a:c0ff:fea0:5bd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:19652 (19.6 KB)

pan0:avahi Link encap:Ethernet  HWaddr ca:5a:c0:a0:5b:d2
          inet addr:169.254.9.65  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1   
  
```

---

### Post by Hei Ku on 2009-08-15
Postea tu archivo /etc/network/interfaces

---

### Post by FB91 on 2009-08-15
> **Hei Ku said:**
> Postea tu archivo /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

---

### Post by Hei Ku on 2009-08-15
Proba primero agregando estas dos lineas al archivo interfaces:

```

auto eth0
iface eth0 inet dhcp

```

Si el windows tiene un dhcp activado, eso debería funcionar. Si no. la configuramos con ip estatica y listo.

---

### Post by FB91 on 2009-08-15
no tiene dhcp activado... como sería para configurarlo con ip estatica?

---

### Post by Hei Ku on 2009-08-15
Sería así:

```

auto eth0
iface eth0 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1

```

---

### Post by FB91 on 2009-08-15
Puse lo que me dijiste pero no pasa nada... el icono de las conexiones que está en la barra de abajo no me aparece como para conectarme, la verdad que me tiene un poco mareado :S

probé reiniciando y nada...  también intenté crear desde el kde network manager una nueva conexión con los datos que tengo (gateway, dns, ip, etc...) y no pasa nada!  

el problema es internet, ya que puedo ver a la otra pc en la red pero no puedo usar internet

---

### Post by Hei Ku on 2009-08-16
la otra pc es la que tiene el modem, no?

Tambien tendrias que fijarte que tengas algo en el archivo /etc/resolv.conf

Si no, ponele esto:

nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by FB91 on 2009-08-16
> **Hei Ku said:**
> la otra pc es la que tiene el modem, no?

Tambien tendrias que fijarte que tengas algo en el archivo /etc/resolv.conf

Si no, ponele esto:

nameserver 208.67.222.222
nameserver 208.67.220.220

=D>=D>=D>=D>

10 puntos! me funcionó!

(ahora mismo te escribo desde la compu con Kubuntu :D)

EDIT.: me duró poco la alegría :( [http://ubuntuforums.org/showthread.php?t=1241486](http://ubuntuforums.org/showthread.php?t=1241486)

Gracias de todos modos Hei Ku !!

---

