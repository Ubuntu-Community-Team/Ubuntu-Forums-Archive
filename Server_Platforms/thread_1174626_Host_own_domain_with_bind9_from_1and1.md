---
title: "Host own domain with bind9 from 1and1"
date: 2009-05-31
forum: Server Platforms
---

### Post by mzw! on 2009-05-31
Hi!

I am trying to setup a domain registered at 1and1, but I need a little bit of help.

I am using bind9 to do that and I already have configured the zones in my ubuntu machine.

Let my domain be example.com and my ip 1.2.3.4

What I have done is the following:

[LIST=1]
[*]Add a subdomain called ns.example.com
[*]Modified dns settings for the subdomain to get other ip addresses, so it generates A entry: ns.example.com to point to my server ip using the 1and1 dns server 1.2.3.4
[*]Modify DNS settings to example.com to use my dns server hosted in 1.2.3.4 with bind9. Then, I changed to use my own dns in the options, and then use ns.example.com as primary dns server and 1and1 as secondary.
[*] It says I have to use slv1.1and1.com [IP = 217.160.224.4] and make an AXFR in my own dns, so I added the line in named.conf.local to zone example.com "allow-transfer {217.160.224.4;};
[*]in the db.example.com I added
```

@ IN NS slv1.1and1.com.
slv1.1and1.com. IN      A       217.160.224.4

```
[*]In db. (reverse zone) I added
```

@       IN      NS      slv1.1and1.com.
1.0.0   IN      PTR     slv1.1and1.com.
```
[/LIST]

when I do "dig ns.example.com" it appears as other IP.

Have someone tried to confiugure a domain with 1and1?
are the steps I made correct?

Thanks for your help!

---

### Post by windependence on 2009-05-31
Would be much easier to configure your DNS from their control panel and just use their DNS servers. Did you buy the domain from them? You don't need to run bind to run a web site.

-Tim

---

### Post by mzw! on 2009-05-31
Yes, would be easier to use their control panel (yes, I bought the domain from them) but I want to have the total control of the domain for mainly 2 reasons:
[LIST=1]
[*]I want "unlimited" subdomains, cname, A, MX etc entries.
[*]I always want to learn, and like the idea of having total control of what is happening with my server.
[/LIST]

Did you find something that could be end up in an error or misconfiguration?

---

### Post by tourret on 2011-01-20
Hi mzw!

I'm trying to do exactly what you want. Please let me know if you succeed!
I have a dedicated server in 1and1, i wan't total control over the server as well.

Did you set up the MX records and the email worked fine too?

Thanks in advance!

---

