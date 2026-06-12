---
title: "how to set up private web proxy - Ubuntu 10.04 server"
date: 2011-11-02
forum: Server Platforms
---

### Post by NathanScrivener on 2011-11-02
Hi there,

I have a Xen VPS running Ubuntu 10.04 which I use to serve up a couple of websites. The server is located in California.

I personally am based in New Zealand. My home internet connection has a static IP address.

How would I go about setting up a private web proxy on my server that only allows connections from my home IP address?

The objective is to be able to access websites that are geo-restricted.

Thank you in advance.

Nathan

---

### Post by dixon on 2011-11-02
It's very simple. Just use ssh socks proxy.

Ssh -D 8080 username@sshserverip

Then just use localhost:8080 proxy. Tip: I use proxy switchy extension for google chrome, when one can choose for which sites the proxy should be used. Hope it helps. Sry for formatting I'm posting from my cell phone...

---

### Post by Lars Noodén on 2011-11-02
+1 for the suggestion of a SOCKS proxy. 

Otherwise, you'll have to set up either Squid or Varnish.  Neither are that difficult to get configured but it is still a lot more than the one-liner needed for SOCKS.

---

### Post by NathanScrivener on 2011-11-02
Thank you. It was a little more difficult to access from my windows box as I had to install copssh (putty confused the hell out of me). Got it working though.

---

### Post by dixon on 2011-11-04
Glad it worked. Just FYI with putty it also isn't that difficult.
```
putty.exe -D 9853 username@sshhost
```

---

