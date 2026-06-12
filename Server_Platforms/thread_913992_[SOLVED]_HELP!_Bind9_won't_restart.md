---
title: "[SOLVED] HELP! Bind9 won't restart"
date: 2008-09-08
forum: Server Platforms
---

### Post by shizakapayou on 2008-09-08
Ubuntu 8.04.1 64-bit.  When I try /etc/init.d/bind9 restart, I get the following:

```
rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [fail]
 * Starting domain name service... bind                                  [fail]
```

Note apparmor is NOT running.

/etc/bind/named.conf:
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

key "rndc-key" {
        algorithm hmac-md5;
        secret "wifgeRHbzM8n3id1X2HUGw==";
};

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

include "/etc/bind/named.conf.local";

//Accepts queries only from internal hosts
options {
                 allow-query { 192.168.1/24; } ;
                 allow-transfer { none; } ;
                 allow-recursion { 192.168.1/24; } ;
                 listen-on { 192.168.1.2; } ;
                 forward { only; } ;
                 forwarders { A.B.C.D; } ;
     };

```

/etc/bind/rndc.key:
```

key "rndc-key" {
        algorithm hmac-md5;
        secret "wifgeRHbzM8n3id1X2HUGw==";
};

```

Relevant from /var/log/syslog:
```
Sep  8 10:36:52 mercury named[6479]: starting BIND 9.4.2-P1 -u bind
Sep  8 10:36:52 mercury named[6479]: found 8 CPUs, using 8 worker threads
Sep  8 10:36:52 mercury named[6479]: loading configuration from '/etc/bind/named.conf'
Sep  8 10:36:52 mercury named[6479]: /etc/bind/named.conf:48: 'options' redefined near 'options'
Sep  8 10:36:52 mercury named[6479]: loading configuration: already exists
Sep  8 10:36:52 mercury named[6479]: exiting (due to fatal error)
```

Any suggestions?  I'm googling all I can but I need a speedy answer....

---

### Post by inphektion on 2008-09-08
at the top of named.conf see where it includes the file called named.conf.options?

that's where you put your options.  You have them redefined at the bottom of named.conf which is why it has a fatal error.

---

### Post by shizakapayou on 2008-09-08
Thanks!  As soon as I removed the stuff at the bottom of named.conf, it worked.

---

