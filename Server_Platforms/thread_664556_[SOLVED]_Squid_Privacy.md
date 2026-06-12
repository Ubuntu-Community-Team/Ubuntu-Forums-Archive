---
title: "[SOLVED] Squid Privacy"
date: 2008-01-11
forum: Server Platforms
---

### Post by expatCM on 2008-01-11
I took a look at this site from a network client
[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

I knew that my public IP would be shown but it appears that Squid also shares the package name / version, port used, your local host name and private IP address.

Is there any way to either stop the local information from being shared or otherwise simply share generic information?

---

### Post by HermanAB on 2008-01-11
Well, not unless you don't need the packets to get to you...

---

### Post by expatCM on 2008-01-11
Thought that was the role of NAT on the server?

---

### Post by PetePete on 2008-01-11
you need to look under squid.conf under header access..   i have following in my conf and it works (for my needs)

```

header_access Via deny all
header_access X-Forwarded-For deny all

```
then websites dont know you are using a proxy. :)

---

### Post by expatCM on 2008-01-11
Perfect :)

Thank you for your help.

---

