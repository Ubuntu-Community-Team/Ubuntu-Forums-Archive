---
title: "Problema Con Iptables"
date: 2012-03-03
forum: Software
---

### Post by sistemasCIAF on 2012-03-03
Buenas tardes amigos

en estos momento tengo un servidor en ubuntu 8.4, esta configurado con squid para que me haga filtrado de paginas a una red local, pero tengo un inconveniente, las paginas que abren por protocolos https, entre otros el no las permite abrir, y otro inconveniente es que las personas que usan outlook en la red o otro gestor de correos no les permite sincronizar su bandeja de entrada, en estos momentos quiero que por este servidor pasen las peticiones de los puertos de outlook que son:

25 110 143 993 995 

también e escuchado que por medio de iptables puedo hacer que mi squid escuche peticiones por el puerto 80 21 443 entre otros, y las redirija al puerto 3128 que fue el que le habilite para trabajar

ya e probado infinidad de reglas de iptables que e encontrado en diferentes foros, sin resultados positivos.

quiero saber si debo cambiar mi distribución o mi vercion de ubuntu, y cual me recomendarían para que me funcione como servidor proxy

Muchas gracias por su atención

Cesar Blandon
Auxiliar de sistemas
Univercidad CIAF Pereira

---

### Post by guillermolisi on 2012-03-05
La version deberias cambiarla para poder contar con algunos años mas de soporte ya que a la que estas usando le queda (relativamente) poco tiempo mas de vida, ademas de varias mejoras introducidas en la 10.04.
No es urgente pero estaria pensando en llevar a cabo una migracion a la 12.04 dada la proximidad de su lanzamiento.

Para saber si el problema radica en Squid o en iptables seria conveniente tener vista de como esta configurado Squid, como esta iptables y que ruteos estan programados y son requeridos.

---

### Post by sistemasCIAF on 2012-03-05
Muchas gracias guillermolisi....
claro que si en el transcurso del dia subo el archivo de configuracion de squid y uno que hize de iptables

---

### Post by sistemasCIAF on 2012-03-07
Buenos Días 
que pena la demora para poner las reglas..... tu sabes mucho trabajo

bueno te cuento tengo un archivo en init.d con nombre iptables.cf con el siguiente contenido:
_____________________________________
#!/bin/sh
##SCRIPT DE IPTABLEs
echo -n Aplicando reglas de Firewall
## FLUSH DE REGLAS

iptables -F
iptables -X
iptables -Z
iptables -t nat -F

#HABILITAR FORWARD DE PAQUETES
iptables -t nat -a POSTROUNTING -o -i eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

##SE ESTABLECEN POLITICAS POR DEFECTO
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

## EMPIEZA EL FILTRADO, eth0 es la salida a internet, eth1 la salida a red local

#El localhost se deja abierto
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

#Abrimos el puerto del Ftp
iptables -A OUTUT -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -p tcp --sport 21 -j ACCEPT

#Abrimos el puerto del WEb, PUERTO 80
iptables -A INPUT -i eth1 -p tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT

#Abrimos el puerto del WEbmin, PUERTO 10000
iptables -A INPUT -i eth1 -p tcp --sport 10000 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 10000 -j ACCEPT

#PERMITIR LA SALIDA SMTP, PUERTO 25 DEL CORREO
iptables -A INPUT -i eth0 -p tcp --sport 25 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 25 -j ACCEPT
#SMTP
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 25 -j ACCEPT
#POP3
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 110 -j ACCEPT

#Dejamos abierto el acceso al firewall desde la red local
iptables -A INPUT -s 192.168.0.0/24 -i eth1 -j ACCEPT

#Hacemos enmascaramiento de la red local y activamos el bit de FORWARDING
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE

#REDIRECCIONO LA INFO A UN PUERTO, TRANSPARENCIA
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.0/24  -d ! 192.168.0.0/24 -p tcp --dport 80 -j REDIRECT --to-port 3128
echo *OK, verifiquese el script con iptables -L -n*
#FIN DEL SCRIPT
____________________________________________________

