---
title: "Bind9 multiple zones"
date: 2009-09-21
forum: Server Platforms
---

### Post by The87 on 2009-09-21
Admittedly, I'm new to the whole server administration thing... But here's what I've been *trying* to do.

I want to set up a pair of name servers to host multiple domain names. I stumbled into this thread [http://ubuntuforums.org/showthread.php?t=699931](http://ubuntuforums.org/showthread.php?t=699931) but it didn't seem to quite answer my question - hence my registering here.

for the purposes of getting it configured, I am just running a web server on the same IP as the main name server. Later, i'll move it over to its own virtualization. So I'm looking to get this configuration going:

ns1.domain1.net: 10.0.0.8
[www.domain1.net:]("http://www.domain1.net:") 10.0.0.8

[www.domain2.com:]("http://www.domain2.com:") 10.0.0.8

ns2.domain1.net: 10.0.0.10

Then, apache will handle virtual host redirection between [www.domain1.net]("http://www.domain1.net") and [www.domain2.com]("http://www.domain2.com")


Anyway, so here's what I got...

named.conf.local:
```
zone "domain1.net"{
        type master;
        file "/etc/bind/zones/domain1.net.db";
        allow-transfer { 10.0.0.10; };
};

zone "domain2.com"{
        type master;
        file "/etc/bind/zones/domain2.com.db";
};

zone "0.0.10.in-addr.arpa"{
        type master;
        file "/etc/bind/zones/rev.0.0.10.in-addr.arpa";
        allow-transfer { 10.0.0.10; };

```domain1.net.db:
```

$TTL 3D
@ IN SOA ns1.domain1.net. admin.domain1.net. (
   2007062001
   28800
   3600
   604800
   38400
);

@               IN      NS      ns1.domain1.net.
@               IN      NS      ns2.domain1.net.

domain1.net. IN      NS      ns1.domain1.net.
ns1             IN      A       10.0.0.8
ns2             IN      A       10.0.0.10
www             IN      A       10.0.0.8
gw              IN      A       10.0.0.1
                        TXT     "Network Gateway"

```

domain2.com.db:
```
$TTL 3D
domain2.com. IN SOA domain1.net. admin.domain1.net. (
   2007062001
   28800
   3600
   604800
   38400
);

domain2.com. IN      NS      ns1.domain1.net.

www             IN      A       10.0.0.8

```I *think* that I'm close to getting this to work. named-checkconf and named-checkzone both work but when I try to access domain2.com from a browser, the connection times out.

Thanks in advance!

---

### Post by Bachstelze on 2009-09-21
> **The87 said:**
> 
domain2.com.db:
```
$TTL 3D
domain2.com. IN SOA domain1.net. admin.domain1.net. (
   2007062001
   28800
   3600
   604800
   38400
);

domain2.com. IN      NS      ns1.domain1.net.

www             IN      A       10.0.0.8

```

You must put the name of your master name server in your SOA record, so:

```
$TTL 3D
domain2.com. IN SOA ns1.domain1.net. admin.domain1.net. (
   2007062001
   28800
   3600
   604800
   38400
);

domain2.com. IN      NS      ns1.domain1.net.

www             IN      A       10.0.0.8

```

It is also good practice to define $ORIGIN explicitly, even if BIND does it implicitly:

```
$TTL 3D
$ORIGIN domain1.net.
@ IN SOA ns1.domain1.net. admin.domain1.net. (
   2007062001
   28800
   3600
   604800
   38400
);

@               IN      NS      ns1.domain1.net.
@               IN      NS      ns2.domain1.net.

ns1             IN      A       10.0.0.8
ns2             IN      A       10.0.0.10
www             IN      A       10.0.0.8
gw              IN      A       10.0.0.1
                        TXT     "Network Gateway"
```

```
$TTL 3D
$ORIGIN domain2.com.
@ IN SOA ns1.domain1.net. admin.domain1.net. (
   2007062001
   28800
   3600
   604800
   38400
);

@ IN      NS      ns1.domain1.net.

www             IN      A       10.0.0.8

```

---

### Post by The87 on 2009-09-21
Thanks for the tips.

As it turns out, I think my problems are that I am not assigning the proper internal and external IPs.

My local network is 10.0.0.x but I obviously have different IPs as seen by the outside world. When I tried to ping [domain2.com] it came up with 10.0.0.8 instead of the actual IP.

How does one handle different internal/external IPs with Bind9?

---

### Post by Bachstelze on 2009-09-21
With views.

[http://www.oreillynet.com/pub/a/oreilly/networking/news/views_0501.html](http://www.oreillynet.com/pub/a/oreilly/networking/news/views_0501.html)

---

### Post by The87 on 2009-09-21
ahhh... thanks.

Somehow I never came across this in my travels.

So then, I'll be actually making 2 zone records for each domain. In other words, I'll have domain2.com.db.internal and domain2.com.db.external

Then, in the external, i'll have www point to the external IP instead of 10.0.0.8

Correct?

---

### Post by Bachstelze on 2009-09-21
> **The87 said:**
> ahhh... thanks.

Somehow I never came across this in my travels.

So then, I'll be actually making 2 zone records for each domain. In other words, I'll have domain2.com.db.internal and domain2.com.db.external

Then, in the external, i'll have www point to the external IP instead of 10.0.0.8

Correct?

Correct.

---

