---
title: "Bind9 errors: unknown option 'zone'"
date: 2010-08-11
forum: Server Platforms
---

### Post by edkasky on 2010-08-11
I am trying to get bind 9 up and running on a new installation of server 10.04 and keep getting errors when starting the daemon -

    * /etc/bind/named.conf.local:19: unknown option 'zone'
    * /etc/bind/named.conf.local:20: unknown option 'zone'
    * /etc/bind/named.conf.default-zones:3: unknown option 'zone'
    * /etc/bind/named.conf.default-zones:11: unknown option 'zone'
    * /etc/bind/named.conf.default-zones:16: unknown option 'zone'
    * /etc/bind/named.conf.default-zones:21: unknown option 'zone'
    * /etc/bind/named.conf.default-zones:26: unknown option 'zone' 

The onlything I could find after scrubbing the internet is once ina while there's a missing bracket.  But I have checked and triple checked my config files and the syntax and can't find anything wrong.  I have another installation of bind9 running on Fedora and the same exact syntax works just fine.

Anyone have any ideas of what I am missing here??  Any insight/help will be greatly appreciated!!

Ed

Here are the two files mentioned:

 /etc/bind/named.conf.local:
//
// Do any local configuration here
// If severity debug is used, the debug option can be set from 1 to 3.
// If a level isn't specified level 1 is the default.

 logging {
        channel named_info {
                file "/var/log/named.log" versions 10 size 750K;
                severity info;
                print-category yes;
                print-severity yes;
                print-time yes;
                };

// Consider adding the 1918 zones here, if they are not used in your
// organization
// include "/etc/bind/zones.rfc1918"

zone "wrenkasky.com" {
      type master; 
      file "/var/lib/bind/wrenkasky.com";
};

zone "10.10.10.in-addr.arpa" {
      type master;
      file "/var/lib/bind/10.10.10";
};

and /etc/bind/named.conf.local
//
// Do any local configuration here
// If severity debug is used, the debug option can be set from 1 to 3.
// If a level isn't specified level 1 is the default.

 logging {
        channel named_info {
                file "/var/log/named.log" versions 10 size 750K;
                severity info;
                print-category yes;
                print-severity yes;
                print-time yes;
                };

// Consider adding the 1918 zones here, if they are not used in your
// organization
// include "/etc/bind/zones.rfc1918"

zone "wrenkasky.com" {  type master; file "/var/lib/bind/wrenkasky.com"; };
zone "10.10.10.in-addr.arpa" { type master; file "/var/lib/bind/10.10.10"; };

root@atlas:/usr/src# cat /etc/bind/named.conf.default-zones
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

---

### Post by Bachstelze on 2010-08-11
```
logging {
channel named_info {
file "/var/log/named.log" versions 10 size 750K;
severity info;
print-category yes;
print-severity yes;
print-time yes;
};
```

Two opening, one closing.

---

### Post by edkasky on 2010-08-11
One of these days I will learn to not do this kind of stuff when I am too tired.  Thanks - that did the trick.  

Ed

---

