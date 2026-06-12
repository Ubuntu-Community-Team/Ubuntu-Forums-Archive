---
title: "Problema para compartir internet en LAN"
date: 2009-07-03
forum: Software
---

### Post by KlesK on 2009-07-03
Saludos, gente!

Acabo de instalar Ubuntu Jaunty, después de probar Intrepid. Ambas me parecieron excelentes distribuciones, pero en las dos instalaciones tuve el problema del título del thread (en realidad, hay un par más, pero este es el más importante).

Tengo que compartir internet entre dos PCs, el servidor con Ubuntu, y la terminal con Windows XP. Me conecto a internet con un módem USB (que logré hacer funcionar gracias a [**esta guía**]("http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810"))

La conexión a internet es nas0, mientras la conexión LAN es eth0 (si sirve de algo). Traté de seguir [**esta guía**]("http://ubuntu-ar.org/soporte/comos/compartir-internet") para compartir internet en LAN, pero no hay resultado ya que en el momento en que activo la conexión eth0 (le pongo un IP fijo), muere la conexión a internet (nunca puedo tener las dos activadas). Si tiro pings de una PC a la otra al estar eth0 activada, se responden. También, cuando es una red entre dos Windows (tengo ambos instalados) la conexión anda perfectamente.

Sé manejarme básicamente en Linux, pero de redes realmente no entiendo nada. Llevo un tiempo buscando en el foro, e internet pero no encontré nada que me ayude a resolver el problema. Por eso les pido a los que sepan o a los que hayan tenido el problema si me pueden ayudar con esto.

Gracias a todos de antemano.

---

### Post by guillermolisi on 2009-07-03
> **KlesK said:**
> Saludos, gente!

Acabo de instalar Ubuntu Jaunty, después de probar Intrepid. Ambas me parecieron excelentes distribuciones, pero en las dos instalaciones tuve el problema del título del thread (en realidad, hay un par más, pero este es el más importante).

Tengo que compartir internet entre dos PCs, el servidor con Ubuntu, y la terminal con Windows XP. Me conecto a internet con un módem USB (que logré hacer funcionar gracias a [**esta guía**]("http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810"))

La conexión a internet es nas0, mientras la conexión LAN es eth0 (si sirve de algo). Traté de seguir [**esta guía**]("http://ubuntu-ar.org/soporte/comos/compartir-internet") para compartir internet en LAN, pero no hay resultado ya que en el momento en que activo la conexión eth0 (le pongo un IP fijo), muere la conexión a internet (nunca puedo tener las dos activadas). Si tiro pings de una PC a la otra al estar eth0 activada, se responden. También, cuando es una red entre dos Windows (tengo ambos instalados) la conexión anda perfectamente.

Sé manejarme básicamente en Linux, pero de redes realmente no entiendo nada. Llevo un tiempo buscando en el foro, e internet pero no encontré nada que me ayude a resolver el problema. Por eso les pido a los que sepan o a los que hayan tenido el problema si me pueden ayudar con esto.

Gracias a todos de antemano.
Por favor, confirma si estas usando Network Manager para activar la conexion a Internet via USB o ambas conexiones estan como "no administradas" (porque estan configuradas a mano en /etc/network/interfaces).

---

### Post by gmunioz on 2009-07-03
Hola kle....:

La forma de utilizar iptables, es ir escribiendo regla por regla.

Como estas reglas se guardan en memoria, perdiéndose cuando apagas el

ordenado, para evitarlo, lo que puedes hacer es escribir en orden las

reglas en un script, el cual puedes ejecutar en el inicio del sistema

Para ello, editas un archivo de texto, por ejemplo, y para ser original

/etc/init.d/firewall donde pondrias las reglas 

Tu red es la interfaz eth0 y sales a Internet a través de la interfaz 

nas0. 

1- Configura tu tarjeta de red, para la red local sin puerta de enlace

ya que si le pones puerta de enlace, al activarla, los paquetes para

2- Prueba estos comandos:

 
```
sudo iptables -t nat -A POSTROUTING -s eth0 -o nas0 -j MASQUERADE

sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```

Si tu ordenador sigue conectado a internet y tiene a su vez conexión

a la red local, entonces configura definitivamente el sistema:


3-

3.1- Habilita definitivamente el forwarding en el kernel, ejecuta en 

consola:

```
sudo gedit /etc/sysctl.conf
```

Busca las líneas que dicen:

```
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1


# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1
```

Y dejalas asi, sin almohadilla en las que dice net.ipv4.xxxxxxxx:

```
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
```

Guardas el archivo.

3.2

Pulsas nuevo y le pegas este contenido:


```
#!/bin/sh
# Script para habilitar conexión compartida de internet

# Dispositivo de red de internet nas0
# Dispositivo de red local eth0

# Limpieza de las reglas preexistentes

iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

# Establecer politica por defecto

iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

# Marcar paquetes salientes con su ip de origen

iptables -t nat -A POSTROUTING -o nas0 -j MASQUERADE

# Aceptar paquetes para reenviar desde la red local

iptables -A FORWARD -i eth0 -o nas0 -j ACCEPT

# Aceptar paquetes para reenviar desde internet de conexiones ya establecidas

iptables -A FORWARD -i nas0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT

```

Lo guardas en /etc/init.d con el nombre firewall

Le das permisos de ejecución:

```
sudo chmod +x /etc/init.d/firewall
```

Y lo pones en el arranque del sistema:

```
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall
```

En los clientes de tu red local, lo único que tendrás que hacer es poner 

como puerta de enlace predeterminada (o gateway), la ip de la maquina que 

acabas de configurar.

---

### Post by deafters on 2009-07-03
hola yo tengo una configuracion similar a la tuya modem usb a internet, y placa de red configurada con ip estatica, lo que hice fue lo siguiente instale dhcp3-server ( sudo apt-get install dhcp3-server ), luego instale firestarter, le corri el asistente y voila esta andando de maravillas.
el dhcp server podrias configurarlo a mano y tambien funcionaria pero el firestarter no solo te permite compartir internet sino que ademas es un fronted muy piola para iptables como para poner un poco de seguridad en esa red ya que podes controlar todo lo que entra y sale

---

