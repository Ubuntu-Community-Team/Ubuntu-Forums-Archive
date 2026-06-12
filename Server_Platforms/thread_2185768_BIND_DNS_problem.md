---
title: "BIND DNS problem"
date: 2013-11-04
forum: Server Platforms
---

### Post by typhon7 on 2013-11-04
Hello everyone,

I have a dedicated server with Ubuntu Server 12.10 and BIND9 installed and configured. I have approximately 10 domains configured and working fine.

One of them, let's say mydomain.cat, also works fine and it can be accessed by mydomain.cat or [www.mydomain.cat]("http://www.mydomain.cat"). I have few subdomains configured in its config file, for instance, *webmail *and *resources. *The issue here is that *webmail *works fine but *resources *sometimes resolves externally (it returns me the correct info of a *nslookup*, it shows me the webpage etc.) and sometimes does not resolve. Between this periods of time (hours or days) I don't change absolutely nothing in the server.

Zone config in *named.conf.local *is:

```
zone "mydomain.cat" {
        type master;
        file "/var/lib/bind/mydomain.cat.hosts";
        };
```

File */var/lib/bind/mydomain.cat.hosts* (chaning domain names and IP, originals are all correct and they point to my server's IP):

```
$TTL    86400
@   IN  SOA myserver.kimsufi.com. info.mydomain.cat. (
         2013010800
              28800
               7200
             604800
              86400 )


@                    IN      NS          myserver.kimsufi.com.
@                    IN      NS          ns.kimsufi.com.
@                    IN      MX      0   mydomain.cat.
@                    IN      A           X.X.X.X
                     IN      A           X.X.X.X
www                  IN      A           X.X.X.X
mail                 IN      A           X.X.X.X
webmail              IN      A           X.X.X.X
phpmyadmin           IN      A           X.X.X.X
example              IN      A           X.X.X.X
exampleb             IN      A           X.X.X.X
examplec               IN      A           X.X.X.X
resources             IN      A           X.X.X.X
stats                IN      A           X.X.X.X
mydomain                  IN      CNAME       mydomain.cat.
mydomain.cat.                     TXT         "v=spf1 a mx ~all"
mydomain.cat.                     TXT         "v=spf1 a -all"

```
All subdomains resolve except *resources* and the 3 called *example*. I have other domains and subdomains configured with the same syntax and they all work fine.

[FONT=verdana][COLOR=#000000]Return of *named-checkzone*:

[/COLOR][/FONT]```
# named-checkzone mydomain.cat mydomain.cat.hosts
zone mydomain.cat/IN: loaded serial 2013010800
OK
```
[FONT=verdana][COLOR=#000000]
Return of *named-checkconf*:

[/COLOR][/FONT]```
# named-checkconf mydomain.cat.hosts
mydomain.cat.hosts:1: unknown option '$TTL'
mydomain.cat.hosts:26: unexpected token near end of file
```
[FONT=verdana][COLOR=#000000]
Same result is returned when *named-checkconf* is called with my other domains (and they work).

If I call *nslookup *from the server it resolves: 

[/COLOR][/FONT]```
# nslookup resources.mydomain.cat
Server:         213.186.33.99
Address:        213.186.33.99#53

Non-authoritative answer:
Name:   resources.mydomain.cat
Address: X.X.X.X
```
[FONT=verdana][COLOR=#000000]
But if I call *nslookup* from another host it doesn't work, but the thing I don't understand is that sometimes work and sometimes don't.

It's been many days with this problem, it's not an issue provoked by a recent config change. Of course I have restarted all services and the server itself many times.

I had *mydomain.cat* in another registrar but I changed it a few months ago. I'm not sure, but it's possible that I created the subdomains that don't work sometimes after the registrar change, and the subdomains that work always were created before the change. In the current registrar I have primary DNS pointing to my server and secondary DNS pointing to *ns.kimsufi.com* (same as all my other domains).

I would gratefully thank any idea that could help solve my problem.[/COLOR][/FONT]

---

### Post by typhon7 on 2013-11-05
In case someone come to this thread with a similar issue, I have solved it (or at least it's been working more than 24 hours by now) using command *rndc *(in particular, *rndc flush* and *rndc reload*) and changing the *Serial Number* of *mydomain.cat.hosts.*

---

