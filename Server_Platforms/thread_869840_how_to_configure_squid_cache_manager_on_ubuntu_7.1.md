---
title: "how to configure squid cache manager on ubuntu 7.10"
date: 2008-07-25
forum: Server Platforms
---

### Post by lawalsulaiman on 2008-07-25
Please I need help on how to configure squid cache manager on ubuntu 7.10

---

### Post by Sef on 2008-07-25
Moved to its own thread.

---

### Post by ChumleyEX on 2008-07-25
one word..


Webmin

---

### Post by foxmajik on 2010-04-26
> **ChumleyEX said:**
> one word..


Webmin

Not only is this answer completely unhelpful it's also untrue.

Webmin doesn't help you to install or configure cache manager.

You have to setup Apache to make cache manager work.  It's really not of any use unless you really need to get statistical data about your Squid proxy.

If you do, install it this way:

```
$ sudo aptitude install squid-cgi
```

---

### Post by cong06 on 2010-07-12
> **foxmajik said:**
> You have to setup Apache to make cache manager work.  It's really not of any use unless you really need to get statistical data about your Squid proxy.

If you do, install it this way:

```
$ sudo aptitude install squid-cgi
```

Ok... well, I got apache set up (I'm actually using webalizer now) and I installed squid-cgi...

But I can't figure out how to use it. I've tried different ports in the /etc/squid3/cachemgr.conf file, but I must be missing something.

Is the port defaulted to 80? or 3128 (the proxy port). Is it supposed to be the same as the proxy port? an if so how are you supposed to go to it?
I assume I'm supposed to use a browser to get to:
http://localhost:<port>/

The man page: *man cachemgr.cgi* isn't really very useful. No more info then the configuration file...

---

