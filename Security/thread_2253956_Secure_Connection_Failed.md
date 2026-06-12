---
title: "Secure Connection Failed"
date: 2014-11-23
forum: Security
---

### Post by pfeiffep on 2014-11-23
I am perplexed by the ambiguity with different browsers of this message received using FireFox 33.0 on Ubuntu  accessing a particular site.
> Secure Connection Failed

An error occurred during a connection to xxxxxxxxxxxxxxxxxxxxxxxx Peer's Certificate has been revoked. (Error code: sec_error_revoked_certificate)

    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
    Please contact the website owners to inform them of this problem.
I tested the same site with similar results using:[INDENT]Chrome on Windows 7
Internet explorer on Windows 7
Safari on Mac 
[/INDENT]
 
Using Chrome 39.0 and Chromium 38.0 on Ubuntu I was immediately provided login prompt which is the expected response. 

I'm installing Safari on my Ubuntu installation now and will post again with results.

_[SIZE=5]Update[/SIZE]_
[COLOR=#ff0000]Safari via wine failed to identify the certificate issue[/COLOR]

**Opera did identify the certificate issue**

So what's the real issue here with Chrome and Chromium on Linux (since the Safari failure is running on wine via playonlinux I don't place much weight on the failure) ?

---

### Post by untrustytahr on 2014-11-24
> **pfeiffep said:**
> ...So what's the real issue here with Chrome and Chromium on Linux...

   The problem is there is no great standard on how to check certificate revocation status (CRL, OCSP, OCSP stapled) and what to do if check fails (hard-fail, soft-fail). It's been a known issue for a while.  As always, it's a trade-off between being secure vs usability.
 

 This topic came up again during the “Heartbleed” debacle a few months ago... presumably due to all the revoked certificates that were hitting the web.  I heard that the browsers were moving to a “must-staple” model.

---

### Post by pfeiffep on 2014-11-24
This morning the site seems to be OK as tested with FireFox on Ubuntu and Internet Explorer on Windows 7. 

Since this occured on a Sunday and it is NOT a commercial site I suspect a slight mistake was made during a maintenance window. 

I'm happy the I discoverd this anomoly in Chrome & Chromium running on Ubuntu since I use Ubuntu exclusively for all my financial transactions. I have already switched my default browser to Fire Fox and have adopted a personal policy to not log into any site henceforth using Chromium or Chrome on Ubuntu.

I did notice that FF seems a bit sluggish compared to Chromium

---

