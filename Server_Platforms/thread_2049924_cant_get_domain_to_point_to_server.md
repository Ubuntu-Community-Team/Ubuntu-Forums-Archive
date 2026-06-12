---
title: "cant get domain to point to server"
date: 2012-08-29
forum: Server Platforms
---

### Post by Desaints on 2012-08-29
I have ohiotech.net pointing to the NS my VPS host provided.

ns1-ns4

I have ubuntu 12.04 x64 with ISPconfig Mysql and Apache2 on the VPS

ISPconfig's dns is set up like this:

```
	A	mail	64.111.29.240	0	
A	ohiotech.net	64.111.29.240	0	
A	www	64.111.29.240	0	
MX	mail.ohiotech.net	mail.64.111.29.240	10	
NS	ns1.ohiotech.net	ns1.64.111.29.240	0	
NS	ns2.ohiotech.net	ns2.64.111.29.240	0	
   Page 1 of 1 
```

I'm not exactly positive what other information to post..

when going to ohiotech.net i get nothing or my old host depending on how i type it in.

going to the ip works perfectly.

---

### Post by Bachstelze on 2012-08-29
If you have configured your domain name to use your provider's nameservers, then you need to do the configuration on your provider's name servers. If you want to use your own nameserver, then you need to configure your domain to use it.

---

### Post by sandyd on 2012-08-29
+1 to what Bachstelze said, also

Your current nameservers, 
ns1.frontrangehosting.com [204.45.250.249]
ns3.frontrangehosting.com [50.116.61.110]

are refusing querries for your domain.

---

### Post by lisati on 2012-08-29
Don't get me wrong (I'm fairly new to this side of hosting), but the "www" entry seems out of place. Shouldn't it be something like [www.ohiotech.net](www.ohiotech.net)?

edit: +1 to what the others have said. On my setup I have most of the entries pointing to my server, but for the name servers, I have left them at my provider's defaults.

---

### Post by Bachstelze on 2012-08-29
> **lisati said:**
> Don't get me wrong (I'm fairly new to this side of hosting), but the "www" entry seems out of place. Shouldn't it be something like [www.ohiotech.net](www.ohiotech.net)?

No, but the ohiotech.net entry above probably is (should be ohiotech.net. -- with a trailing period). Also the MX and NS records seem wrong as well, but maybe it's the "ISPConfig" thing that displays them like that...

---

### Post by lisati on 2012-08-29
> **Bachstelze said:**
> No, but the ohiotech.net entry above probably is (should be ohiotech.net. -- with a trailing period).

Thanks. It looks like the OP's setup is slightly different to mine, so I'll stand back and watch with interest.

---

### Post by Bachstelze on 2012-08-29
> **lisati said:**
> Thanks. It looks like the OP's setup is slightly different to mine, so I'll stand back and watch with interest.

To be honest, though, it would be better to have the actual BIND config file rather than what "ISPConfig" gives, which is incomplete and probably wrong as well.

<rant>If you want to manage a server with something as complex as DNS yourself, you should be prepared to do the actual work, not use a shiny control panel. Otherwise, just use the provider's nameservers.</rant>

---

### Post by sandyd on 2012-08-30
Or just use webmin to generate the bind config
/hides

---

### Post by Desaints on 2012-08-30
how would one do this with webmin? which i now have installed?

(googling this now...)

still any tips is helpful..

---

### Post by Bachstelze on 2012-08-30
That was of course a joke. For starters, what you need to do is to either configure your domain to use your nameservers, or configure your provider's nameservers to serve your domain correctly. None of this is done on your server. If you don't know how to do it, contact your provider.

If you really want to use your own nameserver and have configured your domain accordingly, we need your actual BIND config files (/etc/bind/named.conf.*).

---

### Post by SeijiSensei on 2012-08-30
Anyone who wants to run a nameserver needs to read [this RFC]("http://www.zoneedit.com/doc/rfc/rfc1912.txt"), and in particular, this paragraph:

> Running a nameserver is not a trivial task.  There are many things that can go wrong, and many decisions have to be made about what data to put in the DNS and how to set up servers.

---

### Post by Bachstelze on 2012-08-30
> **SeijiSensei said:**
> Anyone who wants to run a nameserver needs to read [this RFC]("http://www.zoneedit.com/doc/rfc/rfc1912.txt"), and in particular, this paragraph:

Running any kind of server is not a trivial task, really. That in itself is not a reason not do to it (but it is a reason not to use things like ISPConfig or Webmin).

---

### Post by Habitual on 2012-08-30
[http://intodns.com/ohiotech.net](http://intodns.com/ohiotech.net) looks great today, but had multiple visual indications of errors yesterday.

Today, it at least resolves to the assigned IP with a footer showing "Powered by ISPConfig"

Today, your A records on the 4 nameservers are showing the assigned IP, 
```
host -t ns ohiotech.net | while read dom ns server; do dig +short $dom; done
64.111.29.240
64.111.29.240
64.111.29.240
64.111.29.240
```

Yesterday, it pooped out.

This is looking better and better from a DNS point-of-view. :)

---

### Post by Desaints on 2012-08-31
I've set it up to point to their ns1-ns4 and set the proper records in their control panel.

So far i have the domain actually working and pointing to the server. I'll get to hosting another domain shortly using my own NS. Which like you said I'll most likely have to configure BIND. And i'll need to learn to do it sooner or later. The tech support from my host said i could just point ns1.ohiotech.net and ns2.ohiotech.net to ns1-ns2 of theirs...

---

