---
title: "How to use my Server to Proxy Chain"
date: 2010-02-26
forum: Server Platforms
---

### Post by HereSomeHow on 2010-02-26
Hi, I hope can put in words waht I need to do:

I'm running a console only Ubuntu file server in my blding at work, to serve a bunch of Windows machines. It is running fine, with Samba and a FTP service.

It's in the corporate network, in which we use a SOCKS 5 proxy (or something similar, I don't run it, it's way beyond my reach) that uses simple user/password authentication (not NTLM nor anything fancy).

What I want to do, is to setup my server with squid, and re-route all the windows machines to it, and let Ubuntu handle the authentication with the coporate server, making all the windows machines access the internet without needing to supply user/password each time they open a browser, and also making some proxy-unaware apps run, like the blackberry desktop, which can't synch if it's not internet direct.

The corporate proxy already has a brutally convoluted and big as hell set of rules to negate access to the internet to apps and pages not suited to office work :) so the setup in my server doesn't need to check for anything else, only redirect, cache and authenticate with the corporate proxy.

Is it possible to do it? and what should I config or set up in Squid in my server? I've already spent a few hours googling but can't find anything intelligible (for me) to do it.

Any help appreciatted. Thx.

---

