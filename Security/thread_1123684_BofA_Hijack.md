---
title: "BofA Hijack?"
date: 2009-04-12
forum: Security
---

### Post by Xamiga on 2009-04-12
It appears Bank of America may be hijacked:  

I just got data being sent thru 

bankofamerica.via.infonow.net

Can anyone check this out?

---

### Post by HermanAB on 2009-04-12
No, that was simple spoof.  The domain is infonow.net

Some suckers my fall for it though.

---

### Post by Xamiga on 2009-04-13
thanks.
Using FF3.5.

so a 'simple spoof' is accomplished how?  I start my banking by clicking on a https bookmark, every page i see is verified as being [https://*.bankofamerica.com](https://*.bankofamerica.com), but my pdnsd cache shows I'm going to bankofamerica.via.infonow.net.  Seems like that meand my ISP's dns is comprimised.

---

### Post by cdenley on 2009-04-13
> **Xamiga said:**
> thanks.
Using FF3.5.

so a 'simple spoof' is accomplished how?  I start my banking by clicking on a https bookmark, every page i see is verified as being [https://*.bankofamerica.com](https://*.bankofamerica.com), but my pdnsd cache shows I'm going to bankofamerica.via.infonow.net.  Seems like that meand my ISP's dns is comprimised.

Based on your vague original post, I think he assumed it was a phishing scam. If you were a victim of DNS poisoning, and [https://*.bankofamerica.com](https://*.bankofamerica.com) was being spoofed, then you would receive a warning about the SSL certificate not being signed by a trusted certificate authority.

It appears the second page you mention, bankofamerica.via.infonow.net, is a third party tool B of A redirects to for users to locate ATM's and banks.
[http://www.bankofamerica.com/locator/](http://www.bankofamerica.com/locator/)
There doesn't appear to be anything malicious going on.

---

### Post by Xamiga on 2009-04-13
Thanks.
Seems my paranoia may be being fed by Firefox 3.5 and its dns preload feature!!!

---

