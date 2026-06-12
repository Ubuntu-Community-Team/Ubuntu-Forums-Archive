---
title: "bind9: example.com works, www.example.com doesnt, and how to block urls"
date: 2011-09-11
forum: Server Platforms
---

### Post by Shwick2 on 2011-09-11
1)
I was following a guide to setup bind again after I formatted to Ubuntu 10.04.2 LTS.
[http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html#dns-primarymaster-configuration](http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html#dns-primarymaster-configuration)

I can get my domain example.com to resolve but I want "www.example.com" to resolve to the actual domain on the web.

I don't have a webserver setup on my domain at the moment so I would rather it resolve properly.

So "ping example.com" works and resolves to my local address but "ping www.example.com" gives "ping: unknown host www.example.com".

Here is the file db.example.com,

```

;
; BIND data file for example.com
;
$TTL    604800
@       IN      SOA     ns.example.com. root.example.com. (
                              9         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.example.com.
@       IN      A       10.11.12.1
;www    IN      A       10.11.12.1
ns      IN      A       10.11.12.1

```

I tried adding in a www entry but it only resolves to the same local ip as example.com so I commented it out.


2)
I am planning on adding all of the urls from the ad block site [http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt) to bind so as to block them on my network.

So how would I add this list to bind?

---

### Post by Dangertux on 2011-09-11
your www A entry resolves to the local ip because you are telling it to. You have to set it to the IP you want it to resolve to.

As far as blocking domains/hosts you can use a PTR record 

This might be helpful.
[http://www.freebsd.org/doc/handbook/network-dns.html](http://www.freebsd.org/doc/handbook/network-dns.html)

---

### Post by Habitual on 2011-09-11
[http://corz.org/serv/tricks/htaccess.php](http://corz.org/serv/tricks/htaccess.php)
[http://corz.org/serv/tricks/htaccess2.php](http://corz.org/serv/tricks/htaccess2.php)
[http://tips-scripts.com/www](http://tips-scripts.com/www)

---

