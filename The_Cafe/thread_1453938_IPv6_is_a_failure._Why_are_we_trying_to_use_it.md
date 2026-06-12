---
title: "IPv6 is a failure. Why are we trying to use it?"
date: 2010-04-13
forum: The Cafe
---

### Post by Luke has no name on 2010-04-13
I read this a while back, and am glancing over it again:

[http://cr.yp.to/djbdns/ipv6mess.html](http://cr.yp.to/djbdns/ipv6mess.html)

It boggles my mind that IPv6 wasn't made to be back-compatible with IPv4. If it had been, or had some intermediate protocol been established with v4 AND v6 compatibility, we would all be on an IPv6 network right now.

Knowing how much trouble this spec would give the world, why wasn't it modified or scrapped? It started in '98. They've had 12 years to fix this issue, and they haven't.

Discuss.

---

### Post by FuturePilot on 2010-04-13
At some point you have to stop being backwards compatible. It just brings tons of extra baggage along inhibiting further advancements. There's a lot of restrictions with IPv4 that IPv6 doesn't have precisely because it isn't backwards compatible.

---

### Post by toupeiro on 2010-04-13
> **Luke has no name said:**
> I read this a while back, and am glancing over it again:

[http://cr.yp.to/djbdns/ipv6mess.html](http://cr.yp.to/djbdns/ipv6mess.html)

It boggles my mind that IPv6 wasn't made to be back-compatible with IPv4. If it had been, or had some intermediate protocol been established with v4 AND v6 compatibility, we would all be on an IPv6 network right now.

Knowing how much trouble this spec would give the world, why wasn't it modified or scrapped? It started in '98. They've had 12 years to fix this issue, and they haven't.

Discuss.

you can run IPv4 and IPv6 protocols simultaneously on the same machine.  Making a single protocol backwards compatibile, when the ultimate problem with IPv4 is running out of address space, is sort of pointless.  Migrate to it over time and use both protocols until you've learned to support IPv6 properly.

---

### Post by the yawner on 2010-04-13
It's not a failure. It's just the transition plans, or lack thereof.

---

### Post by toupeiro on 2010-04-13
> **the yawner said:**
> It's not a failure. It's just the transition plans, or lack thereof.

^ This.

---

### Post by shazbut on 2010-04-14
> **the yawner said:**
> It's not a failure. It's just the transition plans, or lack thereof.

That, and the bandaid solution for IPv4, NAT, worked a little too well and became a bit of a security blanket for a lot of people.

---

