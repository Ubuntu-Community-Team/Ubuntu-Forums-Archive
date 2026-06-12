---
title: "Bind9 Issues"
date: 2005-11-19
forum: Server Platforms
---

### Post by s0c0 on 2005-11-19
I recently setup bind9 using the method outlined here: [http://www.projektfarm.com/en/support/debian_setup/index.html](http://www.projektfarm.com/en/support/debian_setup/index.html)

I have verified everything works fine.  I can ping based on hostnames, access the internet using my dns server, and when I run ethereal on my windows box it shows dns lookups being directed sent to my linux box and it responding.  Ethereal shows the same thing on my linux box.  There is one minor problem though.  When I enter the /etc/init.d/bind9 restart command to restart the service I get the following output:

```

kernel:/home/chris# /etc/init.d/bind9 restart
Stopping domain name service: namedrndc: connect failed: connection refused
.
Starting domain name service: named.
kernel:/home/chris# 

```

I should also note that the website I previously listed walked me through setting up bind chrooted.  I believe this has something to do with the error.

I have another question.  I registered my domain through yahoo.  How come when I use dig it shows yahoo name servers in the authoritive section and not my  dns?  Is this normal or is there something else I should be doing?

Also if someone could verify that my named.conf and host is setup properly that would be great!

**NAMED.CONF >**
```

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

zone "xn.net" {
        type master;
        file "xn.hosts";
        notify yes;
        allow-updates { none; };
        };

zone "1.168.192.in-addr.arpa" in {
        file "master/1.168.192.in-addr.arpa";
        type master;
};

```
[B]
XNSOLUTIONS.NET >[/B]
```

$TTL    604800
@                IN      SOA     kernel.xn.net webmaster.kernel.xn.net (
                                      1         ; Serial
                                 604800         ; Refresh
                                  86400         ; Retry
                                2419200         ; Expire
                                 604800 )       ; Negative Cache TTL

; XNName Servers
                IN      NS      kernel.xn.net

; XNMail Servers

; Local Host
localhost       IN      A       127.0.0.1

; Hosts in this zone
kernel          IN      A       192.168.1.102

```

---

### Post by nagilum on 2005-11-20
As for the first error, the startup scripts use the 'rndc' tool to control the server. For this to work you have to create a key and add it to your named.conf and rndc.conf (the keys of course have to match). See the BIND HOWTO or manpages on how to create the key and properly specify it.

And for the Yahoo problem, registering a domain does not automatically mean that you will be allowed to run your own domain name sever for that domain, it depends on your contract.

---

