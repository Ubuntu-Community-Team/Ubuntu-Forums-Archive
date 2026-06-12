---
title: "named-checkconf error on DNSSEC"
date: 2023-09-03
forum: Ubuntu Cloud and Juju
---

### Post by Karti on 2023-09-03
Hi,

OS: Ubuntu 22.04 LTS

Hoping someone can point me in the right direction. I have been trying to set this up as a development server for my training for a few days now with limited success. I can set up a working DNS with Bind9 but when I start to elaborate on it with DNSSEC, it doesn't play well.

My error is :

```
karti@mail:/etc/bind/zones$ named-checkconf
/etc/bind/Kjetj.ltd.+007+59298.key:1: '}' expected near ';'
```

and my /etc/bind/named.conf.options is:

```
options {
    directory "/var/cache/bind";
    recursion yes;
    dnssec-validation yes;
    listen-on-v6 { any; };
    listen-on { 192.168.122.247; };
    allow-query { localhost; 192.168.122.0/24; }; // Allow queries from localhost and your local network
    managed-keys-directory "/var/cache/bind"; // Path to keys file //
    forwarders {
        8.8.8.8;
        8.8.4.4;
    };
};


```

And for my /etc/bind/named.conf.local

```
 //
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "jetj.ltd" {
    type master;
    file "/etc/bind/db.jetj.ltd";
    // Add other zone-specific options here
    include "/etc/bind/Kjetj.ltd.+007+55485.key";
};

zone "122.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.192";
    // Add other zone-specific options here
    include "/etc/bind/Kjetj.ltd.+007+55485.key";
};


```


Any pointers would be appreciated.

Regards

Karti

---

### Post by nvanschoote on 2024-07-09
Hello Karti,

More recent versions of BIND9 tend to encourage a  more automated approach to DNSSEC. Hence instead of manually specifying  the DNSSEC key, you should define a DNSSEC policy and let BIND9 take  care of DNSSEC.

Here is the /etc/bind/named.conf.local on my server:
```

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";

dnssec-policy "my-policy" {
    keys {
         ksk key-directory lifetime P1Y algorithm ECDSAP256SHA256;
         zsk key-directory lifetime P60D  algorithm ECDSAP256SHA256;
    };

    // Key timings
    dnskey-ttl PT1H;
    publish-safety PT1H;
    retire-safety PT1H;
    purge-keys P90D;

    // Signature timings
    signatures-refresh P5D;
    signatures-validity P14D;
    signatures-validity-dnskey P14D;

    // Zone parameters
    max-zone-ttl P1D;
    zone-propagation-delay PT5M;
    parent-ds-ttl P1D;
    parent-propagation-delay PT1H;
};

zone "my-domain.com" {
    type primary;
    file "/etc/bind/zones/db.my-domain.com";
    dnssec-policy "my-policy";
    key-directory "/etc/bind/keys";
    inline-signing yes;
};

zone "222.10.in-addr.arpa" {
    type primary;
    file "/etc/bind/zones/db.10.222";
    dnssec-policy "my-policy";
    key-directory "/etc/bind/keys";
    inline-signing yes;
};

```

Hope it helps

Nathan

---

