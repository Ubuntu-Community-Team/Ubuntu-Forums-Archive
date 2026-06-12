---
title: "mod_rewrite for hostname in FQDN?"
date: 2005-10-29
forum: Server Platforms
---

### Post by mwnovak on 2005-10-29
This isn't specific to Ubuntu, but I'm hoping someone here might be able to answer a question.

I recently moved my personal web server across the country with me, and my new isp blocks incoming traffic on port 80.  Fun.  So, I've got dyndns.org doing redirects (what they call "webhops") as follows:

host1.mydomain.com ends up at host1.x.mydomain.com:8080
host2.mydomain.com ends up at host1.x.mydomain.com:8080
etc.

The ".x." bit is probably poor form, but my question would apply equally well if the redirects mapped to, for example, "host1x.mydomain.com:8080".

So, here's my question: is it possible to use Apache's mod_rewrite (or something else?) to clean up these URLs?

The closest I've been able to come is with the following syntax (taken from [this tutorial]("http://www.socialpatterns.com/search-engine-marketing/cleaning-up-canonical-urls-with-redirects/")):

```
 RewriteEngine On
RewriteCond %{HTTP_HOST} ^socialpatterns\.com$ [NC]
RewriteRule ^(.*)$ http://www.socialpatterns.com/$1 [R=301,L]

```

The one time I got that example to match (I'm not very good with regular expressions, I'm afraid), it functioned like an http redirect and caused the browser to try loading the URL indicated by RewriteRule... and that doesn't help: if I could access host1.mydomain.com directly, I wouldn't be mod_rewrite'ing anything in the first place. :???:

Is there are way to rewrite the host name in my FQDN that doesn't trigger an http redirect?  This may well be impossible ... I'm just trying to find out if I should keep messing with it or just accept the ugly urls.

Thanks in advance,

--MW

---

