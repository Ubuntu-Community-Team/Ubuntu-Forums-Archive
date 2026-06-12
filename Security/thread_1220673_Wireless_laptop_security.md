---
title: "Wireless laptop security?"
date: 2009-07-23
forum: Security
---

### Post by rfLarke on 2009-07-23
Okay so, I recently set up UFW (using GUFW) on my Ubuntu Jaunty Laptop out of paranoia, but I'm very unfamiliar with any of this stuff.

First problem that comes to mind is, it wouldn't let me access my Windows Desktop's wireless network. So what I did was set this rule in UFW:

```
ufw allow from 192.168.2.101 to any 
```

The IP address being my Windows Desktop's Local Network Address. So here's my concern: Wouldn't this mean that ANY computer with an IP of 192.168.2.101 has the doors open on my Laptop? (EG connected to an arbitrary network while on the roam)

Second question (unrelated to UFW): I just set up SAMBA fully so I can Wirelessly share files from my Laptop (As opposed to JUST connecting to my Windows machine to transfer files). I'm just a bit concerned that someone could access my laptop remotely via SAMBA now, so is there any security I need to implement, or would such a person be strictly confined to the shares I have set up?

That's all, Thanks for the help guys!

---

### Post by bacil on 2009-07-23
Answer is yes any coputer with given IP will have access to any services on your laptop.

With samba it depends on how you have it set up. you can have users allowed only to given shares or even use fakeroot so tey will not be able to even see your directory structure.

But i dont think you should be concerned this much about this. i have been traveling with my laptops and never had this problem (i meen being attacked or even tried)

---

### Post by rfLarke on 2009-07-23
Ah okay. Thanks! Out of curiosity, though, IS it possible to set the rule a bit more specifically so I can allow JUST my Windows machine and no other?

---

### Post by brian_p on 2009-07-23
> **rfLarke said:**
> Ah okay. Thanks! Out of curiosity, though, IS it possible to set the rule a bit more specifically so I can allow JUST my Windows machine and no other?

Iptables has a MAC module.

Your favourite search engine: iptables mac

---

