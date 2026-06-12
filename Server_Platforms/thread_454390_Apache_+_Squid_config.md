---
title: "Apache + Squid config"
date: 2007-05-25
forum: Server Platforms
---

### Post by catfox on 2007-05-25
Hi folks,
I've got a server running apache and a number of python/zope applications.
The server is accessed by ip:port and apache rewrites from that onto the zope applications.

so: [internet] ---> apache:80 -- {rewrite} --> zope:8080

what i need to do is put squid caching in between them, so i'll have:
[internet] --> apache:4000 --> squid --> zope:8080

I've tried various configs with squid, and just can't get it running at all.
The squid logs give stuff like:
 127.0.0.1 TCP_DENIED/400 1574 GET /http/zopetest/80/error/HTTP_BAD_REQUEST.html.var - NONE/- text/html

since apache is listening on 80, does squid listen on that?
or does it go like this:
apache:80 -> {rewrite} -> squid:3128 -> {rewrite} -> zope:8080

urgh! i'm really stuck on this one. getting apache -> zope rewriting was easy enough though :) 

any thoughts?
thanks for reading

---

### Post by turinglabs on 2007-05-25
I think the easiest way to do what you want is with a squid reverse proxy - see [http://www.visolve.com/squid/whitepapers/reverseproxy.php](http://www.visolve.com/squid/whitepapers/reverseproxy.php) for config details. It will cache inbound web requests for you, and relay them to apache as needed. A nice benefit of this is that you can move the apache and zope servers off-box at some point in the future if load gets too high.

With this setup, you can keep your existing rewrite rules. You'll just have to change the apache port to 81, or something unused:

[internet]->squid:80 -> apache:81-> {rewrite} ->zope:8080

---

