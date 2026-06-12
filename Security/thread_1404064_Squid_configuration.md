---
title: "Squid configuration"
date: 2010-02-11
forum: Security
---

### Post by manilodisan on 2010-02-11
I have a server with 10 ip's that I want to give access to some friends via authentication but I'm stuck on squid's config file.

**Let's say I have these ip's available on my server:**

212.77.23.10
212.77.1.10
68.44.82.112

**And I want to allocate each one of them to a different user like so:**

212.77.23.10 goes to user manilodisan using password 123456
212.77.1.10 goes to user manilodisan1 using password 123456
68.44.82.112 goes to user manilodisan2 using password 123456


I have a basic setup from different bits I found over the internet but nothing seems to work. Here's my squid.conf (all comments are removed to make it lighter):

```
#	custom config
acl ip1 myip 212.77.23.10
tcp_outgoing_address 212.77.23.10 ip1
http_port 8088

#	squid default
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

http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
icp_access allow all
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
hosts_file /etc/hosts
forwarded_for off
coredump_dir /var/spool/squid
```

I will appreciate a little help on this matter.
Thank you.

---

### Post by cariboo on 2010-02-12
This is probably a better place to get an answer, than where it was.

---

