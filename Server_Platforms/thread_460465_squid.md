---
title: "squid"
date: 2007-05-31
forum: Server Platforms
---

### Post by vanoorgasmic on 2007-05-31
I need som help, I don't know what else to do.
When a client (windows) downloads any file, the connection with my proxy server[FONT="Arial Black"][SIZE="4"] squid ends[/SIZE][/FONT].
The same server (ubuntu server 6.10) has a firewall called "firestarter" with gnome desktop. I'm using that firewall because I want to know what's happening in real time.

I'm sorry if my English suxs, I don't speak English.

This is my squid file:

http_port 192.168.0.1:3128
icp_port 3130
cache_mem 150 MB
cache_swap_low 90
cache_swap_high 95
maximum_object_size 4096 KB
cache_dir ufs /var/spool/squid 700 16 256
cache_access_log /var/spool/squid/access.log
cache_log /var/spool/squid/cache.log
cache_store_log /var/spool/squid/store.log
dns_nameservers 200.x.x.x 200.x.x.xx
client_netmask 255.255.255.0

#Directorio de errores --> en espaÃ±ol
error_directory /etc/squid/errors/
#Correo del administrador del USSDH-Puente
cache_mgr [email]ujkik@ppp.edu.pe[/email]

#Listas de control de Acceso

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl RedLocal src 192.168.0.0/255.255.255.0

#Mas LISTAS

acl SSl_ports port 443 563 10000
acl Safe_ports port 21 70 80 210 443 563 1025-65535
acl Safe_ports port 280
#http-mgmt
acl Safe_ports port 488
#gss-http
acl Safe_ports port 591
#filemker

acl Safe_ports port 10000


#**************************Bloqueo de Messenger Microsoft********************
#****************************************************************************
acl Aplicaciones_Prohibidas req_mime_type "/etc/squid/squid.mime-prohibido"
# Bloqueamos gateway.dll para versiones viejas de MSN Messenger
acl msn_url url_regex -i gateway.dll
# Bloqueamos el puerto utilizado por todas las versiones
acl msn_port port 1863
# Bloqueamos el metodo POST utilizado por las nuevas versiones de MSN Messenger
acl msn_method method POST
#
acl msn-messenger url_regex -i gateway.dll


#*************************Bloqueo de Messenger Yahoo**************************
#*****************************************************************************


acl yahoo url_regex http.pager.yahoo.com
acl yahooo url_regex http.msg.yahoo.com
acl yahoooo url_regex messenger.yahoo.com


acl CONNECT method CONNECT
acl Sitios_Prohibidos url_regex -i "/etc/squid/sitios_prohibidos"


#Configuracion por defecto

http_access allow manager localhost
http_access allow manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports

http_access allow localhost
http_access allow RedLocal !Sitios_Prohibidos



#********Denegar Messenger****************
#*****************************************


http_access deny Aplicaciones_Prohibidas
http_access deny msn_method msn_url
# bloqueamos el url que contenga gateway.dll
http_access deny msn_port
# bloqueamos el puerto
http_access deny CONNECT msn_port
# bloqueamos por tunneling

#
http_reply_access deny msn-messenger
http_access deny yahoo

#******************Denegar Messenger Yahoo***********
#****************************************************

http_access deny yahooo
http_access deny yahoooo
http_access deny all

#*****************************************
#*****************************************


#request_headers_max_size 10 KB
#request_body_max_size 512 KB
#reply_body_max_size 512 KB

visible_hostname Puente

---

