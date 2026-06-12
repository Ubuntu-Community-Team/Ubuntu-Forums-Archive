---
title: "DNS Server rndc problem"
date: 2008-01-31
forum: Server Platforms
---

### Post by TekZonz on 2008-01-31
Hello,

I am trying to install a DNS server to handle my domain name. I installed bind9 et I configured it with the help of a few tutorials. I am encountering the same error over and over again and I have not been able ton find any info on it. Your help will be very precious to me.

The error i get is :

[I]root@ns26550:/etc/bind# /etc/init.d/bind9 restart
Stopping domain name service...: bindrndc: no server specified and no default
failed[/I]

Here is my named.conf

[I]include "/etc/bind/rndc.key"
options {
        directory "/var/named";
        /*
        * If there is a firewall between you and nameservers you want
        * to talk to, you might need to uncomment the query-source
        * directive below.  Previous versions of BIND always asked
        * questions using port 53, but BIND 8.1 uses an unprivileged
        * port by default.
        */
        // query-source address * port 53;
};

//
// a caching only nameserver config
//
zone "." IN {
        type hint;
        file "caching-example/named.ca";
};

zone "localhost" IN {
        type master;
        file "caching-example/localhost.zone";
        allow-update { none; };
};

zone "0.0.127.in-addr.arpa" IN {
        type master;
        file "caching-example/named.local";
        allow-update { none; };
};

zone "esportsfrance.com" {
        type master;
        file "esportsfrance.com";
};

zone "toplay.fr" {
        type master;
        file "toplay.fr";
};

zone "esportfrance.com" {
        type master;
        file "esportfrance.com";
};
controls {
inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };
};
#server 91.121.79.116 {
#        keys {
#               TRANSFER;
#       };
#};
#include "/etc/bind/rndc.key"
[/I]

The zone configuration is taken from a functional server so it should be fine

Here is rndc.key :

[I]key "rndc-key" {
        algorithm HMAC-MD5;
        secret "FFWoEIwVr9304AmkX9rpHbtNCHHWKH/Ag1r0anfaX8aSmHS/EXW1XzfXlymTOBlnfe9wQguQb0bMXZma9c9KbA==";
};[/I]

I am getting pretty desperate with this so if you have any idea where the problem might be, it would be fantastic.

Thank you in advance,

Antoine

---

### Post by koenn on 2008-01-31
> zone "esportsfrance.com" {
type master;
file "esportsfrance.com";
};
you do have zone files for your domains, don't you ?

try using an absolute path for 'file', like
```
 file "/path/to/esportsfrance.com
```

---

### Post by TekZonz on 2008-02-02
Hello,

I will try that but the error does not seem to have a relation with the zones. You never know :D

Thank you,

Antoine

---

