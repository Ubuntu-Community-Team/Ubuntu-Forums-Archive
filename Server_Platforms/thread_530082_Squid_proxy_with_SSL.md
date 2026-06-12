---
title: "Squid proxy with SSL"
date: 2007-08-20
forum: Server Platforms
---

### Post by pantheon13 on 2007-08-20
Hello! 
My name is George, I have a problem with squid proxy.
We run Ubuntu Feisty Fawn 7.04 and squid 2.6 stable

My squid.conf file is this:
```

# SQUID CONFIGURATION FILE
visible_hostname Linux-Proxy 
http_port 8080
icp_port 8080
cache_peer 10.70.31.203 parent 8080 8080 no-query default
dns_nameservers 10.70.31.245 10.10.32.245 10.10.19.12


cache_mem 950 MB
#acl QUERY urlpath_regex cgi-bin \?
#no_cache deny QUERY
#hierarchy_stoplist cgi-bin asp jsp srf \?
cache_dir ufs /etc/squid/cache 40960 16 2048
cache_log /etc/squid/cache.log
log_fqdn on
redirect_rewrites_host_header off
emulate_httpd_log on

#Access lists
acl localnet src 10.0.0.0/255.255.255.0
acl localhost src 127.0.0.1/255.255.255.255
acl permitted_hosts src 10.70.19.244
acl ncc src 10.70.21.0/255.255.255.0
acl ifx src 10.70.19.0/255.255.255.0
acl www proto HTTP SSL
acl ftp proto FTP
acl GET method GET
acl SSL_ports port 443 563
acl Safe_ports port 80 443 210 119 70 21 563 1025-65535
acl all src 0.0.0.0/0.0.0.0

#Unwanted file types
acl forbiden_prefix url_regex -i ftp \.mp3$ \.avi.$ \mpeg$ \.mpg$ \.flv$
acl banned_sites url_regex /etc/squid/banned_url.list

#Access
http_access allow localnet
http_access allow localhost
http_access allow permitted_hosts
http_access allow ncc
http_access allow ifx
http_access allow all
http_access allow GET
http_access allow www
http_access deny !Safe_ports
http_access deny banned_sites


acl cache_prevent1 url_regex cgi-bin /?
acl cache_prevent2 url_regex Servlet
no_cache deny cache_prevent1
no_cache deny cache_prevent2


maximum_object_size 30000 KB
store_avg_object_size 50 KB


cache_mgr [email]nccsup1@olympic-airways.gr[/email]
cache_effective_user squid
cache_effective_group squid
log_icp_queries off
buffered_logs on

```
My squid proxy IP is 10.70.19.246 and listens to port 8080
The connection is through only 1NIC (if you suggest a 2nd i can install).
The connection is through one Cache Engine
Cache Engine IP: 10.70.31.203:8080
the cache engine is connected to a DMZ router and supplies our network.
When i start the proxy everything is ok and all computers can see normal pages but when we try to login to GMAIL or HOTMAIL or any https site we got an error:
```

The requested URL could not be retrieved

While trying to retrieve the URL: www.google.com:443

The following error was encountered:

    Unable to determine IP address from host name for 

The dnsserver returned:

    Name Error: The domain name does not exist. 

This means that:

 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 

Your cache administrator is nccsup1@olympic-airways.gr.
Generated Mon, 20 Aug 2007 06:34:34 GMT by Linux-Proxy (squid/2.6.STABLE5) 

```

Can anyone help me with this problem?
I thing it might be something with IPTABLES but since i am new with linux i don't know what to do!
If someone can please give a hand with how to open IPTABLES and a correct configuration for the netowork above.


Thank you for your replies  :KS

---

### Post by a9k on 2007-08-21
The error is a complaint about DNS but with your configuration working for HTTP (80), DNS must be working somewhere. Maybe only directly and not for the squid machine? Try [COLOR="Red"]host www.google.com[/COLOR] from every machine involved to make sure DNS is working on all of them.

In general HTTPS (SSL) caching is a problem.  I don't believe you can cache SSL or it would be vulnerable to "replay" attacks.

When I set up squid (version 2.3 I think) squid didn't understand SSL or HTTPS. I believe that they added https support but it just forwards the request without caching.

So you may be able to avoid the error by adjusting your iptables script to let port 443 go direct while redirecting port 80 (and whatever)

If you still have problems, you might want to post the output of [COLOR="Red"]iptables -nL[/COLOR]

---

### Post by pantheon13 on 2007-08-22
well our network is with many pc's and i've tried what you said... google just open ok from all pc's. Also all normal pages opens ok but if you try to login to a forum or to open gmail etc i got this error. What i can do to forward the 443 port directly to cache engine?
I think it's ok not to cache to squid those sites but for static pages we want the caching due to only 2mbps internet connection and high amount of users.
Can you give me the full command please?
Thanks for your reply!
This is what i get with [COLOR=Red]iptables -nL[/COLOR]
> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination



---

