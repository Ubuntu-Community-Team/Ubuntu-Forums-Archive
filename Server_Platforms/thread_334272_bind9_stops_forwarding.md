---
title: "bind9 stops forwarding"
date: 2007-01-08
forum: Server Platforms
---

### Post by ChAoS.ct on 2007-01-08
Hi!
I have an Ubuntu Dapper Server with bind9 installed as a dns server.
This bind9 has a local zone for my LAN and forwards all other querys to the router.

The problem is: bind9 stops forwarding dns queries aparently whithout reason. Afer a reload bind9 runs normally.

How can I activate debug messages in the logs to see what's happening?

Sorry for my English.

---

### Post by linuchsan on 2007-01-08
you have to be more specific...like any updates you did, software that conflicts, firewalls installed, config files...ect.

---

### Post by ChAoS.ct on 2007-01-08
I have the official bind9 package installed from the repository, no firewalls.
/etc/bind/named.conf.options:
```
options {
        directory "/var/cache/bind";
        auth-nxdomain no;    # conform to RFC1035
        forward only;
        forwarders {
                192.168.1.1;
                };
};

```

where 192.168.1.1 is my router which has a dns service.

When bind9 stops forwarding dns queries , i can ask for dns's to the router and bind9 also returns addresses  of my LAN.

---

