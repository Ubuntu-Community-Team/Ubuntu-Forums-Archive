---
title: "compartir coneccion a internet"
date: 2009-02-08
forum: Software
---

### Post by tsueseres on 2009-02-08
estoy desesperado, llevo toda la tarde tratando de compartir internet de ubuntu a ubuntu (de una laptop a una de escritorio), he seguido algunos tutoriales pero no puedo

tengo ubuntu 8.04 en las 2 
he instalado firestarter 
mis dispositivos son
wlan0 que esla que se conecta a internet
eth2 que es con la que quiero compartir internet

si me pudieran ayudar

---

### Post by hictio on 2009-02-08
Cómo están conectadas las dos máquinas? Directamente una a otra mediante ethernet, o bien hay un hub en el medio?
La máquina que comparte internet funciona como servidor DHCP de la otra, o estás usando direcciones IP fijas?
Las máquinas, entre si, se ven? Responden al ping de una a otra?

No me quedó claro lo de las interfaces que pusiste, "wlan0", tenés un router WiFi en la red?

---

### Post by tsueseres on 2009-02-08
> **hictio said:**
> Cómo están conectadas las dos máquinas? Directamente una a otra mediante ethernet, o bien hay un hub en el medio?
La máquina que comparte internet funciona como servidor DHCP de la otra, o estás usando direcciones IP fijas?
Las máquinas, entre si, se ven? Responden al ping de una a otra?

No me quedó claro lo de las interfaces que pusiste, "wlan0", tenés un router WiFi en la red?

ok tengo un router con el cual me conecto a internet con el dispositivo wlan0 ( mi wireless card de la laptop) y quiero pasarle internet a la de escritorio por medio del dispositivo eth2 (conexion lan de la laptop a la de escritorio) 

espero haberme explicado

---

### Post by faktorqm on 2009-02-09
Lo que podes hacer es:

1) Habilitar el forwarding en el kernel, ejecutando en consola, (Aplicaciones - Accesorios - Terminal):

sudo gedit /etc/sysctl.conf

Buscar las líneas que dicen:

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

Y dejarlas asi, sin almohadilla en la segunda:

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Guardar el archivo.

2) Estando en gedit (editor de texto) pulsar en nuevo y previo copiar el siguiente contenido, pegarlo en el archivo.


#!/bin/sh
# Script para habilitar conexión compartida de internet

# Limpieza de las reglas
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

# Habilitación de compartición
iptables -A INPUT -i eth2 -j ACCEPT
iptables -t nat -A POSTROUTING -s eth2 -o wlan0 -j MASQUERADE
iptables -A FORWARD -i eth2 -j ACCEPT


Guardar el archivo como /etc/init.d/firewall
Cerrar gedit

3) Ejecutar las siguientes ordenes:
sudo chmod +x /etc/init.d/firewall
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall

Reiniciar la pc

4) En la pc cliente
Lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la máquina que acabas de configurar. (no en dhcp)

Créditos a gmunioz, yo solo cambie los nombres de los dispositivos. Salu2!!

---

