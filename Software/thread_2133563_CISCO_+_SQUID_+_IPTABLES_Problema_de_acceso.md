---
title: "CISCO + SQUID + IPTABLES: Problema de acceso"
date: 2013-04-08
forum: Software
---

### Post by soyfilipo on 2013-04-08
Buenas tardes, 
 Tengo un problema de configuración en mi red interna, tiene que ver con acceso transparente al Squid
 Mi red posee un router cisco capa 3 que tiene como ruta por defecto  de salida la interfaz de entrada de un servidor ubuntu 12.04 con squid3
 El problema para navegar se presenta que para poder acceder a  internet, tengo que configurar manualmente la dirección del proxy en los  equipos, cuando anteriormente tenia un servidor squid que no había sido  configurado por mi persona, con la misma IP y me permitía salir sin  configurar el proxy de forma manual en los navegadores.
 El problema se dio al averiarse el hardware del servidor viejo,  configure uno nuevo pero ahora no puedo salir como antes. Tengo  entendido que es un problema de firewall y debo configurarlo para que  reenvíe los paquetes que entren por la interfaz interna del proxy hacia  la externa sin perder la permisología que se crea al poner el proxy  "transparente"
 Mi configuración: 
 Servidor Proxy:
 Ubuntu 12.04
Squid 3.1
eth0: Interfaz interna - 192.168.0.16
eth1: Interfaz Externa - Ip Externa (DHCP del ISP)
 Core Cisco Layer 3
Defaul Gateway 192.168.0.16

---

### Post by hictio on 2013-04-08
Lo que necesitás es agregar una regla en el firewall que redireccione todo el tráfico web (TCP 80) al puerto TCP donde está escuchando el Squid, por default el 3128.

---

### Post by soyfilipo on 2013-04-08
Ya lo he hecho, he agregado las siguientes reglas y activado el reenvio de paquetes:

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.0.16:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

Pero tengo una pantalla de error, alguien me dijo que activara la función de proxy transparente y en efecto me funciona poniéndolo transparente, pero pierde la capacidad de autentificación de usuario, y no quiero que la pierda.

---

