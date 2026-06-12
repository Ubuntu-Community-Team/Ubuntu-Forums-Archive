---
title: "DDoS attacks - Wireshark?"
date: 2009-10-07
forum: Security
---

### Post by Roasted on 2009-10-07
Just curious... regardless of what OS you're on, if your computer is the victim of a DDoS attack and you fire up wireshark and sit idle with nothing downloading, nothing running, etc, would it be obvious through wireshark that you're passing off a high amount of traffic?

---

### Post by psusi on 2009-10-07
Of course...

---

### Post by Roasted on 2009-10-07
> **psusi said:**
> Of course...

Well I just wasn't sure on how crazy wireshark would be barfing out entries.

Like you know when you sit idle you sometimes still see random activity here and there? I wasn't sure if most DDoS attacks were throttled back enough so it wasn't obvious to the user that they are a victim. I just wasn't sure if it would throttle back enough in wireshark to notice.

---

### Post by psusi on 2009-10-07
If it were throttled then it wouldn't be a very effective attack would it?  The whole point is to flood you with more information than your pipes can handle.

---

### Post by Roasted on 2009-10-07
> **psusi said:**
> If it were throttled then it wouldn't be a very effective attack would it?  The whole point is to flood you with more information than your pipes can handle.

I'm not talking about me being the target of the DDoS attack. I know in that situation I'd be hammered. But I'm talking if I'm a victim of being a zombie computer in accordance with a DDoS attack. The point of a DDoS attack is to flood 1 source with as many "clients" as possible. However, at the same token, you don't want the clients to know they're infected, hence why clients are typically throttled back so it's not noticeable, therefore rendering the attack a "power of numbers" type.

So my question was assuming I was a zombie bot infected to be part of a DDoS scheme to attack 1 source. Would I be able to notice in wireshark that I'm a zombie in any way?

---

### Post by PrePenguin on 2009-10-07
Its possible but I would also monitor the size of the packets hence just a routine system ping will not be large packet where hence a DDos attack usually are and are more frequent then something in the background running other then a virus.

---

