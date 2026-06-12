---
title: "Apache2 reverse proxy load balancing"
date: 2011-02-03
forum: Server Platforms
---

### Post by daniele75 on 2011-02-03
Hello, we have an ubuntu server (10.04 LTS) with apache2 (2.2.9) and mod_proxy + proxy_balancer enabled.

Reverse proxy works greatly, but I can't get load balancing working.
Apache connect always to first member.

My configuration is as follow:

ProxyRequests Off
        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>
        <Proxy balancer://test>
                Allow from all
                BalancerMember [http://192.168.0.1:8080/](http://192.168.0.1:8080/) loadfactor=10
                BalancerMember [http://192.168.0.2:8080/](http://192.168.0.2:8080/) loadfactor=10
                BalancerMember [http://192.168.0.3:8080/](http://192.168.0.3:8080/) loadfactor=10
        </Proxy>
        ProxyPass /test balancer://test

It seems to work, but it always connect to first member of balancer (192.168.0.1 in this case).

If I invert member, for example if I configure 192.168.0.2 like first member, apache connect always to 192.168.0.2...

Any help will be greatly appreciated.

Daniele

---

### Post by Thirtysixway on 2011-02-03
Is your first balancer being overloaded?

---

### Post by daniele75 on 2011-02-03
> **Thirtysixway said:**
> Is your first balancer being overloaded?

No, but I don't understand why this question :)

---

### Post by HermanAB on 2011-02-03
KISS: Round robin DNS.

Any BIND DNS can do that for you.

---

### Post by daniele75 on 2011-02-04
> **HermanAB said:**
> KISS: Round robin DNS.

Any BIND DNS can do that for you.

It'a a dynamic site, so I need to use Apache load balancing, because I need that sessions coming from one ip address remain connected always to the same member...
Bu I don't understand why it's not possible to do that with apache, in documentation it's clear that apache can do that...

---

### Post by rudelgurke on 2011-02-05
> **HermanAB said:**
> KISS: Round robin DNS.

Any BIND DNS can do that for you.

And any BIND DNS with Round Robin will just spread the requests without checking for the health of the backends, unlike a real load balancer. ;)


> **daniele75 said:**
> <Proxy balancer://test>
                Allow from all
                BalancerMember http://192.168.0.1:8080/ loadfactor=1__
                BalancerMember http://192.168.0.2:8080/ loadfactor=1
                BalancerMember http://192.168.0.3:8080/ loadfactor=1
_[U]_[/U]</Proxy>
        ProxyPass /test balancer://test

Tried to rename your cluster ? Because of:

ProxyPass /test (which is the name of your cluster) balancer://test

Oh - the final / behind your port number shouldn't be required.

---

### Post by daniele75 on 2011-02-08
> **rudelgurke said:**
> 


Tried to rename your cluster ? Because of:

ProxyPass /test (which is the name of your cluster) balancer://test

Oh - the final / behind your port number shouldn't be required.


Thanks for your suggestion, 've tried to rename cluster yet, but balancing still not work...
All requests always go to first member...

---

