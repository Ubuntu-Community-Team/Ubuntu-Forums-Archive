---
title: "Auxilioooo!!! no puedo configurar los ip fijos en ubuntu 8.10"
date: 2009-02-23
forum: Software
---

### Post by elgranzalo on 2009-02-23
Estimados llevo ya 20 dias he googleado todo lo posible y no he podido configurar dos ip estaticos en ubuntu 8.10 tengo 2 ethernet una onboard y otra pci si lo configuro la onboard con mi proveedor de internet que me da una ip fija un netmask, un gateway , y dns primary y dns secondary los configuro pero reinicio y se pierde la conexion ... he editado todo archivo posible en mi terminal y no consigo nada..

les grafico ej..
eth1 (placa onboard)
190.226.45.185
255.255.255.249
190.226.45.180

dns 200.45.171.32
dns2 200.45.171.40

y mi eth0 (placa pci)

10.0.0.109
255.0.0.0
190.226.45.185

a su vez necesito que rutee el servicio para compartirlo y me sirva de filtro para web. si alguien puede ayudarme estare ETERNAMENTE AGRADECIDO... Ya que estoy debutando en mi trabajo y debutando con Ubuntu... 

GRACIAS...

---

### Post by guillermolisi on 2009-02-23
> **elgranzalo said:**
> Estimados llevo ya 20 dias he googleado todo lo posible y no he podido configurar dos ip estaticos en ubuntu 8.10 tengo 2 ethernet una onboard y otra pci si lo configuro la onboard con mi proveedor de internet que me da una ip fija un netmask, un gateway , y dns primary y dns secondary los configuro pero reinicio y se pierde la conexion ... he editado todo archivo posible en mi terminal y no consigo nada..

les grafico ej..
eth1 (placa onboard)
190.226.45.185
255.255.255.249
190.226.45.180

dns 200.45.171.32
dns2 200.45.171.40

y mi eth0 (placa pci)

10.0.0.109
255.0.0.0
190.226.45.185

a su vez necesito que rutee el servicio para compartirlo y me sirva de filtro para web. si alguien puede ayudarme estare ETERNAMENTE AGRADECIDO... Ya que estoy debutando en mi trabajo y debutando con Ubuntu... 

GRACIAS...
Como para ver si mas o menos entiendo el contexto:

La conexion de Internet esta en eth1 ?
eth0 es la que mira hacia la LAN ?
La configuracion de las placas la haces via Network Manager o editaste el archivo /etc/network/interfaces para configurarlas ?

Para compartir la conexion de Internet podrias empezar leyendo un tutorial que se publico en el sitio web de Ubuntu-ar. Entras por Soporte (menu superior a la derecha).
FIjate que recientemente se publico un indice con todos los tutoriales disponibles.

Creo que en el foro hay algun thread que habla sobre el tema tambien.

Filtrar web, a que te referis precisamente a un proxy/cache de contenidos, de URLs, de puertos (Squid ?).

---

### Post by totolinux on 2009-02-24
Hola te cuento que me pasó lo mismo y pensé que no entendia la forma de configurar o sea no comprendía los cambios de la herramienta networ-manager yo tambien tengo dos placas eth1 y eth0 casi el mismo caso no insistí demasiado me canse de configurar los ip cada día y me quedé con 8.04 Pregunto puede tener que ver el hecho de tener dos placas de red? aca de seguro alguien nos podrá explicar como hacerlo para poder en algún momento actualizar a 8.10 y acá te dejo como configurar firestarter para compartir internet entre dos pc (una con dos placas de red) gracias GUILLERMO¡¡¡ 

[http://ubuntuforums.org/showthread.php?t=1036910&highlight=totolinux](http://ubuntuforums.org/showthread.php?t=1036910&highlight=totolinux)

---

### Post by fmsismo on 2009-02-24
Hola si queres tener la ip fija, sobre todo sin iniciar la session en las X (porque estoy asumiendo que lo estas usando de gateway al servidor), tenes que editar el archivo /etc/network/interfaces y configurar las placas ahí.

Te paso un ejemplo de lo que tengo yo hecho en el debian de mi casa.

auto eth0
allow-hotplug eth0
iface eth0 inet static
	address xxx.xxx.xxx.xxx
	netmask xxx.xxx.xxx.xxx
	gateway xxx.xxx.xxx.xxx

auto eth1
allow-hotplug eth1
iface eth1 inet static
	address 10.0.0.1
	netmask 255.255.255.0
	network 10.0.0.0
	broadcast 10.0.0.255

Este archivo lo podes editar con el vi o con el nando.

sudo vi /etc/network/interfaces

o

sudo nano /etc/network/interfaces

Despues tenes que poner los dns en el archivo /etc/resolv.conf

Tiene que quedarte una cosa así.

nameserver 200.49.130.29
nameserver 200.49.130.28
nameserver 200.49.130.34
nameserver 172.20.2.12

También lo podes editar con vi o nano

sudo vi /etc/resolv.conf
sudo nano /etc/resolv.conf

Tendrías que deshabilitar el networkmanager para que no intente pisarte la configuración.

update-rc.d -f NetworkManager remove

Fijate este link que explica como configurarlo un poco más en detalle

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

### Post by diegolmfr on 2009-03-10
Estimado Granzalo.
No te preocupes es secillo.
El problema reside en ciertas combinaciones de Ubuntu y ciertos motherboards y/o placas de red con el Network Manager.
Casualmete el bug es que una vez condfigurada la conexion y rebooteda la computadora el programa no retiene las configuraciones y siempre retorna a tratar de obtener un ip dinamica de un servidor DHCP.
La solucion: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) este administrador lo bajas de este link, el te borrara al Network manager y podras configruar sin problema tus placas alambricas como inalambricas, es mucho mas sencillo y poderoso a la vez.
Espero te sirva.
Saludos.

---

### Post by diegolmfr on 2009-03-10
Por la cuestion de configuracion adicional que necesitarias para establecer ruteos te recomiendo que lo hagas en forma grafica a traves del Webmin [http://webmin.com/](http://webmin.com/), es un aplicativo que lo podes instalar si queres desde el administrador de paquetes de ubuntu synaptic, o sino tye bajas el paquete del link es sencillo, una vez alii desde tu navegador podras configurar muy sencillamente gran parte de todo tu ubuntu, en forma grafica y muy sencilla, es una gran herramienta para un entry level como te definis y para los que no los somos tanto es extremadamente practica.
Abrazo.

---