anteriormente tenia otro con este otro contenido 

____________________________________________________
#!/bin/sh
echo -n Aplicando Reglas de Firewall...
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 21 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 3128
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 25 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 110 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 995 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 587 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 21 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 25 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 587 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p udp --dport 110 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p udp --dport 995 -j ACCEPT
iptables -F
iptables -X
iptables -Z
iptables -t nat -F
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -p tcp --sport 80 -j ACCEPT
iptables -A FORWARD -p tcp --sport 21 -j ACCEPT
iptables -A FORWARD -p tcp --dport 21 -j ACCEPT
iptables -A FORWARD -p tcp --dport 25 -j ACCEPT
iptables -A FORWARD -p tcp --sport 25 -j ACCEPT
iptables -A FORWARD -p tcp --dport 110 -j ACCEPT
iptables -A FORWARD -p tcp --sport 110 -j ACCEPT 
iptables -A FORWARD -p tcp --dport 995 -j ACCEPT
iptables -A FORWARD -p tcp --sport 995 -j ACCEPT
iptables -A FORWARD -p tcp --dport 587 -j ACCEPT
iptables -A FORWARD -p tcp --sport 587 -j ACCEPT
iptables -A FORWARD -p tcp --sport 443 -j ACCEPT
iptables -A FORWARD -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -p tcp --sport 3128 -j ACCEPT
echo " OK . Verifique que lo que se aplica con: iptables -L -n"

# Fin del script

___________________________________________________________

en el squid solo e configurado esto, aparte de las acl´s y las http_access

# Squid normally listens to port 3128
http_port 3128 transparent

#Default:
cache_dir ufs /var/spool/squid 1000 16 256
______________________________________________________

tengo una versión squid 2.6 stable18
y ubuntu 8.4

muchas gracias en lo que me puedan colaborar
pero ya estoy pensando en comprar mas maquina y actualizar el ubuntu

---

### Post by guillermolisi on 2012-03-08
Me parece que al Squid le falta un poco mas de configuracion, esa es una de las razones por las que no podes acceder a sitios que solo utilizan SSL (port 443).

El Outlook no se que puertos utiliza, ademas de los necesarios para dialogar con el o los servidores de correo.

Ademas de eso, y en forma similar a como debe realizarse tambien en un firewall, al final de todo lo permitido tiene que haber una sentencia que repudie lo demas, asi te aseguras que si algo se escapa por no estar contemplado explicitamente (goteo) esa sentencia se encarga de descartar o inhibir el acceso.

Ejemplos:

> #Recommended minimum configuration:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 #0.0.0.0/32
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
# acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
# acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
# acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
#
acl SSL_ports port 402		#
acl SSL_ports port 502		#
acl SSL_ports port 8443		#
acl SSL_ports port 10000 	#Webmin
acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 91		# [http://mail.server.org.ar:91](http://mail.server.org.ar:91)
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 402 	# empresa1
acl Safe_ports port 502 	# empresa1
acl Safe_ports port 8443 	# empresa1
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 10000 	#Webmin
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

Con esto determinas que ports/servicios son accesibles a traves de Squid.

> #Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
# Only allow purge requests from localhost
http_access deny manager
http_access allow purge localhost
# Deny requests to unknown ports
http_access deny purge
# Deny CONNECT to other than SSL ports
http_access deny !Safe_ports
#
# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
http_access deny CONNECT !SSL_ports
http_access allow AccesoTotal
http_access allow AccesoTotalSinDownUp !no_bajables !no_subibles
http_access allow AccesoGerentes
http_access deny gateway !AccesoTotal !dstcomun
http_access deny gateway2 !AccesoTotal !dstcomun
http_access deny msn_m !AccesoTotal
http_access deny msn_me !AccesoTotal
http_access deny msn_servicios !AccesoTotal
http_access deny aplicaciones_prohibidas
http_access allow !sitiosProhibidos !audiovideo AccesoUsuarios
http_access allow !sitiosProhibidos !audiovideo !no_bajables_AccesoDownloads AccesoDownloads
http_access allow AccesoCobranzaslimitado CobranzasLimitados !sitiosProhibidos !audiovideo

