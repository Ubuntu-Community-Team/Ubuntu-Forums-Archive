---
title: "Squid3 simple proxy setup"
date: 2010-03-01
forum: Server Platforms
---

### Post by cplain on 2010-03-01
I have set up Hardy to use as a little proxy server with a white list for a few Windows kiosks that are located in an unwatched area of a plant. I have no choice about the Windows part. I do not need a DHCP server or a firewall just a simple proxy. 

I followed the instructions from 2 blogs. The proxy is working but not the way I need it to. The white list file is loaded but ignored and https:// sites that are not on the white list load. The blog posts are here 

[LIST]
[*][http://www.sheepguardingllama.com/?p=2610](http://www.sheepguardingllama.com/?p=2610)
[*][http://www.edugeek.net/forums/nix/29121-squid3-acl.html](http://www.edugeek.net/forums/nix/29121-squid3-acl.html)
[/LIST]

My squid.conf file is below. Most of it is the default settings that came with Squid3.

```
#Recommended minimum configuration:
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 192.168.100.0/255.255.255.0, 192.168.101.0/255.255.255.0
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais#Recommended minimum configuration:
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 192.168.100.0/255.255.255.0, 192.168.101.0/255.255.255.0
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

http_access deny to_localhost

icp_access deny all

htcp_access deny all

http_port 3128
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid3/access.log squid

#We recommend you to use the following two lines.
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY

#Suggested default:
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid3

acl whitelist dstdomain "/etc/squid3/whitelist"


http_access deny !localnet
http_access deny !whitelist
http_access deny all

acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports

http_access deny to_localhost

icp_access deny all

htcp_access deny all

http_port 3128
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid3/access.log squid

#We recommend you to use the following two lines.
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY

#Suggested default:
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid3

acl whitelist dstdomain "/etc/squid3/whitelist"


http_access deny !localnet
http_access deny !whitelist
http_access deny all

```

---

### Post by cplain on 2010-05-26
With much help from the Squid mailing lists :) at [www.squid-cache.org](www.squid-cache.org) here is a corrected squid.conf in case others might be interested. I am running this on Ubuntu 10.4 server AMD64.

```

#Recommended minimum configuration:
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 192.168.100.0/24 192.168.101.0/24
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

http_access deny to_localhost
icp_access deny all
htcp_access deny all

http_port 3128
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid3/access.log squid


#Suggested default:
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern .		0	20%	4320
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid3

acl whitelist dstdomain "/etc/squid3/whitelist.txt"

# Allow localnet machines to whitelisted sites
http_access allow localnet whitelist

# block all other access
http_access deny all

```

---

### Post by Farenheit on 2012-11-16
This worked for me...thanks!

---

### Post by rajhanschinmay on 2013-09-02
I am on a network that uses proxy with authentication scheme.
Can anyone help me edit the conf file.

When I tried installing squid in Ubuntu 12.04, it automatically installed squid, squid3 and squid-common.

so let me know how to edit its conf file.

Thank you in advance.

---

### Post by iebo on 2014-02-19
> **rajhanschinmay said:**
> I am on a network that uses proxy with authentication scheme.
Can anyone help me edit the conf file.

When I tried installing squid in Ubuntu 12.04, it automatically installed squid, squid3 and squid-common.

so let me know how to edit its conf file.

Thank you in advance.

```
auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/squid_passwd
acl ncsa_users proxy_auth REQUIRED
http_access allow ncsa_users

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all
http_port 3128

hierarchy_stoplist cgi-bin ?
coredump_dir /var/spool/squid3
cache deny all

refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern .        0    20%    4320

icp_port 3130

forwarded_for off

request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access User-Agent allow all
request_header_access Cookie allow all
request_header_access All deny all
END

htpasswd -b -c /etc/squid3/squid_passwd $u $p

service squid3 restart

clear

echo " "
echo "***************************************************"
echo "   Squid proxy server set up has been completed."
echo " "
echo "You can access your proxy server at $ip"
echo "on port 3128 with user name $u"
echo " "
echo "***************************************************"
echo " "
echo " "
```

---

