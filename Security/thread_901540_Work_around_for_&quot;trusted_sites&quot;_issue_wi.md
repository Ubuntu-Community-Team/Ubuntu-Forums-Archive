---
title: "Work around for &quot;trusted sites&quot; issue with OpenSSL?"
date: 2008-08-26
forum: Security
---

### Post by strife303 on 2008-08-26
Hey!

Followed a fantastic guide to getting SSL going and giving myself some certificates: 
[http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)

Unfortunately the latest browser (IE7 and FF3) are displaying gigantic error messages on the sites because the certificates are self-signed. Is there a way to get around this, or does everyone just pony up the money for VeriSign?

Thanks.

---

### Post by cdenley on 2008-08-26
The error message is there for a good reason. Anyone can make a self-signed certificate, so how do people know they're actually sending their data to you? It sort of defeats the purpose of using SSL encryption for first-time visitors. If there were a "way to get around this", then it would be exploited to trick people into giving away login credentials without warning.

---

### Post by Dr Small on 2008-08-26
Self-signed certificates are signed by you, not by some company, organization, or certificate authority. Naturally, the browser is going to display a big warning that the site you are attempting to connect to is not Authorized by an authority, and could be a fake site collecting your information.

Of course, this isn't the case for alot of folks who just want encryption to their website without paying for an authorized certificate.

Basically, there is no way around the errors (server side).

Dr Small

---

