---
title: "Nameserver Non-Authoritative after Views Implementation"
date: 2013-05-14
forum: Server Platforms
---

### Post by buee on 2013-05-14
First, let me say that I'm relatively new to setting up BIND, I get the concept, but this is the first time ever setting up authoritative servers.

My end game is this, to be able to host the namespace for multiple domains.  I've gotten this to work. However, now I've moved on to part two of my headache and that's serving internal subdomains to internal users while leaving the public stuff on (hopefully) a separate zone. For example, I want:

```
cameras.test.com -> 192.168.1.15
management.test.com -> 192.168.1.26
web.test.com -> 42.245.212.55
email.test.com -> 42.245.212.60
```

From what I've read, I need to set up views.  Specify an "internal" view for the private domains and an "external" view for the public domains.

The problem I'm having is that I have the views setup, dropped items where I believe they're supposed to go, and then all of the sudden, transfers to the slave stop.  On the slave, I get:

```
May 14 13:45:34 ns2 named[3270]: client 192.168.1.188#22604: view internal: received notify for zone 'test.com': TSIG 'transfer': not authoritative

```

No matter what I do, that's what comes up.  All I did, from a confirmed working system, is add views and place zones in those views.

Unfortunately, I had to do all this with Webmin as my company has a firm policy that no one person can be the keeper of procedures so it has to be relatively user friendly.

Here's my named.conf.local:

```
view "internal" {
        match-clients {
                192.168.1.0/24;
                };
        recursion yes;
        also-notify {
                192.168.1.199;
                };
        zone "0.in-addr.arpa" {
                type master;
                file "/etc/bind/db.0";
                };
        zone "127.in-addr.arpa" {
                type master;
                file "/etc/bind/db.127";
                };
        zone "255.in-addr.arpa" {
                type master;
                file "/etc/bind/db.255";
                };
        zone "localhost" {
                type master;
                file "/etc/bind/db.local";
                };
        zone "." {
                type hint;
                file "/etc/bind/db.root.internal";
                };
        zone "test.com" {
                type master;
                file "/var/lib/bind/test.com.internal.hosts";
                also-notify {
                        192.168.1.199;
                        };
                };
        };
view "external" {
        recursion no;
        allow-transfer { 192.168.1.199; };
        also-notify {
                192.168.1.199;
                };
        zone "publicdomain.org" {
                type master;
                file "/var/lib/bind/publicdomain.org.hosts";
                also-notify {
                        192.168.1.199;
                        };
                notify yes;
                };
        zone "212.245.42.in-addr.arpa" {
                type master;
                file "/var/lib/bind/42.245.212.rev";
                also-notify {
                        192.168.1.199;
                        };
                };
        zone "." {
                type hint;
                file "/etc/bind/db.root";
                };
        };

```

And here's the test.com zone file:
```
$ttl 38400
test.com.       IN      SOA     ns1.test.com admin.lrcommunication.com. (
                        1368556740
                        10800
                        3600
                        604800
                        38400 )
test.com.       IN      NS      ns1.test.
transfer.test.com.      IN      A       192.168.1.4

```

I'm probably very wrong in this, but doesn't the SOA in the zone file indicate that it's authoritative?  So I call upon the BIND gutus for help.

---

