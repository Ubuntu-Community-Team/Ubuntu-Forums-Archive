---
title: "Internet en VirtualBox"
date: 2009-04-23
forum: Software
---

### Post by sanflores on 2009-04-23
Buenas gente, les comento que necesito instalar un windows XP para poder acceder a una vpn (del trabajo). Hasta ahora estuve usando la vpn de cisco para linux, pero quiero hacerlo dentro de VirtualBox para poder usar mi propia conexión en mi debian, y la conexión del laburo dentro de la máquina virtual (muy restringida).

Para eso estuve viendo montón de páginas, pero casi el 90% son sobre dhcp... el problema radica en que yo tengo IP fija y no estoy logrando hacer el bridge en las conexiones... este aca es mi /etc/network/interfaces

<code>
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug eth0
#iface eth0 inet static
#       address 201.216.XXX.YYY
#       netmask 255.255.255.252
#       network 201.216.XXX.YYY
#       broadcast 201.216.XXX.YYY
#       gateway 201.216.204.222
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 200.69.XXX.1 200.69.XXX.2
#       dns-search XXX.iplannetworks.net

iface eth0 inet manual

auto tap0 tap1 tap2 tap3
iface tap0 inet manual
tunctl_user sanflores
iface tap1 inet manual
tunctl_user sanflores
iface tap2 inet manual
tunctl_user sanflores
iface tap3 inet manual
tunctl_user sanflores

auto br0
iface br0 inet static
        address 201.216.XXX.YYY
        netmask 255.255.XXX.YYY
        network 201.216.XXX.YYY
        broadcast 201.216.XXX.YYY
        gateway 201.216.XXX.YYY
        dns-nameservers 200.69.XXX.1 200.69.XXX.2
        dns-search XXX.iplannetworks.net
        bridge_maxwait 0
        bridge_ports eth0 tap0 tap1 tap2 tap3
        bridge_fd 0
</code>

Después de leer varias paginas llegue a esa configuración... pero el problema radica al hacer esto:

<code>
sanflores@PC:~$ sudo /etc/init.d/networking restart
Reconfiguring network interfaces...Set 'tap0' persistent and owned by uid 1000
if-up.d/mountnfs[tap0]: waiting for interface tap1 before doing NFS mounts (warning).
if-up.d/mountnfs[tap0]: waiting for interface tap2 before doing NFS mounts (warning).
if-up.d/mountnfs[tap0]: waiting for interface tap3 before doing NFS mounts (warning).
if-up.d/mountnfs[tap0]: waiting for interface br0 before doing NFS mounts (warning).
Set 'tap1' persistent and owned by uid 1000
if-up.d/mountnfs[tap1]: waiting for interface tap2 before doing NFS mounts (warning).
if-up.d/mountnfs[tap1]: waiting for interface tap3 before doing NFS mounts (warning).
if-up.d/mountnfs[tap1]: waiting for interface br0 before doing NFS mounts (warning).
Set 'tap2' persistent and owned by uid 1000
if-up.d/mountnfs[tap2]: waiting for interface tap3 before doing NFS mounts (warning).
if-up.d/mountnfs[tap2]: waiting for interface br0 before doing NFS mounts (warning).
Set 'tap3' persistent and owned by uid 1000
if-up.d/mountnfs[tap3]: waiting for interface br0 before doing NFS mounts (warning).
SIOCSIFADDR: No such device
br0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
br0: ERROR while getting interface flags: No such device
br0: ERROR while getting interface flags: No such device
Failed to bring up br0.
done.
sanflores@PC:~$ id -a
uid=1000(sanflores) gid=1000(sanflores) grupos=20(dialout),24(cdrom),25(floppy),29(audio),44(video),46(plugdev),110(netdev),115(powerdev),116(vboxusers),117(uml-net),1000(sanflores)
sanflores@PC:~$ 
</code>

alguien me puede tirar algo de luz sobre que me falta configurar?

Se agradece enormemente.

-Santiago

---

### Post by josecuervo86 on 2009-04-23
Hola sanflores

