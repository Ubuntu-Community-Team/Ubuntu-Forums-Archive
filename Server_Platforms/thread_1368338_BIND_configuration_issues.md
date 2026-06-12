---
title: "BIND configuration issues"
date: 2009-12-30
forum: Server Platforms
---

### Post by dlegatt on 2009-12-30
So I am building myself a linux gateway and was playing with setting up a BIND DNS server.  Why? Because its fun to torture myself.
I've looked in two different books and as far as I can tell, it looks like it is set up correctly, but I cannot resolve my names.

I have two virtual machines, both running ubuntu server:
gateway: 192.168.118.128
client1:  192.168.118.129

I am trying to set it up using the domain home.local
Ive never done this before and I'm willing to accept that everything I've done is wrong, so here it all is.

My /etc/bind/named.conf.local file:
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "home.local" in {
        allow-transfer { any; };
        file "/etc/bind/db.home.local";
        type master;
};

zone "118.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.118.168.192";
};

```

Here is /etc/bind/db.home.local:
```

$TTL 2D
@       IN SOA  gateway.home.local.     admin.gateway.home.local. (
                09123000        ; serial
                3H              ; refresh
                1H              ; retry
                1W              ; expiry
                1D )            ; minimum

home.local      IN NS   gateway.home.local.
gateway         IN A    192.168.118.128
client1         IN A    192.168.118.129
gateway         IN CNAME        gateway.home.local.
client1         IN CNAME        client1.home.local.

```

And here is /etc/bind/db.118.168.192:
```

$TTL 2D
@       IN SOA  gateway.home.local.     admin.gateway.home.local. (
                09123000        ; serial
                3H              ; refresh
                1H              ; retry
                1W              ; expiry
                1D )            ; minimum

''              IN NS   gateway.home.local.
128             IN PTR  gateway.home.local.
129             IN PTR  client1.home.local.

```

---

### Post by dlegatt on 2009-12-30
So apparently it really did not like my cname records, I have removed them and now I can resolve gateway.home.local and client1.home.local
I guess I misunderstood how cname works
Is there a way for me to resolve "client1" to 192.168.118.129?

---

### Post by dlegatt on 2009-12-30
Problem solved.
I installed resolvconf and edited /etc/resolvconf/resolvconf.d/base to include:
```

search home.local
nameserver 127.0.0.1

```

and now its all happy

---

