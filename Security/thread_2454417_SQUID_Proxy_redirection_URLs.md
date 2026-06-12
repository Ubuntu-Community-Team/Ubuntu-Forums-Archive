---
title: "SQUID Proxy redirection URLs"
date: 2020-11-29
forum: Security
---

### Post by creation4251 on 2020-11-29
[COLOR=#333333][FONT=&quot]Morning guys,[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I'm trying to redirect specific URLs to another one just using the instance "deny_info". So when from my browser I want to go to [www.A.com]("http://www.a.com/") squid proxy will redirect to [www.B.com]("http://www.b.com/") authomatically.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]From docuemntation I can see that this is possible in Ubuntu but I am not totally sure how to use this instance inside squid.conf.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Any suggestion or examples?[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Thanks![/FONT][/COLOR]

---

### Post by EuclideanCoffee on 2020-11-29
The wiki explains how to accomplish this with scripts. It's a bit involved.

[https://wiki.squid-cache.org/Features/Redirectors](https://wiki.squid-cache.org/Features/Redirectors)

Here's an example.

[https://gist.github.com/peter279k/ea81a487ae0db811894687b8178b3175](https://gist.github.com/peter279k/ea81a487ae0db811894687b8178b3175)

Here's a question asking how to accomplish this explicitly, but the answer says it won't be possible for HTTPS unless squid is configured as a MitM.

[https://serverfault.com/questions/764855/redirect-certain-https-url-with-squid](https://serverfault.com/questions/764855/redirect-certain-https-url-with-squid)

The final result is this HTTP template from this source. I'll copy it here for convenience.

[https://servercomputing.blogspot.com/2012/03/squid-proxy-redirect-url.html](https://servercomputing.blogspot.com/2012/03/squid-proxy-redirect-url.html)

```

[COLOR=#741b47][FONT=Trebuchet MS]**[root@server ~]# vi /etc/squid/squid.conf**[/FONT][/COLOR]
[FONT=Trebuchet MS]**acl lan src 192.168.10.0/24                           *#client acl for the lan***[/FONT][B]
[FONT=Trebuchet MS][COLOR=#38761d]**acl badsites dstdomain .bing.com                 **[/COLOR]*#to deny "**bing.com**"*[/FONT]
[FONT=Trebuchet MS][COLOR=#38761d]**deny_info http://google.com lan                   **[/COLOR]*#D**eny with redirect to google.com for lan*[/FONT]
[COLOR=#38761d][FONT=Trebuchet MS]**http_reply_access deny badsites lan             **[/FONT][/COLOR][FONT=Trebuchet MS] [I]# Deny badsites to lan
**[root@server ~]# service squid reload**[/I][/FONT][/B]

```

I think it's easier to enforce these controls with your own proxy server. Having a local proxy server is not secure.

Edit.

Couldn't you accomplish this easier with host files?

---

### Post by creation4251 on 2020-12-02
Hi thanks for your answer.

I would like to know if allocating those ACL under the following one is ok? 

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1


# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines


acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
[FONT=&quot]**acl lan src 192.168.10.0/24                           *#client acl for the lan***[/FONT][B]
[FONT=&quot][COLOR=#38761d]**acl badsites dstdomain .bing.com                 **[/COLOR]*#to deny "**bing.com**"*[/FONT]
[FONT=&quot][COLOR=#38761d]**deny_info [http://google.com](http://google.com) lan                   **[/COLOR]*#D**eny with redirect to google.com for lan*[/FONT]
[COLOR=#38761d][FONT=&quot]**http_reply_access deny badsites lan             **[/FONT][/COLOR][FONT=&quot] *# Deny badsites to la*[/FONT][/B]


After that, if i reload the squid i get this error:

sudo /etc/init.d/squid reload
squid: ERROR: Could not send signal 1 to process 6864: (3) No such process



sudo /etc/init.d/squid status
squid dead but pid file exists

I tried to reload few times the squid proxy, i restarted the machine and also deleted the var/run pid file and cache from squid.
Same issue all the time.

---

