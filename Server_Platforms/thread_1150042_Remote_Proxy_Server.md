---
title: "Remote Proxy Server"
date: 2009-05-05
forum: Server Platforms
---

### Post by oxsyn on 2009-05-05
I'd like to set up a remote proxy server at home running https for secure browsing from remote locations.

I.E. I'd like to be able to browse to [https://myhomedomain/proxy/](https://myhomedomain/proxy/) (this would provide a secure https tunnel) and be able to browse from that page to other pages on the internet w/o worrying about my **** being snooped.

Yes, I know that I can use openssh and shove my http traffic through an ssh tunnel.  That's not what I'm looking for.

Not sure what solutions are available.  Is this something squid could be used for?

---

### Post by Dr Small on 2009-05-05
Something like setting up Apache, Php, SSL and setting up [bblocked](http://www.bblocked.org/), sound plausible?

Of course, there are other web based proxies (that you can install and run on your system) out there too.

---

### Post by oxsyn on 2009-05-05
> **Dr Small said:**
> Something like setting up Apache, Php, SSL and setting up [bblocked](http://www.bblocked.org/), sound plausible?

Of course, there are other web based proxies (that you can install and run on your system) out there too.

That's beautiful, thanks dude.  Exactly what I was looking for.  Also, for anyone else researching this, here are other options I stumbled on earlier:

[http://www.ghacks.net/2006/04/07/setting-up-your-own-proxy-server/](http://www.ghacks.net/2006/04/07/setting-up-your-own-proxy-server/)

---

