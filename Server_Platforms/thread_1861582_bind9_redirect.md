---
title: "bind9 redirect"
date: 2011-10-15
forum: Server Platforms
---

### Post by ant2ne on 2011-10-15
Lets suppose that I want all of my internal network clients to be redirected to an internal machine when they try to access and external fqdn. For example, regardless of the protocol, if someone was to attempt to access ubuntuforums.org they would be directed to an internal IP 192.168.3.22. 

I have tried adding
```
ubuntuforums.org   A   192.168.3.22

```and 
```
ubuntuforums.org.   A   192.168.3.22

```
to my db.mynetwork.net.hosts file which is what I modify for internal names.

---

### Post by vasile002 on 2011-10-16
you need to set up the pcs from your internal network to use your dns server for resolving everything

---

### Post by ant2ne on 2011-10-16
> **vasile002 said:**
> you need to set up the pcs from your internal network to use your dns server for resolving everything

Ok, lets assume for a minute I"m not that dense. I have an internal DHCP3 server that assigns IP address and THIS bind9s DNS server. The clients ARE using the correct dns server. nslookup gets the reply from my dns server. I just want (in the example above) the nslookup for ubuntuforums.org to return with 192.168.3.22. This requires my dns server to NOT use its forwarders (it doesn't use root hints) and use an A record that I assigned it. HOW?

---

### Post by SeijiSensei on 2011-10-17
You need to create a zone file for "ubuntuforums.org" and an entry in /etc/named.conf that makes your server the master for that domain.

I hope you're intending only to redirect a couple of domains, because trying to do this on a large scale would be a ridiculous amount of work.

Perhaps a better question is why are you trying to do this?  Maybe there are better solutions to offer if we know what the more fundamental issue is.

---

### Post by jonobr on 2011-10-17
SeijiSensei's kung-fu is strong - I had to do something similar,
[here]("http://ubuntuforums.org/showthread.php?t=1851094").

I was trying to setup resolution for something I had no control over - I could not change the names it was trying to resolve, so I had to setup this kind of resolution.
The way I got it working was as SeijiSensei described.

Turned out to be a problematic file in the end that was stopping it working, but now its working well.
I agree with him/her though, resolving using multiple zones will get unwieldy after a while

---

### Post by SeijiSensei on 2011-10-17
It's pretty common for organizations to run internal name servers for their own domains that provide a different set of results from those returned by the public nameservers for those same domains.  In those cases you have a local zone file on a private server that provides the internal mappings and another zone file on a public server that answers queries for objects like [www.example.com](www.example.com) and example.com's public NS and MX records.

---

### Post by ant2ne on 2011-10-23
I will do that Snesei, thanks

BTW [This is why I'm doing it.]("http://www.runuo.com/community/threads/internal-clients-dc-external-are-just-fine.487844/#post-3756855")

---

### Post by ant2ne on 2011-10-23
That did work. I can now resovle the way I want to. It hasn't solved my overall problem though.

---

