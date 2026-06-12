---
title: "Problem With Squid"
date: 2021-08-12
forum: Server Platforms
---

### Post by orelsasi on 2021-08-12
Hey, we have a raspberry pi machine that's running a squid proxy server with 7 Hauwei mobile routers attached to it through a hub.
The squid configuration and latest logs will be attached at the end of this message.
Basically, it all works well for about an hour in a row until one or more of the 7 different 4G proxies that we got (one for each mobile router) stops working, sometimes for a few minutes, and sometimes for entire hours.
We do not know why it's happening, but we do know a few things almost for sure:
1. When we restart squid, it all suddenly starts working again (most of the time)
2. We receive a NONE_ABORTED:HIER_NONE error when we check the access logs.


Our squid configuration is as follows:
acl port1 myport 20001
acl port2 myport 20002
acl port3 myport 20003
acl port4 myport 20004
acl port5 myport 20005
acl port6 myport 20006
acl port7 myport 20007


auth_param basic program /usr/lib/squid/basic_db_auth --plaintext --persist
auth_param basic children 5
auth_param basic realm Web-Proxy
auth_param basic credentialsttl 1 hour
auth_param basic casesensitive off
external_acl_type acl_helper %MYPORT %LOGIN /usr/bin/php /home/pi/external_acl.php
acl user external acl_helper
http_access allow user
http_port 20001
http_port 20002
http_port 20003
http_port 20004
http_port 20005
http_port 20006
http_port 20007


tcp_outgoing_address 192.168.9.114 port1
tcp_outgoing_address 192.168.10.116 port2
tcp_outgoing_address 192.168.11.118 port3
tcp_outgoing_address 192.168.12.120 port4
tcp_outgoing_address 192.168.13.122 port5
tcp_outgoing_address 192.168.14.124 port6
tcp_outgoing_address 192.168.15.125 port7


access_log /var/log/squid/access.log common
coredump_dir /var/spool/squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320

---