Mira, yo apenas instale XP en Virtualbox me conecto solo a internet. No se si es lo que estas buscando, pero dentro de las opciones de virtualbox tenes la pestaña **red**, y lo unico que hice fue marcar el checkbox donde dice **Habilitar adaptador de red**

---

### Post by sanflores on 2009-04-23
Por lo que pude ver, eso se da solo cuando tenes dhcp (el proveedor de internet te da una IP dinamica) pero yo tengo IP estatica, asi que no me funciona asi de una, tengo que hacer una especie de bridge por lo que lei, pero no lo puedo hacer andar

---

### Post by sebastianabate on 2009-04-23
Qué versión de VirtualBox tenés instalada? Desde la 2.1 en adelante no tenés que configurar nada en el archivo interfaces, lo único que tenés que hacer desde la configuración de VirtualBox es setear la placa de red virtual como bridge y seleccionar la interfaz física que querés usar. Este es mi archivo interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.253.1
netmask 255.255.255.0
gateway 192.168.253.254

```Y acá están las capturas de las pantallas de configuración de la placa de red de mi Ubuntu virtualizado en un VirtualBox 2.2 NO OSE (el bajado del sitio de VirtualBox con soporte para USB y RDP):

[IMG]http://img509.imageshack.us/img509/7509/screenshotubuntudomsett.png[/IMG]

[IMG]http://img408.imageshack.us/img408/7980/screenshotbridgednetwor.png[/IMG]

Ahora la pregunta del millón es: Si tenés ip fija con máscara 255.255.255.252 quiere decir que podés usar una sola IP, y asumo que la estás usando para tu máquina real, ¿qué IP estás usando para la virtual? Acordate que no podés usar la misma IP en la máquina real y en la virtual al mismo tiempo, a lo sumo podés cambiar la configuración de la placa real a alguna IP privada (10.0.0.1) y después sí usar la IP que te dió tu proveedor para la placa de la máquina virtual, pero vas a poder navegar únicamente desde una máquina por vez.

---

### Post by jonipet on 2011-02-24
Hola, soy un poco nuevo en esto y me preguntaba si algun crack me puede ayudar un poquito... vereis he instalado el virtualbox en ubuntu 10.10 y dentro windows vista, el caso es que necesito conectar a internet desde alli y no se como hacerlo he estado probando varias configuraciones dentro de las opciones de red pero windows dentro de virtualbox no detecta nada de nada. Alguien me puede ayudar? gracias.

---

### Post by biale on 2011-02-24
Hasta donde se solo hay que configurar en Vbox una interfase de red y luego configurar un adaptador de red en el guest (WVista). Según la configuración que se aplique a Vbox, si Vista no toma DHCP habría que configurar a mano.

---

### Post by sebasthian777 on 2011-02-26
Lo de la IP fija que nombras, es por el tipo de coneccion que tenes a Internet?

Yo hace mucho, tuve un problema similar, donde hicierla lo que hiciera no compartia la coneccion, despues pase por otro problema que era que la VM me tomaba internet como algunas VPN, dejando a la maquina HOST sin internet. 
Creo que en ese momento la solucion que encontre a este problema, fue actualizar la VM, siempre usando la de Oracle si no le pifio.

Otra cosa, no se como sera tu coneccion, pero si no tenes dhcp, fijate de setearle la ip siguiente a la que tiene la maquina host, o sino fijate si tenes un router, no creo, pero capaz este restringido el rango de dhcp.

Por las moscas, primero prova de actualizar a full la maquina virtual como dije ahi, yo tuve problemas utilizando con el ubuntu 7.04 maquinas virtuales viejas, como dijeron por ahi arriba, las ultimas versiones andan de lujo. Es mas, hasta comparto el VDI (creo que esa es la extension de las maquinas virtuales) tanto con host en linux como windows.

Contame que justo en estos dias tengo que instalar sobre ubuntu una maquina virtual por un tema del laburo, si sirve de algo pruebo de reproducir el mismo estado que el tuyo, no soy un crack para nada, pero dos cabezas trabajan mejor que una.

---

