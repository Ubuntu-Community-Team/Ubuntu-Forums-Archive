---
title: "help with bind config"
date: 2013-06-10
forum: Server Platforms
---

### Post by floobit on 2013-06-10
I'm setting up bind and am having some problems.  I'm using the tutorial [here]("http://wiki.kartbuilding.net/index.php/DNS_-_Bind9#Configing_Bind_.28version_9.29:").  For testing, I set up a machine with hostname dc01.home, ip=192.168.1.100.  I installed bind, and configured per the tutorial so that there should be a new A record for dc01.home.  When I dig my new record, I get a servfail.  bind is running (the caching function works great), and I have incremented the serial several times.  Here are my config files:

/etc/bind/named.conf.local:
```
logging {
    channel query.log {
        file "/var/log/query.log";
        severity debug 3;
    };

    category queries { query.log; };
};


zone "home" {
        type master;
        file "/etc/bind/db.home";
};

zone "168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192.168";
};
```

/etc/bind/db.home:
```
$TTL    604800
@       IN      SOA     dc01.home. myemail.gmail.com. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      dc01.home.
@       IN      A       192.168.1.100
```

/etc/bind/db.192.168:
```
$TTL    604800
@       IN      SOA     dc01.home. myemail.gmail.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      dc01.home.
100.1   IN      PTR     dc01.home.
```

Thoughts?

---

### Post by sanderj on 2013-06-10
/etc/db.home ? Really? If so ... check the other reference you use.

---

### Post by floobit on 2013-06-10
Sorry, typo.  That file is in /etc/bind/db.home.  Original post edited to correct.

---

### Post by floobit on 2013-06-11
Found the answer on another tutorial.  correct contents of db.home are as follows.  The takeaway is that the NS record should not be a fqdn, and there needs to be a shortname A record as well:

```
$TTL    604800
@       IN      SOA     dc01.home. dylannevans.gmail.com. (
                              7         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      dc01
dc01    IN      A       192.168.1.100
```

---

