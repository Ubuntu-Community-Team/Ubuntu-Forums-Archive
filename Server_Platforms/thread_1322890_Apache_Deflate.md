---
title: "Apache Deflate"
date: 2009-11-11
forum: Server Platforms
---

### Post by Vegan on 2009-11-11
Anybody remember the command to activate the Apache deflate so that my fater P4 can serve documents even faster?

TIA.

---

### Post by DJ_Max on 2009-11-11
It's going to serve docs faster depending on the browser the client is using, and how much your server can handle.

[http://httpd.apache.org/docs/2.0/mod/mod_deflate.html](http://httpd.apache.org/docs/2.0/mod/mod_deflate.html)

---

### Post by Vegan on 2009-11-12
I just added 

```
AddOutputFilterByType DEFLATE text/html text/plain text/xml
``` 

to the httpd.conf as I only wanted to compress stuff that can be compressed.

I just wanted a quick fix to speed up things.

The forum software supports it, so why not generally.

---

### Post by DJ_Max on 2009-11-13
> **Vegan said:**
> I just added 

```
AddOutputFilterByType DEFLATE text/html text/plain text/xml
``` 

to the httpd.conf as I only wanted to compress stuff that can be compressed.

I just wanted a quick fix to speed up things.

The forum software supports it, so why not generally.
From my understanding most forum software use Zlib rather than plain DELFATE.

---

### Post by Vegan on 2009-11-13
Would that be harder than deflate to implement?

---

### Post by DJ_Max on 2009-11-13
Zlib is the wrapper, DEFLATE is raw data.

It's up to the browser to interepret the raw data.
[http://stackoverflow.com/questions/1574168/gzip-vs-deflate-zlib-revisited](http://stackoverflow.com/questions/1574168/gzip-vs-deflate-zlib-revisited)

---

