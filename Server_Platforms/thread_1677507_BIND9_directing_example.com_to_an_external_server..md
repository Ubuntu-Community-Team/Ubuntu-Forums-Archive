---
title: "BIND9 directing example.com to an external server."
date: 2011-01-28
forum: Server Platforms
---

### Post by iiz on 2011-01-28
Hello,

I have BIND9 installed on a lucid server. I am attempting to get BIND9 to act as a caching server and route a few domain names internally and externally.

The BIND9 server has the ip 10.0.1.9
Our internal webserver has the address 10.0.1.10
And we have an external site hosted at 75.32.142.9
(the last address is hypothetical)

I want both example.com and www.example.com to route to 75.32.142.9
And I want beta.example.com to route to 10.0.1.10

I got www and beta to work, but I cannot seem to get example.com to route no matter what i do.

My Config Files:

/etc/bind/named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
// include "/etc/bind/zones.rfc1918";

zone "example.com" {
        type master;
        file "/etc/bind/db.example.com";
};

```

/etc/bind/db.example.com
```
$TTL    604800
@       IN      SOA     comtread.net   root.example.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1
ns1     IN      A       10.0.1.9
beta    IN      A       10.0.1.10
www     IN      A       75.32.142.9
```
I have tried setting the ns1 record, putting no ns record, an additional @ line, using the original @ line. I tried 20 or so different things.

I also searched, to my knowledge, thoroughly, but I cannot seem to locate anyone requesting a similar configuration.

Thank you in advance.

-nick

---

### Post by SeijiSensei on 2011-01-29
```
$TTL    604800
@       IN      SOA     comtread.net   root.example.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

        IN      A       75.32.142.9   <===== add this

        IN      NS      ns1

ns1     IN      A       10.0.1.9
beta    IN      A       10.0.1.10
www     IN      A       75.32.142.9
```

Add an A record with no initial host entry as I did above.

---

### Post by iiz on 2011-02-01
> **SeijiSensei said:**
> ```
$TTL    604800
@       IN      SOA     comtread.net   root.example.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

        IN      A       75.32.142.9   <===== add this

        IN      NS      ns1

ns1     IN      A       10.0.1.9
beta    IN      A       10.0.1.10
www     IN      A       75.32.142.9
```

Add an A record with no initial host entry as I did above.

awesome thank you, that worked for me. just a note, i mislabeled the servername it should have been example.com not comtread.net for anyone who looks at this post.

---

