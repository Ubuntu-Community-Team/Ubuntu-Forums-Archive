---
title: "Yahoo Messenger cannot connect through Squid Proxy."
date: 2010-05-12
forum: Server Platforms
---

### Post by sikander3786 on 2010-05-12
Hi buddies.

I am having trouble connecting yahoo messenger through squid. Yahoo messenger is unable to log me in. I have asked in squid forums but not helpful. Can anyone here help please. Here is my config.

```

visible_hostname server

acl all src 0.0.0.0/0.0.0.0
acl localhost src 127.0.0.1/255.255.255.255
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
acl Safe_ports port 5050	# YIM
acl Safe_ports port 80		# YIM
acl Safe_ports port 23		# YIM
acl purge method PURGE
acl CONNECT method CONNECT
acl lanhome src 192.168.0.0/255.255.255.0

http_access allow localhost
http_access allow lanhome
http_access allow Safe_ports
http_access deny !Safe_ports

http_access deny all

http_port 192.168.0.0:8080

access_log /var/log/squid/access.log squid

# Apache mod_gzip and mod_deflate known to be broken so don't trust
# Apache to signal ETag correctly on such responses
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache


#  TAG: extension_methods
#	Squid only knows about standardized HTTP request methods.
#	You can add up to 20 additional "extension" methods here.
extension_methods REPORT MERGE MKACTIVITY CHECKOUT

#cgi-bins will not be cached.
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

acl magic_words1 url_regex -i 192.168

acl magic_words2 url_regex -i ftp .exe .mp3 .vqf .tar.gz .gz .rpm .zip .rar .avi .mpeg .mpe .mpg .qt .iso .raw .wav .mov .flv

acl day time 09:00-23:59

delay_pools 2

delay_class 1 2

delay_parameters 1 -1/-1 -1/-1

delay_access 1 allow magic_words1

delay_class 2 2

delay_parameters 2 30000/150000 30000/120000

delay_access 2 allow day
delay_access 2 deny !day
delay_access 2 allow magic_words2

acl YIM_ports port 5050 80 23
acl YIM_domains dstdomain .yahoo.com .yahoo.co.jp
acl YIM_hosts dstdomain scs.msg.yahoo.com cs.yahoo.co.jp messenger.yahoo.com
acl YIM_methods method CONNECT
http_access allow YIM_methods
http_access allow YIM_domains
http_access allow YIM_ports
http_access allow YIM_hosts

acl MSN_ports port 1863 443 1503
acl MSN_domains dstdomain .microsoft.com .hotmail.com .live.com .msft.net .msn.com .passport.com
acl MSN_hosts dstdomain messenger.hotmail.com
acl MSN_nets dst 207.46.111.0/255.255.255.0
acl MSN_methods method CONNECT
http_access allow MSN_domains
http_access allow MSN_methods
http_access allow MSN_ports
http_access allow MSN_hosts

```

---

