---
title: "Sooo. Me and my DNS server aren't getting along..."
date: 2006-04-28
forum: Server Platforms
---

### Post by Elif Tymes on 2006-04-28
I can't get my DNS server to work properly. 

Here's what I want it to do:

I have my server "g1" located @ 10.0.0.3. This is running bind9.

First, I want to have a view("internals") That is accessible to the internal network. (10.0.0.x). This will redirect all requests to eliftymes.com, zacharyspencer.com, and fallenperfection.com to the local ip: 10.0.0.3. 

Second, I want a view("externals") That is accessible to the outside network. This will populate the DNS servers at xname.org, which should populate the rest of the internet.

Third: I want the server(10.0.0.3) to utilize the DNS server as it's own DNS server. TO make myself more clear, I want it to send all dns from itself to itself(this server is also an apache server :-p)



I can dig 10.0.0.3

here is the results.

```

; <<>> DiG 9.3.1 <<>> 10.0.0.3
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 48458
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;10.0.0.3.                      IN      A

;; AUTHORITY SECTION:
.                       9394    IN      SOA     A.ROOT-SERVERS.NET. NSTLD.VERISIGN-GRS.COM. 2006042701 1800 900 604800 86400

;; Query time: 9 msec
;; SERVER: 69.41.0.4#53(69.41.0.4)
;; WHEN: Fri Apr 28 10:46:53 2006
;; MSG SIZE  rcvd: 101

```

Here is my named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


acl slaves {
    195.234.42.0/24;    // XName
    193.218.105.144/28; // XName
    193.24.212.232/29;  // XName
}

acl internals {
    127.0.0.0/8;
    10.0.0.0/24;
};

view "internal" {
        match-clients {
                internals;
                };
        zone "eliftymes.com" {
                type master;
                file "/etc/bind/internals/db.eliftymes.com";
        };
        zone "fallenperfection.com" {
                type master;
                file "/etc/bind/internals/db.fallenperfection.com";
        }
        zone "zacharyspencer.com" {
                type master;
                file "/etc/bind/internals/db.zacharyspencer.com";
};

view "external" {
        match-clients {
                any;
                 };
        zone "eliftymes.com" {
                type master;
                file "/etc/bind/externals/db.fallenperfection.com";
                allow_stransfer { slaves; };
        };
        zone "fallenperfection.com" {
                type master;
                file "/etc/bind/externals/db.fallenperfection.com";
                allow_stransfer { slaves; };
        };
        zone "zacharyspencer.com" {
                type master;
                file "/etc/bind/externals/db.zacharyspencer.com";
                allow_stransfer { slaves; };
        };


};


```


and here is my /internals/db.eliftymes.com
```

; eliftymes.com
$TTL    604800
$ORIGIN eliftymes.com.
@       IN      SOA     ns1.eliftymes.com. root.eliftymes.com. (
                        2006020203
                        604800
                        86400
                        2419200
                        604800 )
;
$include "/etc/bind/external/db.eliftymes.com"
@       IN      A       10.0.0.3
www     IN      A       10.0.0.3
mail    IN      A       10.0.0.3

```

Doh. And I almost forgot: 

my external/db.eliftymes.com

```

; eliftymes.com
$TTL    604800
@       IN      SOA     ns1.eliftymes.com. root.eliftymes.com. (
                     2006020201 ; Serial
                         604800 ; Refresh
                          86400 ; Retry
                        2419200 ; Expire
                         604800); Negative Cache TTL
;
@       IN      NS      ns1
        IN      MX      10 mail
        IN      A       69.41.10.142
ns1     IN      A       69.41.10.142
mail    IN      A       69.41.10.142
www     IN      A       69.41.10.142

```

---

### Post by LuisC-SM on 2006-04-29
Hi.

You will find usefull resources at:
1. [http://forums.devshed.com/](http://forums.devshed.com/) and
2. [http://www.tek-tips.com/threadminder.cfm?pid=950](http://www.tek-tips.com/threadminder.cfm?pid=950)

Kind Regards

Luis C. Suárez

---

