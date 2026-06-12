---
title: "Squid Confi won't work"
date: 2013-02-03
forum: Server Platforms
---

### Post by lucas.robb on 2013-02-03
Hi All,

I've searched hi and low for this but I cannot seem to get squid to work for me.  I'll post the two /etc/squid3/squid.conf files I've used.  What I'm looking for is a squid config that will work for all computers on my network (wired, wireless, or VPN) I'm using a 192.168.10.0/24 for my addressing, and my server is at 192.168.10.119

```
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
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
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access allow all
http_access allow localhost
http_access deny all
http_port 3128
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .		0	20%	4320
acl internal_network src 192.168.10.0/24
http_access allow internal_network

```

```
acl all src 0.0.0.0/0.0.0.0
acl internal_network src 192.168.10.0/24
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 # https, snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 563 # https, snews
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access allow internal_network
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
http_port 3128

```

so far nothing has worked at all, I point my http proxy to 192.168.10.119:3128 and nothing will work

---

### Post by SeijiSensei on 2013-02-03
[QUOTE=lucas.robb;12490740]
```
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
[stuff]
http_access deny all
[stuff]
acl internal_network src 192.168.10.0/24
http_access allow internal_network

```

You have the default "deny all" rule above the rule permitting your internal network.  Squid evaluates access rules in the order they appear.  I usually group all the acls together above the http_access rules, so put the internal_network definition up with the localhost definition, and move the matching http_access directive above the "deny all" line.

---

### Post by lucas.robb on 2013-02-04
wonderful, my current configuration will work to pass traffic, the only thing is that it won't pass https:// pages, what directive must I change for that?

---

### Post by lucas.robb on 2013-02-04
this is my current config

acl all src 0.0.0.0/0.0.0.0
acl internal_network src 192.168.10.0/24
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 # https, snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 563 # https, snews
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access allow internal_network
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access allow all
http_reply_access allow all
icp_access allow all
http_port 3128

---

### Post by SeijiSensei on 2013-02-04
Squid cannot proxy HTTPS traffic without it appearing to be a "man-in-the-middle" attack. Recently some clever developers are working on [solutions]("http://wiki.squid-cache.org/Features/SslBump") for this, but it requires that you generate an SSL certificate and install it on the proxy and all of the clients.  As of yet, this method requires that the proxy be specified on each client's browser as well; a "[transparent]("http://tuxnetworks.blogspot.com/2012/07/squid-3-transparent-proxy.html")" proxying method like the one available for HTTP is in the works.

---

### Post by lucas.robb on 2013-02-04
That makes a lot of sense, with that being said.  I am running squid from my server which is a CA for my vpn clients.  I have a friend in the US who needs a canadian IP for some things, since I have him on the vpn I have a .crt, .csr, .key for that client that validates against my CA for VPN purposes.  Can you think of an easy way that I could provide him a canadian IP for doing what he wishes to do? I've used dynamic ssh forwarding as a SOCKS server, I could look into creating a user for him so he can use SSH and use PUTTY as a SOCKS client, and configure the proxy settings in windows 7 for him.

(Server is ubuntu 12.04, client is windows 7)

Thank you so much for your assistance.

---

### Post by SeijiSensei on 2013-02-04
Can't help with that I'm afraid, and even if knew the answer, telling you would bump up against the forum rules banning help on anything intended to circumvent legal restrictions.  Most times when someone "needs" an IP in another country, circumvention is the usual reason.

---

### Post by lucas.robb on 2013-02-04
that makes total sense with me.  Last thing I would want would be to circumvent the law, nor to violate the rules of the forum, I have options such as socks server, etc. but I still would like to learn to set this up anyway, if you can direct me to where there is a how to I would appreciate it, but I understand otherwise.

---

