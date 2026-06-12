---
title: "BIND9 &quot;no current owner name&quot; on check of config files"
date: 2009-07-18
forum: Server Platforms
---

### Post by R.Bucky on 2009-07-18
I am working on establishing DNS for my web server. I host 9 domains on Ubuntu Server 8.04. When I check my configuration files I get back the text below - 9 times. Once for each domain.
```

# /etc/bind/db.buckycomputing.net:5: no current owner name
# /etc/bind/db.buckycomputing.net:12: no current owner name
# /etc/bind/db.buckycomputing.net:14: no current owner name
# /etc/bind/db.buckycomputing.net:15: no current owner name
# /etc/bind/db.buckycomputing.net:16: no current owner name
# zone buckycomputing.net/IN: loading from master file /etc/bind/db.buckycomputing.net failed: no owner
# _default/buckycomputing.net/IN: no owner 
```

I read one page on the net that said that I needed to configure permissions for the ns, but it did not elaborate. Below is my db.buckycomputing.net. Can anyone lend a hand? My other 8 domains are configured exactly the same, exchanging the domain names for their own.

 ```
 ;
     ; BIND reverse data file for buckycomputing.net
     ;
$ORIGIN buckycomputing.net
     @       IN      SOA    ns.buckycomputing.net. root.buckycomputing.net. (
                             0718200         ; Serial
                              604800         ; Refresh
                               86400         ; Retry
                             2419200         ; Expire
                              604800 )       ; Default TTL
     ;
             IN      NS      dns.buckycomputing.net.
     
     30 IN      PTR     www.buckycomputing.net.
     35 IN      PTR     dns.buckycomputing.net.
     40 IN      PTR     mail.buckycomputing.net.

```

---

### Post by gombadi on 2009-07-18
> 
$ORIGIN buckycomputing.net


Try the above line with a . on the end.

---

### Post by R.Bucky on 2009-07-18
Right on! Thank you. 1 error down, 3 to go!!! Picky, picky BIND!!!

```
# /etc/bind/db.buckycomputing.net:16: TTL set to prior TTL (30)
# /etc/bind/db.buckycomputing.net:17: TTL set to prior TTL (30)
# zone buckycomputing.net/IN: NS 'dns.buckycomputing.net' has no address records (A or AAAA) 
```

---

### Post by windependence on 2009-07-19
Mark, are you doing this to learn or because you think you have to to run the websites? If you just wanna learn, that's OK and I'll give you a hand, but seriously if you are beating yourself up with Bind because you want to run web sites, you don't have to. You can just use your registrar's DNS control panel and point all those at your server IP.

-Tim

---

### Post by R.Bucky on 2009-07-19
Hello Tim - A couple of reasons for the BIND install. I always want to learn more about networking. That is just a gimme. Secondly, there is point where functionality comes into play. Anyone on my network should be able to visit my sites within a network without having to go through a proxy. I login and edit my sites now by forwarding X11 through my daily linux box. Not the way it should be done.

Any guidance or resources would be appreciated.

~Mark

---

### Post by edcompsci on 2012-05-04
I know this thread is a few years old, but if you can help:

I had this problem reading my named log file and added such an ORIGIN line to the zone file and now when I try to reload named, it fails. It was fine before, it loaded but just had no name for the in-addr zone. How do I get it to load again?

---

