---
title: "DNS subzone question"
date: 2011-06-03
forum: Server Platforms
---

### Post by tapi0n on 2011-06-03
I'm writing a script to add a subzone (subzone.sub.domain.tld) to my subdomain (sub.domain.tld).

The subzone requirements are the following:

its own zonefile
reference in named.conf.local
NS record and glue record in db.domain.tld

This is the current state of affairs:

I've got the named.conf.local part right
I know how to make the NS record and the glue record in db.domain.tld (except for one last bit, i'll get to that in a minute)
But I have no idea what to do about the zone file. To be more precise, I don't know what to put in there. I've read up on subzones and everything but in the examples they're all using different IP addresses. I have to put everything on 1 IP (virtual zones).

This is my zone file for domain.tld


```
$TTL 1H
$ORIGIN sub.domain.tld
@               IN      SOA     ns.sub.domain.tld. root.sub.domain.tld. (
                                2011053010      ;serial
                                1H              ;refresh
                                1H              ;retry
                                1H              ;expire
                                1H)             ;minimum ttl
;
@               IN      NS      ns.sub.domain.tld.
                IN      NS      ns.domain.tld.
                IN      MX      10 mx

                IN      A       xxx.xxx.xxx.xxx
ns              IN      A       xxx.xxx.xxx.xxx
www             IN      CNAME   ns
www1            IN      CNAME   ns
www2            IN      CNAME   ns
secure          IN      CNAME   ns
mx              IN      A       xxx.xxx.xxx.xxx
test            IN      A       xxx.xxx.xxx.xxx
```

So adding the NS record and the glue record would look something like this right?

```
...
mx              IN      A       xxx.xxx.xxx.xxx
test            IN      A       xxx.xxx.xxx.xxx

$ORIGIN subzone.sub.domain.tld

@             IN           NS         ????????? ;NS record
????          IN           A           ns.sub.domain.tld.
```

The '?'s in the code snippet shows where I start to get lost. I don't quite know what to put here.

As far as the zone file goes, I'm even more lost. Do you need to make a new SOA record in there or what? 

A friend told me that if you used $ORIGIN you can 'recycle' your zonefile for every subdomain you create. But I have no idea what he means by that. Could anyone shed some light on that? 

Cheers

---

### Post by SeijiSensei on 2011-06-03
If you want a separate zone, I think the following approach will work.  Set up a separate zone for the subdomain in named.conf:

```

zone "example.com" {
    type master;
    file "example.com";
};

zone "sub.example.com" {
     type master;
     file "sub.example.com";
};

```

then in the zone file for example.com include

```

sub       IN   NS   ns.example.com.

```

so that queries will be answered by the other zone file.

---

### Post by tapi0n on 2011-06-03
> **SeijiSensei said:**
> 
[/code]then in the zone file for example.com include

```

sub       IN   NS   ns.example.com.

```so that queries will be answered by the other zone file.

Yeah that's what I had in mind too, but seeing how *ns.example.com. *is already in my *example.com *zone file, how will it ever get to the *sub.example.com* zone file?

---

### Post by terazen on 2011-06-03
If the zone is in your named.conf the server will read the other zone file.

---