http_access allow AccesoElTrapial ElTrapial !sitiosProhibidos !audiovideo
http_access allow AccesoTecnicosJLG TecnicosJLG !sitiosProhibidos !audiovideo
http_access allow AccesoOperacion Operacion !sitiosProhibidos !audiovideo
http_access allow AccesoSucursales AccesoSucursales		

#http_access allow AccesoUsuarios dstcomun
http_access allow java-applet all

##############
### TALLER ###
##############
acl AccesoTaller external ldap_group AccesoTaller
acl Taller dstdomain "/etc/squid/listas/TallerLimitados.acl"
http_access allow AccesoTaller Taller !sitiosProhibidos !audiovideo

# log_uses_indirect_client on
# And finally deny all other access to this proxy
http_access deny sitiosProhibidos audiovideo no_bajables no_subibles

#
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
# http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

Fijate que hay varias ACLs y con distintas restricciones cada una.

---

### Post by guillermolisi on 2012-03-08
Me parece que al Squid le falta un poco mas de configuracion, esa es una de las razones por las que no podes acceder a sitios que solo utilizan SSL (port 443).

El Outlook no se que puertos utiliza, ademas de los necesarios para dialogar con el o los servidores de correo.

Ademas de eso, y en forma similar a como debe realizarse tambien en un firewall, al final de todo lo permitido tiene que haber una sentencia que repudie lo demas, asi te aseguras que si algo se escapa por no estar contemplado explicitamente (goteo) esa sentencia se encarga de descartar o inhibir el acceso.

Ejemplos:

> #Recommended minimum configuration:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 #0.0.0.0/32
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
# acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
# acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
# acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
#
acl SSL_ports port 402		#
acl SSL_ports port 502		#
acl SSL_ports port 8443		#
acl SSL_ports port 10000 	#Webmin
acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 91		# [http://mail.server.org.ar:91](http://mail.server.org.ar:91)
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 402 	# empresa1
acl Safe_ports port 502 	# empresa1
acl Safe_ports port 8443 	# empresa1
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 10000 	#Webmin
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

Con esto determinas que ports/servicios son accesibles a traves de Squid.

> #Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
# Only allow purge requests from localhost
http_access deny manager
http_access allow purge localhost
# Deny requests to unknown ports
http_access deny purge
# Deny CONNECT to other than SSL ports
http_access deny !Safe_ports
#
# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
http_access deny CONNECT !SSL_ports
http_access allow AccesoTotal
http_access allow AccesoTotalSinDownUp !no_bajables !no_subibles
http_access allow AccesoGerentes
http_access deny gateway !AccesoTotal !dstcomun
http_access deny gateway2 !AccesoTotal !dstcomun
http_access deny msn_m !AccesoTotal
http_access deny msn_me !AccesoTotal
http_access deny msn_servicios !AccesoTotal
http_access deny aplicaciones_prohibidas
http_access allow !sitiosProhibidos !audiovideo AccesoUsuarios
http_access allow !sitiosProhibidos !audiovideo !no_bajables_AccesoDownloads AccesoDownloads
http_access allow AccesoCobranzaslimitado CobranzasLimitados !sitiosProhibidos !audiovideo

http_access allow AccesoElTrapial ElTrapial !sitiosProhibidos !audiovideo
http_access allow AccesoTecnicosJLG TecnicosJLG !sitiosProhibidos !audiovideo
http_access allow AccesoOperacion Operacion !sitiosProhibidos !audiovideo
http_access allow AccesoSucursales AccesoSucursales		

#http_access allow AccesoUsuarios dstcomun
http_access allow java-applet all

##############
### TALLER ###
##############
acl AccesoTaller external ldap_group AccesoTaller
acl Taller dstdomain "/etc/squid/listas/TallerLimitados.acl"
http_access allow AccesoTaller Taller !sitiosProhibidos !audiovideo

