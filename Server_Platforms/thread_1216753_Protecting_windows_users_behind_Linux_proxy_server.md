---
title: "Protecting windows users behind Linux proxy server from viruses/spyware/adware"
date: 2009-07-18
forum: Server Platforms
---

### Post by marklodge on 2009-07-18
I have a Squid proxy server running on Debian distro. Windows clients are behind this proxy server.
Could i create something like a hosts file that will block all known spyware urls (on the server)?
So when a windows user requests a banned url it will be blocked automatically.

Basically, i just want to protect my windows users from viruses/spyware before it reaches them.


Thanks
Mark

---

### Post by koenn on 2009-07-18
what you're asking is something like this: 
```

acl blacklist dstdomain "/etc/squid/blacklist"

http_access deny blacklist
http_access allow all
```

read squid.conf, it has very extensive documentation. And google.

You probably realise that this will only work if you know the domain name  or url of every untrustworthy site on the internet. 

maybe you also need to read about RBL

---

### Post by giggins on 2009-07-18
Great suggestions from koenn. You might also consider using [havp]("http://www.server-side.de/") as a parent proxy, to catch URLs that aren't already known. [Dansguardian]("http://dansguardian.org/") (patched with the [anti-virus patch]("http://www.harvest.com.br/asp/afn/dg.nsf")) is also an option, depending on where you've setup squid. Its fee for non-commercial use. Both are available in .deb packages.

---

