---
title: "Authentication in LAN? (Prevent impersonating IP in LAN)"
date: 2012-06-13
forum: Security
---

### Post by codell on 2012-06-13
I have a gateway with a few clients.

It's compulsory that the clients can not spoof their LAN IP's.

What's the most simple authentication mechanism for LAN's? Encryption is not necessary (but ok) and MITM in LAN is also not possible.

I simply want to ensure that once a client has been compromised he can not pretend to have another IP.

---

### Post by spynappels on 2012-06-13
You could start by doing some reading of ARP spoofing and seeing how this can be avoided, I'm not sure how you would prevent this in practise though...

---

### Post by movieman on 2012-06-15
IPSEC. It's very hard to spoof but it's far from simple to set up.

Note that they could still fake an IP address -- anyone can do that -- but they won't be able to talk to any other machines since they won't have the correct key to authenticate with.

---

### Post by codell on 2012-10-23
Static ARP entries will work.

---

### Post by samiux on 2012-10-23
> **codell said:**
> I have a gateway with a few clients.

It's compulsory that the clients can not spoof their LAN IP's.

What's the most simple authentication mechanism for LAN's? Encryption is not necessary (but ok) and MITM in LAN is also not possible.

I simply want to ensure that once a client has been compromised he can not pretend to have another IP.

I agreed with codell.  If you router can configure to static ARP, it is the better solution to the ARP Spoofing.

One of the threat in the LAN is the ARP Spoofing.  You can prevent it by following [this tutorial]("http://samiux.blogspot.com/2012/06/howto-protect-you-from-being-arp.html").

Samiux

---

