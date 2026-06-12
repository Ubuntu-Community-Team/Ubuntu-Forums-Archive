---
title: "question about DHCP TTL"
date: 2010-03-16
forum: Security
---

### Post by jacksmash on 2010-03-16
Just wondering if there is anyway that I can tell the TTL on the IP address that is currently assigned to me by my ISP? I'm behind a router... if that helps.

Cheers.

---

### Post by cdenley on 2010-03-16
It depends on your router.

---

### Post by jacksmash on 2010-03-16
> **cdenley said:**
> It depends on your router.

Ok?

---

### Post by cdenley on 2010-03-16
> **jacksmash said:**
> Ok?

The IP assigned from your ISP is leased to your router. That lease contains an expiration date. Your router has the expiration. How or if that information can be obtained from your router varies from one router to the next.

---

### Post by jacksmash on 2010-03-16
> **cdenley said:**
> The IP assigned from your ISP is leased to your router. That lease contains an expiration date. Your router has the expiration. How or if that information can be obtained from your router varies from one router to the next.

Ok, just wondering if there was a way i could tell from the command line. I found the DHCP info on my router, but it only shows the IP address, nothing else.

---

### Post by cdenley on 2010-03-16
> **jacksmash said:**
> Ok, just wondering if there was a way i could tell from the command line. I found the DHCP info on my router, but it only shows the IP address, nothing else.

If your computer had the lease, then it would be possible. However, since your router is the only system that received the lease, you must pull that information from the router somehow, and I don't know of any standard way.

---

### Post by terazen on 2010-03-17
Depending on the isp you can possibly take your router out and plug your modem directly into the pc.

---

