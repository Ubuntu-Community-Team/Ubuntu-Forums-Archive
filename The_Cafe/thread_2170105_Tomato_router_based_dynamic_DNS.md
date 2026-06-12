---
title: "Tomato router based dynamic DNS"
date: 2013-08-24
forum: The Cafe
---

### Post by SchnappiJedi on 2013-08-24
Does anyone use a Tomato router based dynamic dns service? If so has it worked well for you? 

I am more concerned with the reliability of the Tomato router rather than the dynamic dns provider.

---

### Post by pqwoerituytrueiwoq on 2013-08-24
You mean [tomato firmware](http://www.polarcloud.com/tomato) right?
I am using it, DDNS via dyndns.com, configured on the router. I have not had any issues except that dyndns has changed policies so to keep my free account i have to login once a month

---

### Post by SchnappiJedi on 2013-08-25
Yes, I do mean tomato firmware. Thanks.

You are using the standard firmware and not a VPN (or other) modification, correct?

---

### Post by papibe on 2013-08-25
> **pqwoerituytrueiwoq said:**
> dyndns has changed policies so to keep my free account i have to login once a month
Annoying, isn't it? Any way, they provide good service.

@schnappi2, there is also a Linux package you can use (ddclient). It is set as a service, and works with most DNS providers. You would need a server, or a 24/7 machine in order to work properly.

Regards.

---

### Post by SchnappiJedi on 2013-08-25
> **papibe said:**
> Annoying, isn't it? Any way, they provide good service.

@schnappi2, there is also a Linux package you can use (ddclient). It is set as a service, and works with most DNS providers. You would need a server, or a 24/7 machine in order to work properly.

Regards.

I was never able to get ddclient to work with freedns.afraid.org

---

