---
title: "Apache mod_rewrite includes document root in rewrite"
date: 2010-10-31
forum: Server Platforms
---

### Post by lynwode on 2010-10-31
Hi Guys,
I am experimenting with mod_rewrite and am experiencing some unexpected behaivior. I have enabled the mod-rewrite features and can successfully redirect a URL to another website eg [http://mydomain.com/abc/index.html](http://mydomain.com/abc/index.html) -> [http://www.google.com](http://www.google.com). However if I try and point to another file within my docroot I get a weird rewrite. The following are the setup details:

Ubuntu 10.04
Apache 2.2.14
Doc root = /var/www
initial URL = [www.mydomain.com/abc/index.html](www.mydomain.com/abc/index.html)
RewriteRule ^abc/index\.html$ abc/fred.html [R=301,L]

I expect the following re-written URL:
[www.mydomain.com/abc/fred.html](www.mydomain.com/abc/fred.html)

However this is what I get:
[www.mydomain.com/var/www/abc/fred.html](www.mydomain.com/var/www/abc/fred.html)

This of course is giving me a page can't be found error.

Does anyone have any idea as to what I may be doing wrong?

Cheers,
Tim

---

### Post by SeijiSensei on 2010-10-31
That is strange.  What if you use leading slashes like this:

```
RewriteRule ^/abc/index\.html$ /abc/fred.html [R=301,L]
```

---

### Post by lynwode on 2010-10-31
Thanks for the suggestion, I had tried that in the past and it hadn't worked.
After some more tinkering (using the above suggestion) I have got it working and guess what it was - yep the pages were being cached by the browser. Even setting the browser to check for a new page each visit wasn't enough. I have to clear the entire cache first... looks like I need to have a look at some HTTP headers now....

Thanks.

---

### Post by SeijiSensei on 2010-10-31
> **lynwode said:**
> Thanks for the suggestion, I had tried that in the past and it hadn't worked.
After some more tinkering (using the above suggestion) I have got it working and guess what it was - yep the pages were being cached by the browser. Even setting the browser to check for a new page each visit wasn't enough. I have to clear the entire cache first... looks like I need to have a look at some HTTP headers now....

Thanks.

In PHP, I send these headers to forbid caching:

```

header("Pragma: no-cache");
header("Cache-Control: no-cache; must-revalidate");
header("Expires: -1");

```

I think those cover most browsers.  "Pragma: no-cache" in particular works with HTTP/1.0 I believe.  The latter two rely on HTTP/1.1 cache control.

---

