---
title: "Apache Wildcard Redirect, with server-status still working?"
date: 2009-11-12
forum: Server Platforms
---

### Post by victorhooi on 2009-11-12
heya,

I was trying to setup a wildcard entry in Apache, so that sites like "foobar.oursite.com" would redirect to "oursite.com".

In the DNS records, we have a *.oursite.com A-Record pointing to the IP of the server.

In Apache, for the default virtualhost, we have

```
RedirectMatch permanent ^(.*)$ http://www.oursite.com
```

That worked fine, until I realised that it also knocked out the Apache server stats (ie. [http://xx.xx.xx.xx/server-status](http://xx.xx.xx.xx/server-status)). This in turn knocked out many of our Munin Apache plugins, which depended on that.

What's the recommended way of setting up wildcard 301 redirects in Apache, with Virtualhosts? Or at least making the default site point to a redirect, while still having the server-status work?

Cheers,
Victor

---

### Post by Valasule on 2009-11-12
Have you tried making another dns record for somethingelse.oursite.com, then set the default vhost for this address and another vhost with your catch all redirect?
This might be the simplest approach since the dns wildcard will only match anything that doesn't have an IN A record in your dns files.

---

### Post by victorhooi on 2009-11-12
heya,

I'm not sure if I quite understand your solution, but that won't deal with people typing in foobar.oursite.com, only with things we explicitly setup in the DNS and in an Apche vhost (which is what we're trying to get away from).

The thing is, we want to catch everything (i.e. anything.oursite.com), except for that particular page ([http://127.0.0.1/server-status](http://127.0.0.1/server-status)), which is being called by Munin scripts.

Is it possible to setup a redirect in the default vhost that does this? (excluding that particular page).

Cheers,
Victor

---