# log_uses_indirect_client on
# And finally deny all other access to this proxy
http_access deny sitiosProhibidos audiovideo no_bajables no_subibles

#
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
# http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

Fijate que hay varias ACLs y con distintas restricciones cada una.

---

### Post by guillermolisi on 2012-03-08
Me parece que al Squid le falta un poco mas de configuracion, esa es una de las razones por las que no podes acceder a sitios que solo utilizan SSL (port 443).

El Outlook no se que puertos utiliza, ademas de los necesarios para dialogar con el o los servidores de correo.

Ademas de eso, y en forma similar a como debe realizarse tambien en un firewall, al final de todo lo permitido tiene que haber una sentencia que repudie lo demas, asi te aseguras que si algo se escapa por no estar contemplado explicitamente (goteo) esa sentencia se encarga de descartar o inhibir el acceso.

Ejemplos:

> #Recommended minimum configuration:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 #0.0.0.0/32
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
# acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
# acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
# acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
#
acl SSL_ports port 402		#
acl SSL_ports port 502		#
acl SSL_ports port 8443		#
acl SSL_ports port 10000 	#Webmin
acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 91		# [http://mail.server.org.ar:91](http://mail.server.org.ar:91)
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 402 	# empresa1
acl Safe_ports port 502 	# empresa1
acl Safe_ports port 8443 	# empresa1
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 10000 	#Webmin
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

Con esto determinas que ports/servicios son accesibles a traves de Squid.

> #Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
# Only allow purge requests from localhost
http_access deny manager
http_access allow purge localhost
# Deny requests to unknown ports
http_access deny purge
# Deny CONNECT to other than SSL ports
http_access deny !Safe_ports
#
# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
http_access deny CONNECT !SSL_ports
http_access allow AccesoTotal
http_access allow AccesoTotalSinDownUp !no_bajables !no_subibles
http_access allow AccesoGerentes
http_access deny gateway !AccesoTotal !dstcomun
http_access deny gateway2 !AccesoTotal !dstcomun
http_access deny msn_m !AccesoTotal
http_access deny msn_me !AccesoTotal
http_access deny msn_servicios !AccesoTotal
http_access deny aplicaciones_prohibidas
http_access allow !sitiosProhibidos !audiovideo AccesoUsuarios
http_access allow !sitiosProhibidos !audiovideo !no_bajables_AccesoDownloads AccesoDownloads
http_access allow AccesoCobranzaslimitado CobranzasLimitados !sitiosProhibidos !audiovideo

http_access allow AccesoElTrapial ElTrapial !sitiosProhibidos !audiovideo
http_access allow AccesoTecnicosJLG TecnicosJLG !sitiosProhibidos !audiovideo
http_access allow AccesoOperacion Operacion !sitiosProhibidos !audiovideo
http_access allow AccesoSucursales AccesoSucursales		

#http_access allow AccesoUsuarios dstcomun
http_access allow java-applet all

##############
### TALLER ###
##############
acl AccesoTaller external ldap_group AccesoTaller
acl Taller dstdomain "/etc/squid/listas/TallerLimitados.acl"
http_access allow AccesoTaller Taller !sitiosProhibidos !audiovideo

# log_uses_indirect_client on
# And finally deny all other access to this proxy
http_access deny sitiosProhibidos audiovideo no_bajables no_subibles

#
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
# http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

Fijate que hay varias ACLs y con distintas restricciones cada una.

---

### Post by hictio on 2012-03-09
> **sistemasCIAF said:**
> Buenos Días 
que pena la demora para poner las reglas..... tu sabes mucho trabajo

bueno te cuento tengo un archivo en init.d con nombre iptables.cf con el siguiente contenido:
_____________________________________
#!/bin/sh
##SCRIPT DE IPTABLEs
echo -n Aplicando reglas de Firewall
## FLUSH DE REGLAS

iptables -F
iptables -X
iptables -Z
iptables -t nat -F

#HABILITAR FORWARD DE PAQUETES
iptables -t nat -a POSTROUNTING -o -i eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

