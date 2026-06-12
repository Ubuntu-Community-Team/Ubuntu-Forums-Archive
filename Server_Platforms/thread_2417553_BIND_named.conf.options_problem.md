---
title: "BIND named.conf.options problem"
date: 2019-04-24
forum: Server Platforms
---

### Post by jbamford92 on 2019-04-24
Hi folks,

Im trying to setup BIND for a DNS Server however im having a problem with editing the named.conf.options. I keep getting this error /etc/bind/named.conf.local:15: '{' expected near '"' would anyone have any ideas?

```
acl "trusted" {        68.183.3;    # ns1 - can be set to localhost
        68.183.4;    # ns2
        81.150;  # mail
        81.150;  # web
};


options {
        directory "/var/cache/bind";


        recursion yes;
        allow-recursion { trusted; };
        listen-on { 68.183; };
        allow-transfer { none; };


        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


         forwarders {
                1.1.1.1;
                9.9.9.9;


         };


        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation no;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};



```

Thanks.

---

### Post by jbamford92 on 2019-04-24
Update.

Ive managed to sort it. 

Thanks.

---

### Post by wildmanne39 on 2019-04-24
That is good news, will you please post your solution here so the whole community can benefit from your solution.

Thanks

---

### Post by jbamford92 on 2019-04-24
> **wildmanne39 said:**
> That is good news, will you please post your solution here so the whole community can benefit from your solution.

Thanks

It turned out to be a problem in the named.config.local i made a few typo errors. i missed out " between violetdragonsnetwork.co.uk" 

```
zone "violetdragonsnetwork.co.uk" {    type master;
    file "/etc/bind/zones/db.violetdragonsnetwork.co.uk";
    allow-transfer { 68.183.47.141; };
};


zone "183.68.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.68.183";
    allow-transfer { 68.183.47.141; };
};
```

---

