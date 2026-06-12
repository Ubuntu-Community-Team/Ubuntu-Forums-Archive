---
title: "bind9 dns question"
date: 2008-10-30
forum: Server Platforms
---

### Post by fouadk on 2008-10-30
hi everyone...

the scenario is that i have two servers...one with windows server 2008 and the other with ubuntu server 8.04

what i need to do is install active directory on the windows server....active directory requires dynamic dns in order to work...
my question is the following: how to configure bind9 to make dynamic ???

i have a similar working scenario but with windows server 2003 instead of 2008 and it works like a charm and the dns is not dynamic...this wont work with 2008 coz it requires dynamic dns...

how to make bind9 dynamic ???

please help 

thanks in advance

---

### Post by Wayne_V on 2008-10-30
try adding 
    allow-update { any; };

to your zone stanzas in named.conf.

There was an old problem with apparmor not allowing journal files to be created as well - not sure if that is fixed yet.   Watch syslog and if you see errors regarding journal files you may need to take a look at /etc/apparmor.d/usr.sbin.named and possibly add a 
   journal "/path/to/<domain>.hosts.jnl"; 
to your zone stanzas as well.

---

### Post by davidshere on 2008-10-30
Use the windows server as your primary DNS and the Ubuntu server as your secondary dns.  We do that here and it works very well.

---

### Post by Wayne_V on 2008-10-30
If you are using Hardy as your dhcp server you can configure it to do the dns update when it hands out an IP as well.   Use the following as a starting point:

> # dhcpd.conf
authoritative;
ddns-updates on;
ddns-update-style interim;
update-static-leases on;
ignore-client-updates;
default-lease-time 604800;
max-lease-time 604800;
option    domain-name    "your.domain.com";

allow bootp;
allow booting;

key rndc-key {
    algorithm    hmac-md5;
    secret        "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx";
};

subnet 192.168.2.0 netmask 255.255.255.0 {
    option    ntp-servers    x.x.x.x;
    option    routers        192.168.2.x;
    option    subnet-mask    255.255.255.0;
    range 192.168.2.y 192.168.2.z;
    }


> // named.conf
acl clients {
    127.0.0.1;
    192.168.2.0/24;
};

options {
    directory "/var/cache/bind";
    listen-on    { clients; };
    allow-recursion { clients; };
    dump-file "/var/cache/bind/cache_dump.db";
    statistics-file "/var/cache/bind/named_stats.txt";
    forwarders {
        // (your ISP name servers)
        x.x.x.x;
        x.x.x.x;
        };
};

// same key as in dhcpd.conf
include "/etc/bind/rndc.key";

// 
// a caching only nameserver config
// 
controls {
    inet 127.0.0.1 allow { localhost; } keys { rndc-key; };
};

zone "." IN {
    type hint;
    file "/etc/bind/named.ca";
};

zone "localdomain" IN {
    type master;
    file "/etc/bind/localdomain.zone";
    allow-update { none; };
};

zone "localhost" IN {
    type master;
    file "/etc/bind/localhost.zone";
    allow-update { none; };
};

zone "0.0.127.in-addr.arpa" IN {
    type master;
    file "/etc/bind/named.local";
    allow-update { none; };
};

zone "your.domain.com" {
    type master;
    file "/etc/bind/your.domain.com.hosts";
    allow-query { clients; };
    allow-update { key rndc-key; };
    //allow-transfer { <your slave server IP>; };
    journal "/var/lib/bind/your.domain.com.hosts.jnl";
    };

zone "2.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/192.168.2.rev";
    allow-query { clients; };
    allow-update { key rndc-key; };
    //allow-transfer { <your slave server IP>; };
    journal "/var/lib/bind/192.168.2.rev.jnl";
    };


(and lets see if /quote does what I think it should too ....)

---

### Post by fouadk on 2008-10-30
the allow-update{any;} did not do the trick...

lets say i go with the solution that davidshere provided...
can i make bind9 to replicate the windows DNS ??and if yes how ???

---

### Post by davidshere on 2008-10-30
> **fouadk said:**
> the allow-update{any;} did not do the trick...

lets say i go with the solution that davidshere provided...
can i make bind9 to replicate the windows DNS ??and if yes how ???

Put this in the named.conf.local file:
```

zone "yourdomain.com" {
	type slave;
	file "/etc/bind/zones/yourdomain.com.db";
	masters { windows.server.ip.adddress; };
};

```

Using the Ubuntu server as your DHCP is also a good solution.  Just not the one we use.

---

### Post by fouadk on 2008-10-30
ok david....and by doing this the linux dns server will always  replicate the windows dns ???? and if the windows dns crashes linux will take over automatically right ???? 

my current setup is with windows server 2003....everything is on linux(dns, dhcp, oracle database(red hat), mysql, samba, web server )i dont trust microsoft product and only use them when i really need to(active directory)

windows server 2008 is not working with bind9 coz most probably microsoft people dont follow the standards....so i will most probably use the solution you provided.

thanks a lot

---

### Post by davidshere on 2008-10-30
> **fouadk said:**
> ok david....and by doing this the linux dns server will always  replicate the windows dns ???? and if the windows dns crashes linux will take over automatically right ????

Yes.  Having a master/slave configuration is a very normal setup.  You can use both of them for DNS queries.  They should return identical results.  If one is down (or being reset), the other should continue to resolve names and your clients shouldn't notice the difference.

We actually have one Windows master and two Ubuntu slaves.  I've been experimenting with a FreeBSD slave, too.

---

### Post by fouadk on 2008-11-01
thanks a lot david....i will try that as i soon as possible...do you think a linux based dhcp is better than a windows one....my current setup is with with linux dhcp which works fine.
does the dhcp description above would update the dns server ????

---

### Post by khaled22 on 2011-01-21
> **davidshere said:**
> Use the windows server as your primary DNS and the Ubuntu server as your secondary dns. We do that here and it works very well.
 
hey 
how can i windows server as primary dns and ubuntu server as secondary dns.
2:how can i ubuntu as secondary dns conf withe withich commands
help step by step
thnks

---

### Post by khaled22 on 2011-01-21
hey 
how can i windows server as primary dns and ubuntu server as secondary dns.
2:how can i ubuntu as secondary dns conf withe withich commands
help step by step
thnks

---