##SE ESTABLECEN POLITICAS POR DEFECTO
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

## EMPIEZA EL FILTRADO, eth0 es la salida a internet, eth1 la salida a red local

#El localhost se deja abierto
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

#Abrimos el puerto del Ftp
iptables -A OUTUT -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -p tcp --sport 21 -j ACCEPT

#Abrimos el puerto del WEb, PUERTO 80
iptables -A INPUT -i eth1 -p tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT

#Abrimos el puerto del WEbmin, PUERTO 10000
iptables -A INPUT -i eth1 -p tcp --sport 10000 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 10000 -j ACCEPT

#PERMITIR LA SALIDA SMTP, PUERTO 25 DEL CORREO
iptables -A INPUT -i eth0 -p tcp --sport 25 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 25 -j ACCEPT
#SMTP
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 25 -j ACCEPT
#POP3
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 110 -j ACCEPT

#Dejamos abierto el acceso al firewall desde la red local
iptables -A INPUT -s 192.168.0.0/24 -i eth1 -j ACCEPT

#Hacemos enmascaramiento de la red local y activamos el bit de FORWARDING
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE

#REDIRECCIONO LA INFO A UN PUERTO, TRANSPARENCIA
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.0/24  -d ! 192.168.0.0/24 -p tcp --dport 80 -j REDIRECT --to-port 3128
echo *OK, verifiquese el script con iptables -L -n*
#FIN DEL SCRIPT

~snip~



Si estás usando este script, y el mail server está fuera de tu red interna (como me imagino que es el caso porque abrís el puerto SMTP (25)); te faltan puertos por abrir.
Tenés solamente abierto el puerto POP3 (110), para un servidor de email standard te faltarían: el IMAP (143), el POP3S (995) y el IMAPS (993); para el puerto que comentás del Outlook, abrí el puerto 587 (Submission), todos los puertos son TCP.
Otra cosa para simplificarte la vida con las reglas, iptables acepta que uses nombres de servicio en lugar de puertos, y obtiene el puerto equivalente del archivo /etc/services; por eso podés usar la regla:

```

#Abrimos el puerto del WEb, PUERTO 80
iptables -A INPUT  -i eth1 -p tcp --sport http -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport http -j ACCEPT

```

Y al ejecutar el script, va a traducir http por el puerto correspondiente.

Otra cosa, si estás usando el script que posteaste arriba, te falta agregar también, el puerto HTTPS (443), es casi seguro que por eso no pueden navegar o acceder a páginas con web con SSL.

---

### Post by anarko on 2012-03-12
Haber si entendi, lo que queres hacer por lo menos en la parte de outlook es que cualquier PC de la red pueda pasar a travez del server para chequear mail. 
```

# Donde eth0 es la placa de red con ip publica ( internet ) 
# PUERTOS MAIL Y SSL-MAIL PARA TODOS
/sbin/iptables -A POSTROUTING -t nat -o eth0 -s 0/0 -d 0/0 --protocol tcp --destination-port 110 -j MASQUERADE
/sbin/iptables -A POSTROUTING -t nat -o eth0 -s 0/0 -d 0/0 --protocol tcp --destination-port 995 -j MASQUERADE

```

Claramente tenes que configurar los clientes para que usen como gateway la IP del servidor y poner las IP de los servidores de correo en ves de los nombres de host, sino tenes que darles salida a algun DNS.

Con esto pueden recibir mails. Con los otros puertos podes hacer lo mismo, pero yo no dejaria abiertos los de smtp ya que cualquier windows "envichado" puede ponerse a madar spam desde tu IP. Mas bien si tenes una IP fija configura los registros MX en el DNS y monta un smtp, postfix es muy flexible cunado lo entendes. 

Sobre lo del squid, abrir https lo puede hacer tranquilamente solo hace falta configuracion, te recominedo que te leas todos los tutoriales que encuentres hasta que lo puedas manejar bian porque copipastear una configuracion de alguien te va a traer quilombos.

---

