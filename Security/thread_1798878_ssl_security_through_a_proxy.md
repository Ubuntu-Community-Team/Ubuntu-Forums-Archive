---
title: "ssl security through a proxy"
date: 2011-07-06
forum: Security
---

### Post by wlraider70 on 2011-07-06
Is my ssl connection secure if I'm going through a proxy. Is it possible to craft a malicious proxy to steal/crack authentication?

---

### Post by Dangertux on 2011-07-06
> **wlraider70 said:**
> Is my ssl connection secure if I'm going through a proxy. Is it possible to craft a malicious proxy to steal/crack authentication?

The short answer -- maybe. 

The slightly more complicated answer -- No

The security of your data IMHO comes from the encryption quality ; NOT how far you move it from the source. The same problem with people putting too much trust in Tor or other similar proxies. Anonymity is not equal to security.

So let's take a look at the SSL Tunnel itself, SSL is crackable, anything that uses a public-key cipher is crackable, if the attacker wants to spend enough time getting it. 

Sniffing the traffic to or from a proxy server is only slightly more difficult then sniffing the traffic of a "direct" connection.

Now --  Unless you are transmitting Top Secret Documents, the real question you need to ask, "Is my data reasonably secure?" Only you can answer that question since only you know what it is you're protecting. 

There is not ever going to be a 100% secure method of protecting anything, it's about factoring whether the unlikely potential that it COULD occur is worth accepting. If the answer to that question is no, then it's better to not transmit that data, encrypted or otherwise.

---

### Post by wlraider70 on 2011-07-07
My data is of no real value other then perhaps typical IDE Ty theft email hacking...

My only real concern is that there might be some kind of inherent risk with using a proxy that I don't control. 
My understanding per the earlier post is my ssl is no more or less vulnerable due to a proxy.

---

