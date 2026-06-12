---
title: "Secure Device Protocol"
date: 2011-03-21
forum: Security
---

### Post by emiller12345 on 2011-03-21
I detected an &quot;attack&quot; this morning on my cable modem, but for the life of me I can't figure out what the fell is going on. UDP packets started showing up at my modem from port 32388 to port 3432 which is &quot;OSDCP / Secure Device Protocol&quot;. The data portion of the packets increases from 0x00040001 to 0x00040008. I can not find any reference to this protocol anywhere on the internet, nor can I find any software that might use it. Has anyone ever heard of this?

---

### Post by nevius on 2011-03-21
> **emiller12345 said:**
> I detected an &quot;attack&quot; this morning on my cable modem, but for the life of me I can't figure out what the fell is going on. UDP packets started showing up at my modem from port 32388 to port 3432 which is &quot;OSDCP / Secure Device Protocol&quot;. The data portion of the packets increases from 0x00040001 to 0x00040008. I can not find any reference to this protocol anywhere on the internet, nor can I find any software that might use it. Has anyone ever heard of this?

Might be a UDP port scan, but it doesn't really make any difference whether it is or not. My router's firewall reports port scans all the time. There's nothing you can do to stop them. Just keep up with security updates. Read the security sticky. Learn to stop worrying and embrace the bomb. Or something like that.

---

### Post by emiller12345 on 2011-03-21
This was directed at my Cable Modem of all things, not my router or firewall.  It was directed at the MAC address of the cable modem, which I don't believe has an IP address anyway, let alone port numbers to connect to, but how they got my CM MAC address is a little discerning. They tried an IP address that is common to my ISP, and a single port number that I'm not familiar with (3432). I was wondering if it was some special service that someone else knows about. IANA has registered it but has no other information on it other then the name.

---

