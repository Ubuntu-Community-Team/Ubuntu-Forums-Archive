---
title: "Transparent Proxy Issues"
date: 2009-02-24
forum: Server Platforms
---

### Post by shoaibi on 2009-02-24
I have a firewall machine which itself has squid. I want to enable transparent proxy.

Now if I set it in my browser proxy settings, squid works fine, but if I use firewall(shorewall) to give a transparent proxy to all web traffic from my ip, I get:



Firefox page shows:
```

#
ERROR
#
The requested URL could not be retrieved
#
 
#
While trying to process the request:
#
 
#
GET /2007/11/14/hosting-git-repositories-the-easy-and-secure-way HTTP/1.1
#
Host: scie.nti.st
#
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/2.0.0.12;MEGAUPLOAD 1.0
#
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
#
Accept-Language: en-us
#
Accept-Encoding: gzip,deflate
#
Accept-Charset: UTF-8,*
#
Keep-Alive: 300
#
Connection: keep-alive
#
If-Modified-Since: Mon, 23 Feb 2009 15:11:51 GMT
#
If-None-Match: "-1225905936"
#
 
#
 
#
 
#
The following error was encountered:
#
 
#
    * Invalid Request
#
 
#
Some aspect of the HTTP Request is invalid. Possible problems:
#
 
#
    * Missing or unknown request method
#
    * Missing URL
#
    * Missing HTTP Identifier (HTTP/1.0)
#
    * Request is too large
#
    * Content-Length missing for POST or PUT requests
#
    * Illegal character in hostname; underscores are not allowed
#
 
#
Your cache administrator is root@cosp.org.pk.
#
Generated Tue, 24 Feb 2009 04:00:06 GMT by cosp.org.pk (squid/2.6.STABLE18) 

```


squid/access.log's tail:
```

#
1235448006.259      0 172.20.0.101 TCP_DENIED/400 2063 GET error:invalid-request - NONE/- text/html
#
1235448007.078      0 172.20.0.101 TCP_DENIED/400 2567 GET error:invalid-request - NONE/- text/html
#
1235448011.381      0 172.20.0.101 TCP_DENIED/400 1637 GET error:invalid-request - NONE/- text/html
#
1235448036.737      1 172.20.0.101 TCP_DENIED/400 1919 GET error:invalid-request - NONE/- text/html
#
1235448036.946      0 172.20.0.101 TCP_DENIED/400 2513 GET error:invalid-request - NONE/- text/html
#
1235448036.983      0 172.20.0.101 TCP_DENIED/400 1900 GET error:invalid-request - NONE/- text/html
#
1235448040.903      0 172.20.0.101 TCP_DENIED/400 1930 GET error:invalid-request - NONE/- text/html
#


```


Firewall(shorewall) rule:
```

REDIRECT        loc:172.20.0.101                3128    tcp     www     -       !202.147.161.xx


```


Squid.conf without comments
```

#
acl all src 0.0.0.0/0.0.0.0
#
acl manager proto cache_object
#
acl localhost src 127.0.0.1/255.255.255.255
#
acl to_localhost dst 127.0.0.0/8
#
acl SSL_ports port 443          # https
#
acl SSL_ports port 563          # snews
#
acl SSL_ports port 873          # rsync
#
acl Safe_ports port 80          # http
#
acl Safe_ports port 21          # ftp
#
acl Safe_ports port 443         # https
#
acl Safe_ports port 70          # gopher
#
acl Safe_ports port 210         # wais
#
acl Safe_ports port 1025-65535  # unregistered ports
#
acl Safe_ports port 280         # http-mgmt
#
acl Safe_ports port 488         # gss-http
#
acl Safe_ports port 591         # filemaker
#
acl Safe_ports port 777         # multiling http
#
acl Safe_ports port 631         # cups
#
acl Safe_ports port 873         # rsync
#
acl Safe_ports port 901         # SWAT
#
acl purge method PURGE
#
acl CONNECT method CONNECT
#
 
#
http_access allow manager localhost
#
http_access deny manager
#
http_access allow purge localhost
#
http_access deny purge
#
http_access deny !Safe_ports
#
http_access deny CONNECT !SSL_ports
#
 
#
 
#
acl home_networks src 172.20.0.0/24  
#
http_access allow home_networks      
#
http_access allow localhost          
#
http_access deny all
#
 
#
 
#
 
#
icp_access allow all
#
http_port 3128
#
hierarchy_stoplist cgi-bin ?
#
access_log /var/log/squid/access.log squid
#
 
#
acl QUERY urlpath_regex cgi-bin \?
#
cache deny QUERY
#
 
#
refresh_pattern ^ftp:           1440    20%     10080
#
refresh_pattern ^gopher:        1440    0%      1440
#
refresh_pattern .               0       20%     4320
#
 
#
 
#
 
#
acl apache rep_header Server ^Apache
#
broken_vary_encoding allow apache
#
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
#
 
#
cache_mgr root@cosp.org.pk
#
visible_hostname cosp.org.pk
#
hostname_aliases ns1.cosp.hq nextcube.doesntexist.org cosp.dontexist.org cosp.doesntexist.org nextcube.cosp.hq
#
 
#
 
#
hosts_file /etc/hosts
#
coredump_dir /var/spool/squid

```

any ideas?

---

### Post by jimv on 2009-02-24
this:

http_port 3128

should be this:

http_port 3128 transparent vhost

---

### Post by shoaibi on 2009-02-24
XXget same errorXXX
Forgot to restart squid:

```

/etc/init.d/squid restart
 * Restarting Squid HTTP proxy squid                                                                                                                         2009/02/24 12:00:23| Can't be both a transparent proxy and web server accelerator on the same port
FATAL: Bungled squid.conf line 929: http_port 3128 transparent vhost
Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
                                                                                                                                                      [fail]


```

Removing "vhost" makes it work...

---

### Post by jimv on 2009-02-24
Oh, I'm using squid3, so that might not work if you're using squid 2.6.

---

### Post by daveharlowe on 2009-03-02
Thanks to you both! 

I was getting these errors as well:

 TCP_DENIED/400 xxxx GET error:invalid-request - NONE/- text/html


This fix outlined above worked well on ubuntu with squid 2.7.
update squid.conf:
http_port 3128 transparent


I am using iptables to mark the packets (so as to seperate incoming traffic to split between 2 DSL gw's).

This is what I am using upstream of the DSL box on a proxy:


(1) - settings on router "upstream" of squid proxy box
 ip route flush table 4 
 ip route show table main | grep -Ev ^default \
>   | while read ROUTE ; do
>     ip route add table 4 $ROUTE
> done
 ip route add table 4 default via 10.4.1.1
 ip route show table 4
 iptables -t mangle -A PREROUTING -s 10.4.3.0/24 -j MARK --set-mark 4
 iptables -t mangle -nvL
 ip rule add fwmark 4 table 4



(2) - settings on squid box
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-ports 3128




A combination of marking of the packets in (1) above and redirecting the packets from port 80 to 3128 squid proxy in (2) above seemed to mean that the transparent setting needed to be configured on the dsl gw's squid.conf.

regards,
Dave

---

