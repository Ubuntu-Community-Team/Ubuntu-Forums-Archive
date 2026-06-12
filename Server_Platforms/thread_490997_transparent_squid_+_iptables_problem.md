---
title: "transparent squid + iptables problem"
date: 2007-07-03
forum: Server Platforms
---

### Post by Erdem on 2007-07-03
hi
i have a little problem...
i cant set up squid transparent.

i find a command for that

[HTML]iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128[/HTML]

but when i run this comman i have this message:

[HTML]iptables v1.3.4: can't initialize iptables table '-nat': Table does not exist (do you need to insmod?) Perhaps iptables or your kernel need to be upgraded.[/HTML]

here is my squid.conf
[HTML]http_port 3128 transparent

hierarchy_stoplist cgi-bin ?


acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY


acl apache rep_header Server ^Apache
broken_vary_encoding allow apache

cache_mem 50 MB

cache_dir ufs /var/spool/squid 1000 16 256

access_log /var/log/squid/access.log squid


hosts_file /etc/hosts


refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320

acl all src 0.0.0.0/0.0.0.0

acl yerelAg src 192.168.1.0/255.255.255.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8

acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

http_access allow localhost
http_access allow yerelAg
http_access deny all
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports


http_reply_access allow all

icp_access allow all
cache_effective_group proxy
visible_hostname server.bnc.ld
coredump_dir /var/spool/squid

httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on[/HTML]

i use ubuntu 7.04 server edition (no x)

thanks for answers...

---

### Post by J-Rod on 2007-07-03
Do you have iptables installed? I don't know how much I can help, but I have been using webmin to manage the proxy server, and iptables was not installed by default on my system. Your error code talks about maybe needing to upgrade iptables, but you're on a new version of Ubuntu, so I doubt it's an issue of you running an *old* version.

---

### Post by MJLINUX on 2007-07-06
> **Erdem said:**
> hi
i have a little problem...
i cant set up squid transparent.

i find a command for that

[HTML]iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128[/HTML]

but when i run this comman i have this message:

[HTML]iptables v1.3.4: can't initialize iptables table '-nat': Table does not exist (do you need to insmod?) Perhaps iptables or your kernel need to be upgraded.[/HTML]

here is my squid.conf
[HTML]http_port 3128 transparent

hierarchy_stoplist cgi-bin ?


acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY


acl apache rep_header Server ^Apache
broken_vary_encoding allow apache

cache_mem 50 MB

cache_dir ufs /var/spool/squid 1000 16 256

access_log /var/log/squid/access.log squid


hosts_file /etc/hosts


refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320

acl all src 0.0.0.0/0.0.0.0

acl yerelAg src 192.168.1.0/255.255.255.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8

acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

http_access allow localhost
http_access allow yerelAg
http_access deny all
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports


http_reply_access allow all

icp_access allow all
cache_effective_group proxy
visible_hostname server.bnc.ld
coredump_dir /var/spool/squid

httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on[/HTML]

i use ubuntu 7.04 server edition (no x)

thanks for answers...
I think that 
first u need to switch su, after that enter the command

good luck

---

### Post by koenn on 2007-07-06
this is a hint :
"table '-nat': Table does not exist (do you need to insmod?)"

for ipables to do this kind of NAT/Redirection, you might need an additional module such a conntrack

try running ```
 modprobe ip_conntrack
``` before the iptables redirect statement.

---

