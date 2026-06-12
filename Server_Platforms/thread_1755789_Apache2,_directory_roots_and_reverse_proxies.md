---
title: "Apache2, directory roots and reverse proxies"
date: 2011-05-11
forum: Server Platforms
---

### Post by thelost on 2011-05-11
Currently trying to understand how to set up apache for multiple web apps so that I can have them all behind a reverse proxy.

I have several web apps including subsonic that I'd all like to be accessable at:

[https://home.domain.tld/webapp1/](https://home.domain.tld/webapp1/)
[https://home.domain.tld/webapp2/](https://home.domain.tld/webapp2/)

and so on.

Because my understanding of Apache2 and virtual server directives is sketchy at best, I've been struggling with this. Looking at the error log, I can clearly see that for subsonic, apache is trying to look at the web root /var/www rather than /var/subsonic. I figured that I would need to either set up a new virtual server to handle requests to subsonic, or add an alias to /var/subsonic on the https virtual server.

I'm aware of how to use the Location directive (although a little fuzzy on the importance of slashes), for subsonic it looks like this:

```
<Location /subsonic>
order deny,allow
deny from all
allow from all
ProxyPass http://localhost:15003/
ProxyPassReverse http://localhost:15003/
</Location>

```

So to summarise, what do I need to do to point various webapps to the correct resources locally while having them reverse proxied?

---

