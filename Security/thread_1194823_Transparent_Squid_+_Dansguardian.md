---
title: "Transparent Squid + Dansguardian"
date: 2009-06-23
forum: Security
---

### Post by hackbac on 2009-06-23
I have a Web content filtering server using Dansguardian.  I having trouble getting the proxy to become transparent.  (That is, when the Web client browses to WhatIsMyIP.com, it should see the client IP address instead of the Proxy IP address.) 

The server is not directly connected to the network that it is filtering.  It has a single Ethernet port.

Ubuntu 9.04 (2.6.28-13-server) 
Squid Cache: Version 3.0.STABLE8
iptables v1.4.1.1
DansGuardian 2.9.9.7

I've tried many of the Squid configurations (like "http_port 3128 transparent") to enable transparent proxying, but none seem to work. 

```

*nat
-A PREROUTING -s 203.95.x.x/21 -d ! 203.95.x.x/21 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080 
-A PREROUTING -s 216.236.x.x/23 -d ! 216.236.x.x/23 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080 
-A PREROUTING -s 216.236.x.x/23 -d ! 216.236.x.x/23 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080 
COMMIT
*filter
-A INPUT -s ! 127.0.0.1/32 -p tcp -m tcp --dport 3128 -j DROP 
-A INPUT -s 203.95.x.x/21 -p tcp -m tcp --dport 8080 -j ACCEPT 
-A INPUT -s 216.236.x.x/23 -p tcp -m tcp --dport 8080 -j ACCEPT 
-A INPUT -s 216.236.x.x/23 -p tcp -m tcp --dport 8080 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 8080 -j DROP 
-A INPUT -i eth0 -j ACCEPT 
-A FORWARD -i eth0 -j ACCEPT 
```

```

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
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
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
icp_access deny all
htcp_access deny all
http_port 3128
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid3/access.log squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern (cgi-bin|\?)	0	0%	0
refresh_pattern .		0	20%	4320
icp_port 3130
always_direct allow all
coredump_dir /var/spool/squid3

```

---

### Post by jimv on 2009-06-23
Do you mean that you are seeing the client's address instead of the server's address on whatismyip.com?  Because if the proxy is working, you should only see the server's address.  "Transparent" means that all of the traffic routes through the proxy server without having to setup anything on the clients.

---

### Post by hackbac on 2009-06-23
Thanks for the quick reply!

I realize the definition of "transparent proxy," but I'm not exactly sure what else to call it. I found this definition on Wikipedia... 
> RFC 2616 (Hypertext Transfer Protocol&#8212;HTTP/1.1) offers different definitions:
    "A 'transparent proxy' is a proxy that does not modify the request or response beyond what is required for proxy authentication and identification".

I do have an intercepting proxy on my network that sends the HTTP request to Internet Web servers with a source IP address of the Web client.  (WhatIsMyIp.com shows the client IP address.)  Though, I'm not sure how this server is set up exactly. 

I am trying to host a single proxy to provide Web content filtering for three different customers. If the source address of HTTP requests get aggregated to a single IP address, it's harder to track which client is accessing which sites.

---

### Post by jimv on 2009-06-23
Ha, I noticed that later today that "transparent" has two different meanings when it comes to proxies.

EDIT

I think this should do it:

> Tag Name  	forwarded_for
Usage 	forwarded_for on|off

Description
Current HTTP/1.1 does not provide any standard way of indicating the client address in the request. Since a number of people missed having the originating client address in the request, Squid now adds its own request header called "X-Forwarded-For" which looks like this: X-Forwarded-For: 192.1.2.3|unknown

If set, Squid will include your system's IP address or name in the HTTP requests it forwards. By default it looks like this:
X-Forwarded-For: 192.1.2.3
If you disable this, it will appear as X-Forwarded-For: unknown

Default 	forwarded_for on

More info:

[http://en.wikipedia.org/wiki/X-Forwarded-For](http://en.wikipedia.org/wiki/X-Forwarded-For)

---

### Post by ayomacro on 2009-06-25
See the post.
[http://ubuntuforums.org/showthread.php?t=320733&highlight=proxy+squid+dansguardian](http://ubuntuforums.org/showthread.php?t=320733&highlight=proxy+squid+dansguardian)

---

