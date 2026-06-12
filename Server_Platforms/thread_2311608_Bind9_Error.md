---
title: "Bind9 Error"
date: 2016-01-28
forum: Server Platforms
---

### Post by n-mike-3 on 2016-01-28
Hello, can someone point me in the right direction?  Bind won't start.  Syntax checker throws the following.

@server-1:/etc/bind$ sudo named-checkconf
/etc/bind/named.conf.local:1: unknown option 'zone'
/etc/bind/named.conf.local:6: unknown option 'zone'
/etc/bind/named.conf.default-zones:2: unknown option 'zone'
/etc/bind/named.conf.default-zones:10: unknown option 'zone'
/etc/bind/named.conf.default-zones:15: unknown option 'zone'
/etc/bind/named.conf.default-zones:20: unknown option 'zone'
/etc/bind/named.conf.default-zones:25: unknown option 'zone'
/etc/bind/named.conf:12: '}' expected near end of file





named.conf.local is nothing complicated.  I can't see any missing brackets.   

zone "hive.yukaputz.net" {
    type master;
    file "/etc/bind/zones/db.hive.*somedomain*.net";};

zone "168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.168.192";};





named.conf.options is straight forward as well

acl "trusted" {
                   192.168.1.0/24;
};

options {
        directory "/var/cache/bind";

        recursion yes;                
        allow-recursion { trusted; }; 
        listen-on { 192.168.1.10; 127.0.0.1; };   
        allow-transfer { none; };      

        forwarders {
               8.8.8.8;
               8.8.4.4;
};



Any ideas?

---

### Post by darkod on 2016-01-28
Because one file calls another it is sometimes difficult but I think I see at least one missing bracket in named.conf.options...
```
options [COLOR=#ff0000]{[/COLOR]
directory "/var/cache/bind";

recursion yes; 
allow-recursion { trusted; }; 
listen-on { 192.168.1.10; 127.0.0.1; }; 
allow-transfer { none; }; 
```

The first bracket does not have a closing match, no?

---

### Post by QDR06VV9 on 2016-01-28
[COLOR=#333333]bind has files that check your config files and tell you where the mistake is.[/COLOR]
And closing Brackets
[COLOR=#333333]name-checkconf[/COLOR]
[COLOR=#333333]name-checkzone
Whoops you beat me.

[/COLOR]

---

### Post by Habitual on 2016-01-28
Line 12 of /etc/bind/named.conf, 
Verify } near end of file

---

### Post by n-mike-3 on 2016-01-28
Thank you sirs.  I was missing two brackets actually.  ugh.  I go hung up on the first errors instead of investigating all of them.   Thanks Habitual .

---

### Post by Habitual on 2016-01-28
You are very welcome.

---

