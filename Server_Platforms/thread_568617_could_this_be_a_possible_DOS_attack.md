---
title: "could this be a possible DOS attack?"
date: 2007-10-06
forum: Server Platforms
---

### Post by Dseed on 2007-10-06
I'm running an Ubuntu 7.04 (Feisty Fawn) Server.

I am running a webserver and a dns server, as well as a bunch of other services (ftp, ssh, postfix etc)

the other day I noticed something strange in my syslog (/var/log/syslog)

here is the concerning part of my syslog:

cat /var/log/syslog

```

Oct  6 00:18:04 www named[7883]: client 217.160.246.244#51831: transfer of 'mydomain1.com/IN': AXFR started
Oct  6 00:18:04 www named[7883]: client 217.160.246.244#51831: transfer of 'mydomain1.com/IN': AXFR ended
Oct  6 00:18:05 www named[7883]: client 217.160.246.244#51832: transfer of 'mydomain2.com/IN': AXFR started
Oct  6 00:18:05 www named[7883]: client 217.160.246.244#51832: transfer of 'mydomain2.com/IN': AXFR ended

```

(mydomain1.com and mydomain2.com is substituted for the real domain names I own and serve via my DNS server)

this happens from the *same* client (217.160.246.244) over and over

(where it says 'client 217.160.246.244#51831 <--  am I right in thinking that the #51831 is how many times this has happened??)

anyway I was hoping someone would have some insight as to weather or not this is some form of DOS attack or as I have read 
> AXFR is also sometimes used by unauthorized third parties who want to sneak a peek at a site's data. 
 - http://cr.yp.to/djbdns/axfr-notes.html


any help at all would be appreciated

Thanks!

---

### Post by MJN on 2007-10-06
AXFR's are zone transfers (see [http://en.wikipedia.org/wiki/DNS_zone_transfer](http://en.wikipedia.org/wiki/DNS_zone_transfer)) and are a means to obtain all of the resource records within a particular zone (domain) without having to request each record individually (and therefore already know of their existence). They are usually used by secondary name servers which are authoritive for your domain and hence require the ability to copy your entire zone when it gets updated.

If you are worried about them then look up the **allow-transfer **directive in BIND (assuming that's the server you're using) and use it to restrict who can perform a zone transfer. You can ban everyone from doing so using **allow-transfer {"none";}; **in the options section of named.conf.

Mathew

---

### Post by Dseed on 2007-10-06
> Denial of Service

If a malicious entity is able to perform a DNS zone transfer they can launch a Denial of Service attack against that zone's DNS servers by bogging them down with many multiple requests. Not only can the name servers be made slow and unresponsive, in some cases this can lock-out the ability to do legitimate DNS updates by keeping the DNS servers database backend in a "write lock" mode.

taken from [http://en.wikipedia.org/wiki/DNS_zone_transfer](http://en.wikipedia.org/wiki/DNS_zone_transfer)

this is what I am pretty sure is happening.  becuase it is an AXFR request non-stop from a non-authoritive client... 217.160.246.244 is not a slave server to my domains.

Thanks for your insight Mathew

---

