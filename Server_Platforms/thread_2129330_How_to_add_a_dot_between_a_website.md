---
title: "How to add a dot between a website"
date: 2013-03-25
forum: Server Platforms
---

### Post by Fertech on 2013-03-25
I Have my website running, and have a domain, just wondering how to do this [http://mywebsite.com](http://mywebsite.com)  to  this-->> [http://plus.mywebsite.com](http://plus.mywebsite.com)

---

### Post by sandyd on 2013-03-25
You need to add a CNAME record for plus.mywebsite.com with the value (without quotes) mywebsite.com

Then, you setup the Apache Virtual Hosts for the extra subdomain

---

### Post by CharlesA on 2013-03-25
> **sandyd said:**
> You need to add a CNAME record for plus.mywebsite.com with the value (without quotes) mywebsite.com

Then, you setup the Apache Virtual Hosts for the extra subdomain

Hmmm... I've been using A records for my subdomains, am I doing it wrong?

---

### Post by lisati on 2013-03-26
> **CharlesA said:**
> Hmmm... I've been using A records for my subdomains, am I doing it wrong?

Same here. Spambots and other visitors seem to find them OK.

---

### Post by Fertech on 2013-03-26
Any Free Cpanel?

---

### Post by CharlesA on 2013-03-26
> **Fertech said:**
> Any Free Cpanel?

This is one I found via google..
[http://www.000webhost.com/free-cpanel-hosting](http://www.000webhost.com/free-cpanel-hosting)

Keep in mind that you get what you pay for. :)

---

### Post by SeijiSensei on 2013-03-26
> **CharlesA said:**
> Hmmm... I've been using A records for my subdomains, am I doing it wrong?

The usual procedure is to have one A record for the base name of the host and CNAMEs for any aliases.  In practice the two methods are equivalent.

I also see the term "subdomain" used here a lot to refer to fully-qualified hostnames.  I think of a subdomain as something for which a separate nameserver is maintained like this:

```

...
sub        IN     NS     mysub.example.com.

host       IN     A      10.10.10.10
mysub      IN     A      10.10.10.11

```

Here "sub.example.com" is a subdomain of example.com with a nameserver for the subdomain at 10.10.10.11.  Both "host.example.com" and "mysub.example.com" are fully-qualified host names.  The subdomain will contain A records for hosts like host.mysub.example.com.  A good example of this in practice is where you want to partition a domain between servers, which might be in example.com, and workstations, which might be in the local.example.com subdomain.

A subdomain may also have associated MX records if you want mail for something.example.com to be handled by a different SMTP exchanger than example.com.  For instance, I manage a bunch of listservers for a client on a server i maintain.  The domain's records are all hosted at the client's web provider.  So there is an MX in the main zone file that points traffic for lists.example.com over to my server while mail for example.com goes somewhere else.

I'm not trying to be pedantic here, but there is a substantial difference from a DNS perspective if the first part of name.example.com refers to a host or a subdomain.

---

### Post by CharlesA on 2013-03-26
That makes sense. Thanks.

Not to detail the thread too much (the OP might find it helpful...maybe...), but I currently have all my stuff hosted on a VPS and the way my domain registrar has the DNS set up was to have everything pointed to the ip address of the server via A records, so it looked like this:

```

*		ip-address
mx		ip-address
mail		ip-address
serenity	ip-address
charlesa.net	ip-address
```

All those entries belonged to charlesa.net (and apparently I can ping charlesa.net.charlesa.net and it resolves to the correct IP, but I dunno why they set it up this way. :confused:  )

There are no CNAME records and only 2 MX records, one referencing * and the other referencing @. No idea what those mean, so I guess I will have to do some research. :)

---

### Post by SeijiSensei on 2013-03-26
```
@   IN  MX smtp.example.com.
```

The "@" stands for the entire domain, so this says to send mail for [email]someone@example.com[/email] to smtp.example.com.  I'd guess the "*" handles mail for *.example.com, but I can't say for sure.  I don't use wildcards in DNS records.

I usually set up the top of a zone file like this:

```

@     IN     SOA   example.com support.example.com.   (
                          stuff
                         )


        IN    NS       ns1.example.com.
        IN    NS       ns2.example.com.

        IN    MX        0 smtp.example.com.
        IN    MX       10 smtp2.example.com.

etc.

```

Since each line is empty before the "IN" field, it inherits the contents of the field above it, in this case "@".  So all those NS and MX records implicitly apply to example.com.

---

### Post by CharlesA on 2013-03-26
Thanks for the explanation. I'm not too sure what sort of setup my domain registrar has for handling DNS, but they present you with a web interface to modify CNAMES, A records, TXT records and the like.

I ended up having to contact their support to get an domainkeys entry setup because the web form wouldn't take the entire string.

---

