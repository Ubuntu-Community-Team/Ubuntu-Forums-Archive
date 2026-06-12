---
title: "Lighttpd problem"
date: 2009-09-23
forum: Server Platforms
---

### Post by dragos2 on 2009-09-23
I have a problem with redirection in lighttpd (Ubuntu 8.04 32 bits)

```

url.redirect = ( "^/app/(.*)" => "https://site.com/$1",
                 "^/awstats/(.*)" => "https://site.com/$1"
)

```

The upper code does not redirect well for 2 reasons:

1) [http://site.com/app](http://site.com/app) (or /awstats) redirects to [https://site.com/](https://site.com/)
instead of [https://site.com/awstats/](https://site.com/awstats/)
2) If I call it like this [http://site.com/awstats/somepage.html](http://site.com/awstats/somepage.html) it
redirects to [https://site.com/somepage.html](https://site.com/somepage.html) which is incorrect and
it fails with 404.

Any help is appreciated.

---

