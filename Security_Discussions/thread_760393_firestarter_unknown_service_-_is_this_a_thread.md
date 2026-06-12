---
title: "firestarter unknown service - is this a thread?"
date: 2008-04-20
forum: Security Discussions
---

### Post by tommyhakinen on 2008-04-20
Hi,

I saw an unknown service on firestarter event.
this is the source name "ae-73-73.ebr3.LosAngeles1.Level3.net" when i look for hostname. it's under ICPM protocol. what is this? Is it a thread or something? The IP address was 4.69.137.xx with xx varied.

---

### Post by rickyjones on 2008-04-20
> **tommyhakinen said:**
> Hi,

I saw an unknown service on firestarter event.
this is the source name "ae-73-73.ebr3.LosAngeles1.Level3.net" when i look for hostname. it's under ICPM protocol. what is this? Is it a thread or something? The IP address was 4.69.137.xx with xx varied.

Are you sure the protocol wasn't "ICMP"?

ICMP is the protocol that "ping" uses... so most likely that event is in response to a ping request.

-Richard

---

### Post by tommyhakinen on 2008-04-20
yes. it's ICMP protocol but an unknown sevice. a ping request? so it was not a thread or intruder, right?

---

### Post by rickyjones on 2008-04-21
> **tommyhakinen said:**
> yes. it's ICMP protocol but an unknown sevice. a ping request? so it was not a thread or intruder, right?

If it was an intruder then I'm pretty sure your firewall blocked it. But last I checked the only traffic that uses the ICMP protocol is PING... and unless they are using PING to DDOS you then you have nothing to worry about.

-Richard

---

### Post by tommyhakinen on 2008-04-21
Thank you very much. Is there anything than firewalls we need on linux for security? I read on Linux Format mentioning about Intruders Detector.

---

### Post by rickyjones on 2008-04-22
> **tommyhakinen said:**
> Thank you very much. Is there anything than firewalls we need on linux for security? I read on Linux Format mentioning about Intruders Detector.

I'm not the complete expert on Linux security but it really depends on your configuration and the role that your server/workstation provides.

My advice? Sit behind a hardware firewall (a simple Linksys router would suffice). Use strong passwords, at least 7 characters using letters and numbers. Keep all your software up-to-date.

Beyond that may be overkill for your situation. Example, a home user would be fine with the above protocols. A business user may need more, for example they might wish to install an intrusion detection system on the network.

I hope this helps!

-Richard

---

### Post by tommyhakinen on 2008-04-23
okay. Thank you very much for the advices.

---

