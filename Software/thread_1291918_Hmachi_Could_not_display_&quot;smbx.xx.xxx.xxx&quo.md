---
title: "Hmachi: Could not display &quot;smb://x.xx.xxx.xxx&quot;."
date: 2009-10-15
forum: Software
---

### Post by capcabgue on 2009-10-15
Hola a todos:
 
Tengo Ubuntu 9.04 en mis 2 equipos que quiero instalar la red  y en una máquina virtual uso también la misma versión de linux más guin2. Todas las máquinas y pcs tienen instalado Hamchi.
Bueno una vez creada la red, y los PC unidos a ésta (join existing network), compartidas las carpetas respectivas e instalado VTUN, me dispongo a hacer "examinar" en los pcs que veo y no me deja, más aún me indica:
 
Could not display "smb://x.xx.xxx.xxx".

Nautilus cannot handle "smb" locations. 

Solo puedo hacer ping sobre los terminales linux. Si pongo VNC se abre una ventana en negro que no alcanzo a leer y se cierra casi inmediatamente.
Desde guin2 los botones de activo de los pcs que veo están en verde pero pestañando. 
 
En todos los terminales instalé hamachi de la siguiente manera 

** sudo modprobe tun**
**sudo gedit /etc/modules (add tun)**
** ls /dev/net/tun**
**Bajé ****hamachi-0.9.9.9-20-lnx.tar.gz y lo descomprimí**
[B]cd hamachi-0.9.9.9-20-lnx/
[/B][B]sudo make install
[/B][B]sudo tuncfg
[/B][B]sudo groupadd hamachi
[/B]**sudo gpasswd -a user hamachi**
[B]sudo gpasswd -a root hamachi
[/B][B] sudo chmod 760 /var/run/tuncfg.sock
[/B][B]sudo chgrp hamachi /var/run/tuncfg.sock
[/B][B]hamachi-init
[/B][B]sudo hamachi start
[/B][B]sudo hamachi set-nick user_pc
[/B][B]sudo hamachi login
[/B]** sudo hamachi ****create (join)**[B]network, (según corresponda)
[/B]
Luego para tener una interfaz más amigable instalé ghamachi, lo hice ejecutable y lo incluí como aplicación. (la instalación de ambos SW lo hice según este link: [http://www.ubuntu-es.org/?q=node/67368](http://www.ubuntu-es.org/?q=node/67368))

 
Creo que esto es todo lo que me pasa y es todo los antecedentes que se me ocurren importante.

Alguien sabe que puede ser.?

Gracias y atento a sus respuestas.

---

### Post by capcabgue on 2009-11-02
Hola:

Bueno escribo para dar más datos, quizás así alguien me pueda ayudar.
La VPN con hamachi, creo que me funcionó ya que veo todos los pc conectados (son varios ya que me conecté desde la maquina virtual teniendo windows).
Bueno la cosa es que me puedo conectar desde windows a Linux o entre windows, pero cuando trato de linux a cualquier otro pc me arroja el error de smb:..etc.
Espero que me puedan ayudar a arreglar mi problema o me digan que puedo hacer para conectarme desde la pega a la casa.

Gracias y espero atento

---

### Post by moreback on 2009-11-02
Podrías revisar si tienes instalada la herramienta smbclient. Se usa desde la consola y te abre una conexion parecida a un FTP. Este programita me parece que es el que usa el Nautilus para las redes de windows.

---

### Post by capcabgue on 2009-11-03
Si, tengo instalado smbclient.

Que otra cosa puede ser??

---

### Post by asterix77 on 2009-11-03
Si estás usando samba para conectar tus pcs, me imagino que deben pertenecer al mismo grupo de trabajo. Para ello tienes que editar el archivo /etc/samba/smb.conf y en la sección Global Settings buscar workgroup y verificar que todos digan lo mismo. Además a cada pc debes asignarle una ip estática, que es mejor.

---

### Post by capcabgue on 2009-11-03
> **asterix77 said:**
> Si estás usando samba para conectar tus pcs, me imagino que deben pertenecer al mismo grupo de trabajo. Para ello tienes que editar el archivo /etc/samba/smb.conf y en la sección Global Settings buscar workgroup y verificar que todos digan lo mismo. Además a cada pc debes asignarle una ip estática, que es mejor.
La verdad un tiempo atras conecte el pc de mi sra y compartí un par de cosas. Sin embargo como me dijiste, puse el pc de mi casa y el notebook en el mismo workgroup (la red de hamachi) y aún así me da el error de smb:....
En cuanto a la IP estática, esa no me la da el servidor hamachi (5.algo).

Que más puedo hacer

---

### Post by moreback on 2009-11-03
No sé si sirva, pero podrías agregar el grupo de trabajo en la clave "/system/smb/workgroup" usando gconf-editor.

---

### Post by capcabgue on 2009-11-04
> **moreback said:**
> No sé si sirva, pero podrías agregar el grupo de trabajo en la clave "/system/smb/workgroup" usando gconf-editor.

No entendí, sé como editar ese archivo, pero para empezar no existe (¿lo debo crear?) y que pongo aqui
password: el de la red hamachi?

me puedes explicar que hago aqui, por favor.

Gracias

---

### Post by moreback on 2009-11-04
Abre gconf-editor con Alt+F2, navega hasta la clave "/system/smb/workgroup", edítala y agrega el nombre de tu grupo de trabajo.

Dije lo mismo pero al revés :-P

---

### Post by capcabgue on 2009-11-05
> **moreback said:**
>  agrega el nombre de tu grupo de trabajo

Supongo que lo debo hacer en todos los PC que conecte vía hamachi?

---

### Post by capcabgue on 2009-11-26
Bueno les cuento que la solición fue desinstalar ghamachi y volver a instalar hamachi.
Lo primero que tuve que hacer fue arreglar una ruta invalida de hamachi:
La solución es esta:
ifconfig
ham0      Link encap:Ethernet  HWaddr 00:FF:CA:D0:F5:AA  
          inet addr:5.23.68.35  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:26780 (26.1 KB)  TX bytes:21076 (20.5 KB)

luego se chequea las rutas de las tablas:
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
64.238.220.160  0.0.0.0         255.255.255.240 U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         5.0.0.0      255.0.0.0       UG    0      0        0 ham0
0.0.0.0         64.238.220.161  0.0.0.0         UG    100    0        0 eth0

Como ven el gw no corresponde a la dirección ip que me da hamachi, por lo cual hay que hacer lo siguiente:
route del -net 5.0.0.0 gw 0.0.0.0 netmask  255.0.0.0 dev ham0
route add -net 5.0.0.0 gw 5.23.68.35 netmask  255.0.0.0 dev ham0

Luego, no se por que, tengo que volver a hacer hamachi-ini, start, go-online y puedo hacer ahora ping, o control remoto o cualquier cosa con el otro pc.

Espero que les sirve, si tienen dudas, les dejo los link de las páginas que solucionó mi problema:
[http://ubuntuforums.org/archive/index.php/t-208692.html](http://ubuntuforums.org/archive/index.php/t-208692.html)
[http://enavas.blogspot.com/2008/10/crea-tu-vpn-con-logmein-hamachi.html](http://enavas.blogspot.com/2008/10/crea-tu-vpn-con-logmein-hamachi.html) 
[http://www.supware.net/HamachiUbuntuHowto/](http://www.supware.net/HamachiUbuntuHowto/)

---

