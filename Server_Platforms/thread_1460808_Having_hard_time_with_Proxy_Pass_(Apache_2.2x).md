---
title: "Having hard time with Proxy Pass (Apache 2.2x)"
date: 2010-04-23
forum: Server Platforms
---

### Post by Spooky Neo on 2010-04-23
Hi everyone,
 
I'll try to explain my issue as clear and as simple as possible.
 
I have one WebServer called R1. This WebServer has Apache 2.2x installed with many mods such as Proxy_Pass.
 
R1 serves mostly as a Proxy to forward most requests to another server, a JBoss Server. The JBoss Server is not important in this topic, so we'll leave it alone.
 
Currently, R1 has a Proxy_Pass configuration similar to this:
 
>  ProxyPass /balancer-manager !
ProxyPass / [http://jboss:8080]("http://jboss:8080/")
ProxyPassReverse / [http://jboss:8080/](http://jboss:8080/)
 
This works, and everything will be forwarded to the JBoss Server.
 
Most of the clients who will access the website ([www.test.com]("http://www.test.com")) will access the website using their client name ([www.test.com/microsoft]("http://www.test.com/microsoft"), [www.test.com/apple]("http://www.test.com/apple"), etc).
 
What I want is that everything EXCEPT the root of the website ([www.test.com]("http://www.test.com")) is forwarded to the JBoss Servers. Meaning that if a client enters [www.test.com]("http://www.test.com"), it will load the index.html web page on the Apache server and will not be forwarded to the JBoss Servers.
 
The problem though, is that I cannot (and this is a software limitation issue) use ProxyPass for each client. I must forward everything to the JBoss Servers, except the root of the web site.
 
We've tried doing a ProxyPass /index.html !, but because the URL does not contain index.html (only [www.test.com]("http://www.test.com")), it will proxy to the JBoss Server anyway.
 
Anyone has a clue on how to do it in Apache ?
 
Thank you,
 
Neo.

---

### Post by cdenley on 2010-04-23
Maybe something like this?
```

ProxyPass /balancer-manager !
ProxyPassMatch ^(/.*/)$ http://jboss:8080/$1
ProxyPassReverse / http://jboss:8080/

```

---

### Post by Spooky Neo on 2010-04-23
This seems to be working... I'll let it for a couple of hours in the test environment and see if this causes issues.
 
It's been a while since I've used RegEx. I read that ProxyPass cannot use RegEx but ProxyPassMatch does the same thing as ProxyPass but you can use RegEx with it. Is that right ?

---

### Post by cdenley on 2010-04-23
Correct.
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypassmatch](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypassmatch)
> 
This directive is equivalent to ProxyPass, but makes use of regular expressions, instead of simple prefix matching.


---

