---
title: "DNS mx configuration issue"
date: 2009-09-20
forum: Server Platforms
---

### Post by tr333 on 2009-09-20
When I run named-checkzone on my bind9 configuration files ("db.0.0.10") I get the following error:
The domain name is 'mydomain' (not public, just running on a local LAN)
```
zone mydomain/IN: mydomain/MX 'mail' (out of zone) has no addresses records (A or AAAA)
```
There is no error when running named-checkzone on "db.mydomain".

In db.mydomain, I have a MX record setup for "mail.mydomain." and a A record setup for "mail".
```
$ORIGIN .
$TTL 604800     ; 1 week
mydomain                IN SOA  ns.mydomain. myuser.localhost. (
                                2009092002 ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      ns.mydomain.
                        A       127.0.0.1
                        MX      10 mail.mydomain.
                        AAAA    ::1
$ORIGIN mydomain.
mail                    A       10.0.0.3
ns                      A       10.0.0.1
                        A       127.0.0.1
```

In db.0.0.10, I have a MX record setup for "mail." and a PTR record setup for "mail."
```
$TTL    604800
@       IN      SOA     ns.mydomain. myuser.localhost. (
        2009092001      ; Serial
        604800          ; Refresh
        86400           ; Retry
        2419200         ; Expire
        604800 )        ; Negative Cache TTL
;
@       IN      NS      ns.
@   IN  MX  10  mail.
1       IN      PTR     ns.mydomain.
3   IN  PTR mail.
```

When I try to send an e-mail to myuser@mydomain it fails to send, but if I send it to [email]myuser@mail.mydoma[/email]in it sends successfully.
How can I get my mail server to accept e-mails going to myuser@mydomain instead of just [email]myuser@mail.mydoma[/email]in?

---

### Post by Bachstelze on 2009-09-20
> **tr333 said:**
> 
```

@       IN      NS      ns.
@   IN  MX  10  mail.
1       IN      PTR     ns.mydomain.
3   IN  PTR mail.
```

Should be:

> **tr333 said:**
> 
```

@       IN      NS      ns.mydomain.
1       IN      PTR     ns.mydomain.
3   IN  PTR mail.mydomain.
```

A MX record on a reverse zone is obviously nonsensical. Also, you didn't define an $ORIGIN in your second zone.

---

### Post by tr333 on 2009-09-20
Thanks.  named-checkzone isn't giving any errors now.  I modified my db.0.0.10 to be:
```
$TTL    604800
@       IN      SOA     ns.mydomain. myuser.localhost. (
        2009092001      ; Serial
        604800          ; Refresh
        86400           ; Retry
        2419200         ; Expire
        604800 )        ; Negative Cache TTL
;
@       IN      NS      ns.
$ORIGIN mydomain.
1       IN      PTR     ns.
3   IN  PTR mail.
```
Is it correct to change ns.mydomain. to ns. if $ORIGIN is defined?

When I look in syslog after restarting bind with this new configuration I get:
```

Sep 21 11:25:57 ubuntu named[12352]: /var/lib/bind/db.0.0.10:14: ignoring out-of-zone data (1.mydomain)
Sep 21 11:25:57 ubuntu named[12352]: /var/lib/bind/db.0.0.10:18: ignoring out-of-zone data (3.mydomain)
```
Is this a problem?

---

### Post by Bachstelze on 2009-09-21
> **tr333 said:**
> 
Is it correct to change ns.mydomain. to ns. if $ORIGIN is defined?

No. Think of the domain name hierarchy as a filesystem one: "ns." is something like "/ns", because the terminating period is the root of the system. If you want to define a record relative to the ORIGIN, you must put just "ns".

> **tr333 said:**
> When I look in syslog after restarting bind with this new configuration I get:
```

Sep 21 11:25:57 ubuntu named[12352]: /var/lib/bind/db.0.0.10:14: ignoring out-of-zone data (1.mydomain)
Sep 21 11:25:57 ubuntu named[12352]: /var/lib/bind/db.0.0.10:18: ignoring out-of-zone data (3.mydomain)
```
Is this a problem?

Of course. Since "1" is not a fully qualified name (it is not terminated with a period), it is interpreted relative to the ORIGIN. Since you have defined ORIGIN to be mydomain., it will be 1.mydomain., which is not what you want. If you want to define your ORIGIN to "domain.", you must define your entries that are not relative to it with their fully qualified names, i.e.:

```
1.0.0.10.in-addr.arpa.       IN      PTR     ns
3.0.0.10.in-addr.arpa.   IN  PTR mail
```

---

### Post by tr333 on 2009-09-21
DNS configs appear to be going fine now that there are no errors from named-checkzone and no errors in syslog.

[https://help.ubuntu.com/9.04/serverguide/C/dns-troubleshooting.html](https://help.ubuntu.com/9.04/serverguide/C/dns-troubleshooting.html) says I should be able to ping the domain name, but it's not finding anything:
```
$ ping mydomain
ping: cannot resolve mydomain: Unknown host
```
I can ping ns and ns.mydomain and they both give the correct IP address.
Does the domain name need a A record in addition to the SOA?

I am still unable to send mail directly to myuser@mydomain.  Is this related to the problem of not being able to ping the domain directly?

---

