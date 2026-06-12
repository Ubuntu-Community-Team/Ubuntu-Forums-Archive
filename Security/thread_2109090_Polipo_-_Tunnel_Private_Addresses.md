---
title: "Polipo - Tunnel Private Addresses?"
date: 2013-01-26
forum: Security
---

### Post by war59312 on 2013-01-26
Hi,

Anyone had success with Polipo and tunneling private addresses?

That is..

I have Polipo, Privoxy, and Squid3 all running together and working fine.

The issue is that if the user then wants to browse to a private address, the users gets the "Welcome to Polipo" page instead of the expected site. Or even a 404.

For example I am running CouchPotato at [http://192.168.1.193:5050/](http://192.168.1.193:5050/) and if the user tries to browse to that page while connected through Polipo, Privoxy, or Squid3, the users get the "Welcome to Polipo" page instead of the expected site.

Even worse, if the users tries to browse to a private address that includes a directory, for example [http://192.168.1.193:5050/movie/](http://192.168.1.193:5050/movie/) then the users get's an ugly "404 Not found" page.

So basically if the users wants to browse to a private addresses then the proxy should "tunnel" that connection as is.

I thought by adding this to Polipo's config it would do jus that, but it makes no difference at all:

```
allowedPorts = 1-65535
tunnelAllowedPorts = 1-65535
```

Thanks for the help,

Will

---

