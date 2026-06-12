---
title: "Squid Issues"
date: 2009-01-05
forum: Security
---

### Post by txhellkat138 on 2009-01-05
Ok so I have a proxy setup  on my ubuntu box here. the ubuntu box is also a firewall/router as well as an http proxy. I'm using dansguardian for content filtering which was working grat untill I setup user authentication for my AD clients. now anything that goes through the proxy as a router work perfect with dansguardian but the authenticated users ge no filtering whatsoever.

here is what my squid.conf looks like.

```
http_port 127.0.0.1:3128 transparent
http_port 192.168.1.1:3128 transparent
http_port 80 transparent


access_log /var/log/squid/access.log squid

auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm children 5
auth_param ntlm keep_alive on

auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off
auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp

acl all src 0.0.0.0/0.0.0.0
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
acl msn req_mime_type application/x-msn-messenger
acl authenticated proxy_auth REQUIRED

http_access allow authenticated
http_access allow localhost
http_access deny all

cache_effective_user squid
cache_effective_group squid
cache_mgr  xxxxxxxxxxxx
visible_hostname dfwprx13

```


 im thinking im just needing an extra rule for it but im not sure what I am missing. any ideas or a point in the right direction would be greatly appreciated.

---

