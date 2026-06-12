---
title: "BIND9 DNS Cache"
date: 2008-04-19
forum: Server Platforms
---

### Post by doogy2004 on 2008-04-19
I am using BIND9 with OpenDNS as my forwarders.  Where can I find the current list of cached domains?

Thanks

---

### Post by ikonia on 2008-04-20
cached domains ??

do you mean the current domains your caching name server haslooked up and is storing on record until expiry ?

if so, thats in a db file that is not human readable.

why do you want to know the list of domains that your name server has looked up (you can always enable logging and do a sort -u against it)

---

### Post by doogy2004 on 2008-04-20
I am just curious as to what domains have been looked up and are currently stored on my server.  I wanted to be able to do this so that I can verify that a domain has been looked up when i'm troubleshooting my network for problems.

Thanks

---

### Post by ikonia on 2008-04-20
enalbe logging is the best way for you then have a script that runs a sort -u against it.

---

### Post by doogy2004 on 2008-04-20
> **ikonia said:**
> enalbe logging is the best way for you then have a script that runs a sort -u against it.

ok, thanks

---

### Post by doogy2004 on 2008-04-23
I have found something showing how to turn logging on at [http://www.netadmintools.com/art233.html](http://www.netadmintools.com/art233.html)

It states to add the following to named.conf
```
logging {
category "default" { "debug"; };
category "general" { "debug"; };
category "database" { "debug"; };
category "security" { "debug"; };
category "config" { "debug"; };
category "resolver" { "debug"; };
category "xfer-in" { "debug"; };
category "xfer-out" { "debug"; };
category "notify" { "debug"; };
category "client" { "debug"; };
category "unmatched" { "debug"; };
category "network" { "debug"; };
category "update" { "debug"; };
category "queries" { "debug"; };
category "dispatch" { "debug"; };
category "dnssec" { "debug"; };
category "lame-servers" { "debug"; };
channel "debug" {
file "/tmp/nameddbg" versions 2 size 50m;
print-time yes;
print-category yes;
};
};
```

I have the following:
```
named.conf
named.conf.local
named.conf.options
```

Which named.conf should I put the configuration into?

---

