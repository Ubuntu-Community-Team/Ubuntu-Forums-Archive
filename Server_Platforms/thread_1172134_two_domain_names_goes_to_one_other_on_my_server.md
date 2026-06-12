---
title: "two domain names goes to one other on my server?"
date: 2009-05-28
forum: Server Platforms
---

### Post by dorogon on 2009-05-28
I got two domain names that goes to another domain name,
i got two (A) on all my domain names (domainname.com & www,domaimname.com)
but only two of them works without "www" .

The problem started when my hard drive in the server crashed and i had to replace it with a new one and reinstall Ubuntu Server again.

Any one know what i missed or done wrong?

---

### Post by cdenley on 2009-05-28
Do the domain names resolve to the correct IP?
```

dig +short www.mydomain.com
dig +short mydomain.com

```
What do the vhost configurations look like?
```

cat /etc/apache2/sites-enabled/*

```

How do they not work? Do you get the wrong vhost, or do you get some kind of error?

---

