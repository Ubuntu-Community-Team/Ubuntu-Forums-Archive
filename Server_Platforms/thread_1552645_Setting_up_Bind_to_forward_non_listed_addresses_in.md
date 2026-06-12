---
title: "Setting up Bind to forward non listed addresses in zone"
date: 2010-08-13
forum: Server Platforms
---

### Post by andynz22 on 2010-08-13
I am setting up bind on a local LAN webserver using Ubunutu 9.1 server  and webmin for configuration.

I have setup a master zone for domain.co.nz and have added addresses for  www. etc.  I would like to be able to forward non listed addresses such  as other.domian.co.nz to an external name server as domain.co.nz also  exists in the outside world as well.  I have setup forwarding in the  "forwarding and transfer" section but how do I setup a master zone to  forward all non listed addresses.

Is this possible or do I need to do it in a different way. Maybe it  should be a slave rather than master zone?

Cheers
Andy

---

### Post by kidders on 2010-08-15
Hi there,

I'd suggest checking out bind's config files to make sure webmin has added a "forwarders" list to your "options" section. It should contain a list of servers to pass queries to, when bind doesn't have an authoritative answer.

---

### Post by andynz22 on 2010-08-22
Thanks for the reply.  Yes the have the forwarders (ISP DNS) setup in 'named.conf.options' as shown below:

auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
    forwarders {
        58.28.4.2;
        58.28.6.2;
        };

I notice it shows v6 but I thought the system was v4.  My knowledge is a bit lacking here.

Cheers
Andy

---

### Post by kidders on 2010-08-22
Hi there,

I've just re-read your o/p & realised I completely missed the point! Sorry. That'll teach me to reply to posts late at night :P

If a DNS server considers itself authoritative for domain.co.nz, the expected behaviour is that it'll act that way for all subdomains of domain.co.nz as well. Afaik, the way to defeat that behaviour is to explicitly delegate to another server on a case by case basis.

For example, you probably already have a zone with something like this in it, where "ns.domain.co.nz" is your bind server ...```
domain.co.nz. IN NS ns.domain.co.nz.
``` 

Supposing sub.domain.co.nz exists in the real world (ie outside your LAN), you could create another zone with this in it ...```
sub.domain.co.nz. IN NS ns.sub.domain.co.nz.
```

You should be able to find the right nameserver(s) to use in the subdomain's WHOIS record. Alternatively, I suppose, you could just delegate to the WorldxChange nameservers you're using as forwarders.

Incidentally, if you're not using IPv6, you can ignore the "listen-on-v6" option. If you'd prefer, you could probably just delete it.

I hope that's more useful!

---

### Post by andynz22 on 2010-08-23
Yes that's great thanks.  I thought it might be the case of explicitly setting sub domains to the external address.  I tried that and it works fine.  Just had this memory from the bad days of using MS2003SRV and non listed subdomains were redirected automatically.  But then the setup was probably not the same guessing it was not set up as a master.

Does "listen-on-v6" effect performance if it is not being used?

Thanks again

---

### Post by kidders on 2010-08-23
> **andynz22 said:**
> Does "listen-on-v6" effect performance if it is not being used?I wouldn't think so ... it just configures bind to answer IPv6 queries. By default, it doesn't.

---

