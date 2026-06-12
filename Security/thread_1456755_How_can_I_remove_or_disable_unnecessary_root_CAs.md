---
title: "How can I remove or disable unnecessary root CAs?"
date: 2010-04-17
forum: Security
---

### Post by dalesd on 2010-04-17
I'm troubled by the recent discovery that SSL has been compromised by the Packet Forensics device, and would like to remove (or otherwise disable) unnecessary root certificate authorities.  

Disabling them in Firefox is relatively easy.  Does Ubuntu have its own store of root CA certificates?  And if so, how do I disable or remove them?

I found this site, netsekure.com, which shows how to disable them in FF and remove them from Windows, but I haven't found something similar for Ubuntu.

Links:
[http://netsekure.org/](http://netsekure.org/)
[http://www.wired.com/threatlevel/2010/03/packet-forensics/](http://www.wired.com/threatlevel/2010/03/packet-forensics/)
[http://www.crypto.com/blog/spycerts/](http://www.crypto.com/blog/spycerts/)
[http://www.grc.com/sn/sn-243.htm](http://www.grc.com/sn/sn-243.htm)

---

### Post by lovinglinux on 2010-04-17
I think they are stored in Firefox only.

---

### Post by bodhi.zazen on 2010-04-18
> **dalesd said:**
> I'm troubled by the recent discovery that SSL has been compromised by the Packet Forensics device, and would like to remove (or otherwise disable) unnecessary root certificate authorities.  

Disabling them in Firefox is relatively easy.  Does Ubuntu have its own store of root CA certificates?  And if so, how do I disable or remove them?

I found this site, netsekure.com, which shows how to disable them in FF and remove them from Windows, but I haven't found something similar for Ubuntu.

Links:
[http://netsekure.org/](http://netsekure.org/)
[http://www.wired.com/threatlevel/2010/03/packet-forensics/](http://www.wired.com/threatlevel/2010/03/packet-forensics/)
[http://www.crypto.com/blog/spycerts/](http://www.crypto.com/blog/spycerts/)
[http://www.grc.com/sn/sn-243.htm](http://www.grc.com/sn/sn-243.htm)

I would suggest you read this :

In particular see point 5.
[http://www.mail-archive.com/dev-security@lists.mozilla.org/msg00095.html](http://www.mail-archive.com/dev-security@lists.mozilla.org/msg00095.html)

---

### Post by cdenley on 2010-04-19
> **dalesd said:**
> I'm troubled by the recent discovery that SSL has been compromised by the Packet Forensics device, and would like to remove (or otherwise disable) unnecessary root certificate authorities.  


SSL has not been compromised. Someone made a hardware device which performs a MITM attack for SSL connections. People are assuming that the only purpose for such a device being made is if trusted CA's are issuing certificates for domains to law enforcement agencies so they can use this device without targets being warned about self-signed or invalid certificates. Even if this assumption were true, which I doubt, the compromise is with CA's issuing certificates they shouldn't, not the existence of a hardware device which performs an attack which can easily be done with software.

---

