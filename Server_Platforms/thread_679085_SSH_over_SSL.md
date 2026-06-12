---
title: "SSH over SSL"
date: 2008-01-26
forum: Server Platforms
---

### Post by ericbarch on 2008-01-26
Just trying to get some input on the best way to handle my case. Here's what I need to do:

PC #1: I have an Apache2 server with mod_ssl and mod_proxy (AllowCONNECT set to 22) running on port 443 open to the outside world.

PC #2: I need to be able to establish an encrypted tunnel (using SSL) and connect to the SSH server running on PC #1 through this SSL tunnel.

Any input on how to do this would be greatly appreciated. proxytunnel seems that it doesn't work with apache's SSL and I haven't found anything else.

---

### Post by ericbarch on 2008-01-26
From what I've read, proxytunnel will do exactly what I need to do, but Apache's SSL module does not allow CONNECTs. Has anyone heard of a patch for this?

---

### Post by HermanAB on 2008-01-26
stunnel?

---

### Post by Maxtorm on 2008-01-27
> **ericbarch said:**
> PC #2: I need to be able to establish an encrypted tunnel (using SSL) and connect to the SSH server running on PC #1 through this SSL tunnel.

Any input on how to do this would be greatly appreciated. proxytunnel seems that it doesn't work with apache's SSL and I haven't found anything else.

I think I'm missing something here. What do mod_ssl or mod_proxy have to do with establishing an encrypted tunnel to the SSH server? When you connect to the SSH server on PC#1, you are encrypted already by virtue of the SSH server. By default, this will on port 22, but you can change that to whatever you wish and then open that port on the public side of PC#1.

mod_ssl is for serving SSL encrypted web pages and mod_proxy is only of relevance to clients on the local network of PC#1 (unless you're intending to set up a public proxy or a reverse proxy).

---

### Post by yeehawjared on 2008-05-16
are there any recent guides on how to do this?

I've looked for guides for stunnel, corkscrew, and proxytunnel and can't find any clear-cut recent howtos.  Any links so something that'll work in hardy would be greatly appreciated

---

